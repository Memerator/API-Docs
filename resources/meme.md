---
description: Information about the meme object
---

# Meme

The Meme object is returned when requesting 1 or multiple memes. An example object is as follows.

| Field | Type | Description |
| :--- | :--- | :--- |
| disabled | boolean | is the meme disabled? |
| memeid | string | the meme's id |
| caption | string | the meme's caption |
| author | User | a user object of the author |
| rating | hash | hash of the rating, with the average and total ratings |
| url | string | the url of the image of the meme |
| permalink | string | the url of the meme on memerator.me |
| timestamp | timestamp | when the meme was submitted |
| time\_ago | string | what appears on the website how long ago it was submitted |

```javascript
{
    "disabled": false,
    "memeid": "aaaaaaa",
    "caption": "***__AAAAAAAA__***",
    "author": {
        "username": "Chew",
        "bio": "#1 most depressed memerator user. pronouns: she/her",
        "id": 476488167042580481,
        "stats": {
            "memes": 171,
            "followers": 26,
            "following": 20
        },
        "perks": {
            "verified": true,
            "staff": true,
            "translator": false,
            "pro": true
        },
        "permalink": "https://memerator.me/profile/476488167042580481",
        "joined": "2018-10-11T15:37:03.000Z"
    },
    "rating": {
        "average": 3.75,
        "total": 4
    },
    "url": "https://cdn.memerator.me/K7bLRy9.jpg",
    "permalink": "https://memerator.me/meme/aaaaaaa",
    "timestamp": "2019-02-15T13:29:01.000Z",
    "time_ago": "11 months"
}
```

{% api-method method="get" host="https://api.memerator.me/v1/" path="meme/:id" %}
{% api-method-summary %}
Get a Meme
{% endapi-method-summary %}

{% api-method-description %}
This request gets a meme by its ID.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Meme ID" type="string" required=true %}
The ID of the meme you want
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Response of a valid Meme
{% endapi-method-response-example-description %}

```javascript
{
    "disabled": false,
    "memeid": "aaaaaaa",
    "caption": "***__AAAAAAAA__***",
    "author": {
        "username": "Chew",
        "bio": "#1 most depressed memerator user. pronouns: she/her",
        "id": 476488167042580481,
        "stats": {
            "memes": 171,
            "followers": 26,
            "following": 20
        },
        "perks": {
            "verified": true,
            "staff": true,
            "translator": false,
            "pro": true
        },
        "permalink": "https://memerator.me/profile/476488167042580481",
        "joined": "2018-10-11T15:37:03.000Z"
    },
    "rating": {
        "average": 3.75,
        "total": 4
    },
    "url": "https://cdn.memerator.me/K7bLRy9.jpg",
    "permalink": "https://memerator.me/meme/aaaaaaa",
    "timestamp": "2019-02-15T13:29:01.000Z",
    "time_ago": "11 months"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Response of an invalid auth key
{% endapi-method-response-example-description %}

```javascript
{
    "error": "Auth not valid"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Response of a meme that doesn't exist \(or is disabled, and you aren't the owner\)
{% endapi-method-response-example-description %}

```javascript
{
    "error": "meme does not exist"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.memerator.me" path="/v1/meme/random" %}
{% api-method-summary %}
Get a Random Meme
{% endapi-method-summary %}

{% api-method-description %}
Gets a random meme. Note: Not completely random?
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
[a meme object]
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Response when using an invalid API key
{% endapi-method-response-example-description %}

```javascript
{
    "error": "Auth not valid"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.memerator.me" path="/v1/meme/:id/caption" %}
{% api-method-summary %}
Set Meme Caption
{% endapi-method-summary %}

{% api-method-description %}
Change the caption of a meme you own.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name=":id" type="string" required=true %}
ID of the meme
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="caption" type="string" required=true %}
The caption you want to set it to
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A successful caption change response
{% endapi-method-response-example-description %}

