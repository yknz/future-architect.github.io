---
title: "Engineer Camp 2022（プロパンガス配送計画の最適化に向けた数値データ解析）参戦記"
date: 2022/09/14 00:00:00
postid: a
tag:
  - インターン
  - インターン2022
category:
  - Culture
thumbnail: /images/20220914a/thumbnail.jpg
author: 荒木太一
lede: "みなさん、こんにちは！Future Engineer Camp 2022に参加いたしました、荒木です。本インターンに参加した経緯やそこでの学びについてお話ししたいと思います。元々、以下のような基準でインターンシップを探していました。"
---

<img src="/images/20220914a/gas-burner-g16bcb7cba_640.jpg" alt="" width="640" height="427">

みなさん、こんにちは！ Future Engineer Camp 2022に参加いたしました、荒木です。
本インターンに参加した経緯やそこでの学びについてお話ししたいと思います。

## 参加した動機

元々、以下のような基準でインターンシップを探していました。

1. **バックエンド開発に触れられる**
1. **できればGo言語を使いたい**
1. **長期**

この条件を満たすプロジェクトがFuture Engineer Camp 2022に奇跡的にあり、友人からの誘いもあって、あまり何も考えずに応募しました。

## 参加する前の自分のスキルセット

私のインターン参加前のスキルセットは以下です。

* **フロント: HTML,CSS,JavaScript,PHP**
* **バックエンド: Go**
* **DB: 経験なし**
* **OS: Windows, MacOs, Linux**
* **その他: C, C++, Python**

HTML, CSS, JavaScript, PHPは自分でECサイトを作ったときにガッツリ使用しましたが、それからは使ってないです。私は競プロをやっているのですが、そこではC++をメインで使っています。Pythonは自分でCSを勉強するときに、メインで使用しています。Cは大学の授業で触れましたが、使いにくいので現在は絶縁しています。Goは入門書とProgateを走っただけ、インフラ周りは名前しかわからないという感じでした。

プログラムは書けるけど、開発を知らない典型的な大学生のスキルセットだったと思います。

## 参加させていただいたプロジェクト

Goでの開発を望んでいた私は、「**（10）プロパンガス配送計画の最適化に向けた数値データ解析**」に応募しました。このプロジェクトの内容は、簡単にいえば「**Goを用いてデータ解析やアルゴリズムを構築し、業務の効率化を図る**」というものです。他のテックブログにも記事が載っているので、気になる方はぜひ読んでみてください。

