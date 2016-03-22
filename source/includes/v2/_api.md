# RamenJS API

## `_ramen.boot()`

```javascript
_ramen.boot("09889723985786254", {
  custom_bug_image_url: "https://thecatapi.com/api/images/get?format=src"
});
```

This is the first method called. It takes two arguments:

* `organization_id`: String, required
* `options`: Object, optional

`organization_id` uniquely identifies your Ramen account. It can be found on the
Getting Started page.

`options` is where you can pass in configuration options:

### Customization Options
* `custom_bug_image_url`: See [Customization](#customization)


### Product Center Options
* `custom_trigger_id`: See [Product Center](#product-center)
* `custom_trigger_class`: See [Product Center](#product-center)
* `custom_links`: See [Product Center](#product-center)


## `_ramen.ready()`

```javascript
_ramen.ready(function() {
  window.all_your_amazing_logic();
});
```

Before RamenJS finishes booting, this method takes a
function and pushes it onto a queue.
It can be called multiple times. Once RamenJS is booted,
these callbacks will be called in the order they were pushed onto the queue.

After RamenJS finishes booting, subsequent calls to `_ramen.ready()` will
result in the function being executed immediately.


## `_ramen.identify()`

This method identifies a visitor. It **must** be called before RamenJS
will ask any questions.

There are three ways to call `_ramen.identify()`

### Anonymous Visitor

```javascript
_ramen.identify();
```

This will identify an anonymous visitor. The visitor will be tagged as such
in Ramen, and you will be able to target questions to anonymous visitors.

You can still identify Anonymous visitors even if you have [Secure Mode](#secure-mode)
enabled.

### Logged-in User 

```javascript
_ramen.identify({
  id: "12345", // Required
  email: "customer@yoursite.com", // Optional
  name: "Bugs Bunny" // Optional
});
```

This will identify a logged-in user. The user will be recorded in Ramen.

 
### Logged-in User w/ Secure Mode

```javascript
_ramen.identify({
  id: "12345",                    // Required
  email: "customer@yoursite.com", // Optional
  name: "Bugs Bunny",             // Optional
  traits: user_traits             // See Custom Traits
}, {
  timestamp: 1234567890,          // Required
  auth_hash: 'CALCULATED_HASH'    // Required
});
```

This will identify a logged-in user in Secure Mode.
The user will be recorded in Ramen.

See [Secure Mode](#secure-mode) for more information.
 

## `_ramen.group()`

```javascript
_ramen.group({
  id: "1234567890",             // Required
  name: "Customer, Inc.",       // Required
  url: "https://customer.com"   // Optional
  traits: company_traits        // See Custom Traits
});
```

This will assign an `identify`'d user to a "Company" inside of Ramen.

### Secure Mode

Even with Secure Mode enabled, you do not need to pass an additional
object to `_ramen.group()` with the `auth_hash`.


## `_ramen.track()`

```javascript
_ramen.track('Logged-in pageview');
```

This will track a named event that can be used to target a question.
You can, for example, target questions at Logged-in Users that have
been customers for under 1 day with more than 100 Logged-in pageviews.

You cannot pass any other options to `_ramen.track()`.


## `_ramen.ask()`

```javascript
_ramen.ask("QUESTION_ID");

This will trigger a question to be asked of the currently
`identify`'d user, but ONLY if they have not already been asked
that question.

### Force ask

```javascript
_ramen.ask("QUESTION_ID", {force: true});
```

This will force a question to be asked regardless of whether or
not the currently `identify`'d user has already been asked this
question. This can be handy for certain workflow questions
(eg. "Why are you canceling your account?").



## `_ramen.page()`

```javascript
_ramen.page();
```

This records a pageview. You cannot pass it any arguments. It will
look at the current value of `window.location`, pass that value to
Ramen, and check to see if the user is eligible to be asked a question.


## `_ramen.reset()

```javascript
_ramen.reset();
```

This will clear the current user. Useful to use when a user logs out
of your application.
