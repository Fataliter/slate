---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - json
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

This document covers documentation and usage of BoomBit's server.

Administration panel is available here: `http://178.62.237.78`

# Starting Requests
> Request-example:

```
"Ap": "1233102938"
"r": "1234567890123456"
"auth": "1203nc09cn13cn"
```

*Parameters which always are in requests:*

{String} Ap, App Identificator

{String} r, Random char string that identifies request (16 chars)

{string} auth, String calculated with formula:  md5("a:”+Ap+”:”+r+”:”+AMPWFX_CODE)

## Start Session
> Response-example:

```json
{
  "Ss":true,
  "Data":{
    "sessid":"QBLDEEPPHSNAWLMM"
  }
}
```

### Parameters:
*Primary:* -

*Optional:* -

### Response full names:
{Boolean} Ss, Information if request was done

{String} sessid, Session ID

## Validate Session
> Request-example:

```
"sessid": "QBLDEEPPHSNAWLMM"
```

> Response-example:

```json
{
  "Ss":true,
  "Data":{
    "active":true
  }
}
```

### Parameters:
*Primary:* -

*Optional:* 

{String} sessid, Session ID

### Response full names:
{Boolean} Ss, Information if request was done

{Boolean} active, Information if session is active

## GetGuestId
> Request-example:

```
"Nnam": "ABC"
"Fs": "ABCD,AJDH,SKBD,SKBC"
"D": "ABCDHSLFIYDB"
"AD": ""
"Co": "Poland"
"sessid": "QBLDEEPPHSNAWLMM"
```

> Response-example:

```json
{
  "Ss":true,
  "Data":{
    "Ulvl":0,
    "CL": "10",
    "F": "ABCD,AJDH,SKBD,SKBC",
    "GId":"g_KNPKCGIC"
  }
}
```

### Parameters:
*Primary:* -

*Optional:*

{String} Nnam, Nickname

{String} Fs, Friends

{String} D, Push notification (it depends from the platform: if iOS - send: "ABCDHSLFIYDB", if Android - send: "Android:ABCDHSLFIYDB")

{String} AD, Additional Data (any data)

{String} Co, Country

{String} sessid, Session ID

### Response full names:
{Boolean} Ss, Information if request was done

{Number} Ulvl, User league level

{String} CL, Current League

{String} F, Friends

{String} GId, Guest Id

## Set Player Data
> Request-example:

```
"P": "g_KNPKCGIC"
"Nnam": "ABC"
"Fs": "ABCD,AJDH,SKBD,SKBC"
"D": "ABCDHSLFIYDB"
"AD": ""
"Co": "Poland"
"Ulvl": 5
"sessid": "QBLDEEPPHSNAWLMM"
```

> Response-example:

```json
{
  "Ss":true,
  "Data":{
    "Ulvl":5,
    "CL":"10",
    "F":"ABCD,AJDH,SKBD,SKBC"
  }
}
```

### Parameters:
*Primary:*

{String} P, Player Id

*Optional:*

{String} Nnam, Nickname

{String} Fs, Friends

{String} D, Push notification (it depends from the platform: if iOS - send: "ABCDHSLFIYDB", if Android - send: "Android:ABCDHSLFIYDB")

{String} AD, Additional Data (any data)

{String} Co, Country

{Number} Ulvl, User league level

{String} sessid, Session ID

### Response full names:


# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
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

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
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