[Future Engineer Campの詳細](/articles/20220606b/#10-%E3%83%97%E3%83%AD%E3%83%91)

## インターン参加までの選考フロー

インターンの選考フローは、**（1） ES提出**  **（2） コーディング試験**  **（3） オンライン面接**の3段階です。みなさんに気をつけていただきたいのは、**（2） コーディング試験**です。難易度的には**AtCoderの茶色〜水色レベル**で、正直大学の授業でプログラムに触れただけでは、かなり厳しいと思います。応募する際は、それなりに言語の仕様や競プロ的な問題でデータ構造とアルゴリズム構築の演習を積んでおくことをお勧めします。オンライン面接では、インターン受け入れ先の人から技術的な質問と、大学時代に頑張ったことや自分の短所、長所などの質問がされます。この辺は友達と練習するなり、場数を踏んでおけばなんとかなると思います。

私の場合ですが、コーディング試験で3分の1程度しか解けず絶望していたのですが、結果は合格、MacBook Pro貸与、フルリモートと開発者にとっては最高の環境を提供していただき、非常に嬉しかったです。

## インターンの内容

初日はプロキシ周りの設定と環境構築をします。プロキシ周りのことはマニュアルが準備されているし、社員の方が優しくサポートしてくださるので、詳しくなくても大丈夫です。プロキシの設定後は、セキュリティの講義やインターン中のルールなどのお話があり、その後GoとDockerの環境構築をします。私の場合はGoの環境構築は経験していたので苦ではなかったですが、一度もやったことないと苦労するかもしれません。違うプロジェクトで環境構築に3日ほどかかっていた人もいたので、その辺はメンターさんと頑張りましょう。テストがパスしたら、環境構築終了、業務開始です！

実際に業務でやったことは以下です。

* Futureが開発したGo-ExcelTestingの改修 ([Go-ExcelTesting](https://github.com/future-architect/go-exceltesting))
* SQLのUPSERT, TRUNCATE処理の改修と一括化
* Googleが開発したgo-cmpの出力形式をプロジェクト要望にそってカスタマイズ
* AWS CLIとGo SDK V2の速度検証
* 必要であれば各プロジェクトのTest実装

業務で用いた技術は以下です。

* 言語: Go, SQL
* DB: PostgeSQL
* インフラ: AWS
* その他: Slack, GitHub

タスクのほとんどはGoを書くことやコードを読んで理解することに時間をあてていました。

## インターン中の1日

ここではインターン中どんな感じで生活していたかをまとめたいと思います。

**10:00〜: 朝会に参加**
私のプロジェクトでは、毎朝「朝会」というものがあります。これは前日の進捗状況と今日やることを報告する会で、私も毎朝参加していました。

**10:30〜: 業務開始**
今日やることをSlackにまとめてスレを立てて、業務を始めます。どうしても手詰まりになれば、メンターさんに泣きつきます。

**13:00〜: 昼休憩**
私の場合は基本的に昼飯と昼寝をここでしてました。休憩の開始時間とかは細かく決められていないので、作業の進捗次第で休憩に入るタイミングは決めていました。

**14:00〜: 業務再開**
ガリガリ頑張ります。

**18:00〜: インターン夕会**
その日の振り返り、先輩方と雑談をします。夕会は割と自由で、業務と関係ない話を先輩方とすることも多々ありました。基本的にみなさんめっちゃ優しいので、色々質問して自分に足りないことを盗むことが大切だと思います。

**〜19:00: 業務終わり**
日報と勤務時間を登録して、その日は終わりです。

## インターンでの学び

ここでは個人的に成長できたと思うことを述べたいと思います。

**・Git、SQLの使い方**
私は個人でもGitを使ってファイルのバージョン管理みたいなことをしていました。個人開発ではブランチの概念を考えたり、コンフリクトが起こることはないですが、集団開発だとそういうことが往々にして起こります。私は実際、コンフリクトを起こして解決できずメンターの方に解決していただきました。このままで終わっては成長につながらないので、週末に自分でGitの本を1冊買って、勉強したことでその後はGit関係のことは全部自分で解決しました。

SQLに関しては、インターン前の私は読み書きすらできなかったのでこれも週末に1冊本を買って、ローカルでPostgreSQLを動かして文法やお作法を覚えました。この2点に関しては、大きく成長したと思います。

**・Go言語**
結論、Go好きです。高機能な使いやすいC言語感があっていいですね。柔軟に自分の考えをコードで書けるので学びやすい言語だと思います。私自身インターンを通してGoに明るくなったと思います。他パッケージから隠すのかどうかを意識したり、変数名の付け方、Goにおける綺麗なコードとは何か、みたいなものを肌感覚として理解できました。

**・ググる力**
のちにも言いますが、AWSやGoのドキュメントは基本全部英語で、これらに関するエラーや実装方針については圧倒的に英語の情報量が多いです。ググるときに日本語だけで検索しないで、Stackoverflowなどで英語で検索すると自分と同じところで詰まっている人がたくさんいるので解決することが多かったです。
英語に明るくなるという1つの目標もできました。

**・コミュ力と開発のお作法**
エンジニアにコミュ力は必須です。自分がどこかで詰まってしまったときに、自分の状況を分かりやすく相手に伝える必要があります。自分がどこまで調べたのか、どのようなエラーが出ているのか、どのような原因でエラーが出てそうなのか。この辺を相手に伝えることって当たり前に思えて、案外できません。私もできませんでした。インターンを通して、この辺を意識してSlackで質問するようになってから、問題が早く解決するようになりました。

開発のお作法についてですが、ここでは主にPull Request（以下PR）について話します。PRレビューをお願いする際には、Slackにそのリンクを貼るであったり、マークダウンを使って実装の意図を説明するなどといったことが必要です。個人で開発する時は、オープンソースにコミットする時でない限り、PRなんて作らなかったので、インターンに参加することでコミュ力と開発のお作法も短い期間で身につけられたと思います。

## インターンでの振り返り

インターンを振り返ってみて、一番最初に思い出す瞬間は、自分のPRが初めてマージされた時の瞬間ですね。一人で家の中ではしゃいでいました(笑)
どんなに拙いコードでも自分のコードが世の中に出る瞬間は、とても嬉しいものです。初マージの際は、Slackで祝っていただきました！

<img src="/images/20220914a/スクリーンショット_2022-09-13_15.39.06.png" alt="" width="811" height="115" loading="lazy">

インターンを全体的に振り返ると、インターン参加前に得たかった経験は全て得られたと思います。GitやSQL、AWSなどの新しい知識、Goでの実装経験、ドキュメントなどを読みながら実装する経験など、望んでいたもの以上に素晴らしい経験をさせていただきました。毎日８時間働いていましたが、業務が楽しくて毎日があっという間でした。

タスクの難易度は難しいものが多かったです。タスクを実装するために何が必要なのかから自分で調べる必要があったり、リファクタする際には、書かれているコードがどのような挙動をしているのかを理解する必要があります。分からない場合は、積極的にSlackでコミュニケーションをとる必要があるのでプログラミング力だけではなく、自主性や思考力も必要とされたインターンだったと思います。反省点としては、会議を何度かすっぽかしてしまったことです。以後気をつけます。

また、毎週Futureの各部門のスペシャリストの方の講義を聞けたのは貴重な経験でした。COVID-19のワクチン開発にAI技術を用いてアプローチしていたお話は非常に興味深かったです。

## 今後について

AWS周りの知識をインターン後にしっかり学びたいです。GitやDB周りの知識も新たに得たので、オープンソースにも積極的に参加していきたいと思います。
英語にも明るくなれるように頑張ります。

## 最後に

自分の都合により、初日を欠席して参加する形となりましたが、温かく迎え入れていただいて嬉しかったです。
メンターの宮本さんをはじめ、技術的にサポートしていただいたプロジェクトの皆様、毎週懇談をしていただいたHRの皆様、このような貴重な機会をありがとうございました。

アイキャッチの画像は <a href="https://pixabay.com/ja/users/stroganova-2345018/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=6935480">Marina Stroganova</a>による<a href="https://pixabay.com/ja//?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=6935480">Pixabay</a>を利用しました
