---
title: Ramen API Reference
language_tabs:
  - shell
  - ruby
includes:
  - errors
search: true
---

# Introduction

Welcome to the Ramen API! 

# Authentication

  Ramen uses API keys to authenticate API requests. 

  You can create and revoke API keys within each Kitchen on the API keys page, `/projects/{{project_name}}/kitchen/api_keys`. Each API key is scoped to only access within its respective Kitchen. You cannot use one API key to access two different Kitchens.

# Required API Parameters

During each of the API requests, you'll need to provide the following URL params, 

URL Parameters

Parameter | Description
--------- | -----------
version | API version (defaults to, "v1")
project_slug | Project slug as it appears in URL
client_id | The client_id
client_secret | The client_secret

The Ruby client library sets these required fields as initialization:

```ruby
Ramen.configure do |c|
  c.client_id = "your_client_id"
  c.client_secret = "your_client_secret"
  c.project_slug = "your-project-name"
  c.api_version = "v1" # default 
end


```

# Project

## Basic Info

Get basic project info.

### HTTP Request

`GET https://ramen.is/api/v1/project/`

<aside class="success">
</aside>

# Features


`CREATE`

```json
{
  "feature" : {
    "name" : "New Awesome Feature"
  }
}
```

`SHOW`

`LIST`

`UPDATE`

`DELETE`


## Get a specific feature
## List features
## Update a feature
## Delete a feature



# Invitations

## Create invitation


## Search for invitation


```shell
$ curl \
https://ramen.is/api/:version/projects/:project_slug/invitations/find?client_id<id>&client_secret=<secret>&email=user%40example.com

{ "invitation":
  { "recipient_email" : "user@example.com",
    "invitation_type" : "kitchen_customer",
    "used_at" : null,
    "used" : false,
    "id" : "544bf72a646d614812030000"
  }
}
```

```ruby
Ramen.find_invitation({email: 'user@example.com'})

{ "invitation":
  { "recipient_email" : "user@example.com",
    "invitation_type" : "kitchen_customer",
    "used_at" : null,
    "used" : false,
    "id" : "544bf72a646d614812030000"
  }
}
```

### HTTP Request

`GET /api/v1/projects/:project_slug/invitations/find`

### URL Parameters

Parameter | Description
--------- | -----------
Required API Parameters | <a href="#required-api-parameters">link to section</a>
email | Email address to search by

### HTTP Response

Parameter | Description
----------|------------
invitation | Object type
recipient_email | Email addresss invitation sent to 
invitation_type | Invitation type
used_at | DateTime value at which invitation was used
used | Boolean indication if invitation has been used
id | Primary ID of the invitation object 

## List invites
## Update an invite
## Revoke or delete an invite

# Community Members

# Labels

# Segments

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import 'kittn'

api = Kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/3"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Isis",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the cat to retrieve

