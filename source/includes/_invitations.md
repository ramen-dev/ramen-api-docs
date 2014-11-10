# Invitations

## The Invitation Object
<!-- TODO describe the object -->

## Create

```shell
$ curl \
  -X POST \
  -H "Content-Type: application/json" \
  -H "RAMEN_CLIENT_ID: 123" \
  -H "RAMEN_CLIENT_SECRET: abc" \
  -d '{ "recipient_email": "user@example.com", "invitation_type": "kitchen_open_invite" }' \
  https://ramen.is/api/v1/invitations

HTTP 200
{
  "recipient_email":"user@example.com",
  "invitation_type":"kitchen_open_invite",
  "used_at":null,
  "meta_data":{},
  "used":false,
  "id":"545ea888646d6115461d0000",
  "object":"invitation"
}

--- or ---

HTTP 404
{
  "error": 
  {
    "message":"recipient_email already invited",
    "param":"recipient_email"
  }
}
```

```ruby
invitation = Ramen::Invitation.create(
  recipient_email: "user@example.com", 
  invitation_type: "kitchen_open_invite"
)

puts invitation.inspect

#<Ramen::Invitation:0x3fd621b79314 id=54605542646d61117b020000> JSON: {
  "id": "54605542646d61117b020000",
  "recipient_email": "user@example.com",
  "invitation_type": "kitchen",
  "used_at": null,
  "meta_data": {},
  "used": false,
  "object": "invitation"
}

--- or ---

# raises this error if recipient_email already invited
Ramen::InvalidRequestError 
```

### HTTP Request
`POST /api/v1/invitations`

### JSON Body Parameters
Parameter | Description
--------- | -----------
recipient_email | Email address (required)
invitation_type | Invitation type (required). Possible values, "team", "champion", "kitchen", "kitchen_open_invite", "org_open_invite", "kitchen_team", "kitchen_customer"
meta_data | Hash for addtional attributes (optional)
meta_data - name | Name displayed on Ramen profile (optional). For example, "First Last".
meta_data - title | Title displayed on Ramen profile (optional)
meta_data - segment | Apply Ramen label/segment to invite and user when they join (optional)

### HTTP Response
Returns Invitation object or raises an error.

## List

```shell
$ curl \
  -H "Content-Type: application/json" \
  -H "RAMEN_CLIENT_ID: 123" \
  -H "RAMEN_CLIENT_SECRET: abc" \
  http://ramen.dev/api/v1/invitations

[
  {
    "recipient_email": "user+1@example.com",
    "invitation_type": "kitchen_open_invite",
    "used_at": null,
    "meta_data": {},
    "used": false,
    "id": "545ea888646d6115461d0000",
    "object": "invitation"
  },
  {
    "recipient_email": "user+2@gamil.com",
    "invitation_type": "kitchen_open_invite",
    "used_at": "2014-11-09T23:59:13-07:00",
    "meta_data": {},
    "used": true,
    "id": "54606182646d61258a030000",
    "object": "invitation"
  }
]
```

```ruby
invitations = Ramen::Invitation.all

puts invitations.inspect

[#<Ramen::Invitation:0x3fd621b79314 id=545ea888646d6115461d0000> JSON: {
  "id": "545ea888646d6115461d0000",
  "recipient_email": "user+1@example.com",
  "invitation_type": "kitchen_open_invite",
  "used_at": null,
  "meta_data": {},
  "used": false,
  "object": "invitation"
}, #<Ramen::Invitation:0x3fd621b80434 id=54606182646d61258a030000> JSON: {
  "id": "54606182646d61258a030000",
  "recipient_email": "user+2@gmail.com",
  "invitation_type": "kitchen_open_invite",
  "used_at": "2014-11-09T23:59:13-07:00",
  "meta_data": {},
  "used": true,
  "object": "invitation"
}]
```

### HTTP Request
`GET /api/v1/invitations`

### HTTP Response
Returns list of Invitation objects.

## Show
```curl
```
```ruby
```

### HTTP Request
`GET api/v1/invitations/:id`

### HTTP Response
Returns Invitation object or raises error.

## Update
```curl
```
```ruby
```
### HTTP Request
`PUT api/v1/invitations/:id`

### HTTP Response
Returns Invitation object or raises error.

## Delete
```shell
```
```ruby
```

### HTTP Request
`DELETE api/v1/invitations/:id`

### HTTP Response
Returns JSON with deleted object's primary ID.

Parameter | Description
----------|------------
deleted | Boolean confirmation of removal
id | Primary ID of the invitation object 

