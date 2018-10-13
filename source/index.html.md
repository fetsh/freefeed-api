---
title: FreeFeed API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - attachments
  - bookmarklet
  - comments
  - posts

search: true
---

# Freefeed API

Unoficial Freefeed API documentation.

# Authentication

> To obtain API token:

```ruby
require 'freefeed'

client = Freefeed::Client.new()

client.authenticate(username: 'yourusername', password: 'yourpassword')
```

```shell
curl "https://freefeed.net/v1/session"
  -X POST
  -d "username=yourusername&password=yourpassword"
```

> The above command returns JSON structured like this:

```json
{
  "users": {
    "id": "920196ff-f2b0-4319-8fb2-626e4ac76d2c",
    "username": "yourusername",
    "type": "user",
    "screenName": "your FUNNY username",
    "createdAt": "1538770654480",
    "updatedAt": "1538770654480",
    "isPrivate": "0",
    "isProtected": "0",
    "profilePictureLargeUrl": "",
    "profilePictureMediumUrl": "",
    "statistics": {
      "posts": "9",
      "likes": "0",
      "comments": "0",
      "subscribers": "0",
      "subscriptions": "2"
    },
    "administrators": [
      "920196ff-f2b0-4319-8fb2-626e4ac76d2c"
    ]
  },
  "admins": [
    {
      "id": "920196ff-f2b0-4319-8fb2-626e4ac76d2c",
      "username": "yourusername",
      "type": "user",
      "screenName": "your FUNNY username",
      "updatedAt": "1538770654480",
      "isPrivate": "0",
      "isProtected": "0",
      "profilePictureLargeUrl": "",
      "profilePictureMediumUrl": "",
      "administrators": [
        {
          
        }
      ],
      "statistics": {
        "posts": "9",
        "likes": "0",
        "comments": "0",
        "subscribers": "0",
        "subscriptions": "2"
      }
    }
  ],
  "authToken": "yourFreefeedAPIToken"
}
```

> To authenticate by the API key, use this code:

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "x-authentication-token: yourFreefeedAPIToken"
```

> Make sure to replace `yourFreefeedAPIToken` with your API key.

Freefeed uses API keys to allow access to the API. You can get your API key on [the settings page](https://freefeed.net/settings) (BetterFeed should be turned on), or on the [settings page](https://m.freefeed.net/settings/accounts) of [m.freefeed.net](https://m.freefeed.net/) frontend (no need for BetterFeed).

Or you can obtain your API key by providing your username and password.

### HTTP Request

`POST https://freefeed.net/v1/session`

### POST Payload

Parameter | Description
--------- | -----------
username | Your username
password | Your password


Freefeed expects for the API key to be included in most API requests to the server in a header that looks like the following:

`x-authentication-token: yourFreefeedAPIToken`

<aside class="notice">
You must replace <code>yourFreefeedAPIToken</code> with your personal API key.
</aside>
