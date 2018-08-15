---
title: Javascript SDK
permalink: /docs/javascript-sdk/
---

## Install
------ 

#### npm

```bash
npm install @techoopsie/oopsie
```

#### Script tag

```html
<script src="https://cdn.jsdelivr.net/npm/@techoopsie/oopsie/dist/oopsie.min.js"></script>
```

#### Or a specific version

```html
<script src="https://cdn.jsdelivr.net/npm/@techoopsie/oopsie@<version>/dist/oopsie.min.js"></script>

<!-- For example -->
<script src="https://cdn.jsdelivr.net/npm/@techoopsie/oopsie@0.0.6/dist/oopsie.min.js"></script>
```


# Example

### Initialization

```js
var oopsie = new OopsieSite(apiEndpoint, siteId, customerId);
oopsie.init((err) => {
    
    // We are done loading meta data...
    // Now we can use oopsie to create, get, save, delete entities.
});
```

### Chooce Application and Resource

```js
var app = oopsie.getApp('BookApp');
var bookResource = app.getResource('Book');
```

### Get entities 

```js
bookResource.get().withParams({}).limit(100).execute(callback);
bookResource.get().withParams({}).limit(100).expandRelations().execute(callback);

var query = bookResource.get({}).byView('myView').limit(100).expandRelations().execute(callback);
query.nextPage(callback);
query.prevPage(callback);
query.hasNextPage();
query.hasPrevPage();
```

### Create entity
```js
bookResource.create().withParams({}).execute((err, resp) => {});
```

### Update entity
```js
bookResource.save().withParams({}).execute((err, resp) => {});
```

### Delete entity
```js
bookResource.delete().withParams({}).execute((err) => {});
```

# Api key

If you are using auth on your Site, you can create Api Keys to protect your data.
You can use it in the JS SDK as below, but be carefull, you shouldn't do this in the frontend.
If you do put it in the frontend, be sure it's not any secret data you want to protect.
For example, you may put a read only Api Key in the frontend because you want anyone to be able to read your data, 
but you create data in your backend where you use another Api key with read permissions.

```js
var oopsie = new OopsieSite(apiEndpoint, siteId, customerId);
oopsie.init((err) => {
    
    // We are done loading meta data...
    // Now we can use oopsie to create, get, save, delete entities.
    var apiKey = 'api-key-from-dashboard'; 
    oopsie.setApiKey(apiKey);
});
```

# Handle Users

If you have auth enabled on your site you can manage Users via the SDK.

### Register user

To let Users register via the SDK you need to set this up in the Dashboard for your site. By default no Roles are allowed to register via the API and only the Admin for the Site can add Users in the Dashboard.

```js
var user = {
    email: 'my@email.com',
    password: 'my-super-secret',
    firstname: 'Anja',
    lastname: 'Hrabun'
};
oopsie.register(user, (err) => {
    if (err) {
        // We failed to register user.
        alert(err.message);
        return;
    }
    // User registered.
})
```

### Login user
```js
var user = {
    email: 'my@email.com',
    password: 'my-super-secret'
};
oopsie.login(user, (err) => {
    if (err) {
        // We failed to login.
        alert(err.message);
        return;
    }
    // User logged in.
})
```

### Logout
```js
oopsie.logout((err) => {
    if (err) {
        // We failed to logout.
        alert(err.message);
        return;
    }
    // User logged out.
})
```

# Promises

Oopsie SDK follows nodejs callback pattern so you can use bluebird to promisefy the functions if you rather use promises then callbacks.

