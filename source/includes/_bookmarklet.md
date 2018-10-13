# Bookmarklet

## Create Bookmarklet

```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')
bookmarklet_resource = Freefeed::Bookmarklet.new(client: client)
bookmarklet = Freefeed::Types::Bookmarklet.new(
  title: 'New Post',
  comment: 'First comment',
  image: 'http://example.com/image.jpeg'
)
bookmarklet_resource.create(bookmarklet)
```

```shell
curl "https://freefeed.net/v1/bookmarklet"
  -H "x-authentication-token: yourFreefeedAPIToken"
  -H "content-type: application/json"
  -d '{"Title":"New Post","comment":"First comment","image":"http://example.com/image.jpeg"}'
```

> The above command returns JSON structured like this:

```json
{
  "posts": {
    "id": "7ef5649e-ef13-4a26-aeee-e9c33d94cd0f",
    "body": "New Post",
    "commentsDisabled": "0",
    "createdAt": "1539429526882",
    "updatedAt": "1539429526882",
    "commentLikes": 0,
    "ownCommentLikes": 0,
    "omittedCommentLikes": 0,
    "omittedOwnCommentLikes": 0,
    "createdBy": "920196ff-f2b0-4319-8fb2-626e4ac76d2c",
    "postedTo": [
      "28c68cc1-5bb4-40bd-9767-155c1de480a0"
    ],
    "comments": [
      "ebf22ee2-8825-420e-9e0a-b7eaf2f669f9"
    ],
    "attachments": [
      "f508e4f2-bc0d-4648-a364-fd004ef30a26"
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
      "screenName": "youru FUNNY sername",
      "isPrivate": "0",
      "isProtected": "0",
      "createdAt": "1538770654480",
      "updatedAt": "1538770654480",
      "type": "user",
      "description": "",
      "profilePictureLargeUrl": "",
      "profilePictureMediumUrl": "",
      "statistics": {
        "posts": "11",
        "likes": "0",
        "comments": "4",
        "subscribers": "0",
        "subscriptions": "2"
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
        "posts": "11",
        "likes": "0",
        "comments": "4",
        "subscribers": "0",
        "subscriptions": "2"
      }
    }
  ],
  "comments": [
    {
      "id": "ebf22ee2-8825-420e-9e0a-b7eaf2f669f9",
      "body": "First comment",
      "createdAt": "1539429527056",
      "updatedAt": "1539429527056",
      "hideType": 0,
      "likes": 0,
      "hasOwnLike": false,
      "createdBy": "920196ff-f2b0-4319-8fb2-626e4ac76d2c"
    }
  ],
  "attachments": [
    {
      "id": "f508e4f2-bc0d-4648-a364-fd004ef30a26",
      "fileName": "1fd58ad4-4ce4-47dd-a91c-0a6ddfb31ccb.jpg",
      "fileSize": "42494",
      "url": "https:\/\/media.freefeed.net\/attachments\/f508e4f2-bc0d-4648-a364-fd004ef30a26.jpg",
      "thumbnailUrl": "https:\/\/media.freefeed.net\/attachments\/f508e4f2-bc0d-4648-a364-fd004ef30a26.jpg",
      "imageSizes": {
        "o": {
          "w": 350,
          "h": 175,
          "url": "https:\/\/media.freefeed.net\/attachments\/f508e4f2-bc0d-4648-a364-fd004ef30a26.jpg"
        }
      },
      "mediaType": "image",
      "createdAt": "1539429526723",
      "updatedAt": "1539429526723",
      "createdBy": "920196ff-f2b0-4319-8fb2-626e4ac76d2c"
    }
  ]
}
```

This endpoint creates a post (optionally with a comment and an attachment).

### HTTP Request

Multipart upload request:

`POST https://freefeed.net/v1/bookmarklet`

### JSON Body Parameters

Parameter | Type | Required | Description
--------- | ----------- | ----------- | -----------
title | String | Yes | A body of the post. Must include at least one \S character
comment | String | No | First comment to the post
image | String | No | URL of an image attachment to the post
images | Array of String | No | Array or URLs of image attachments to the post
meta | [MetaBookmarklet](#metabookmarklet) | No | 

### MetaBookmarklet

Parameter | Type | Required | Description
--------- | ----------- | ----------- | -----------
feeds | String or Array of String | Yes | Username or groupname or array of username and/or groupnames which the post should be posted to
