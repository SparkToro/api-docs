---
title: SparkToro API Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - http

toc_footers:
  - <a href='/account/register?redirect_to=/api/dashboard'>Sign up for an API Key</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the SparkToro API! You can use our API to access SparkToro API endpoints, which can get information which social accounts, websites, podcasts, and YouTube channels influence your query.

We are currently working on getting language bindings in Javascript in the future, for now you can use your favorite http request in the language of your choice.

# Authentication

> To authorize, use this code:

```http
# With shell, you can just pass the correct header with each request
GET https://api.sparktoro.com/authorization
Accept: application/json
Authorization: Bearer your_bearer_key
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.sparktoro.com/authorization"
  -H "Authorization: Bearer your_bearer_key"
```

> Make sure to replace `your_bearer_key` with your API key.

> A valid bearer key will true the following response:

```json
HTTP/1.1 200 OK
Content-Type: application/json

{
  "authorization": true
}
```

SparkToro uses API keys to allow access to the API. You can register a new SparkToro API key at our [API Dashbaord](https://sparktoro.com/api/dashboard).

SparkToro expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer your_bearer_key`

<aside class="notice">
You must replace <code>your_bearer_key</code> with your personal API key.
</aside>

# Audience Intelligence

## Social Accounts

```http
# With shell, you can just pass the correct header with each request
GET https://api.sparktoro.com/search/social
Accept: application/json
Authorization: Bearer your_bearer_key
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.sparktoro.com/search/social"
  -H "Authorization: Bearer your_bearer_key"
```

> The above command returns JSON structured like this:

```json
HTTP/1.1 200 OK
Content-Type: application/json

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

## Domains

```http
# With shell, you can just pass the correct header with each request
GET https://api.sparktoro.com/search/websites
Accept: application/json
Authorization: Bearer your_bearer_key
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.sparktoro.com/search/websites"
  -H "Authorization: Bearer your_bearer_key"
```

> The above command returns JSON structured like this:

```json
HTTP/1.1 200 OK
Content-Type: application/json

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

## Podcasts

```http
# With shell, you can just pass the correct header with each request
GET https://api.sparktoro.com/search/podcasts
Accept: application/json
Authorization: Bearer your_bearer_key
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.sparktoro.com/search/podcasts"
  -H "Authorization: Bearer your_bearer_key"
```

> The above command returns JSON structured like this:

```json
HTTP/1.1 200 OK
Content-Type: application/json

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

## YouTube

```http
# With shell, you can just pass the correct header with each request
GET https://api.sparktoro.com/search/youtube
Accept: application/json
Authorization: Bearer your_bearer_key
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.sparktoro.com/search/youtube"
  -H "Authorization: Bearer your_bearer_key"
```

> The above command returns JSON structured like this:

```json
HTTP/1.1 200 OK
Content-Type: application/json

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

## Results

All results are formated in a similar way to help you process the results. 

```json
{
  "data": [
    {
      "id": "22202",
      "domain": "www.chevrolet.com",
      "meta_description": "Official Chevrolet site: see Chevy cars, trucks, crossovers & SUVs - see photos/videos, find vehicles, compare competitors, build your own Chevy & more.",
      "moz_da": 76,
      "moz_links": 35116,
      "relationships": [
          {
              "type": "facebook",
              "user_id": 66395780,
              "username": "chevrolet",
              "data": {
                  "likes": "22484478",
                  "follows": "22385643"
              }
          },
          {
              "type": "instagram",
              "user_id": 66395780,
              "username": "chevrolet",
              "data": null
          },
          {
              "type": "linkedin",
              "user_id": 66395780,
              "username": "chevrolet",
              "data": null
          },
          {
              "type": "twitter",
              "username": "chevrolet",
              "name": "Chevrolet",
              "user_id": 66395780,
              "followers": 1074055,
              "friends": 19511
          },
          {
              "type": "youtube",
              "user_id": 66395780,
              "username": "user/Chevrolet",
              "data": {
                  "subscribers": 645000,
                  "views": "14509591",
                  "join_date": "2006-01-11",
                  "latest_video": "2020-03-01",
                  "average_views": 9618.7999999999993
              }
          }
      ],
      "share": 4.46
    },
    ...
  ],
  "meta": {
    "source_count": 63484,
    "query": "chevy",
    "type": "keyword",
    "api_limits": {
        "previous": true,
        "used": 6,
        "available": 25
    },
    "query_cost": 0
  }
}
```


