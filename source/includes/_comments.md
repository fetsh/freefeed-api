# Comments

## Create Comment

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')

comment_resource = Freefeed::Comment.new(client: client)

comment = Freefeed::Types::CommentCreate.new(
  comment: { body: "Hi, love!", postId: '5579b79b-c5f5-464c-b101-638de4a8f335'}
)

comment_resource.create(comment)
```

```shell
curl "https://freefeed.net/v1/comments"
  -H "x-authentication-token: yourFreefeedAPIToken"
  -H "content-type: application/json"
  -d '{"comment":{"body":"Hi, love!","postId":"5579b79b-c5f5-464c-b101-638de4a8f335"}}'

```

> The above command returns JSON structured like this:

```json
{
  "comments": {
    "id": "8cb67cab-0b4e-46ce-94bb-90b6eb2cc092",
    "body": "Hi, love!",
    "createdAt": "1539384483129",
    "createdBy": "920196ff-f2b0-4319-8fb2-626e4ac76d2c"
  },
  "users": [
    {
      "id": "920196ff-f2b0-4319-8fb2-626e4ac76d2c",
      "username": "yourusername",
      "screenName": "your FUNNY username",
      "isPrivate": "0",
      "isProtected": "0",
      "createdAt": "1538770654480",
      "updatedAt": "1538770654480",
      "type": "user",
      "description": "",
      "profilePictureLargeUrl": "",
      "profilePictureMediumUrl": "",
      "statistics": {
        "posts": "9",
        "likes": "0",
        "comments": "3",
        "subscribers": "0",
        "subscriptions": "2"
      }
    }
  ],
  "admins": [
    {
      "id": "920196ff-f2b0-4319-8fb2-626e4ac76d2c",
      "username": "yourusername",
      "screenName": "your FUNNY username",
      "isPrivate": "0",
      "isProtected": "0",
      "createdAt": "1538770654480",
      "updatedAt": "1538770654480",
      "type": "user",
      "description": "",
      "profilePictureLargeUrl": "",
      "profilePictureMediumUrl": "",
      "statistics": {
        "posts": "9",
        "likes": "0",
        "comments": "3",
        "subscribers": "0",
        "subscriptions": "2"
      }
    }
  ]
}
```

This endpoint creates a comment.

### HTTP Request

`POST https://freefeed.net/v1/comments`

### JSON Body Parameters

