# Invitations

## Create invitation

```shell
curl \
  -X POST \
  -H "Content-Type: application/json" \
  -H "RAMEN_CLIENT_ID: 123" \
  -H "RAMEN_CLIENT_SECRET: abc" \
  -d '{ "recipient_email": "user@example.com", "invitation_type": "kitchen" }' \
  https://ramen.is/api/v1/invitations

HTTP 200
{
  "recipient_email":"user@example.com",
  "invitation_type":"kitchen",
  "used_at":null,
  "meta_data":{},
  "used":false,
  "id":"545ea888646d6115461d0000",
  "object":"invitation"
}

--- or ---

HTTP 404
{
  "error":"recipient_email already invited"
}
```

```ruby
Ramen::Invitation.create(recipient_email: "user@example.com", invitation_type: "kitchen")



--- or ---

{"error":"recipient_email already invited"}
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