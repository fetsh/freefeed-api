# Posts

## Get Post

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')
post_resource = Freefeed::Post.new(client: client)

post_resource.get(id: '7c70927a-4e51-49e7-bfe1-33bc4c1c0618')
```

```shell
curl "https://freefeed.net/v2/posts/7c70927a-4e51-49e7-bfe1-33bc4c1c0618"
  -H "x-authentication-token: yourFreefeedAPIToken"
```

> The above command returns JSON structured like this:

```json
{
  "posts": {
    "id": "7c70927a-4e51-49e7-bfe1-33bc4c1c0618",
    "body": "FAQ: frequently asked questions (and answers). If you have more questions, please contact @support.",
    "commentsDisabled": "1",
    "createdAt": "1449074608680",
    "updatedAt": "1475924950194",
    "commentLikes": 0,
    "ownCommentLikes": 0,
    "omittedCommentLikes": 0,
    "omittedOwnCommentLikes": 0,
    "createdBy": "5df98f17-6085-4a14-bcdc-1ae07cb1957f",
    "postedTo": [
      "8b7db31d-d5f4-41be-a159-829cf9470007"
    ],
    "comments": [
      "1f96e911-e1d7-44b7-81f1-fa3da5bb449e",
      "1d5f34cd-59fb-4967-af90-ae56a60d5392"
    ],
    "attachments": [
      
    ],
    "likes": [
      "ec3a56c7-19b1-4f07-864c-9e643c97ced3",
      "46dbbdbe-efbb-4f91-a853-b91d199176a1",
      "6726abcb-dcc3-4115-9b13-16332dd4cb1d"
    ],
    "omittedComments": 25,
    "omittedLikes": 8
  },
  "users": [
    {
      "id": "5df98f17-6085-4a14-bcdc-1ae07cb1957f",
      "username": "welcome",
      "screenName": "welcome",
      "isPrivate": "0",
      "isProtected": "0",
      "createdAt": "1448302642164",
      "updatedAt": "1452687756552",
      "type": "user",
      "description": "",
      "profilePictureLargeUrl": "",
      "profilePictureMediumUrl": "",
      "statistics": {
        "posts": "3",
        "likes": "1",
        "comments": "40",
        "subscribers": "2009",
        "subscriptions": "0"
      }
    },
  ],
  "subscriptions": [
    {
      "id": "8b7db31d-d5f4-41be-a159-829cf9470007",
      "name": "Posts",
      "user": "5df98f17-6085-4a14-bcdc-1ae07cb1957f"
    }
  ],
  "subscribers": [
    {
      "id": "5df98f17-6085-4a14-bcdc-1ae07cb1957f",
      "username": "welcome",
      "screenName": "welcome",
      "isPrivate": "0",
      "isProtected": "0",
      "createdAt": "1448302642164",
      "updatedAt": "1452687756552",
      "type": "user",
      "description": "",
      "profilePictureLargeUrl": "",
      "profilePictureMediumUrl": "",
      "statistics": {
        "posts": "3",
        "likes": "1",
        "comments": "40",
        "subscribers": "2009",
        "subscriptions": "0"
      }
    }
  ],
  "comments": [
    {
      "id": "1f96e911-e1d7-44b7-81f1-fa3da5bb449e",
      "body": "== About FreeFeed:",
      "createdAt": "1449074650399",
      "updatedAt": "1475924960830",
      "hideType": 0,
      "likes": 0,
      "hasOwnLike": false,
      "createdBy": "5df98f17-6085-4a14-bcdc-1ae07cb1957f"
    },
    {
      "id": "1d5f34cd-59fb-4967-af90-ae56a60d5392",
      "body": "If you have more questions, you can ask them at @support. If you have anything to add to the FAQ here, you can do it here: https:\/\/freefeed.net\/freefeed\/ef954a33-39a3-43e5-a62d-698ed55c9548",
      "createdAt": "1449075294335",
      "updatedAt": "1475928090704",
      "hideType": 0,
      "likes": 0,
      "hasOwnLike": false,
      "createdBy": "5df98f17-6085-4a14-bcdc-1ae07cb1957f"
    }
  ],
  "attachments": [
    
  ]
}
```

This endpoint retrieves a specific post.

### HTTP Request

`GET https://freefeed.net/v2/posts/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the post to retrieve


## Create Post

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')

post_resource = Freefeed::Post.new(client: client)

post = Freefeed::Types::PostCreate.new(
  {
    post: { 
      body: 'Hello World!'
    },
    meta: {
      feeds: ['username']
    }
  }
)

post_resource.create(post)
```

```shell
curl "https://freefeed.net/v1/posts"
  -H "content-type: application/json"
  -H "x-authentication-token: yourFreefeedAPIToken"
  -d '{"post":{"body":"HelloWorld!"},"meta":{"feeds":["yourusername"],"commentsDisabled":false}}'
