---
rank: 3
related_endpoints:
  - get_files_id_content
related_guides:
  - downloads/file
  - uploads/direct/file
required_guides: []
related_resources: []
alias_paths: []
category_id: downloads
subcategory_id: null
is_index: false
id: downloads/get-url
type: guide
total_steps: 6
sibling_id: downloads
parent_id: downloads
next_page_id: downloads/folder
previous_page_id: downloads/file-version
source_url: >-
  https://github.com/box/developer.box.com/blob/master/content/guides/downloads/get-url.md
---
# ダウンロードURLの取得

Box公式SDKでは、ファイルのダウンロード時にバイナリデータが返されます。代わりにデータのダウンロードURLを取得する場合は、SDKの以下のメソッドを使用します。

<Samples id="get_files_id_content" variant="get_url">

</Samples>

## ダウンロードURLの有効期限

このダウンロードURLは、ファイルのダウンロードを許可するためにユーザーのブラウザに渡すことができますが、このURLが期限切れになった後でダウンロードするには再度リクエストする必要があります。ほとんどの場合、ダウンロードURLは15分間有効です。その後、新しいURLをリクエストする必要があります。この有効期限は、事前の通知なしに変更される場合があります。

[api]: e://get_files_id_content
