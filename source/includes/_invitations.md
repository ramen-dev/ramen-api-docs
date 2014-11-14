# Invitations

## The invitation object
```shell 
EXAMPLE OBJECT

{
  "recipient_email":"user@example.com",
  "invitation_type":"kitchen_open_invite",
  "used_at":null,
  "meta_data":{ "title":"product developer", "name": "User", "segmet": "beta"},
  "used":false,
  "id":"545ea888646d6115461d0000",
  "object":"invitation"
}
```

```ruby
EXAMPLE OBJECT

#<Ramen::Invitation:0x3fd621b79314 id=54605542646d61117b020000> JSON: {
  "id": "54605542646d61117b020000",
  "recipient_email": "user@example.com",
  "invitation_type": "kitchen_open_invite",
  "used_at": null,
  "meta_data": { "title":"product developer", "name": "User", "segmet": "beta"},
  "used": false,
  "object": "invitation"
```

Attribute           | Description
--------------------|------------
id                  | string. Primary ID
object              | string. Value is "invitation"
recipient_email     | string. Email address for invitation.
invitation_type     | string. Must be one of: "team", "champion", "kitchen", "kitchen_open_invite", "org_open_invite", "kitchen_team", "kitchen_customer".
used_at             | timestamp. When used.
used                | boolean.
meta_data           | hash. Hash containing addition fields.
meta_data - name    | string. Name displayed on Ramen profile.
meta_data - title   | string. Title displayed on Ramen profile.
meta_data - segment | string. Ramen segment applied to invite.


## Create an invitation

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
  "invitation_type": "kitchen_open_invite",
  "used_at": null,
  "meta_data": {},
  "used": false,
  "object": "invitation"
}

--- or ---

# raises error
#<Ramen::InvalidRequestError: (Status 404) recipient_email already invited>
```

### HTTP Request
`POST /api/v1/invitations`

### Arguments
Parameter           | &nbsp;
------------------- | -----------
recipient_email     | required.
invitation_type     | required. Possible values, "team", "champion", "kitchen", "kitchen_open_invite", "org_open_invite", "kitchen_team", "kitchen_customer"
meta_data           | optional.
meta_data - name    | optional. 
meta_data - title   | optional. 
meta_data - segment | optional.

### HTTP Response
Returns Invitation object or raises an error.

## List invitations

```shell
$ curl \
  -H "Content-Type: application/json" \
  -H "RAMEN_CLIENT_ID: 123" \
  -H "RAMEN_CLIENT_SECRET: abc" \
  https://ramen.is/api/v1/invitations

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

### Arguments 
None.

### HTTP Response
Returns list of Invitation objects.

## Retrieve an invitation
```shell
$ curl \
  -H "Content-Type: application/json" \
  -H "RAMEN_CLIENT_ID: 123" \
  -H "RAMEN_CLIENT_SECRET: abc" \
  https://ramen.is/api/v1/invitations/54606182646d61258a030000

{
  "recipient_email": "user+2@gamil.com",
  "invitation_type": "kitchen_open_invite",
  "used_at": "2014-11-09T23:59:13-07:00",
  "meta_data": {},
  "used": true,
  "id": "54606182646d61258a030000",
  "object": "invitation"
}
```

```ruby
invitation = Ramen::Invitation.retrieve(id: "54606182646d61258a030000")

invitation.inspect

#<Ramen::Invitation:0x3fd621b80434 id=54606182646d61258a030000> JSON: {
  "id": "54606182646d61258a030000",
  "recipient_email": "user+2@gmail.com",
  "invitation_type": "kitchen_open_invite",
  "used_at": "2014-11-09T23:59:13-07:00",
  "meta_data": {},
  "used": true,
  "object": "invitation"
}
```

### HTTP Request
`GET api/v1/invitations/:id`

### Arguments 
Parameters | &nbsp;
-----------|-------
id | required.

### HTTP Response
Returns Invitation object or raises error.

## Update an invitation
```shell
$ curl \
  -X PUT
  -H "Content-Type: application/json" \
  -H "RAMEN_CLIENT_ID: 123" \
  -H "RAMEN_CLIENT_SECRET: abc" \
  -d '{ "meta_data": { "name": "new name" } }'
  https://ramen.is/api/v1/invitations/54606182646d61258a030000

{
  "recipient_email": "user+2@gamil.com",
  "invitation_type": "kitchen_open_invite",
  "used_at": "2014-11-09T23:59:13-07:00",
  "meta_data": {"name": "new name"},
  "used": true,
  "id": "54606182646d61258a030000",
  "object": "invitation"
}
```

```ruby
invitation = Ramen::Invitation.retrieve(id: "54606182646d61258a030000")
invitation.meta_data = {name: "new name"}
invitation.save

invitation.inspect

#<Ramen::Invitation:0x3fd621b80434 id=54606182646d61258a030000> JSON: {
  "id": "54606182646d61258a030000",
  "recipient_email": "user+2@gmail.com",
  "invitation_type": "kitchen_open_invite",
  "used_at": "2014-11-09T23:59:13-07:00",
  "meta_data": {"name": "new name"},
  "used": true,
  "object": "invitation"
}
```

### HTTP Request
`PUT api/v1/invitations/:id`

### Arguments
Same arguments as creating an invitation. See <a href="#create-an-invitation">Create an invitation</a>

### HTTP Response
Returns Invitation object or raises error.

## Delete an invitation
```shell
$ curl \
  -X DELETE
  -H "Content-Type: application/json" \
  -H "RAMEN_CLIENT_ID: 123" \
  -H "RAMEN_CLIENT_SECRET: abc" \
  https://ramen.is/api/v1/invitations/54606182646d61258a030000

{
  "deleted": "true",
  "id": "54606182646d61258a030000"
}
```

```ruby
invitation = Ramen::Invitation.retrieve(id: "54606182646d61258a030000")
invitation.delete

invitation.inspect

#<Ramen::Invitation:0x3fd621b80434 id=54606182646d61258a030000> JSON: {
  "deleted": true,
  "id": "54606182646d61258a030000"
}
```

### HTTP Request
`DELETE api/v1/invitations/:id`

### Arguments
Parameters | &nbsp;
-----------|-------
id | required.

### HTTP Response
Returns JSON with deleted object's primary ID.