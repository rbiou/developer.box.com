---
rank: 3
related_endpoints:
  - get_files_id
related_guides:
  - representations/thumbnail-representation
  - representations/supported-file-types
required_guides:
  - representations/request-a-representation
alias_paths: []
category_id: representations
subcategory_id: null
is_index: false
id: representations/download-a-representation
type: guide
total_steps: 8
sibling_id: representations
parent_id: representations
next_page_id: representations/thumbnail-representation
previous_page_id: representations/request-a-representation
source_url: >-
  https://github.com/box/developer.box.com/blob/master/content/guides/representations/download-a-representation.md
---
# ファイルレプリゼンテーションのダウンロード

レプリゼンテーションをダウンロードするには、[レプリゼンテーションを選択][select_representation]した際に受け取った`url_template`を使用します。`{+asset_path}`は、レプリゼンテーションの種類に応じて置き換えます。

## ページ割りされたレプリゼンテーション

PDFのようにページ割りされたレプリゼンテーションでは、`{+asset_path}`を目的のページ番号とファイル拡張子に置き換えます(例: `1.pdf`)。

<!-- markdownlint-disable line-length -->

```curl
curl https://dl.boxcloud.com/api/2.0/internal_files/123/versions/345/representations/pdf/content/3.pdf \
  -H "Authorization: Bearer ACCESS_TOKEN"
```

<!-- markdownlint-enable line-length -->

## ページ割りされていないレプリゼンテーション

ページ割りされていないレプリゼンテーションでは、`{+asset_path}`を空の文字列に置き換えます。

<!-- markdownlint-disable line-length -->

```curl
curl https://dl.boxcloud.com/api/2.0/internal_files/123/versions/345/representations/jpg_32x32/content/ \
  -H "Authorization: Bearer ACCESS_TOKEN"
```

<!-- markdownlint-eable line-length -->

## 省略可能なクエリパラメータ

レプリゼンテーションを取得する場合、以下の省略可能なヘッダーを使用できます。

| パラメータ                          | オプション                   | デフォルト  |
| ------------------------------ | ----------------------- | ------ |
| `set_content_disposition_type` | `inline` / `attachment` | `null` |

Sets the `Content-Disposition` header in the API response with the specified
value. A disposition type of `attachment` causes most web browsers to prompt
the user to save the response to their device, where the type `inline`
will open the file in the browser.

指定しなかった場合、応答に`Content-Disposition`ヘッダーは含まれません。

| パラメータ                              | オプション                      | デフォルト  |
| ---------------------------------- | -------------------------- | ------ |
| `set_content_disposition_filename` | Filename without extension | `null` |

Allows the application to define the downloaded representation's file name.

定義しなかった場合、ファイル名は、Box内の元のファイル名から派生し、拡張子はレプリゼンテーションのファイルタイプに置き換えられます。

[select_representation]: guide://representations/request-a-representation
