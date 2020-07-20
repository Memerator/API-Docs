# User/Profile

The User object is returned when requesting 1 or multiple users. An example object is as follows

| Field | Type | Description |
| :--- | :--- | :--- |
| username | string | The username of this profile |
| bio | string | This user's bio |
| id | int | The ID of this user. |
| stats | hash | A hash of a user's meme, followers, and following count |
| perks | hash | A hash of a user's perks. |
| permalink | string | The URL to this user's profile |
| joined | timestamp | The exact date this user registered |

{% api-method method="get" host="https://api.memerator.me" path="/v1/profile/:user" %}
{% api-method-summary %}
Get User
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get a user's profile by ID or username.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name=":user" type="object" required=true %}
The user you want. Can be by ID or username
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
User successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
    "username": "Chew",
    "bio": "<script>alert('hi');</script>",
    "id": 476488167042580481,
    "stats": {
        "memes": 67,
        "followers": 2,
        "following": 3
    },
    "perks": {
        "verified": true,
        "staff": true,
        "translator": false,
        "pro": true
    },
    "permalink": "https://memerator.me/profile/476488167042580481",
    "joined": "2018-10-11T15:37:03.000Z"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Could not find a user matching this query.
{% endapi-method-response-example-description %}

```javascript
{
    "error": "this user does not exist!"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.memerator.me" path="/v1/integrations" %}
{% api-method-summary %}
Get Integrations
{% endapi-method-summary %}

{% api-method-description %}
Gets your integrations. Requires "View Integrations" key permission.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A JSONObject consisting of a mapping of service name to an array of integrations for said service name.
{% endapi-method-response-example-description %}

```javascript
{
    "google": [
        "my google email",
        "my second google email",
        "mcdonalds@gov.gov"
    ],
    "apple": [
        "send me @bitcoin"
    ],
    "minecraft": [
        "sdlhfw87e4rt43h7tu34tfelsiofyest8ye4t"
    ],
    "discord": [
        "4756754676574567567"
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



