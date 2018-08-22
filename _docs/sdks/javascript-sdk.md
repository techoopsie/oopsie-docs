---
title: Javascript SDK
permalink: /docs/javascript-sdk/
---

### GitHub

```
 git clone https://github.com/techoopsie/oopsie-sdk-js.git
```

### Install
------ 

#### npm

```bash
npm install @techoopsie/oopsie
```

#### Script tag

```html
<script src="https://cdn.jsdelivr.net/npm/@techoopsie/oopsie/dist/oopsie.min.js"></script>
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
myResource.get().execute((err, res) => {
    if (err) {
        alert('We got an error when getting entities');
        return;
    }

    // Else we have our result
}));

let params = {
    eid: 'f89028c3-7d02-4ce8-8bd4-1d88b51aa461'
};
// Gets data from primary view of the resource
myResource.get().withParams(params).execute(cb);

// To get data in for a specific view.
myResource.get().byView('MyView').withParams(params).execute(cb);

// If you want to change the limit, defaults to 100. Can be 0 to 1000.
myResource.get().limit(100).execute(cb);

// You can also add all of the methods after get() in different order and use the ones you need.
myResource.get().withParams(params).byView('MyView').limit(100).expandRelations().execute(cb);

// You can also store the query to later get nextPage or previous page, if they exists.
var query = myResource.get().byView('MyView').execute(cb);
if (query.hasNextPage()) {
    query.nextPage(cb);
}

if(query.hasPrevPage()) {
    query.prevPage(cb);
}
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

```js
oopsie.me((err, me) => {
    if (err) {
        // Something went wrong!
        return;
    }
    // We can inspect the logged in user, email etc.
});
```

# Promises

Oopsie SDK follows nodejs callback pattern so you can use bluebird to promisefy the functions if you rather use promises then callbacks.

# Examples

Examples can be found in the *examples* folder. Each example will be in a subfolder and include everything needed to run the example. They need a working Oopsie site to run, and we will most likely provide them for you, but you can also create your own Site in the sandbox and try the examples against your own Site.

**NOTE: the examples are meant to give you a better understanding of how you can use Oopsie to store your data and handle your Users, they are not meant to be a beauty for the eye ;)**

**If you can't stand the awesome design of the examples, feel free to give us a pull request**
