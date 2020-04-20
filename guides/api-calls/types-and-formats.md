---
rank: 1
related_endpoints: []
related_guides: []
required_guides: []
alias_paths:
  - /docs/object-model
category_id: api-calls
subcategory_id: null
is_index: false
id: api-calls/types-and-formats
type: guide
total_steps: 7
sibling_id: api-calls
parent_id: api-calls
next_page_id: api-calls/status-codes
previous_page_id: ''
source_url: >-
  https://github.com/box/developer.box.com/blob/master/content/guides/api-calls/types-and-formats.md
---
# タイプと形式

以下のセクションでは、Box API内で使用される可能性があるタイプと形式に関する基本的なコンセプトについて説明します。

## リクエスト

Box APIは、リクエスト本文でJSONを使用します。このルールには注目すべき例外がいくつかあります。

* [`POST /oauth2/token`][post-oauth2-token]はアクセストークンのリクエストに使用され、OAuth 2.0の仕様に従って、コンテンツタイプ`application/x-www-form-urlencoded`で送信される本文を受け入れます。
* [`POST /files/content`][post-files-content]エンドポイントなど、バイナリデータをアップロードするのに使用されるほとんどのAPIでは、コンテンツタイプが`multipart/form-data`のフォームデータとしてデータが送信されることを予期します。

<Message type="notice">

必須ではありませんが、`Content-Type: application/json`のように、送信されるデータのコンテンツタイプを定義するヘッダーを各APIリクエストで渡すことを強くお勧めします。

</Message>

### GZip圧縮

デフォルトでは、Boxから送信されるデータは圧縮されません。帯域幅と応答時間を改善するには、`Accept-Encoding: gzip, deflate`リクエストヘッダーを含めることでAPI応答を圧縮できます。

### 日付と時刻

Box APIは[RFC 3339][rfc3339]タイムスタンプをサポートします。リクエスト内の日付の形式を設定するには、`2013-04-17T09:12:36-00:00`のように時刻をUTCに変換する方法をお勧めします。

タイムスタンプが特定の日に丸められる場合は、時刻部分を省略できます。この場合、`2013-04-17T13:35:01+00:00`は`2013-04-17`になります。タイムスタンプがミリ秒までサポートする場合、予期されるリクエストの形式は`2013-04-17T09:12:36.123-00:00`のようになります。

リクエストを発行する際、タイムゾーンが省略され、時刻が指定されていると、太平洋標準時のタイムゾーンが想定されます。応答では、タイムゾーンが会社の設定に基づいています。これは、管理者が設定したデフォルトのユーザー設定になります。管理対象ユーザーが自分のアカウント設定でタイムゾーンを変更した場合でも、APIによって返されるタイムゾーンには影響しないことに注意してください。

企業のタイムゾーンは経時的に変化するため、タイムゾーンはファイルやフォルダによって異なる場合があります。一般的な例は、夏時間です。標準時に作成された項目のタイムゾーンは、夏時間中に作成された項目とは異なります。このため、APIから返された日付を処理するには、`RFC3339`準拠の日時パーサーを使用することが重要です。

タイムスタンプは、Unixエポック(1970年1月1日)の`00:00:00
UTC`の開始後の日付に制限されます。

## 応答

一般的に、Box APIは応答本文でJSONを返します。このルールにも注目すべき例外がいくつかあります。

* 項目を削除するAPIでは、HTTPステータスコード`204 No Content`とともに空の本文が返されます。
* バイナリデータのリクエストに使用されるAPIでは、バイナリデータが添付されたステータスコード`200 OK`が返されるか、`202 Accepted`が返されるか、またはステータスコード`302 Found`とともに実際のバイナリファイルを指す`Location`ヘッダーのみ(本文なし)が返されます。

<Message type="notice">

`Content-Type`応答ヘッダーを使用すると、APIで返されるコンテンツのタイプがわかります。さらに、各APIエンドポイントの応答タイプについては、APIリファレンスドキュメントで説明されています。

</Message>

### リソース

1つしかリソースが返されない標準的なAPI応答のほとんどは、次の形式に従っています。

```json
{
  "id": "12345",
  "type": "folder",
  ...
}
```

これらのリソースはすべて、常に1つのIDとリソースのタイプを返します。

### コレクション

API応答で複数の項目が返される場合は、コレクションが返されます。これらのコレクションの正確な形式はエンドポイントごとに変わる場合がありますが、一般的には以下の形式になります。

```json
{
  "total_count": 5000,
  "limit": 1000,
  "offset": 2000,
  "order": [
    {
      "by": "type",
      "direction": "ASC"
    }
  ],
  "entries": [
    {
      "id": 12345,
      "etag": 1,
      "type": "file",
      "sequence_id": 3,
      "name": "Contract.pdf"
    }
  ]
}
```

<!-- markdownlint-disable line-length -->

| フィールド         | 必須かどうか? |                                                           |
| ------------- | ------- | --------------------------------------------------------- |
| `entries`     | はい      | コレクション内のエントリのリスト                                          |
| `total_count` | いいえ     | リクエスト可能なコレクション内の合計数。このページの結果数よりも大きくてもかまいません。              |
| `limit`       | いいえ     | オフセットベースのページ割りをサポートするエンドポイントに対して、返される結果の数の制限を指定します。       |
| `offset`      | いいえ     | オフセットベースのページ割りをサポートするエンドポイントに対して、返される結果のオフセットを指定します。      |
| `order`       | いいえ     | 並べ替えをサポートするエンドポイントに対して、結果が返される順番を指定します。                   |
| `next_marker` | いいえ     | マーカーベースのページ割りをサポートするエンドポイントに対して、返すことができる次のページのマーカーを指定します。 |
| `prev_marker` | いいえ     | マーカーベースのページ割りをサポートするエンドポイントに対して、返すことができる前のページのマーカーを指定します。 |

<!-- markdownlint-enable line-length -->

### リクエストID

API呼び出しがエラーで返されると、BoxのAPIから`request_id`フィールドを含むエラーオブジェクトが返されます。

```json
{
  "type": "error",
  "status": 400,
  "code": "item_name_invalid",
  "help_url": "http://developers.box.com/docs/#errors",
  "message": "Method Not Allowed",
  "request_id": "abcdef123456"
}
```

特定のエラーについてサポートに連絡する場合は、サポートチームがリクエストをすぐに見つけられるよう、`request_id`を含むAPI応答全体を提供してください。

<Message type="notice">

ほとんどのAPI呼び出しでは、`BOX-REQUEST-ID`応答ヘッダーも返されます。このヘッダーの値を、エラー応答の本文に含まれる`request_id`値と混同しないでください。

</Message>

### 大きな数値

場合によっては、APIでフィールドに対して極端に大きな数値が返されることがあります。たとえば、フォルダのサイズがテラバイト級のデータまで大きくなった場合、結果として、フォルダの`size`フィールドが、非常に大きな数値になっている可能性があります。

このような場合は、これらの数値は`1.2318237429383e+31`などの[IEEE754][numbers]形式で返されます。

[post-oauth2-token]: endpoint://post-oauth2-token

[post-files-content]: endpoint://post-files-content

[numbers]: https://en.wikipedia.org/wiki/IEEE_754

[rfc3339]: https://www.ietf.org/rfc/rfc3339.txt
