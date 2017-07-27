---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Contact us for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# JSON API Introduction

Caring.com provides [JSON API](http://jsonapi.org/) compliant APIs over HTTPS. Examples are provided for shell assuming basic usage of Curl. Other language exmaples can be provided if requested.

# Authentication

Requests require an API key that you can obtain by contacting us.

> Authentication header examples:

```shell
# With shell, you can just pass the correct header with each request
curl "https://dir.caring.com/api/v2/reviews.jsonapi"
  -H "Caring-Partner: TOKEN_VALUE"
```

> Make sure to replace `TOKEN_VALUE` with your API key.

Caring.com Directory expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Caring-Partner: TOKEN_VALUE`

<aside class="notice">
You must replace <code>TOKEN_VALUE</code> with your personal API key.
</aside>

# Reviews

## GET Reviews

```shell
curl "https://dir.caring.com/api/v2/reviews.jsonapi"
  -H "Caring-Partner: TOKEN_VALUE"
```

> The above command returns [JSON API](http://jsonapi.org/) response structured like this:

```json
{
    "data": [
        {
            "id": "1148701",
            "type": "local_reviews",
            "attributes": {
                "resource_id": 1229142,
                "resource_url": "http://www.caring.com/local/memory-care-facilities-in-dallas-texas/villages-of-lake-highlands",
                "resource_name": "Villages of Lake Highlands",
                "title": "I am a friend or relative of a current/past resident",
                "content": "This is a really good review",
                "rating": 5,
                "staff_score": 0,
                "activities_score": 0,
                "food_score": 0,
                "facilities_score": 0,
                "value_score": 0,
                "provider_response": null,
                "moderation_status": "unmoderated",
                "moderated_at": null,
                "author": {
                    "name": "Bennet52",
                    "email": "8225995e75243d26@example.com",
                    "url": "https://www.caring.com/people/bennet52"
                },
                "source": {
                    "name": "provider_page",
                    "template": "review_form",
                    "type": "organic"
                },
                "origin_url": null,
                "moderation_webhook_url": null,
                "ip_address": "70.121.60.173",
                "created_at": "2017-07-23T14:03:41.000-07:00",
                "updated_at": "2017-07-21T19:23:11.000-07:00"
            }
        }
    ],
    "links": {
        "self": "https://dir.caring.com/api/v2/reviews.jsonapi?page%5Bnumber%5D=1&page%5Bsize%5D=1&per_page=1",
        "next": "https://dir.caring.com/api/v2/reviews.jsonapi?page%5Bnumber%5D=2&page%5Bsize%5D=1&per_page=1",
        "last": "https://dir.caring.com/api/v2/reviews.jsonapi?page%5Bnumber%5D=1799&page%5Bsize%5D=1&per_page=1"
    }
}
```

This endpoint retrieves a paginated list of reviews.

### HTTP Request

`GET https://dir.caring.com/api/v2/reviews.jsonapi`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
per_page | 50 | The number of results per page of reviews.

## Get a Specific Review

```shell
curl "https://dir.caring.com/api/v2/reviews/2.jsonapi"
  -H "Caring-Partner: TOKEN_VALUE"
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

`GET https://dir.caring.com/api/v2/reviews/<ID>.jsonapi`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve
