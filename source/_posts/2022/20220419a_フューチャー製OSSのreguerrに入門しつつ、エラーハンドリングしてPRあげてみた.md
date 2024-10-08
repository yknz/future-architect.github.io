---
title: "フューチャー製OSSのreguerrに入門しつつ、エラーハンドリングしてPRあげてみた"
date: 2022/04/19 00:00:00
postid: a
tag:
  - Go
  - OSS
  - エラーハンドリング
category:
  - Programming
thumbnail: /images/20220419a/thumbnail.png
author: 村田靖拓
lede: "フューチャー製OSSであるreguerrに入門しようと思います。入門の途中でエラーと遭遇したため、途中からエラーハンドリング編に突入しています。入門祭りということで、エラーハンドリングの一例として「こんな風に考えるんだなー」と思いつつ読んでいただければ幸いです。また、最終的にはエラーハンドリングを元に、OSSへPRを投げています。そういったOSSとの向き合い方を感じて頂くきっかけになれば良いなと思っています。"
---
こんにちは、TIGの村田です。
[春の入門祭り連載](/articles/20220418a/)2日目の本記事では、フューチャー製OSSであるreguerrに入門しようと思います。

入門の途中でエラーと遭遇したため、途中からエラーハンドリング編に突入しています。入門祭りということで、エラーハンドリングの一例として「こんな風に考えるんだなー」と思いつつ読んでいただければ幸いです。

また、最終的にはエラーハンドリングを元に、OSSへPRを投げています。そういったOSSとの向き合い方を感じて頂くきっかけになれば良いなと思っています。

では本編に入っていきます。

# reguerrとは

reguerrはエラーハンドリング向けのソースコードを自動生成してくれるGo製のライブラリです。フューチャーの案件でも採用実績があり、体系的なエラー定義とそれに伴うハンドリングが重要となってくるエンタープライズシステムでの利用に足る機能をreguerrは有しています。

# 入門してみる

## 下準備