```javascript
{
    "success": true,
    "caption": "uwu owo nyaa",
    "oldcaption": "you got got guten prankened"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
When a known error occurs, you'll get this. It can differ, so we put a blank error in. Error will always contain something.
{% endapi-method-response-example-description %}

```javascript
{
    "error": ""
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
response when using an invalid api key
{% endapi-method-response-example-description %}

```javascript
{
    "error": "Auth not valid"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
Returned if you try to change the caption of a meme you don't own
{% endapi-method-response-example-description %}

```javascript
{ "error": "you don't own this meme" }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Raised if you try to edit a meme that doesn't exist
{% endapi-method-response-example-description %}

```javascript
{ "error": 'meme does not exist' }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
When an unknown error occurs, you'll get this.
{% endapi-method-response-example-description %}

```javascript
{ "error": 'Unknown Error Changing Caption' }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.memerator.me" path="/v1/meme/:id/comments" %}
{% api-method-summary %}
Get Meme Comments
{% endapi-method-summary %}

{% api-method-description %}
This method returns an array of comments for a specified meme and their author.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name=":id" type="string" required=true %}
meme id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
An array of comments. In each comment object there is ID, author \(User object\), the content, the associated Meme, the timestamp, and the creation in epoch seconds.
{% endapi-method-response-example-description %}

```javascript
[
    {
        "id": 5,
        "author": {
            "username": "Chew",
            "bio": "#1 most depressed Memerator user. pronouns: she/her 🏳️‍⚧️",
            "id": 476488167042580481,
            "stats": {
                "memes": 382,
                "followers": 28,
                "following": 24
            },
            "perks": {
                "verified": true,
                "staff": true,
                "translator": false,
                "pro": true
            },
            "permalink": "https://memerator.me/profile/476488167042580481",
            "joined": "2018-10-11T15:37:03.000Z",
            "joined_epoch_seconds": 1539272223
        },
        "content": "aaaaaaaaaaaaaaaaaaaaaa",
        "meme": {
            "disabled": false,
            "memeid": "aaaaaaa",
            "caption": "***__AAAAAAAA__***",
            "author": {
                "username": "Chew",
                "bio": "#1 most depressed Memerator user. pronouns: she/her 🏳️‍⚧️",
                "id": 476488167042580481,
                "stats": {
                    "memes": 382,
                    "followers": 28,
                    "following": 24
                },
                "perks": {
                    "verified": true,
                    "staff": true,
                    "translator": false,
                    "pro": true
                },
                "permalink": "https://memerator.me/profile/476488167042580481",
                "joined": "2018-10-11T15:37:03.000Z",
                "joined_epoch_seconds": 1539272223
            },
            "rating": {
                "average": 4.0,
                "total": 5
            },
            "age": 1,
            "url": "https://cdn.memerator.me/K7bLRy9.jpg",
            "permalink": "https://memerator.me/meme/aaaaaaa",
            "timestamp": "2019-02-15T13:29:01.000Z",
            "timestamp_epoch_seconds": 1550237341,
            "time_ago": "over 1 year"
        },
        "timestamp": "2020-02-02T15:11:31.000Z",
        "timestamp_epoch_seconds": 1580656291
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.memerator.me" path="/v1/meme/:id/disable" %}
{% api-method-summary %}
Disable a Meme
{% endapi-method-summary %}

{% api-method-description %}
Disables a meme by ID. Meme author only!
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name=":id" type="string" required=true %}
Meme ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
If you did it right!
{% endapi-method-response-example-description %}

```
{ "success": true }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
If the meme is already disabled
{% endapi-method-response-example-description %}

```
{ "error": "this meme is already disabled" }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
If your key is invalid or can't access the resource
{% endapi-method-response-example-description %}

```
{ "error": "Auth not valid" }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
If you don't own the meme
{% endapi-method-response-example-description %}

```
{ "error": "you don't own this meme" }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
If the meme doesn't exist \(or is disabled and you aren't the owner\)
{% endapi-method-response-example-description %}

```
{ "error": "meme does not exist" }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.memerator.me" path="/v1/meme/:id/enable" %}
{% api-method-summary %}
Enable a meme
{% endapi-method-summary %}

{% api-method-description %}
Exact same as disable, but for enabling
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name=":id" type="string" required=true %}
The Meme ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
If you did it right!
{% endapi-method-response-example-description %}

```
{ "success": true }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
If the meme is already enabled
{% endapi-method-response-example-description %}

```
{ "error": "this meme is already enabled" }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
If the API key is invalid or can't access the resource
{% endapi-method-response-example-description %}

```
{ "error": "Auth not valid" }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
If you don't own the meme
{% endapi-method-response-example-description %}

```
{ "error": "you don't own this meme" }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
If the meme doesn't exist or it's disabled and you aren't the owner.
{% endapi-method-response-example-description %}

