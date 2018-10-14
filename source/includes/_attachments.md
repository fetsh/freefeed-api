# Attachments

## Create Attachment
```ruby
require 'freefeed'

client = Freefeed::Client.new('yourFreefeedAPIToken')
Freefeed::Attachment.create(
  client,
  file: Faraday::UploadIO.new("/path/to/your/file.jpg", 'image/jpeg')
)
```

```shell
curl "https://freefeed.net/v1/attachments"
  -H "x-authentication-token: yourFreefeedAPIToken"
  -F "file=@/path/to/your/file.jpg"
```

> The above command returns JSON structured like this:

```json
{
  "attachments": {
    "id": "dd2f5eaa-dad8-439a-93cc-6bdcf74ecee0",
    "fileName": "file.jpg",
    "fileSize": 75694,
    "url": "https:\/\/media.freefeed.net\/attachments\/dd2f5eaa-dad8-439a-93cc-6bdcf74ecee0.jpg",
    "thumbnailUrl": "https:\/\/media.freefeed.net\/attachments\/thumbnails\/dd2f5eaa-dad8-439a-93cc-6bdcf74ecee0.jpg",
    "imageSizes": {
      "o": {
        "w": 700,
        "h": 465,
        "url": "https:\/\/media.freefeed.net\/attachments\/dd2f5eaa-dad8-439a-93cc-6bdcf74ecee0.jpg"
      },
      "t": {
        "w": 263,
        "h": 175,
        "url": "https:\/\/media.freefeed.net\/attachments\/thumbnails\/dd2f5eaa-dad8-439a-93cc-6bdcf74ecee0.jpg"
      },
      "t2": {
        "w": 527,
        "h": 350,
        "url": "https:\/\/media.freefeed.net\/attachments\/thumbnails2\/dd2f5eaa-dad8-439a-93cc-6bdcf74ecee0.jpg"
      }
    },
    "mediaType": "image",
    "createdAt": 1539380940526,
    "updatedAt": 1539380940526,
    "createdBy": "920196ff-f2b0-4319-8fb2-626e4ac76d2c"
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
  "users": [
    {
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
    }
  ]
}
```

This endpoint creates an attachment.

### HTTP Request

Multipart upload request:

`POST https://freefeed.net/v1/attachments`

### Post payload

Parameter | Description
--------- | -----------
file | Contents of a file to be uploaded. Must be posted using multipart/form-data in the usual way that files are uploaded via the browser.
