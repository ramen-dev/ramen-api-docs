# Features

```shell
EXAMPLE OBJECT

{
  "id": "",
  "created_at": "", 
  "updated_at": "",
  "project_id": "",
  "community_member_id": "", 
  "name": "",
  "bucket_name": "",
  "bucket_completion_date": "",
  "phase": "",
  "projected_delivery_date": "",
  "actual_delivery_date": "",
  "last_active_at": "",
  "published_at": "",
  "notified_at": "",
  "archived_at": "",
  "archival_reason": "",
  "publicly_visible": "",
  
  "updates":  [], 
  "comments": [],

  // --- ATTRIBUTES TO NOT EXPOSE VIA API

  "position": "",
  "tags": "",
  "attachment_url": "",
  "status": "",
  "from_idea_id": "",
  "instructions_to_find": "",
  "tracking_enabled": "",
  "tracking_regex_enabled": "",
  "tracking_url": "",
  "tracking_url_regex": "",
  "tracking_js_key": "",
  "used_by_user_ids": "",
  "source_id": "",

}

Attribute | Description
----------|------------
name      | string


## Create a feature

```shell
```

### HTTP Request
`POST /api/v1/projects/:project_id/features`

### HTTP Response
Returns a feature object or error.

## List features

```shell
```
### HTTP Request
`GET /api/v1/projects/:project_id/features`


### HTTP Response
Returns an array of feature objects or an error.

## Retrieve a feature

```shell
```

### HTTP Request
`GET /api/v1/projects/:project_id/features/:id`

### HTTP Response
Returns a feature object or an error.


## Update a feature

```shell
```

### HTTP Request
`PUT /api/v1/projects/:project_id/features/:id`

### HTTP Response
Returns updated feature object or an error.

## Delete a feature

```shell
```
### HTTP Request
`DELETE /api/v1/projects/:project_id/features/:id`

### HTTP Response
Returns JSON with deleted object's primary ID.