まずはフューチャーのGitHubリポジトリ上[reguerr](https://github.com/future-architect/reguerr)のreadmeに沿ってコマンドをインストールします。

```sh
go install github.com/future-architect/reguerr/cmd/reguerr
```

以下のようにヘルプコマンドが実行できればインストール成功です。

```sh
$ reguerr -h
Usage:
  reguerr [command]

Available Commands:
  generate    generate reguerr code
  help        Help about any command
  validate    validate input file

Flags:
  -h, --help   help for reguerr

Use "reguerr [command] --help" for more information about a command.
```

## 自動生成してみる

`generate` コマンドのヘルプを見てみると、-fでインプットファイルを指定すれば良いことが分かります。

```sh
$ reguerr generate --help
generate reguerr code

Usage:
  reguerr generate [flags]

Flags:
      --defaultErrorLevel string   change default log level(Trace,Debug,Info,Warn,Error,Fatal)
      --defaultStatusCode int      change default status code (default -1)
  -f, --file string                input go file
  -h, --help                       help for generate
```

readmeに沿って、以下ファイルをexample.goとして作成します。

```go
package example

import (
	"gitlab.com/future-architect/reguerr"
)

var (
	// No message arguments
	PermissionDeniedErr = reguerr.New("1001", "permission denied").Build()

	// One message arguments
	UpdateConflictErr = reguerr.New("1002", "other user updated: key=%s").Build()

	// Message arguments with label
	InvalidInputParameterErr = reguerr.New("1003", "invalid input parameter: %v").
		Label(0,"payload", map[string]interface{}{}).
		Build()
)
```

そしてexample.goをインプットファイルにして自動生成を実行。

```sh
reguerr generate -f example.go
```

example_gen.goとexample_gen.mdの2つのファイルが作成されます。
goファイルの中身は以下のようになっています。

```go
// generated by reguerr; DO NOT EDIT
package example

import (
        "errors"
        "github.com/future-architect/reguerr"
)

// NewPermissionDeniedErr is the error indicating [1001] permission denied: $err.
func NewPermissionDeniedErr(err error) *reguerr.ReguError {
        return PermissionDeniedErr.WithError(err)
}

// IsPermissionDeniedErr indicates if the passed in error is from the error with code [1001].
func IsPermissionDeniedErr(err error) bool {
        var cerr *reguerr.ReguError
        if as := errors.As(err, &cerr); as {
                if cerr.Code() == PermissionDeniedErr.Code() {
                        return true
                }
        }
        return false
}

// NewUpdateConflictErr is the error indicating [1002] other user updated: key=%s: $err.
func NewUpdateConflictErr(err error, arg1 interface{}) *reguerr.ReguError {
        return UpdateConflictErr.WithError(err).WithArgs(arg1)
}

// IsUpdateConflictErr indicates if the passed in error is from the error with code [1002].
func IsUpdateConflictErr(err error) bool {
        var cerr *reguerr.ReguError
        if as := errors.As(err, &cerr); as {
                if cerr.Code() == UpdateConflictErr.Code() {
                        return true
                }
        }
        return false
}

// NewInvalidInputParameterErr is the error indicating [1003] invalid input parameter: %v: $err.
func NewInvalidInputParameterErr(err error, payload map[string]interface{}) *reguerr.ReguError {
        return InvalidInputParameterErr.WithError(err).WithArgs(payload)
}

// IsInvalidInputParameterErr indicates if the passed in error is from the error with code [1003].
func IsInvalidInputParameterErr(err error) bool {
        var cerr *reguerr.ReguError
        if as := errors.As(err, &cerr); as {
                if cerr.Code() == InvalidInputParameterErr.Code() {
                        return true
                }
        }
        return false
}
```

インプットファイルで定義されたエラーパターンをもとに、それぞれ以下2種の関数が作成されています。

* 引数で受け取ったエラーを、定義した任意のエラーへ変換して返してくれる関数
* 引数で受け取ったエラーが、定義したエラーとエラー内容が一致しているか判定してくれる関数

mdファイルは以下のような内容になっています。エラーが自動的に表形式で整理されるので、各種ドキュメンテーションの際に活躍してくれそうです。

```md
# Error Code List

| CODE |           NAME           | LOGLEVEL | STATUSCODE |           FORMAT            |
|------|--------------------------|----------|------------|-----------------------------|
| 1001 | PermissionDeniedErr      | Error    |        500 | permission denied           |
| 1002 | UpdateConflictErr        | Error    |        500 | other user updated: key=%s  |
| 1003 | InvalidInputParameterErr | Error    |        500 | invalid input parameter: %v |
```

## 自動生成の引数をいじってみる

`generate` コマンドの引数には `--defaultStatusCode` などの可変パラメータが存在していました。次はこちらをいじってみます。

```sh
$ reguerr generate -f example.go --defaultStatusCode 300
$ cat example_gen.md
# Error Code List

| CODE |           NAME           | LOGLEVEL | STATUSCODE |           FORMAT            |
|------|--------------------------|----------|------------|-----------------------------|
| 1001 | PermissionDeniedErr      | Error    |        300 | permission denied           |
| 1002 | UpdateConflictErr        | Error    |        300 | other user updated: key=%s  |
| 1003 | InvalidInputParameterErr | Error    |        300 | invalid input parameter: %v |

```

ステータスコードが指定通りに変更されていることが確認できました。

## エラーハンドリングしてみる

`--defaultErrorLevel` をいじってデフォルトのエラーレベルを変更しようとしたのですが、エラーが出てしまいました。

```sh
$ reguerr generate -f example.go --defaultErrorLevel Info
Usage:
  reguerr generate [flags]

Flags:
      --defaultErrorLevel string   change default log level(Trace,Debug,Info,Warn,Error,Fatal)
      --defaultStatusCode int      change default status code (default -1)
  -f, --file string                input go file
  -h, --help                       help for generate

unknown error level
```

渡している文字列が悪いのか、渡し方が悪いのか、はたまた元のソースコードにバグが存在しているのか。末尾に出ている `unknown error level` がエラーログなので、ソースコードを追って原因を探ってみます。

リポジトリを漁ってみると、[reguerr.goの47行目](https://github.com/future-architect/reguerr/blob/main/reguerr.go#L47)に該当のエラー文言がありました。

```go
func NewLevel(s string) (Level, error) {
	switch strings.ToLower(s) {
	case strings.ToLower(Trace.String()):
		return Trace, nil
	case strings.ToLower(Debug.String()):
		return Debug, nil
	case strings.ToLower(Info.String()):
		return Info, nil
	case strings.ToLower(Warn.String()):
		return Warn, nil
	case strings.ToLower(Error.String()):
		return Error, nil
	case strings.ToLower(Fatal.String()):
		return Fatal, nil
	default:
		return Trace, errors.New("unknown error level")  //ここが47行目
	}
}
```

コマンドの実行引数で渡している `Info` の文字列が `NewLevel` 関数の引数 `s` として渡っていくのだろうと思いますが、このswitch文の中でdefaultに突入、該当のエラーが発生しているだろうと推測されます。

この `NewLevel` 関数自体も呼び元がいるはずなので探ってみると、[cmd配下のroot.go内71行目](https://github.com/future-architect/reguerr/blob/main/cmd/root.go#L71)にて呼び出されていることが確認できました。

```go
var opts []gen.Option
if errLevel != "" {
	level, err := reguerr.NewLevel(errLevel + "Level")  //ここが71行目
	if err != nil{
		return err
	}
	opts = append(opts, gen.DefaultErrorLevel(level))
}
if statusCode != -1 {
	opts = append(opts, gen.DefaultStatusCode(statusCode))
}
```

ここで `--defaultErrorLevel` と `--defaultStatusCode` にて設定された値を処理しているようです。

期待する挙動は、先程のswitch文の中で `strings.ToLower(s)` の値が `strings.ToLower(Info.String())` の値と一致することなのですが、そうなってないようなので何が起きているかもう少し探ってみます。

`NewLevel` のタイミングで各々の値が実際どうなっているのか確認できるようにログを仕込んでみました。

```go
fmt.Printf("[USER]strings.ToLower(s)=%v\n", strings.ToLower(s))
fmt.Printf("[USER]strings.ToLower(Info.String())=%v\n", strings.ToLower(Info.String()))
```

これで再度generateを試してみます。

```sh
reguerr generate -f example.go --defaultErrorLevel Info
[USER]strings.ToLower(s)=infolevel
[USER]strings.ToLower(Info.String())=info
Usage:
  reguerr generate [flags]

Flags:
      --defaultErrorLevel string   change default log level(Trace,Debug,Info,Warn,Error,Fatal)
      --defaultStatusCode int      change default status code (default -1)
  -f, --file string                input go file
  -h, --help                       help for generate

unknown error level
```

ログが出ました。まず、コマンド引数として渡している部分は `infolevel` という文字列になっていました。たしかに `NewLevel` の呼び元で以下のように呼び出していましたね。

```go
reguerr.NewLevel(errLevel + "Level")
```

引数で渡されたエラーレベルの文言に `Level` という文字列を付け加え、それがlowercaseに変換されるのでプログラム上違和感はないです。

ただ、マッチ対象文字列は `level` という文字列を含まないのでこれが原因と考えられます。
試しに `NewLevel` の呼び出し方を以下のように変えてみます。

```go
// level, err := reguerr.NewLevel(errLevel + "Level")
level, err := reguerr.NewLevel(errLevel)
```

以下コマンドで再度generateを実行。エラーなく終了しました。

```sh
reguerr generate -f example.go --defaultErrorLevel Info
```

生成されたマークダウンファイルを覗いてみると、LOGLEVEL部が想定通り `Info` に変わっていることを確認できました。

```sh
$ cat example_gen.md
# Error Code List

| CODE |           NAME           | LOGLEVEL | STATUSCODE |           FORMAT            |
|------|--------------------------|----------|------------|-----------------------------|
| 1001 | PermissionDeniedErr      | Info     |        500 | permission denied           |
| 1002 | UpdateConflictErr        | Info     |        500 | other user updated: key=%s  |
| 1003 | InvalidInputParameterErr | Info     |        500 | invalid input parameter: %v |
```

また、goファイル側ではデフォルトのエラーレベルを変更するinit処理が追加されていることを確認できました。

```go
func init() {
        reguerr.DefaultErrorLevel = reguerr.Info
}
```

## OSSにPRを投げてみる

動作確認を元に以下の変更を加え、[プルリクエスト](https://github.com/future-architect/reguerr/pull/1)を作成しました。
<img src="/images/20220419a/スクリーンショット_2022-04-17_21.19.31.png" alt="Pull Request" width="1138" height="174" loading="lazy">

OSSの挙動でおかしいと思われる点があった際に「このOSS使えねえ！」と騒ぐのではなくissueを起票するかPRをあげよとどこかのエラい人から教わったので、私も例に漏れずそのように行動したいと思います。このPRが少しでも世界平和に繋がることを祈っています。

などと言いつつ、執筆時点(2022.04)でこの修正が全体を鑑みた上でベストなのかどうかは判断しきれていないのが正直なところです。ただ、そこはコードオーナーのレビューに任せ、修正案のたたき台としてこのPRが機能するといいなという気持ちでPRをあげることにします。

# まとめ

さて、今回はフューチャー製OSSであるreguerrに入門しつつ、エラーハンドリングしつつOSSへPRをあげるということに入門してみました。

私のPRがマージされた暁には、本記事で触れているエラーに直面することは無くなるのですが、エラーハンドリングの考え方やOSSとの向き合い方が皆さんの参考になればと思っています。

春の入門祭り連載、次回は戸田さんです。お楽しみに！
