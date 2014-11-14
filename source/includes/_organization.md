# Organization

## TODOs 

<aside class="warning">
Open Questions
</aside>

- Should users be able to create organizations? 
  Weston - don't think so. 
  Api Keys will be scoped per org so creating org from other Api Keys seems to violate this separation.

- Should users be able to delete organizations?
  Weston - don't think so.
  Organizations feel like "long term" account setup stuff. I could be wrong since I'm not eating Ramen full time during the week. 

- Regarding `GET /api/v1/organization`. 
  From Weston.
  Since the Api Key is scoped per organization, for a `GET /api/v1/organization` we can look up the Organization by the API and NOT make the API call include the Organization Id.
  Is this a good idea? 
  I think so but want a 2nd opinion.

## The organization object

```shell
EXAMPLE OBJECT

{
  "id" : "123"
}
```

```ruby
EXAMPLE OBJECT

#<Ramen::Organization:0x3fd621b80434 id=54123> JSON: {
  "id": "123"
}
```

Attribute           | Description
--------------------|------------
id                  | string. Primary ID
object              | string. Value is "organization"
name                | string. Name of organization.

## Retrieve an organization

```shell
$ curl \
  -H "Content-Type: application/json" \
  -H "RAMEN_CLIENT_ID: 123" \
  -H "RAMEN_CLIENT_SECRET: abc" \
  https://ramen.is/api/v1/organization

{
  "id":"54123",
  "name":"Ramen", 
  "object":"organization"
}
```

```ruby
# don't need `id` since you default to organization associated with Api Key
organization = Ramen::Organization.retrieve()

organization.inspect

#<Ramen::Organization:0x3fd621b80434 id=54123> JSON: {
  "id": "545ea888646d6115461d0000",
  "name": "Ramen API",
  "object": "project"
}
```
### HTTP Request
`GET /api/v1/organization`

### HTTP Response
Returns an organization object or error.


## Update an orgnization 

```shell
```

```ruby
```

### HTTP Request
`PUT /api/v1/organizations/:id`

### HTTP Response
Returns updated organization object or error.
