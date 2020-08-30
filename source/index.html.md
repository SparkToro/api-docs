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
GET https://api.sparktoro.com/search/social?keyword=seo&type=keyword
Accept: application/json
Authorization: Bearer your_bearer_key
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.sparktoro.com/search/social?keyword=seo&type=keyword"
  -H "Authorization: Bearer your_bearer_key"
```

> The above command returns JSON structured like this:

```json
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
    {
      "id": "15651700",
      "account_type": 2,
      "description": "Helping SEOs build innovative organic search strategies with easy-to-use tools, reliable data, and accessible training since 2004.",
      "engagement_score": 21,
      "followers": 555612,
      "friends_count": 3342,
      "global_followers": 895086,
      "location": "Seattle, Washington",
      "name": "Moz",
      "profile_image": "https://pbs.twimg.com/profile_images/1266046550817435649/Sf6PL1GT_normal.png",
      "relationships": [
        {
          "type": "domain",
          "username": "https://moz.com",
          "data": null,
          "clean_domain": "moz.com"
        },
        {
          "type": "facebook",
          "username": "moz",
          "data": {
            "likes": "262699",
            "follows": "271733"
          }
        },
        ...
      ],
      "share": 59.36,
      "sparkscore": 59,
      "tweets_7_days": 22,
      "twitter_social_url": "https://mz.cm/3eKDzck",
      "username": "Moz",
      "verified": 1
    },
    ...
  ],
  "meta": {
    "source_count": 212631,
    "query": "seo",
    "type": "keyword",
    "api_limits": {
      "previous": false,
      "used": 1,
      "available": 500,
      "plan_id": 2
    },
    "query_cost": 1
  }
}
```

This endpoint retrieves all social accounts that have an influence over the search terms sent across.

### HTTP Request

`GET https://api.sparktoro.com/search/social?keyword=seo&type=keyword`

### Query Parameters

Parameter | Description
--------- | -----------
keyword | <strong>string (required)</strong> The keyword, website, hashtag, or social account to search for.
type | <strong>string (required)</strong> There are 5 type of searches that can be done, see <a href="#search-types">Search Types</a> for more info.  
social_gems | <strong>boolean</strong> Display only hidden gems.
follower_max | <strong>integer</strong> Max amount of global followers.
follower_min | <strong>integer</strong> Min amount of global followers.
sparkscore_max | <strong>integer</strong> Max SparkScore (1 to 100).
sparkscore_min | <strong>integer</strong> Min SparkScore (1 to 100).
engagement_max | <strong>integer</strong> Min engagement score (1 to 100).
engagement_min | <strong>integer</strong> Max engagement score (1 to 100).
verified | <strong>boolean</strong> Only display verified account when true.
account_type | <strong>integer</strong> Set to 1 for only individuals, 2 for companies.
popular | <strong>boolean</strong> Include popular accounts when true.

## Websites

```http
# With shell, you can just pass the correct header with each request
GET https://api.sparktoro.com/search/websites?keyword=seo&type=keyword
Accept: application/json
Authorization: Bearer your_bearer_key
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.sparktoro.com/search/websites?keyword=seo&type=keyword"
  -H "Authorization: Bearer your_bearer_key"
```

> The above command returns JSON structured like this:

```json
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
    {
      "id": "41020",
      "domain": "searchengineland.com",
      "meta_description": "News On Search Engines, Search Engine Optimization (SEO) & Search Engine Marketing (SEM)",
      "moz_da": 90,
      "moz_links": 88929,
      "relationships": [
        {
          "type": "facebook",
          "user_id": 1059801,
          "username": "searchengineland",
          "data": {
            "likes": "200464",
            "follows": "206892"
          }
        },
        ...
      ],
      "share": 46.0
    },
    ...
  ],
  "meta": {
    "source_count": 212631,
    "query": "seo",
    "type": "keyword",
    "api_limits": {
      "previous": false,
      "used": 1,
      "available": 500,
      "plan_id": 2
    },
    "query_cost": 1
  }
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://api.sparktoro.com/search/websites?keyword=seo&type=keyword&moz_da_min=50`

### Query Parameters

Parameter | Description
--------- | -----------
keyword | <strong>string (required)</strong> The keyword, website, hashtag, or social account to search for.
type | <strong>string (required)</strong> There are 5 type of searches that can be done, see <a href="#search-types">Search Types</a> for more info.  
web_gems | <strong>boolean</strong> Display only hidden gems.
moz_da_max | <strong>integer</strong> Max Moz Domain Authority (1 to 100).
moz_da_min | <strong>integer</strong> Min Moz Domain Authority (1 to 100).
moz_links_max | <strong>integer</strong> Max Moz Linking Domains to display.
moz_links_min | <strong>integer</strong> Min Moz Linking Domains to display.

## Podcasts

```http
# With shell, you can just pass the correct header with each request
GET https://api.sparktoro.com/search/podcasts?keyword=seo&type=keyword
Accept: application/json
Authorization: Bearer your_bearer_key
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.sparktoro.com/search/podcasts?keyword=seo&type=keyword"
  -H "Authorization: Bearer your_bearer_key"
```

> The above command returns JSON structured like this:

