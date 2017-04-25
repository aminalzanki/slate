---
title: Eagle API

language_tabs:
  - cURL

includes:
  - errors

search: true
---

# Introduction

Welcome to the Eagle API. This API documentation is created to ease and breeze the communication and process of development team.

This API documentation should be used internally within Eagle development team only. So it is restricted to expose this API documentation to public.

The API can be access via:

`https://api.eagle.com/v1`

`Authorization: Bearer YOUR_API_TOKEN`

# Authentication

## Login via Email

```shell
curl
  -H "Content-Type: application/json"
  -X POST
  -d '{"email": "nik@eagle.com", "password": "12345678", "latitude": 3.075213, "longitude": 101.6469241}'
  ENDPOINT
```

> The above command returns JSON structured like this:

```json
{
  "status": true,
  "message": "You have successfully registered.",
  "auth_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9",
  "user": {
    "id": 17,
    "email": "nik@eagle.com",
    "latitude": 3.075213,
    "longitude": 101.6469241,
    "state": "Kuala Lumpur",
    "created_at": "2017-01-08T11:19:42.776+08:00",
    "updated_at": "2017-01-08T11:19:42.790+08:00",
    "is_admin": false,
    "is_super_admin": false,
    "pass_code": "1234"
  }
}
```

This endpoint to sign in existing user.

### HTTP Request

`POST /signin`

### Data Parameters

Parameter | Description
--------- | ------- | -----------
email | User email.
password | User password. Minimum length is 8 characters.

## Logout

```shell
curl
  -H "Authorization: Bearer <token>"
  -H "Content-Type: application/json"
  -X DELETE
  -d '{"id": 17}'
  ENDPOINT
```

> The above command returns JSON structured like this:

```json
{
  "status": true,
  "message": "Logout successfully"
}
```

This endpoint to sign out user.

### HTTP Request

`DELETE /account`

### Data Parameters

Parameter | Description
--------- | ------- | -----------
id | User id.

<!-- ========== SURVEY ========== -->

# Survey

## Get all survey

```shell
curl
  -H "Authorization: Bearer <token>"
  -H "Content-Type: application/json"
  -X GET
  ENDPOINT
```

> The above command returns JSON structured like this:

```json
{
    "status": true,
    "message": "Survey successfully retrieved",
    "surveys": [
        {
            "id": 1,
            "questionnaire": [
                {
                    "id": 1,
                    "question": "This is the first question statement",
                    "type": 1
                },
                {
                    "id": 2,
                    "question": "This is the second question statement",
                    "type": 2
                },
                {
                    "id": 3,
                    "question": "This is the third question statement",
                    "type": 3
                }
            ]
        },
        {
            "id": 2,
            "questionnaire": [
                {
                    "id": 1,
                    "question": "This is the first question statement",
                    "type": 1
                },
                {
                    "id": 2,
                    "question": "This is the second question statement",
                    "type": 2
                },
                {
                    "id": 3,
                    "question": "This is the third question statement",
                    "type": 3
                }
            ]
        }
    ]
}
```

This endpoint to sign up new user via email.

### HTTP Request

`GET /surveys`

## Get single survey

```shell
curl
  -H "Authorization: Bearer <token>"
  -H "Content-Type: application/json"
  -X GET
  ENDPOINT
```

> The above command returns JSON structured like this:

```json
{
    "status": true,
    "message": "Survey successfully retrieved",
    "surveys": {
        "id": 1,
        "questionnaire": {
            "id": 1,
            "question": "This is the first question statement",
            "type": 1
        }
    }
}
```

This endpoint to sign up new user via email.

### HTTP Request

`GET /surveys/<id>`

## Submit all surveys

```shell
curl
  -H "Authorization: Bearer <token>"
  -H "Content-Type: application/json"
  -X GET
  ENDPOINT
```

> The above command returns JSON structured like this:

```json
{
    "status": true,
    "message": "Successfully submitted surveys",
    "surveys": [
        {
            "id": 1,
            "questionnaire": [
                {
                    "id": 1,
                    "answer": 1
                },
                {
                    "id": 2,
                    "answer": 2
                },
                {
                    "id": 3,
                    "answer": 3
                }
            ]
        },
        {
            "id": 2,
            "questionnaire": [
                {
                    "id": 1,
                    "answer": 1
                },
                {
                    "id": 2,
                    "answer": 2
                },
                {
                    "id": 3,
                    "answer": 3
                }
            ]
        }
    ]
}
```

This endpoint to sign up new user via email.

### HTTP Request

`POST /user/<id>/surveys`

<!-- SITUATION REPORT -->

# Situation Report

## Get all SitRep

```shell
curl
  -H "Authorization: Bearer <token>"
  -H "Content-Type: application/json"
  -X GET
  ENDPOINT
```

> The above command returns JSON structured like this:

