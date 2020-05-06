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
Getting a Meme
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
Getting a Random Meme
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
This method returns an array of comments for a specifiied meme and their author.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

