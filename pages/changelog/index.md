---
alias_paths:
  - /docs/api-changelog
centered: true
rank: 0
category_id: changelog
subcategory_id: null
is_index: true
id: changelog
type: page
total_steps: 3
sibling_id: pages
parent_id: pages
next_page_id: changelog/2018
previous_page_id: ''
source_url: >-
  https://github.com/box/developer.box.com/blob/master/content/pages/changelog/index.md
---
<!-- alex disable postman-postwoman -->

# 変更ログ

過去の変更ログについては、[2019](page://changelog/2019)および[2018](page://changelog/2018)のリリースノートを参照してください。

## 2020年2月3日/Preview SDK `v2.34.0`のリリース

Preview SDKのバージョン`2.34.0`がリリースされ、新しいJavaScriptとCSSのPreviewファイルが使用可能になりました。新しい変更を導入するには、Content Preview用のリンクを[UI Elementsの手動によるインストール][ui-elements-manual-install]に関する記事で確認してください。

機能の変更点の全一覧については、`v2.34.0`の[リリースノート][preview-2.34-release-notes]を参照してください。

## 2020年1月22日/Preview SDK `v2.33.1`のリリース

Preview SDKのバージョン`2.33.1`がリリースされ、新しいJavaScriptとCSSのPreviewファイルが使用可能になりました。新しい変更を導入するには、Content Preview用のリンクを[UI Elementsの手動によるインストール][ui-elements-manual-install]に関する記事で確認してください。

機能の変更点の全一覧については、`v2.33.1`の[リリースノート][preview-2.33-release-notes]を参照してください。

## 2020年1月20日/Postmanコレクションとクイックスタートを更新

Box Postmanコレクションは、新機能と、統合されたクイックスタートガイドによって更新されました。主な機能は以下のとおりです。

* エンドツーエンドの[Postmanクイックスタートガイド][postman-quick-start-guide]。これは、ユーザーがPostmanのインストール、Boxアプリの設定、PostmanへのAPI資格情報の読み込みを行う際に役立ちます。
* Box API用に[再編成されたPostmanコレクション][postman-collection]。これにより、API資格情報の期限切れが自動的に検出され、必要に応じてこれらの資格情報を更新するための統合ソリューションが提供されます。

しばらくの間は[従来のPostmanコレクション][legacy-postman-collection]も引き続きご利用いただけます。

[postman-quick-start-guide]: g://tooling/postman/quick-start

[postman-collection]: g://tooling/postman/install

[legacy-postman-collection]: g://tooling/postman/legacy

[ui-elements-manual-install]: g://embed/ui-elements/installation/#manual-installation

[preview-2.34-release-notes]: https://github.com/box/box-content-preview/releases/tag/v2.34.0

[preview-2.33-release-notes]: https://github.com/box/box-content-preview/releases/tag/v2.33.1
