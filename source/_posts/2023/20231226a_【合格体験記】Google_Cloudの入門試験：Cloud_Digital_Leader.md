---
title: "【合格体験記】Google Cloudの入門試験：Cloud Digital Leader"
date: 2023/12/26 00:00:00
postid: a
tag:
  - 合格記
  - GCP
  - CloudDigitalLeader
category:
  - Infrastructure
thumbnail: /images/20231226a/thumbnail.JPG
author: 村上一彦
lede: Google Cloudの認定資格であるCloud Digital Leader認定資格を受験し、取得することができました。Cloud Digital Leader認定資格の合格に至った学習過程について書いていこうと思います。"
---
<img src="/images/20231226a/IMG_6276.JPG" alt="IMG_6276.JPG" width="509" height="509" loading="lazy">

こんにちは。
公共サービス事業部の村上一彦です。

先日、Google Cloudの認定資格である「Cloud Digital Leader認定資格」を受験し、取得できました。

Cloud Digital Leader認定資格の合格に至った学習過程について書いていきます。

# 筆者のバックグラウンドについて

大学は経営学部で、会計を中心に学んでおりました。その為、ITスキルはほぼゼロに等しい状況でした。

新卒から約3年ほど金融系システム(Java)の業務に従事、1年ほどAWSに触れる機会がありました。しかし、アプリ主体のチームに所属しており、インフラは別チームでしたので、機能を少し知っている程度です。その後、2020年にフューチャーに転職しましたが、クラウドに関わる経験はなく、クラウドに関する経験はほぼゼロの状況です。

他の資格としては、応用情報技術者試験を取得していますが、今回の試験にはほぼアドバンテージはないと思います。

# 試験と出題範囲について

Cloud Digital Leaderの試験は、Google Cloudの認定資格の中でも一番基礎的な試験として位置づけられています。
※ここから公式サイトの抜粋を引用しています。
https://cloud.google.com/learn/certification/cloud-digital-leader?hl=ja

### 推奨される経験

> 技術専門家と連携した経験
技術的な前提条件はありません

自身が技術専門家として従事した業務経験を前提としていない為、私のようにインフラやクラウドが未経験の人でも目指せる資格ということがわかります。

### 試験の形式

>試験時間: 90 分
登録料: $99
言語: 英語、日本語

### 出題範囲

| 内容 | 配点 |
|:-|:-:|
| Google Cloud によるデジタル トランスフォーメーション | 10% |
| データと Google Cloud によるイノベーション | 30% |
| インフラストラクチャとアプリケーションのモダナイゼーション | 30% |
| Google Cloud のセキュリティとオペレーション | 30% |

ざっくり言うと、Google Cloudで提供している各機能の内容と、導入するメリットなどがメインの内容です。

# 学習過程

## 1\. 「図解即戦力 Google Cloudのしくみと技術がこれ1冊でしっかりわかる教科書」の読了

私は、Google Cloudについての予備知識が全くなかったため、まず入門書の「図解即戦力 Google Cloudのしくみと技術がこれ1冊でしっかりわかる教科書」を読みました。

この本については、他の方が詳しく紹介されていますので、ぜひお読みいただければと思います。

>フューチャー技術ブログ「Google Cloudのしくみと技術がしっかりわかる教科書を読んだ感想」
https://future-architect.github.io/articles/20230302a/

こちらの本は入門書なので読みやすかったです。試験の対策としては、一部カバーしていない部分はありますが、次で紹介する模擬試験でカバーできるので、問題ありませんでした。

模擬試験がメインの試験対策になるため、本の内容は熟読せずに流し読みでも問題ないです。私は１周流し読みしました。4時間くらいかかりました（細かい記載は飛ばしました）。

## 2\. Udemyの模擬試験の反復

Udemyにて、こちらの模擬試験を購入し反復しました。

>GCP：Google Cloud Digital Leader模擬試験問題集（6回分320問）
https://www.udemy.com/course/google-cloud-digital-leader6320/

模擬試験は6回分収録されていますが、私は勉強時間が取れず、5回までを2周しました。

1周目を解いた後、模擬試験の解説をしっかり読み、わからない箇所については、先述の入門書に戻ったりもしました。そのように振り返りをすることで、1周目は40～50点でしたが、2周目では80点以上を取れるようになりました。

おすすめはできませんが、正直、理解を後回しにして、模擬試験の繰り返し学習で、反射的に問題を解けるようになるだけで、合格点を出せるのではないかと思います。

見直し時間も含め、20時間くらいかかりました。

### 模擬試験のいい点

- 本試験の内容をカバーしている。
- 本試験と似たような形式で出題される。
- 解説が非常によく、間違いの選択肢がなぜ誤りかも書いてあるため、腕試しという意味よりも、インプット学習に使用できる内容でした。

### コツ

- 各サービスとキーワードの組み合わせを覚える。
- メインの機能がどのように拡張できるか(できないか)を理解する。
- 非推奨サービスは正答にならない。(経験則)
- 計算問題は答えを覚える（理由は後述）

# 試験当日

試験は近くのテストセンターで受験しました。

**ここで問題だったのが、会場内に筆記用具が持ち込めず（貸し出しもNG）、計算問題を暗算でやるしかありませんでした。**

試験時間は30分以上残して終了しましたので、時間配分はそれほど意識しなくても問題ないと思います。

# さいごに

初めてのGoogle Cloudの認定資格の試験でしたが、業務経験を問わず、丁度いい内容と難易度だと思いました。試験内容が技術に寄りすぎておらず、「Google Cloudにはどんなメリットがあるか」ということを理解できたので、私のように、インフラエンジニアではない人にも、生かしていける知識だと思いました。

また、AWSやAzureなど、他のクラウドサービスにもGoogle Cloudにあるような機能がある為、クラウド全般の入門としてもいいと思いました。

これからクラウドの知識やインフラの知識を身に着けたい人のスタートに良い試験だと思います。ぜひ受験してみてください！
