# Product Center

Product Center is a feature that lets you discuss Features
with your Customers. Product Center is only available on
certain paid plans.

## Custom Links

```javascript
_ramen.boot("ORG_ID", {
  custom_links: [
    {
      title: 'E-mail support',
      href: 'mailto:support@ramen.is',
    },

    {
      title: 'Chat with support',
      callback: 'Interom("showNewMessage")'
      // ^ Not a typo :) If you want to use
      // Intercom w/ Ramen, this is one way
      // to do that.
    }
  ]
});
```

We provide a way for you to customize links that
appear at the bottom of Product Center.

Custom Links have a `title` property and either an
`href` or a `callback` property. `href`s
must be full URIs (including protocol, ie. https).
`callback`s can be JavaScript closures
or strings that will be `eval`'d

You are allowed to provide up to 3 Custom Links.

## Placement

```html
<nav>
<ul>
  <li><a href="/account">Your Account</a></li>
  <li><a href="/product-center" class="custom-ramen-trigger">Product Center</a></li>
</ul>
</nav>

<style>
._r-badge:after {
  top: -5px;
  right: -5px;
  background-color: red;
  -webkit-border-radius: 100px;
  -moz-border-radius: 100px;
  border-radius: 100px;
  content: " ";
  height: 18px;
  width: 18px;
  position: absolute;
  font-size: 12px;
  line-height: 16px; 
}

._r-related {
  font-weight: bold;
}
</style>
```

```javascript
_ramen.boot("ORG_ID", {
  custom_trigger_class: "custom-ramen-trigger"
});
```
You can set a custom placement, called a 'trigger'
for the RamenJS widget so that instead of showing the
icon in the bottom right or left corner of the screen,
a link in your nav can be used to trigger opening
Product Center.

### Styling the Custom Trigger

We apply different styles to the RamenJS widget:

1. When there is a Feature related to the current URL, the widget icon will be full color.
2. When there are no related features, a grayscale image is used instead.
3. When there are newly deployed features, a circular red badge is placed over the top right corner of the icon.

When using a customer trigger, we do not attempt to modify the style to reflect state changes.
Instead, we will add classes to the element. It will be up to you to style the elements.

* `_r-related`: We will add this class when there are Features related to the current URL
* `_r-badge`: We will add this class when there are newly deployed features that have not yet been seen by your customers.



