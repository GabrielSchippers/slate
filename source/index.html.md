---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

### API Base

`https://lift.co/api/v2`

The Lift API has many endpoints, or resources. For example `https://lift.co/api/v2/products` where /products is a resource.

GET Queries to most resources include query paramaters to support advanced queries, paging, sorting, population and more.

> An example of an advanced query using query params:

```shell
# Note: We use --data-urlencode to build query paramters and escape quotes for the query properties json string
curl -G "https://staging.lift.co/api/v2/products" \
  --data-urlencode 'query={"__t": "Oil"}' \
  --data-urlencode 'page=1' \
  --data-urlencode 'per_page=2'
```

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: Bearer token"
```

> Make sure to replace `token` with your JSON Web Token.

Some requests required authentication. The Lift API uses JSON Web Tokens. To get a token, we make a POST request to /auth with a valid email and password. On successful authentication the server repsonse body will include a property called token which you can pass the value of in future requests in a standard Authorization: Bearer header.

`Authorization: Bearer token`

<aside class="notice">
You must replace <code>token</code> with your personal API key.
</aside>

# Pagination
GET queries made to the base paths of some resources are wrapped in a paging body. It has the properties `hits`, `page`, `per_page`, `count`, `pages`, where `hits` is an array of matching documents. Responses will not be wrapped in paging bodies when making a `distinct` call, or using `op="count"` or  `op="aggregate"` as these are not regular quieries that can be paged. To remove the paging body and just return an array of matching documents use [`flat`](#flat).

> A paged query returns JSON structured like this:

```json
{
    hits: [...],
    page: 1,
    per_page: 10,
    count: 1000,
    pages: 100
}
```

# Kittens

## Get All Kittens

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

