# Project

## The project object
```shell 
EXAMPLE OBJECT

{
  "name" : "Ramen API"
}
```

```ruby
EXAMPLE OBJECT

#<Ramen::Project:0x3fd621b79314 id=54605542646d61117b020000> JSON: {
  "id": "54605542646d61117b020000",
  "name": "Ramen API",
  "object": "project"
```

Attribute           | Description
--------------------|------------
id                  | string. Primary ID
object              | string. Value is "project"
name                | string. Name of project.


## Create a project

```shell
$ curl \
  -X POST \
  -H "Content-Type: application/json" \
  -H "RAMEN_CLIENT_ID: 123" \
  -H "RAMEN_CLIENT_SECRET: abc" \
  -d '{ "name": "Ramen API" }' \
  https://ramen.is/api/v1/projects

HTTP 200
{
  "name":"Ramen API",
  "id":"545ea888646d6115461d0000",
  "object":"project"
}

--- or ---

HTTP 404
{
  "error": 
  {
    "message":"project could not be created"
  }
}
```

```ruby
project = Ramen::Project.create(name: "Ramen API")

puts project.inspect

#<Ramen::Project:0x3fd621b79314 id=54605542646d61117b020000> JSON: {
  "id": "54605542646d61117b020000",
  "name":"Ramen API"
  "object": "project"
}

--- or ---

# raises error
#<Ramen::InvalidRequestError: (Status 404) recipient_email already invited>
```

### HTTP Request
`POST /api/v1/projects`

### Arguments
Parameter           | &nbsp;
------------------- | ---------
name                | required.

### HTTP Response
Returns Project object or raises an error.

## List projects

```shell
$ curl \
  -H "Content-Type: application/json" \
  -H "RAMEN_CLIENT_ID: 123" \
  -H "RAMEN_CLIENT_SECRET: abc" \
  https://ramen.is/api/v1/projects

[
  {
    "name": "Ramen API",
    "id": "545ea888646d6115461d0000",
    "object": "project"
  },
  {
    "name": "Mobile App",
    "id": "54606182646d61258a030000",
    "object": "project"
  }, 
  {
    "name": "Ramen",
    "id": "54606132646d61258a030000",
    "object": "project"
  }
]
```

```ruby
projects = Ramen::Project.all

puts projects.inspect

[#<Ramen::Project:0x3fd621b79314 id=545ea888646d6115461d0000> JSON: {
  "id": "545ea888646d6115461d0000",
  "name": "Ramen API",
  "object": "project"
}, #<Ramen::Project:0x3fd621b80434 id=54606182646d61258a030000> JSON: {
  "id": "54606182646d61258a030000",
  "name": "Ramen",
  "object": "project"
}]
```

### HTTP Request
`GET /api/v1/projects`

### Arguments 
None.

### HTTP Response
Returns list of Project objects.

## Retrieve a project
```shell
$ curl \
  -H "Content-Type: application/json" \
  -H "RAMEN_CLIENT_ID: 123" \
  -H "RAMEN_CLIENT_SECRET: abc" \
  https://ramen.is/api/v1/projects/545ea888646d6115461d0000

{
  "name": "Ramen API",
  "id": "545ea888646d6115461d0000",
  "object": "project"
}
```

```ruby
project = Ramen::Invitation.retrieve(id: "545ea888646d6115461d0000")

project.inspect

#<Ramen::Project:0x3fd621b80434 id=545ea888646d6115461d0000> JSON: {
  "id": "545ea888646d6115461d0000",
  "name": "Ramen API",
  "object": "project"
}
```

### HTTP Request
`GET api/v1/projects/:id`

### Arguments 
Parameters  | &nbsp;
------------|-------
id          | required.

### HTTP Response
Returns Project object or raises error.

## Update a project
```shell
$ curl \
  -X PUT
  -H "Content-Type: application/json" \
  -H "RAMEN_CLIENT_ID: 123" \
  -H "RAMEN_CLIENT_SECRET: abc" \
  -d '{ "name": "Ramen API v2"}'
  https://ramen.is/api/v1/projects/545ea888646d6115461d0000

{
  "name": "Ramen API v2",
  "id": "545ea888646d6115461d0000",
  "object": "project"
}
```

```ruby
project = Ramen::Project.retrieve(id: "54606182646d61258a030000")
project.name = "Ramen API v2"
project.save

project.inspect

#<Ramen::Project:0x3fd621b80434 id=54606182646d61258a030000> JSON: {
  "id": "54606182646d61258a030000",
  "name": "Ramen API v2",
  "object": "project"
}
```

### HTTP Request
`PUT api/v1/projects/:id`

### Arguments
Same arguments as creating a project. See <a href="#create-a-project">Create a project</a>

### HTTP Response
Returns Project object or raises error.

## Delete a project
```shell
$ curl \
  -X DELETE
  -H "Content-Type: application/json" \
  -H "RAMEN_CLIENT_ID: 123" \
  -H "RAMEN_CLIENT_SECRET: abc" \
  https://ramen.is/api/v1/project/54606182646d61258a030000

{
  "deleted": "true",
  "id": "54606182646d61258a030000"
}
```

```ruby
project = Ramen::Project.retrieve(id: "54606182646d61258a030000")
invitation.delete

invitation.inspect

#<Ramen::Project:0x3fd621b80434 id=54606182646d61258a030000> JSON: {
  "deleted": true,
  "id": "54606182646d61258a030000"
}
```

### HTTP Request
`DELETE api/v1/projects/:id`

### Arguments
Parameters  | &nbsp;
------------|-------
id          | required.

### HTTP Response
Returns JSON with deleted object's primary ID.