```

> The above command returns JSON structured like this:

```json
{
  "posts": {
    "id": "7c70927a-4e51-49e7-bfe1-33bc4c1c0618",
    "body": "HelloWorld!",
    "commentsDisabled": "0",
    "createdAt": "1539348845566",
    "updatedAt": "1539348845566",
    "commentLikes": 0,
    "ownCommentLikes": 0,
    "omittedCommentLikes": 0,
    "omittedOwnCommentLikes": 0,
    "createdBy": "920196ff-f2b0-4319-8fb2-626e4ac76d2c",
    "postedTo": [
      "28c68cc1-5bb4-40bd-9767-155c1de480a0"
    ],
    "comments": [
      
    ],
    "attachments": [
      
    ],
    "likes": [
      
    ],
    "omittedComments": 0,
    "omittedLikes": 0
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
        "posts": "10",
        "likes": "0",
        "comments": "0",
        "subscribers": "0",
        "subscriptions": "1"
      }
    }
  ],
  "subscriptions": [
    {
      "id": "28c68cc1-5bb4-40bd-9767-155c1de480a0",
      "name": "Posts",
      "user": "920196ff-f2b0-4319-8fb2-626e4ac76d2c"
    }
  ],
  "subscribers": [
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
        "posts": "10",
        "likes": "0",
        "comments": "0",
        "subscribers": "0",
        "subscriptions": "1"
      }
    }
  ],
  "comments": [
    
  ],
  "attachments": [
    
  ]
}
```

This endpoint creates a post.

### HTTP Request

`POST https://freefeed.net/v1/posts`

### JSON Body Parameters

Parameter | Type | Required | Description
--------- | ----------- | ----------- | -----------
post | [PostCreate](#postcreate) | Yes | See PostCreate
meta | [MetaCreate](#metacreate) | Yes | See MetaCreate

### PostCreate

Parameter | Type | Required | Description
--------- | ----------- | ----------- | -----------
body | String | Yes | A body of the post. Must include at least one \S character
attachments | Array of UID | No | Array of previously uploaded attachmets ids

### MetaCreate

Parameter | Type | Required | Description
--------- | ----------- | ----------- | -----------
commentsDisabled | Boolean | No | Indicates whether comments for the post should be disabled (Default is false)
feeds | String of Array of String | Yes | Username or groupname or array of username and groupnames where the post should be posted to



## Delete Post

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')
post_resource = Freefeed::Post.new(client: client)

post_resource.destroy(id: '7c70927a-4e51-49e7-bfe1-33bc4c1c0618')
```

```shell
curl "https://freefeed.net/v2/posts/7c70927a-4e51-49e7-bfe1-33bc4c1c0618"
  -X DELETE
  -H "x-authentication-token: yourFreefeedAPIToken"
```

> The above command returns JSON structured like this:

```json
{
  "postStillAvailable": false
}
```

This endpoint deletes a specific post.

### HTTP Request

`DELETE https://freefeed.net/v1/posts/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the post to delete

### Errors

Code | JSON
--------- | -----------
403 | {"err":"You can't delete another user's post"}
404 | {"err":"Post not found"}


## Update Post

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')

post_resource = Freefeed::Post.new(client: client)

post = Freefeed::Types::PostUpdate.new( { post: { body: 'HelloWorldAgain!' } } )

post_resource.update({id: '7c70927a-4e51-49e7-bfe1-33bc4c1c0618'}, post)
```

```shell
curl "https://freefeed.net/v2/posts/7c70927a-4e51-49e7-bfe1-33bc4c1c0618"
  -X PUT
  -H "content-type: application/json"
  -H "x-authentication-token: yourFreefeedAPIToken"
  -d '{"post":{"body":"HelloWorldAgain!"}}'
```

> The above command returns JSON structured like this:

```json
{
  "posts": {
    "id": "7c70927a-4e51-49e7-bfe1-33bc4c1c0618",
    "body": "HelloWorldAgain!",
    "commentsDisabled": "0",
    "createdAt": "1539348845566",
    "updatedAt": "1539348845566",
    "commentLikes": 0,
    "ownCommentLikes": 0,
    "omittedCommentLikes": 0,
    "omittedOwnCommentLikes": 0,
    "createdBy": "920196ff-f2b0-4319-8fb2-626e4ac76d2c",
    "postedTo": [
      "28c68cc1-5bb4-40bd-9767-155c1de480a0"
    ],
    "comments": [
      
    ],
    "attachments": [
      
    ],
    "likes": [
      
    ],
    "omittedComments": 0,
    "omittedLikes": 0
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
        "posts": "10",
        "likes": "0",
        "comments": "0",
        "subscribers": "0",
        "subscriptions": "1"
      }
    }
  ],
  "subscriptions": [
    {
      "id": "28c68cc1-5bb4-40bd-9767-155c1de480a0",
      "name": "Posts",
      "user": "920196ff-f2b0-4319-8fb2-626e4ac76d2c"
    }
  ],
  "subscribers": [
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
        "posts": "10",
        "likes": "0",
        "comments": "0",
        "subscribers": "0",
        "subscriptions": "1"
      }
    }
  ],
  "comments": [
    
  ],
  "attachments": [
    
  ]
}
```

This endpoint updates a specific post.

### HTTP Request

`PUT https://freefeed.net/v1/posts/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the post to update

