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
## Get a specific feature
## List features
## Update a feature
## Delete a feature



# Invitations

## Create invitation

```shell
curl \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{ "client_id": "123", "client_secret": "abc", "invitation" : {"email": "user@example.com", "type": "kitchen"} }' \
  https://ramen.is/api/v1/projects/:project_slug/invitations

{"status" : "sent"}

{"error" : "email already invited"}
```

```ruby
Ramen.send_invitation(email: "new-user@example.com", type: "kitchen")

{"status" : "sent"}

{"error" : "email already invited"}
```

### HTTP Request

`POST /api/v1/projects/:project_slug/invitations`

### JSON Body Parameters

Parameter | Description
--------- | -----------
Required API Parameters | <a href="#required-api-parameters">link to section</a>
email | Email address (required)
type | Invitation type (required). Possible values, "team", "champion", "kitchen", "kitchen_open_invite", "kitchen_team", "kitchen_customer"
name | Name displayed on Ramen profile (optional). For example, "First Last".
title | Title displayed on Ramen profile (optional)
label | Apply Ramen label to invite and user when they join (optional)
note | Text included in email (optional)

### HTTP Response - Success

Parameter | Description
----------|------------
status | sent


### HTTP Response - Error

Parameter | Description
----------|------------
error | email address already invited


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

### HTTP Request`

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


## List all invites

```shell
$ curl \
https://ramen.is/api/:version/projects/:project_slug/invitations?client_id<id>&client_secret=<secret>

[
  { "invitation": 
    { "recipient_email" : "team_member@example.com",
      "invitation_type" : "kitchen_team",
      "used_at" : null,
      "used" : false,
      "id" : "544bf712646d614812000000"
    }
  },
  { "invitation":
    { "recipient_email" : "user@example.com",
      "invitation_type" : "kitchen_customer",
       "used_at" : "2014-10-23T23:55:26-06:00", 
       "used" : true,
      "id" : "544bf72a646d614812030000"
    }
  }
]
```

```ruby
Ramen.list_invitations

[
  { "invitation": 
    { "recipient_email" : "team_member@example.com",
      "invitation_type" : "kitchen_team",
      "used_at" : null,
      "used" : false,
      "id" : "544bf712646d614812000000"
    }
  },
  { "invitation":
    { "recipient_email" : "user@example.com",
      "invitation_type" : "kitchen_customer",
      "used_at" : "2014-10-23T23:55:26-06:00", 
       "used" : true,
      "id" : "544bf72a646d614812030000"
    }
  }
]

```

### HTTP Request`

`GET /api/v1/projects/:project_slug/invitations`

### URL Parameters

Parameter | Description
--------- | -----------
Required API Parameters | <a href="#required-api-parameters">link to section</a>

### HTTP Response

Parameter | Description
----------|------------
invitation | Object type 
recipient_email | Email addresss invitation sent to 
invitation_type | Invitation type
used_at | DateTime value at which invitation was used
used | Boolean indication if invitation has been used
id | Primary ID of the invitation object 


## List accepted invites

```shell
$ curl \
https://ramen.is/api/:version/projects/:project_slug/invitations/accepted?client_id<id>&client_secret=<secret>

[
  { "invitation":
    { "recipient_email" : "user@example.com",
      "invitation_type" : "kitchen_customer",
       "used_at" : "2014-10-23T23:55:26-06:00", 
       "used" : true,
      "id" : "544bf72a646d614812030000"
    }
  }
]
```

```ruby
Ramen.accepted_invitations

[
  { "invitation":
    { "recipient_email" : "user@example.com",
      "invitation_type" : "kitchen_customer",
      "used_at" : "2014-10-23T23:55:26-06:00", 
       "used" : true,
      "id" : "544bf72a646d614812030000"
    }
  }
]

```

### HTTP Request`

`GET /api/v1/projects/:project_slug/invitations/accepted`

### URL Parameters

Parameter | Description
--------- | -----------
Required API Parameters | <a href="#required-api-parameters">link to section</a>

### HTTP Response

Parameter | Description
----------|------------
invitation | Object type 
recipient_email | Email addresss invitation sent to 
invitation_type | Invitation type
used_at | DateTime value at which invitation was used
used | Boolean indication if invitation has been used
id | Primary ID of the invitation object 


## List waiting invites
```shell
$ curl \
https://ramen.is/api/:version/projects/:project_slug/invitations/waiting?client_id<id>&client_secret=<secret>

[
  { "invitation" : 
    { "recipient_email" : "team_member@example.com",
      "invitation_type" : "kitchen_team",
      "used_at" : null,
      "used" : false,
      "id" : "544bf712646d614812000000"
    }
  }
]
```

```ruby
Ramen.list_invitations

[
  { "invitation" : 
    { "recipient_email" : "team_member@example.com",
      "invitation_type" : "kitchen_team",
      "used_at" : null,
      "used" : false,
      "id" : "544bf712646d614812000000"
    }
  }
]

```

### HTTP Request`

`GET /api/v1/projects/:project_slug/invitations/waiting`

### URL Parameters

Parameter | Description
--------- | -----------
Required API Parameters | <a href="#required-api-parameters">link to section</a>

### HTTP Response

Parameter | Description
----------|------------
invitation | Object type 
recipient_email | Email addresss invitation sent to 
invitation_type | Invitation type
used_at | DateTime value at which invitation was used
used | Boolean indication if invitation has been used
id | Primary ID of the invitation object 

## Resend an invitation

```shell
```

```ruby
```

### HTTP Request

`POST url`

### JSON Body Parameters

### HTTP Response


## Revoke an invitation

```shell
```

```ruby
```

### HTTP Request

`DELETE url`

### JSON Body Parameters

### HTTP Response






# Community Members
TODO 

# Labels
TODO

# Segments
TODO
