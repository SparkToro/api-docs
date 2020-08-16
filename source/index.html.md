---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the SparkToro API! You can use our API to access SparkToro API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.sparktoro.com/"
  -H "Authorization: Bearer your_bearer_key"
```

> Make sure to replace `your_bearer_key` with your API key.

SparkToro uses API keys to allow access to the API. You can register a new SparkToro API key at our [developer portal](http://example.com/developers).

SparkToro expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer your_bearer_key`

<aside class="notice">
You must replace <code>your_bearer_key</code> with your personal API key.
</aside>

# Audience Intelligence

## Get All Kittens

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: Bearer your_bearer_key"
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

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: Bearer your_bearer_key"
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

## Delete a Specific Kitten

```ruby
require 'SparkToro'

api = SparkToro::APIClient.authorize!('Bearer your_bearer_key')
api.kittens.delete(2)
```

```python
import SparkToro

api = SparkToro.authorize('Bearer your_bearer_key')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: Bearer your_bearer_key"
```

```javascript
const SparkToro = require('SparkToro');

let api = SparkToro.authorize('Bearer your_bearer_key');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

