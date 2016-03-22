# Installation

## JavaScript

### Anonymous Visitors

```html
<script>
  !function(){var e=window._ramen=window._ramen||[];if(!e.initialize){if(e.invoked)return void(window.console&&console.error&&console.error("Ramen snippet included twice."));e.invoked=!0,e.methods=["boot","ready","identify","group","track","page","reset","ask"],e.factory=function(r){return function(){var t=Array.prototype.slice.call(arguments);return t.unshift(r),e.push(t),e}};for(var r=0;r<e.methods.length;r++){var t=e.methods[r];e[t]=e.factory(t)}var n=document.createElement("script");n.type="text/javascript",n.async=!0,n.src="https://cdn.ramen.is/assets/ramen.js";var o=document.getElementsByTagName("script")[0];o.parentNode.insertBefore(n,o)}}();

  _ramen.boot('YOUR_ORGANIZATION_ID');
  _ramen.identify()
</script>
```

You can install RamenJS in seconds by just copy/pasting code onto
any page where you want to be able to ask questions with Ramen.

New with v2.0 is our support for anonymous visitors. Prior to
v2.0, the RamenJS JavaScript snippet would need to be edited
by a developer in order to get all the information into our system,
but now you can just copy/paste a static snippet to get started.

### Logged-in users

To track logged-in users, you'll need to pass RamenJS
some information about that user. You'll need to pass
a unique ID, and optionally include their name and email.

```html
<script>
  !function(){var e=window._ramen=window._ramen||[];if(!e.initialize){if(e.invoked)return void(window.console&&console.error&&console.error("Ramen snippet included twice."));e.invoked=!0,e.methods=["boot","ready","identify","group","track","page","reset","ask"],e.factory=function(r){return function(){var t=Array.prototype.slice.call(arguments);return t.unshift(r),e.push(t),e}};for(var r=0;r<e.methods.length;r++){var t=e.methods[r];e[t]=e.factory(t)}var n=document.createElement("script");n.type="text/javascript",n.async=!0,n.src="https://cdn.ramen.is/assets/ramen.js";var o=document.getElementsByTagName("script")[0];o.parentNode.insertBefore(n,o)}}();

  _ramen.boot('YOUR_ORGANIZATION_ID');

  // To identify logged in users, you'll need to have a
  // developer take a look at everything below this line
  _ramen.identify({
    id: "REPLACE_ME-12345", // Replace with a unique user ID. Could be their email
    email: "REPLACE_ME-customer@example.com", // Replace with their email address
    name: "REPLACE_ME-Bugs Bunny" // Replace with their name
  });

  // Check out our options at http://docs.ramen.is/
</script>
```


## Segment.com

[Segment.com](https://segment.com/?utm_source=partners&utm_medium=docs&utm_campaign=ramen.is)
is a "customer data hub". If you already are
a Segment customer, you can install Ramen in just
a few clicks without needing
to write any code or deploy any changes to your application.

RamenJS supports the following Segment methods:

* `identify`
* `group`
* `track` 
* `page`

### Installation methods

Click the 'Install via Segment' button on the _Getting Started_ page of your
Ramen Organization.

Wait a couple minutes, and then head over to your application and
navigate to a page where Segment's `analytics.js` is installed.
After refreshing the page a few times, refresh your _Getting Started_ page and you
should see that RamenJS is sending data to Ramen.

You can read more about the Ramen/Segment integration on by
[clicking here](https://segment.com/docs/integrations/ramen/).

### Learn More About Segment.com

To learn more about Segment, [click here](https://segment.com/?utm_source=partners&utm_medium=docs&utm_campaign=ramen.is)


## Eager.io

[Eager.io](https://eager.io/app/ramen?utm_source=partners&utm_medium=docs&utm_campaign=ramen.is)
lets you install JavaScript libraries at the touch
of a button. If you are already using Eager, you can install Ramen in just a few clicks without needing
to write any code or deploy any changes to your application.

### Installation methods

Click the 'Install via Eager' button on the _Getting Started_ page of your
Ramen Organization.

Wait a couple minutes, and then head over to your application and
navigate to a page where Eager is loaded.
After refreshing the page a few times, refresh your _Getting Started_ page and you
should see that RamenJS is sending data to Ramen.

### Learn More About Eager.io

To learn more about Eager, [click here](https://eager.io/?utm_source=partners&utm_medium=docs&utm_campaign=ramen.is)

## Ruby on Rails Rubygem

Ramen maintains an official Rubygem for Ruby on Rails applications. The Rubygem is used on Ramen.is itself.

[View the Rubygem](https://rubygems.org/gems/ramen-rails)

## Wordpress

Thanks to our integration with Eager, installing RamenJS on Wordpress is a breeze.

### Installation methods

Click the 'Install via Eager' button on the _Getting Started_ page of your
Ramen Organization.

When you are prompted, download and install the Wordpress plugin from Eager.

Wait a couple minutes, and then head over to your application and
navigate to a page where Eager is loaded.
After refreshing the page a few times, refresh your _Getting Started_ page and you
should see that RamenJS is sending data to Ramen.

## Drupal

Thanks to our integration with Eager, installing RamenJS on Drupal is a breeze.

### Installation methods

Click the 'Install via Eager' button on the _Getting Started_ page of your
Ramen Organization.

When you are prompted, download and install the Drupal plugin from Eager.

Wait a couple minutes, and then head over to your application and
navigate to a page where Eager is loaded.
After refreshing the page a few times, refresh your _Getting Started_ page and you
should see that RamenJS is sending data to Ramen.



## Joomla

Thanks to our integration with Eager, installing RamenJS on Joomla is a breeze.

### Installation methods

Click the 'Install via Eager' button on the _Getting Started_ page of your
Ramen Organization.

When you are prompted, download and install the Joomla plugin from Eager.

Wait a couple minutes, and then head over to your application and
navigate to a page where Eager is loaded.
After refreshing the page a few times, refresh your _Getting Started_ page and you
should see that RamenJS is sending data to Ramen.



## Angular

While there is no official library for Angular, we do have an
[Example App](https://github.com/ramen-dev/angular-seed/tree/ramenjs-v2.0)

Pay close attention to the comments on the commits to see what
is going on: [Commits](https://github.com/ramen-dev/angular-seed/commits/master)
