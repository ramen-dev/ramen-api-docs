# Community Members

```shell
{
  "joined_at": "",
  "type": "",
  "title": "",
  "short_bio": "",
  "last_active_at": "",
  "segments": "",
  "created_at": "", 
  "updated_at": ""

  // --- ATTRIBUTES TO NOT EXPOSE VIA API

  "level": "",
  "value": "",
  "project_ids": "",
  "gates": "",
  "last_app_active_at": ""
}
```

Attribute | Description
----------|------------
** rough draft. see example object. **

## Create a community member

Community Members are created when a user accepts an invitation.

## Retrieve a community member

```shell
```

### HTTP Request 
`GET /api/v1/community_members/:id`

### HTTP Response
Returns a community member object or raises an error.

## Update a community member

```shell
```

### HTTP Request 
`PUT /api/v1/community_members/:id`

### HTTP Response
Returns updated community member or returns an error.

## Delete a community member

```shell
```

### HTTP Request 
`DELETE /api/v1/community_members/:id`

### HTTP Response
Returns JSON with deleted object's primary ID.
