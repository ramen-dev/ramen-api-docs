# Secure Mode

```html
<script>
  _ramen.identify({
    email: 'ryan@ramen.is',
    id: 42,
    name: 'Ryan Angilly'
  }, {
    timestamp: 1234567890,
    auth_hash: '09cc0a69233f1bf41e68ed00b9256fde5a4542e9fdba635fe2a9a4edf9ee1ba1'
  });
</script>
```

Secure Mode ensures that nobody can spoof being one
of your customers. It is disabled by default, because
it takes a little extra developer time to setup
correctly.

To enable secure mode, you need to add another argument
to your `_ramen.identify()` call. This argument
is an object with the following attributes:

* `timestamp`: The current time in epoch seconds
* `auth_hash`: A SHA-256 hash

### Timestamp

```ruby
ts = Time.now.to_i
```

```javascript
ts = Math.floor(new Date()) / 1000)
```

The `timestamp` attribute must be a time within the last
15 minutes.

### Calculating `auth_hash`

```ruby
array = []
array << "ryan@ramen.is"
array << 42
array << "Ryan Angilly"
array << 1234567890
array << "oihs9uhasdg8934y8"
str = array.join(":")
digest = (Digest::SHA256.new << str).to_s
digest #=> "09cc0a69233f1bf41e68ed00b9256fde5a4542e9fdba635fe2a9a4edf9ee1ba1"
```

The hash is calculated as follows:

1. Create an array with the following elements:
  * `email`: eg. `"ryan@ramen.is"`
  * `id`: eg. `42`
  * `name`: eg. `Ryan Angilly`
  * `timestamp`: eg. `1234567890`
  * `ORGANIZATION_SECRET_KEY`:  eg. `oihs9uhasdg8934y8`

2. Your array now looks like this:
`["ryan@ramen.is", 42, "Ryan Angilly", 1234567890, "oihs9uhasdg8934y8"`

3. Join the elements of that array together with a
colon (`:`) into a string

4. Your string is now: `"ryan@ramen.is:42:Ryan Angilly:1234567890:oihs9uhasdg8934y8"`

5. Generate a SHA256 hash from that string

6. The SHA256 hash for the string in step 4 is:
`09cc0a69233f1bf41e68ed00b9256fde5a4542e9fdba635fe2a9a4edf9ee1ba1`

