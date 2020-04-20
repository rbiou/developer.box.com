---
rank: 2
related_endpoints: []
related_guides:
  - api-calls/permissions-and-errors/common-errors
  - api-calls/permissions-and-errors/rate-limits
required_guides: []
alias_paths: []
category_id: api-calls
subcategory_id: null
is_index: false
id: api-calls/status-codes
type: guide
total_steps: 7
sibling_id: api-calls
parent_id: api-calls
next_page_id: api-calls/request-extra-fields
previous_page_id: api-calls/types-and-formats
source_url: >-
  https://github.com/box/developer.box.com/blob/master/content/guides/api-calls/status-codes.md
---
# ステータスコード

一般的には、Box APIの使用時に受信したHTTPステータスコードの解釈に以下のルールを適用できます。

<!-- markdownlint-disable line-length -->

| HTTPステータス |                                                                                                                                                                                                                               |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `200-299` | Box received, understood, and accepted the API request. The request has either completed or is in the process of being completed.                                                                                             |
| `300-399` | Box received, understood, and accepted the API request, yet the client must take further action in order to complete the request. Often this includes redirect to other URLs.                                                 |
| `400-499` | An client error occurred when handling the request, often because the client either did not provide the right parameters, did not have access to the resources, or tried to perform an action that is otherwise not possible. |
| `500-599` | Box received and accepted the request, but an error occurred within Box while handling it. These errors signify a problem with Box, not a problem with the client's request                                                   |

<!-- markdownlint-enable line-length -->
