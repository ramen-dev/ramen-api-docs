# Buckets

```shell
EXAMPLE OBJECT

{
  "id": "",
  "created_at": "",
  "updated_at": "",
  "project_id": "",
  "name": "",
  "completion_date": ""
}
```

Attribute | Description
----------|------------
project_id | string. Associated project.
name | string. Bucket name.
completion_date | datetime. defaults to nil.



## Create a bucket 

### HTTP Request
`POST /api/v1/projects/:project_id/buckets`

### Arguments 
Parameter | &nbsp;
----------|-------
project_id | required.
name | required.
completion_date | optional.

### HTTP Response
Returns created bucket object or error(s).



## List buckets

### HTTP Request
`GET /api/v1/projects/:project_id/buckets`

### HTTP Response
Returns array of bucket objects or error(s).



## Retrive a bucket

### HTTP Request
`GET /api/v1/projects/:project_id/buckets/:id`

### HTTP Response
Returns a bucket object or error(s).



## Update a bucket

### HTTP Request
`PUT /api/v1/projects/:project_id/buckets/:id`

### HTTP Response
Returns updated bucket object or error(s).



## Delete a bucket

### HTTP Request
`DELETE /api/v1/projects/:project_id/buckets/:id`

### HTTP Response
Returns JSON with deleted object's primary ID.

