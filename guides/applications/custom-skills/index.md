---
rank: 3
alias_paths:
  - /docs/box-skills
  - /page/box-skills-kit
  - /docs/getting-started-with-box-skills
  - /docs/box-skills-1
  - /skills
category_id: applications
subcategory_id: applications/custom-skills
is_index: true
id: applications/custom-skills
type: guide
total_steps: 2
sibling_id: applications
parent_id: applications
next_page_id: ''
previous_page_id: applications/custom-skills/approval
source_url: >-
  https://github.com/box/developer.box.com/blob/master/content/guides/applications/custom-skills/index.md
---
# カスタムスキル

カスタムスキル(Box Skill)とは、Boxにアップロードされたファイルに対してカスタマイズした処理を実行する一種のアプリケーションです。スキルは、サードパーティの機械学習サービスを使用して、Boxにアップロードされたファイルから情報を自動的に抽出しやすくすることを目的としています。

<ImageFrame shadow>

![スキルの例](./images/skills-example.png)

</ImageFrame>

カスタムスキルは、Box管理者がフォルダに対して有効にする必要があります。そうすると、ファイルがフォルダにアップロードされるたびに、イベントがスキルのアプリケーションサーバーに送信されます。その後、このアプリケーションはファイルをダウンロードするか、調査するか、機械学習サービスに渡し、効果的なメタデータをファイルに書き込むことができます。

## 認証方式

カスタムスキルの操作は、各スキルイベントで提供される事前承認済みのAPI資格情報によって簡素化されます。ただし、このような理由により、カスタムスキルでのAPIアクセスは、主にファイルの読み取りとファイルへのメタデータの書き込みに制限されます。

## 承認

カスタムスキルを使用するには、スキルがトリガーされるフォルダに割り当てておく必要があります。

<CTA to="g://applications/custom-skills/approval">
Learn more about approving Custom Skills

</CTA>

## カスタムスキルを使用する場合

アプリケーションが以下のような場合に、カスタムスキルを使用すると最も効果的です。

* Boxにアップロードされたファイルにメタデータの追加のみを行う
* 新しいファイルをアップロードしない、またはその他のAPI呼び出しを実行しない
* 認証を処理する必要なく、機械学習サービスにファイルを渡せるようにする
