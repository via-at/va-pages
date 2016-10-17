# va-pages

Now Shadow DOM goes to v1 from v0. So this repository has been deprecated. Use [via-at/board](https://github.com/via-at/va-board) instead. `va-board` supports Shadow DOM v1.

## Ready to use

This component requires initialization information like:

```js
VA = {
  prefix: 'my',      // Prefix of custom element name (e.g. \<my-profile\>)
  pageRoot: '/pages' // Root path of pages
};
```

## Usage

Here is `va-pages` example. The element contanins `my-profile` that shows user profile, `my-works` that shows user's works and `my-admin` that can be viewd only administrator (restricted page). The `/admin` page is restricted, so non-admin can be accessed the page (if a user accesses the page, redirect to the default page "profile").
For instance, `va-pages` loads `my-profile` from `/pages/my-profile` and switch to the page when a user accesses to `/profile`.

```js
<dom-module id="my-pages">

<template>
  <va-pages
    page="{{page}}"
    restricted="[[restricted]]"
    restricted-pages="[[restrictedPages]]"
    default-page="profile"
    entry-animation="fade-in-animation"
    exit-animation="fade-out-animation">

      <my-profile></my-profile>
      <my-works></my-works>
      <my-admin></my-admin>

  </va-pages>
  
  <button on-click="allowAdmin">Allow to access admin area.</button>
  
  <a href="/profile">Go to my profile page</a>
  <a href="/works">Go to my works page</a>
  <a href="/admin">Go to admin page</a>

</template>

<script>
Polymer({
  is: 'my-pages',
  
  properties: {
    page: {
      type: String
    },
    restricted: {
      type: Boolean,
      value: false
    },
    restrictedPages: {
      value: ['admin']
    }
  },
  
  
});
</script>

</dom-module>
```