### JSON Body Parameters

Parameter | Type | Required | Description
--------- | ----------- | ----------- | -----------
post | [PostUpdate](#postupdate) | Yes | See PostUpdate

### PostUpdate

At least one parameter required!

Parameter | Type | Required | Description
--------- | ----------- | ----------- | -----------
body | String | No | A body of the post. Must include at least one \S character
attachments | Array of UID | No | Array of previously uploaded attachmets ids
feeds | Array of String | No | Array of username and/or groupnames where the post should be posted to

## Like Post

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')
post_resource = Freefeed::Post.new(client: client)

post_resource.like(id: 'b4a6aca7-c0e0-4b84-a586-30abbf8c29b2')
```

```shell
curl "https://freefeed.net/v2/posts/b4a6aca7-c0e0-4b84-a586-30abbf8c29b2/like"
  -H "x-authentication-token: yourFreefeedAPIToken"
  -X POST
```

> The above command returns empty JSON:

```json
{}
```

This endpoint likes a specific post.

### HTTP Request

`POST https://freefeed.net/v2/posts/<ID>/like`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the post to like

### Errors

Code | JSON
--------- | -----------
403 | {"err":"You can't like post that you have already liked"}
403 | {"err":"You can't like your own post"}
404 | {"err":"Can't find post"}

## Unlike Post

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')
post_resource = Freefeed::Post.new(client: client)

post_resource.unlike(id: 'b4a6aca7-c0e0-4b84-a586-30abbf8c29b2')
```

```shell
curl "https://freefeed.net/v2/posts/b4a6aca7-c0e0-4b84-a586-30abbf8c29b2/unlike"
  -H "x-authentication-token: yourFreefeedAPIToken"
  -X POST
```

> The above command returns empty JSON:

```json
{}
```

This endpoint unlikes a specific post.

### HTTP Request

`POST https://freefeed.net/v2/posts/<ID>/unlike`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the post to unlike

### Errors

Code | JSON
--------- | -----------
403 | {"err":"You can't un-like post that you haven't yet liked"}
404 | {"err":"Can't find post"}

## Hide Post

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')
post_resource = Freefeed::Post.new(client: client)

post_resource.hide(id: 'b4a6aca7-c0e0-4b84-a586-30abbf8c29b2')
```

```shell
curl "https://freefeed.net/v2/posts/b4a6aca7-c0e0-4b84-a586-30abbf8c29b2/hide"
  -H "x-authentication-token: yourFreefeedAPIToken"
  -X POST
```

> The above command returns empty JSON:

```json
{}
```

This endpoint likes a specific post.

### HTTP Request

`POST https://freefeed.net/v2/posts/<ID>/hide`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the post to like

### Errors

Code | JSON
--------- | -----------
404 | {"err":"Can't find post"}

## Unhide Post

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')
post_resource = Freefeed::Post.new(client: client)

post_resource.unhide(id: 'b4a6aca7-c0e0-4b84-a586-30abbf8c29b2')
```

```shell
curl "https://freefeed.net/v2/posts/b4a6aca7-c0e0-4b84-a586-30abbf8c29b2/unhide"
  -H "x-authentication-token: yourFreefeedAPIToken"
  -X POST
```

> The above command returns empty JSON:

```json
{}
```

This endpoint unlikes a specific post.

### HTTP Request

`POST https://freefeed.net/v2/posts/<ID>/unhide`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the post to unlike

### Errors

Code | JSON
--------- | -----------
404 | {"err":"Can't find post"}












## Disable comments for Post

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')
post_resource = Freefeed::Post.new(client: client)

post_resource.disable_comments(id: 'b4a6aca7-c0e0-4b84-a586-30abbf8c29b2')
```

```shell
curl "https://freefeed.net/v2/posts/b4a6aca7-c0e0-4b84-a586-30abbf8c29b2/disableComments"
  -H "x-authentication-token: yourFreefeedAPIToken"
  -X POST
```

> The above command returns empty JSON:

```json
{}
```

This endpoint disables comments for a specific post.

### HTTP Request

`POST https://freefeed.net/v2/posts/<ID>/disableComments`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the post to like

### Errors

Code | JSON
--------- | -----------
403 | {"err":"You can't disable comments for another user's post"}
404 | {"err":"Post not found"}

## Enable comments for Post

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')
post_resource = Freefeed::Post.new(client: client)

post_resource.enable_comments(id: 'b4a6aca7-c0e0-4b84-a586-30abbf8c29b2')
```

```shell
curl "https://freefeed.net/v2/posts/b4a6aca7-c0e0-4b84-a586-30abbf8c29b2/enableComments"
  -H "x-authentication-token: yourFreefeedAPIToken"
  -X POST
```

> The above command returns empty JSON:

```json
{}
```

This endpoint enables comments for a specific post.

### HTTP Request

`POST https://freefeed.net/v2/posts/<ID>/enableComments`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the post to unlike

### Errors

Code | JSON
--------- | -----------
403 | {"err":"You can't enable comments for another user's post"}
404 | {"err":"Post not found"}
