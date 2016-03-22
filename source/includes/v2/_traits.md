# Custom Traits

```javascript
_ramen.identify({
  id: "42",
  name: "Bugs Bunny",
  traits: {
    likes_carrots: true,
    ate_carrot_at: 1234567890
  }
});

_ramen.group({
  id: "421",
  name: "ACME, Inc.",
  traits: {
    employs_coyotes: false,
    ran_into_wall_at: 1234567890
  }
});

```

Both Customers and Companies can have "Traits"
assigned to them. Traits are key/value pairs
that can be used for Audience creation:

![Traits can be used to create Audiences](https://dl.dropboxusercontent.com/spa/c8k9520tqhih2dg/3mz-cobc.png)

## Names

Trait names are strings that can contain any letter,
any number, underscores (`_`) and dashes (`-`).
Trait names are case-sensitive.


## Types

Trait values can be the following types:

* String
* Boolean
* Integer
* Float
* Time (See below)

### Time types

Time types are declared by ending the trait
name in `_at`. For example:

* `last_seen_at`
* `upgraded_at`

You can pass in times in the following formats:

* Epoch seconds: `1234567890`
* XML Schema: `2009-02-13T23:31:30Z` (UTC) or
`2009-02-13T16:31:30-07:00` (with offset)

## Type Casting 

The first time RamenJS sees a new trait with a
non-null value,
it will record the type and cast all future traits
to that type.


