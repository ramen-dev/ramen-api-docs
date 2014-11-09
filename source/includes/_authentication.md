# Authentication

```shell
curl \
  -H "Content-Type: application/json" \
  -H "RAMEN_CLIENT_ID: 123" \
  -H "RAMEN_CLIENT_SECRET: abc" \
  https://ramen.is/api/v1/....
```

```ruby
Ramen.client_id = "your_client_id"
Ramen.client_secret = "your_client_secret"
```

Ramen uses API keys to authenticate API requests. 

You can create and revoke API keys within each Kitchen on the API keys page, 
`/projects/:project-slug/kitchen/api_keys`. Each API key is scoped to only 
access its respective Kitchen. You cannot use one API key to access 
two different Kitchens.

If you're using the API through simple HTTP requests, you'll need to provide 
the `client_id` and `client_secret` in each request as HTTP headers.

If you're using the Ruby client, you need to set the `client_id` and 
`client_secret` at initialization.

Value | Description
----- | -----------
client_id | Api Key client_id
client_secret | Api Key client_secret