```json
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
    {
      "id": 922993934,
      "artwork": "https://is4-ssl.mzstatic.com/image/thumb/Podcasts123/v4/eb/f1/15/ebf1159b-864d-ff87-cde0-6279313ffe24/mza_12389167778388277055.jpg/268x0w.jpg",
      "author": "Search Engine Journal",
      "episodes": 230,
      "global_followers": 407636,
      "link": "https://itunes.apple.com/us/podcast/search-engine-nerds/id922993934",
      "name": "SearchEngineJournal®",
      "podcast_description": "Welcome to The Search Engine Journal Show! This is the official podcast of Search Engine Journal. We talk all things SEO, PPC, social media, content marketing, and digital marketing with the top industry experts and authorities. Your hosts will be Brent Csutoras, Danny Goodwin, and Loren Baker.Welcome to The Search Engine Journal Show! This is the official podcast of Search Engine Journal. We talk all things SEO, PPC, social media, content marketing, and digital marketing with the top industry experts and authorities. Your hosts will be Brent Csutoras, Danny Goodwin, and Loren Baker.",
      "profile_image": "https://pbs.twimg.com/profile_images/1082875994623565824/kLGfvlP4_normal.jpg",
      "recent_date": "2020-08-14",
      "review_count": 45,
      "share": 45.42,
      "stars": 4.30,
      "title": "The Search Engine Journal Show",
      "website": "https://www.searchenginejournal.com"
    },
    ...
  ],
  "meta": {
    "source_count": 212631,
    "query": "seo",
    "type": "keyword",
    "api_limits": {
      "previous": false,
      "used": 1,
      "available": 500,
      "plan_id": 2
    },
    "query_cost": 1
  }
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://api.sparktoro.com/search/podcasts?keyword=seo&type=keyword`

### Query Parameters

Parameter | Description
--------- | -----------
keyword | <strong>string (required)</strong> The keyword, website, hashtag, or social account to search for.
type | <strong>string (required)</strong> There are 5 type of searches that can be done, see <a href="#search-types">Search Types</a> for more info.  
reviews_min | <strong>integer</strong> Max number of reviews for the podcast.
reviews_max | <strong>integer</strong> Min number of reviews for the podcast.
episode_date | <strong>integer</strong> When was the last podcast episode, inputs are 30, 60 or greater than 90 days.

## YouTube

```http
# With shell, you can just pass the correct header with each request
GET https://api.sparktoro.com/search/youtube?keyword=seo&type=keyword
Accept: application/json
Authorization: Bearer your_bearer_key
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.sparktoro.com/search/youtube?keyword=seo&type=keyword"
  -H "Authorization: Bearer your_bearer_key"
```

> The above command returns JSON structured like this:

```json
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
    {
      "id": "1059801",
      "average_views": 205,
      "channel_url": "https://youtube.com/user/SearchEngineland",
      "description": "News & analysis on #SEO #PPC #Google #Bing & more. Sister to @marketingland @martech_today @smx @martechconf. Stay in the loop: https://t.co/AHbg7x2qFZ",
      "global_followers": 690172,
      "image": "https://yt3.ggpht.com/a/AATXAJzZgxM4GsYP7dgT8_7WATKcB1JzVP_qICGsfo8MME8=s88-c-k-c0x00ffffff-no-rj",
      "join_date": "2008-12-29",
      "latest_video": "2020-07-21",
      "share": 29.5,
      "sparkscore": 59,
      "subscribers": 10100,
      "title": "Search Engine Land",
      "views": 4414363,
      "youtube_description": "Search Engine Land is a must read hub for news and information about search engine marketing, optimization and how search engines such as Google, Yahoo and Bing work for searchers."
    },
    ...
  ],
  "meta": {
    "source_count": 212631,
    "query": "seo",
    "type": "keyword",
    "api_limits": {
      "previous": false,
      "used": 1,
      "available": 500,
      "plan_id": 2
    },
    "query_cost": 1
  }
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://api.sparktoro.com/search/youtube?keyword=seo&type=keyword`

### Query Parameters

Parameter | Description
--------- | -----------
keyword | <strong>string (required)</strong> The keyword, website, hashtag, or social account to search for.
type | <strong>string (required)</strong> There are 5 type of searches that can be done, see <a href="#search-types">Search Types</a> for more info.  
subscribers_min | <strong>integer</strong> Min number of subscribers for the channel.
subscribers_max | <strong>integer</strong> Max number of subscribers for the channel.
views_min | <strong>integer</strong> Min number of views for the channel.
views_max | <strong>integer</strong> Max number of views for the channel.
avg_views_min | <strong>integer</strong> Min avg number of views for the channel.
avg_views_max | <strong>integer</strong> Max avg number of views for the channel.
last_video_date | <strong>integer</strong> When was the last video posted, inputs are 30, 60 or greater than 90 days.

## Search Types

Parameter | Description
--------- | -----------
keyword | A keyword that would be used to describe an audience.
describe | A keyword that would be used to describe a person or business. 
domain | A root domain, no subfolders. 
hashtag | Any hashtag that a user might use. If sent with #, URL encode it as %23.
follows | Search the followers of a specific social account. Pass through the full url of the social account (https://facebook.com/moz)

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