Parameter | Type | Required | Description
--------- | ----------- | ----------- | -----------
comment | [CommentCreate](#commentcreate) | Yes | See CommentCreate


### CommentCreate

Parameter | Type | Required | Description
--------- | ----------- | ----------- | -----------
body | String | Yes | A body of the comment. Must include at least one \S character
postId | String | Yes | Id of the post for the comment




## Update Comment

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')

comment_resource = Freefeed::Comment.new(client: client)

comment = Freefeed::Types::CommentUpdate.new(comment: { body: "Bye bye happiness"})

comment_resource.update({id: '8cb67cab-0b4e-46ce-94bb-90b6eb2cc092'}, comment)
```

```shell
curl "https://freefeed.net/v1/comments/8cb67cab-0b4e-46ce-94bb-90b6eb2cc092"
  -X PUT
  -H "x-authentication-token: yourFreefeedAPIToken"
  -H "content-type: application/json"
  -d '{"comment":{"body":"Bye bye happiness"}}'

```

> The above command returns JSON structured like this:

```json
{
  "comments": {
    "id": "8cb67cab-0b4e-46ce-94bb-90b6eb2cc092",
    "body": "Bye bye happiness",
    "createdAt": "1539384483129",
    "createdBy": "920196ff-f2b0-4319-8fb2-626e4ac76d2c"
  },
  "users": [
    {
      "id": "920196ff-f2b0-4319-8fb2-626e4ac76d2c",
      "username": "yourusername",
      "screenName": "your FUNNY username",
      "isPrivate": "0",
      "isProtected": "0",
      "createdAt": "1538770654480",
      "updatedAt": "1538770654480",
      "type": "user",
      "description": "",
      "profilePictureLargeUrl": "",
      "profilePictureMediumUrl": "",
      "statistics": {
        "posts": "9",
        "likes": "0",
        "comments": "3",
        "subscribers": "0",
        "subscriptions": "2"
      }
    }
  ],
  "admins": [
    {
      "id": "920196ff-f2b0-4319-8fb2-626e4ac76d2c",
      "username": "yourusername",
      "screenName": "your FUNNY username",
      "isPrivate": "0",
      "isProtected": "0",
      "createdAt": "1538770654480",
      "updatedAt": "1538770654480",
      "type": "user",
      "description": "",
      "profilePictureLargeUrl": "",
      "profilePictureMediumUrl": "",
      "statistics": {
        "posts": "9",
        "likes": "0",
        "comments": "3",
        "subscribers": "0",
        "subscriptions": "2"
      }
    }
  ]
}
```

This endpoint updates a comment.

### HTTP Request

`PUT https://freefeed.net/v1/comments/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the comment to update

### JSON Body Parameters

Parameter | Type | Required | Description
--------- | ----------- | ----------- | -----------
comment | [CommentUpdate](#commentupdate) | Yes | See CommentUpdate


### CommentUpdate

Parameter | Type | Required | Description
--------- | ----------- | ----------- | -----------
body | String | Yes | A body of the comment. Must include at least one \S character



## Delete Comment

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')

comment_resource = Freefeed::Comment.new(client: client)

comment_resource.destroy(id: '8cb67cab-0b4e-46ce-94bb-90b6eb2cc092')
```

```shell
curl "https://freefeed.net/v1/comments/8cb67cab-0b4e-46ce-94bb-90b6eb2cc092"
  -X DELETE
  -H "x-authentication-token: yourFreefeedAPIToken"
```

> The above command returns empty JSON

```json
{}
```

This endpoint deletes a specific comment.

### HTTP Request

`DELETE https://freefeed.net/v1/comments/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the comment to delete

### Errors

Code | JSON
--------- | -----------
403 | {"err":"You don't have permission to delete this comment"}
404 | {"err":"Can not find comment"}


## Like Comment

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')

comment_resource = Freefeed::Comment.new(client: client)

comment_resource.like(id: '56d1864d-0d58-49b8-9827-109850991f60')
```

```shell
curl "https://freefeed.net/v2/comments/56d1864d-0d58-49b8-9827-109850991f60/like"
  -H "x-authentication-token: yourFreefeedAPIToken"
  -X POST
```

> The above command returns JSON structured like this:

```json
{
  "likes": [
    {
      "userId": "920196ff-f2b0-4319-8fb2-626e4ac76d2c",
      "createdAt": "2018-10-12T23:32:10.109Z"
    }
  ],
  "users": [
    {
      "id": "920196ff-f2b0-4319-8fb2-626e4ac76d2c",
      "username": "yourusername",
      "screenName": "your FUNNY username",
      "isPrivate": "0",
      "isProtected": "0",
      "createdAt": "1538770654480",
      "updatedAt": "1538770654480",
      "type": "user",
      "description": "",
      "profilePictureLargeUrl": "",
      "profilePictureMediumUrl": "",
      "statistics": {
        "posts": "9",
        "likes": "0",
        "comments": "2",
        "subscribers": "0",
        "subscriptions": "2"
      }
    }
  ]
}
```

This endpoint likes a specific post.

### HTTP Request

`POST https://freefeed.net/v2/comments/<ID>/like`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the comment to like


## Unlike Comment

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')

comment_resource = Freefeed::Comment.new(client: client)

comment_resource.unlike(id: '56d1864d-0d58-49b8-9827-109850991f60')
```

```shell
curl "https://freefeed.net/v2/comments/56d1864d-0d58-49b8-9827-109850991f60/unlike"
  -H "x-authentication-token: yourFreefeedAPIToken"
  -X POST
```

> The above command returns JSON structured like this:

```json
{"likes":[],"users":[]}
```


This endpoint likes a specific post.

### HTTP Request

`POST https://freefeed.net/v2/comments/<ID>/unlike`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the comment to unlike

## Get Likes of a Comment

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')

comment_resource = Freefeed::Comment.new(client: client)

comment_resource.likes(id: '56d1864d-0d58-49b8-9827-109850991f60')
```

```shell
curl "https://freefeed.net/v2/comments/56d1864d-0d58-49b8-9827-109850991f60/likes"
  -H "x-authentication-token: yourFreefeedAPIToken"
```

> The above command returns JSON structured like this:

```json
{
  "likes": [
    {
      "userId": "920196ff-f2b0-4319-8fb2-626e4ac76d2c",
      "createdAt": "2018-10-12T23:32:10.109Z"
    }
  ],
  "users": [
    {
      "id": "920196ff-f2b0-4319-8fb2-626e4ac76d2c",
      "username": "yourusername",
      "screenName": "your FUNNY username",
      "isPrivate": "0",
      "isProtected": "0",
      "createdAt": "1538770654480",
      "updatedAt": "1538770654480",
      "type": "user",
      "description": "",
      "profilePictureLargeUrl": "",
      "profilePictureMediumUrl": "",
      "statistics": {
        "posts": "9",
        "likes": "0",
        "comments": "2",
        "subscribers": "0",
        "subscriptions": "2"
      }
    }
  ]
}
```

This endpoint returns likes of a specific comment.

### HTTP Request

`GET https://freefeed.net/v2/comments/<ID>/likes`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the comment for which you want to get likes
