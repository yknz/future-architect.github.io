---
title: "Real World HTTPの第3版ができあがりました"
date: 2024/05/13 00:00:00
postid: a
tag:
  - 書籍
  - RealWorldHTTP
  - 出版
  - 書籍
  - O'Reilly
  - HTTP
  - Web
category:
  - Culture
thumbnail: /images/20240513a/thumbnail.jpg
author: 澁川喜規
lede: "ひとえに読者の皆さんが買ってくれたおかげで、Real World HTTPを改訂し、このたび3版を上梓しました。ありがとうございます。"
---

<a href="https://www.oreilly.co.jp/books/9784814400669/">
<img src="/images/20240513a/PXL_20240404_001054780.jpg" alt="" width="1200" height="901" loading="lazy">
</a>

https://www.oreilly.co.jp/books/9784814400669/

ひとえに読者の皆さんが買ってくれたおかげで、Real World HTTPを改訂し、このたび3版を上梓しました。ありがとうございます。2016年ごろから書き始めて、2017年に初版を出版したので、執筆段階からすると8年ほど経過しているのですが、これだけ長くこの本に関わり続けられるというのは、本書を買ってくださるみなさまのおかげです。

今回は、ひさびさに[無料のミニ版](https://www.oreilly.co.jp/books/9784814400836/)も更新しました。本日、このブログと同時にリリースしました。よりミニ版が学習コンテンツとして使いやすくなるように、そもそもブラウザってどんな動きをするの？ というイントロの章をミニ版とオリジナル版に追加しました。

また、オリジナル版だけになりますが、HTTPが単なるブラウザとの通信を超えてプラットフォーム API化していっている流れに合わせて、既存のOpenSocialの話を独立させて、auさんにも取材させていただいてスーパーアプリの話を入れました。本当は他にも内容を教えてくれたけど会社NGが出て、内容は反映したけどお名前を紹介できなかったスーパーアプリもあったりしました。そんな感じで出せない内容もあったのですが、書いていていろいろ刺激を受けることができて楽しかったです（会社がわからない形で文には混ぜてあります）。

あとは、読書会とかで「どこまで読んだ？」がわかりやすいように、この技術ブログを参考に章の最初にアイキャッチ画像をつけるなどしました。その中で何社か問い合わせを（編集の瀧澤さんがして）許諾を取るなどもやりました。一応、著作権がある某章の画像はSNS等にあげないようにお願いします。2章じゃない方。

# AI時代の本のあり方

AI時代になって新しいサービスが雨後の筍の如くリリースされる日々です。最近リリースされたGoogle Gemini Proだと無料でも扱えるトークン数が多くなって、PDFを丸ごと読み込ませるというのがやりやすい時代になりました。おそらく、きっとそのうち、生成AIに要約させたんだろうな、と思われるような読書感想ブログがポツポツ出てくるのだろうな、という気がしています。

先日知り合いから聞いたのは、入力のバリデーションにassertを使った同僚がいた、みたいな話でした。assertはいろんな言語が持っている機能ですが、基本的にあり得ない状況に陥った時にシステムを止めるブレーカーのようなものです。そんでもって、開発中はいいのですが、本番環境になるとassertは取り除かれて動かなくなり、バリデーションが一切存在しないプログラムとして本番稼働することになります。

こういう実際の失敗談を集めた、実装でやってしまうかもしれないミスを先回りして「こういうことやっちゃダメだよ」みたいなのを集めた、親父の小言集としてもっと発展させていきたいな、と思って書いています。これはこのReal World HTTPに限らず、Goならわかるシステムプログラミングでも、（増刷があるなら）実用Goでも、他の翻訳書の脚注部分でもやっていきたいと思っています。

そもそも失敗系の話、あるいは時代が変わって今では不要や非推奨になった機能の話なんかは生成AIに聞いても理解が浅いなと思うことも多いですし、僕のこめた目次より小さい粒度のこだわりの話も、おそらくAIの要約では省かれてしまう部分かなと思います。もちろん、トークンの中には入っているはずなので聞けば出てくるのでしょうけど、人が読むと得られるが、生成AIで楽しようとするとスルーされて得られない情報、みたいな感じになるんじゃないかなと。そういう感じで「AIではなく人間が頑張ることで価値」が得られる演出は今後本を書く上では意識してみようかと思いました。

もちろん、AIを使わないメリットの話だけをするつもりはありません。前書きにも書きましたが、そのうちやってもいいかもと思っていたGo以外のサンプルなんかはAIにお任せすれば一発です。本書ではおそらく読者にしつこいと思われている（かもしれない）ぐらいcurlのコマンドを紹介していますが、curlコマンドって生成AIにHTTPリクエストの情報を構造化して伝えるにはすごい有用なんですよね。ここからRust版のサンプル作って、とか、自分の環境にあわせた読書法というのがやりやすくなりました。クライアントコードだけではなく、このリクエストを受けるサーバーコードを作らせるのも一瞬です。あと、本書はページ数を収めるために（これでも）、機能の概要しか紹介できていない項目もたくさんあります。そういうのは「もっと詳しく教えて」「もっと詳しい解説が書かれているページを教えて」みたいに問い合わせると、より深く理解できると思います。

そのようなAI時代の読書体験がしやすい書籍になっているのでは、と思いますので、ウェブとかHTTPとか興味はないが、新しい体験をぜひしてみたいという人も一人10冊ぐらい買っていただけるとよいのではないかと思います。

# 今後の発展

内容としては大きなところはだいぶ落ち着いたかな、と思います。というのも、初版の時にはまだHTTP/2が策定されたばかりで、HTTP/3はRFCにはなっていなかったものの、その前身のgQUICは存在していましたし、その要素技術のTLS 1.3も策定中でした。2版では策定されたばかりのTLS 1.3を取り上げ、今回はRFC化したHTTP/3を取り上げることができたので、そう言う意味では初版で見えていた未来に辿り着いた、と言う感じはあります。

ウェブの新しい技術として出てくるものは、流行るか流行らないのかがわからないものが数多くあります。SPDYみたいな約束された未来みたいなものは当初から扱っていましたが、本書では基本的に「すでに普及したもの」に限定しています。過去の版では流行ると思って紹介したけど、今回削った内容もぽつぽつあったりします。

技術的にはWebTransportみたいな、本書ではまだ概要しか触れていないものとか、まだまだ書きたい内容はこれからも出てくるはずですが、もともと本書を書く動機となったのは、ウェブサービスのプログラミングをしていて、そのなかで疑問に思って調べた細かくちらばっていた情報をまとめたい、というところからでした。僕自身は初版を書き終えた時点でウェブサービスを作る上で（HTTPの知識不足で）困ることはだいぶ減りましたが、仕事の中でいろいろな人の相談に乗っていて「あ、こういうところでつまづいていたのか」といった内容がどんどんネタ帳に溜まってきて、改訂のタイミングで盛り込む、という感じで版を重ねています。実施、今回増えた内容も、決して新しいから増えたというものだけではありません。

自分自身も別にHTTPの専門家ではないとはずっと思っていますし、ブラウザ実装者の人とかが書いてくれたらいいなー、でも出ないから仕方なく自分で書くか、みたいな気持ちはずっとあったのですが、先日編集の瀧澤さんから「一連のやり取りをみていて、改めてリアルワールドのHTTPに関する本を渋川さんが書かれてる意味がわかる気がする」と言うコメントを（まったく違う文脈の中で）いただきました。

一次資料を読め、一次資料が絶対だ、というのはIT業界ではいろいろなところで聞く言葉ではあります。この本は一次資料ではありません。ほとんどの内容はRFCを読めば書いてありますが、実際にコードを書いていて、周りの若者がハマった内容とか、そういうのを拾い上げて、これから学習していく自分よりも若い人たちが楽して多くの経験が得られる知識の高速道路本にしていきたいという気持ちは持ち続けています。

書籍を読んだら、その感想をブログにして欲しい、みたいな話はよく出版ブログでは見ますが、前述のような方向性で今後も発展させていきたいので、本書の場合は読んでしばらくしたあとに「あー、これが書いてあって役にたったわー」みたいなSNSのつぶやきもありがたいです。あるいは、若者にウェブ技術を教えていて、前述のassertとか、今回追加したredirect/rewriteの話とか、若者がこんな誤解をしていた！ みたいな話も大好物です。Real World HTTPという書名付きでつぶやいてもらえたら拾いに行きます。

# No.1

オライリーには数多くの本がありますが、日本語書き下ろしで3版まで進んでいるのは現在のところ、[Sphinxをはじめよう 第3版](https://www.oreilly.co.jp/books/9784873119830/)と、本書のみになります。もちろん、英語原著で改版の回数が多い本とか、増刷の回数とか、もろもろだともっと上の本もありますし、続巻スタイルだとゼロから作るDeep Learningシリーズパイセンが圧倒的ですが、まあとりあえず（日本語書き下ろしでの改版数がオライリーで）トップタイで日本一、単著だと堂々の日本一ということになります(分野を小さくして一位を作り出すという姑息な手法はビジネス書的なテクでありますが)。どちらの本も編集者は瀧澤さんです。書籍だけでなく、仕事もそうですが、一緒に関われてよかったと思ってもらえるような実績を周りの人には残せたらな、と思っていたので、これも今回良かったな、と個人的に思っている点です。読者の皆さんには関係のない話ではありますが。

# One More Thing...

もう一冊、並行して書いていた[PlaywrightのWebフロントエンドのE2Eテスト本](https://www.amazon.co.jp/dp/4297142201/)も予約を開始しています。知り合いのテスト系の有名な方々にもレビューしてもらったり、こちらも良い経験ができました。こちらの詳細はまた別途他のメンバーが書いてくれると思います。