```json
{
    "status": true,
    "message": "Situation reports successfully retrieved",
    "reports": [
        {
            "id": 1,
            "title": "Accident happened at KLCC",
            "description": "It happened between Honda CRV and Lorry. 2 dead bodies found, 5 serious injured.",
            "address": "Kuala Lumpur Convention Center",
            "latitude": 3.075213,
            "longitude": 101.6469241,
            "media": {
                "image": [
                    {
                        "url": "http://.../image1.jpg"
                    },
                    {
                        "url": "http://.../image2.jpg"
                    },
                    {
                        "url": "http://.../image3.jpg"
                    }
                ],
                "video": {
                    "url": "http://.../video.mp4"
                },
                "audio": {
                    "url": "http://.../audio.mp3"
                }
            }
        },
        {
            "id": 2,
            "title": "Loop hole at Old Klang Road",
            "description": "Big loop hole nearby KFC Old Klang Road.",
            "address": "KFC Old Klang Road",
            "latitude": 3.075213,
            "longitude": 101.6469241,
            "media": {
                "image": [
                    {
                        "url": "http://.../image1.jpg"
                    },
                    {
                        "url": "http://.../image2.jpg"
                    },
                    {
                        "url": "http://.../image3.jpg"
                    }
                ],
                "video": {
                    "url": "http://.../video.mp4"
                },
                "audio": {
                    "url": "http://.../audio.mp3"
                }
            }
        }
    ]
}
```

This endpoint to sign up new user via email.

### HTTP Request

`GET /reports`

## Create new SitRep

```shell
curl
  -H "Authorization: Bearer <token>"
  -H "Content-Type: application/json"
  -X POST
  -d '{"title":"Accident happened at KLCC","description":"It happened between Honda CRV and Lorry. 2 dead bodies found, 5 serious injured." ,"address":"Kuala Lumpur Convention Center","latitude":3.075213,"longitude":101.6469241,"media":"....base64...."}'
  ENDPOINT
```

> The above command returns JSON structured like this:

```json
{
    "status": true,
    "message": "Report successfully created",
    "reports": {
        "title": "Accident happened at KLCC",
        "description": "It happened between Honda CRV and Lorry. 2 dead bodies found, 5 serious injured.",
        "address": "Kuala Lumpur Convention Center",
        "latitude": 3.075213,
        "longitude": 101.6469241,
        "media": {
            "image": [
                {
                    "url": "http://.../image1.jpg"
                },
                {
                    "url": "http://.../image2.jpg"
                },
                {
                    "url": "http://.../image3.jpg"
                }
            ],
            "video": {
                "url": "http://.../video.mp4"
            },
            "audio": {
                "url": "http://.../audio.mp3"
            }
        }
    }
}
```

This endpoint to create new vehicle

### HTTP Request

`POST /users/<id>/report`

<!-- PRU -->

# Election

## Get all voting post

```shell
curl
  -H "Authorization: Bearer <token>"
  -H "Content-Type: application/json"
  -X GET
  ENDPOINT
```

> The above command returns JSON structured like this:

```json
{
    "status": true,
    "message": "Votes successfully updated",
    "posts": [
        {
            "id": 1,
            "parliament": "Kuala Lumpur",
            "post": "Pantai Dalam",
            "parties": [
                {
                    "id": 1,
                    "name": "UMNO",
                    "vote": 100
                },
                {
                    "id": 2,
                    "name": "PAS",
                    "vote": 100
                },
                {
                    "id": 3,
                    "name": "PKR",
                    "vote": 100
                },
                {
                    "id": 4,
                    "name": "AMANAH",
                    "vote": 100
                },
                {
                    "id": 5,
                    "name": "DAP",
                    "vote": 100
                }
            ]
        },
        {
            "id": 2,
            "parliament": "Kuala Lumpur",
            "post": "Setiawangsa",
            "parties": [
                {
                    "id": 1,
                    "name": "UMNO",
                    "vote": 100
                },
                {
                    "id": 2,
                    "name": "PAS",
                    "vote": 100
                }
            ]
        }
    ]
}
```

This endpoint to sign up new user via email.

### HTTP Request

`GET /votes`

## Update votes

```shell
curl
  -H "Authorization: Bearer <token>"
  -H "Content-Type: application/json"
  -X POST
  -d '{"id":1, "parties":[{"id":1,"votes":100},{"id":2,"votes":100}]}'
  ENDPOINT
```

> The above command returns JSON structured like this:

```json
{
    "status": true,
    "message": "Votes successfully updated",
    "posts": [
        {
            "id": 1,
            "parliament": "Kuala Lumpur",
            "post": "Pantai Dalam",
            "parties": [
                {
                    "id": 1,
                    "name": "UMNO",
                    "vote": 100
                },
                {
                    "id": 2,
                    "name": "PAS",
                    "vote": 100
                },
                {
                    "id": 3,
                    "name": "PKR",
                    "vote": 100
                },
                {
                    "id": 4,
                    "name": "AMANAH",
                    "vote": 100
                },
                {
                    "id": 5,
                    "name": "DAP",
                    "vote": 100
                }
            ]
        },
        {
            "id": 2,
            "parliament": "Kuala Lumpur",
            "post": "Setiawangsa",
            "parties": [
                {
                    "id": 1,
                    "name": "UMNO",
                    "vote": 100
                },
                {
                    "id": 2,
                    "name": "PAS",
                    "vote": 100
                }
            ]
        }
    ]
}
```

This endpoint to create new vehicle

### HTTP Request

`POST /users/<id>/report`