```
{ "error": "meme does not exist" }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.memerator.me" path="/v1/meme/:id/rating" %}
{% api-method-summary %}
Get your Rating
{% endapi-method-summary %}

{% api-method-description %}
Gets your rating on a meme.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name=":id" type="string" required=true %}
the meme id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The rating
{% endapi-method-response-example-description %}

```
{ "rating": 5 }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
If your key isn't valid or it's not allowed to access "Ratings"
{% endapi-method-response-example-description %}

```
{ "error": 'Auth not valid' }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
If the meme doesn't exist or it's disabled and you aren't the owner.
{% endapi-method-response-example-description %}

```
{ "error": 'meme does not exist' }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.memerator.me" path="/v1/meme/:id/ratings" %}
{% api-method-summary %}
Get all Ratings
{% endapi-method-summary %}

{% api-method-description %}
Gets all ratings for a meme. Pro only! Requires "Ratings" key permission.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name=":id" type="string" required=true %}
Meme ID.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A JSONArray of objects. Each Object contains a hash mapping of user to User object, rating to the rating, and the timestamp of the rating.
{% endapi-method-response-example-description %}

```javascript
[
    {
        "user": {
            "username": "treye_2019",
            "bio": "",
            "id": 296476360602419211,
            "stats": {
                "memes": 1,
                "followers": 0,
                "following": 0
            },
            "perks": {
                "verified": false,
                "staff": false,
                "translator": false,
                "pro": false
            },
            "permalink": "https://memerator.me/profile/296476360602419211",
            "joined": "2019-03-02T00:43:26.000Z",
            "joined_epoch_seconds": 1551487406
        },
        "rating": 1,
        "timestamp": "2019-05-20T13:04:33.000Z"
    },
    {
        "user": {
            "username": "Chew",
            "bio": "#1 most depressed Memerator user. pronouns: she/her 🏳️‍⚧️",
            "id": 476488167042580481,
            "stats": {
                "memes": 382,
                "followers": 28,
                "following": 24
            },
            "perks": {
                "verified": true,
                "staff": true,
                "translator": false,
                "pro": true
            },
            "permalink": "https://memerator.me/profile/476488167042580481",
            "joined": "2018-10-11T15:37:03.000Z",
            "joined_epoch_seconds": 1539272223
        },
        "rating": 5,
        "timestamp": "2019-05-20T13:04:33.000Z"
    },
    {
        "user": {
            "username": "Loyal_2019",
            "bio": null,
            "id": 181249274699448320,
            "stats": {
                "memes": 0,
                "followers": 0,
                "following": 0
            },
            "perks": {
                "verified": false,
                "staff": false,
                "translator": false,
                "pro": false
            },
            "permalink": "https://memerator.me/profile/181249274699448320",
            "joined": "2019-03-31T21:35:12.000Z",
            "joined_epoch_seconds": 1554068112
        },
        "rating": 4,
        "timestamp": "2019-05-20T13:04:33.000Z"
    },
    {
        "user": {
            "username": "ur_mom",
            "bio": "is gay",
            "id": 783885855388066361,
            "stats": {
                "memes": 239,
                "followers": 8,
                "following": 4
            },
            "perks": {
                "verified": true,
                "staff": false,
                "translator": false,
                "pro": false
            },
            "permalink": "https://memerator.me/profile/783885855388066361",
            "joined": "2019-10-24T20:37:28.000Z",
            "joined_epoch_seconds": 1571949448
        },
        "rating": 5,
        "timestamp": "2019-11-06T00:28:07.000Z"
    },
    {
        "user": {
            "username": "taketheshake",
            "bio": "I wish I was awesome as chew, but she's almost equivalent to comp sci meme Jesus, so maybe not.",
            "id": 338784252382412800,
            "stats": {
                "memes": 3,
                "followers": 5,
                "following": 1
            },
            "perks": {
                "verified": true,
                "staff": true,
                "translator": false,
                "pro": true
            },
            "permalink": "https://memerator.me/profile/338784252382412800",
            "joined": "2019-04-17T13:27:02.000Z",
            "joined_epoch_seconds": 1555507622
        },
        "rating": 5,
        "timestamp": "2020-02-28T14:39:58.000Z"
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

