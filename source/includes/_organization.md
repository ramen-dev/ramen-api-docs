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
  "id" : "123", 
  "site_url": "", 
  "cname": "", 
  "publicly_visible": "", 
  "trial_end_date": "", 
  "plan": "", 
  "open_invite_enabled": "",
  "create_at": "", 
  "updated_at": "",  

  // --- ATTRIBUTES TO NOT EXPOSE VIA API

  "user_id": "", 
  "logo": ""
}
```

Attribute           | Description
--------------------|------------
** rough draft. see example object. **

## Retrieve an organization

```shell
$ curl \
  -H "Content-Type: application/json" \
  -H "RAMEN_API_KEY: abc" \
  https://ramen.is/api/v1/organization
```

```ruby
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
`PUT /api/v1/organization`

### HTTP Response
Returns updated organization object or error.
