---
title: Javascript SDK
permalink: /docs/javascript-sdk/
---

## Install
------ 

#### npm

```bash
npm install oopsie-sdk
```

#### CDN

```html
<script src="https://cdnjs.cloudflare.com/oopsie/libs/oopsie-sdk/0.99.0/js/oopsie.min.js"></script>
```



## Usage


#### Initialization and basics

```js
var oopsie = new OopsieSite(prodApiUrl, siteId, customerId);
oopsie.init(err => {
    // We have initialized oopsie sdk...
});
```

After the initialization you can start to Create, Get, Delete and Update your entities. You can also Register, Login, Logout and Refresh Users.
The SDK works in the same way as you model and Deploy your Site. You will initialize the SDK for a specific Site to get the Application you want to work with and choose a Resource on it. The Resource object is where you will make all your queries to retrieve and create entities for the specified Resource.

```js
// First you need to get one of your Applications that you have deployed to your site.
var app = oopsie.getApp('MyApp');

// On this object you can then retrieve the different Resources you have.
// It is this object that you use to create, get, update and delete entities on your Resource.
var myResource = app.getResource('MyResource');
```

#### Get

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
myResource.get().withParams(params).execute(cb);
myResource.get().byView('MyView').execute(cb);
myResource.get().limit(100).execute(cb);
myResource.get().expandRelations().execute(cb);

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

#### Create

```js
let params = {
    name: 'Smith',
    age: 22
};
myResource.create().execute(cb);
myResource.create().withParams(params).execute(cb);
```

#### Update

```js
let params = {
    name: 'Smith',
    age: 22,
    // Save will need to have eid and all Partition Keys and Clustering Keys.
    eid: 'f89028c3-7d02-4ce8-8bd4-1d88b51aa461' 
};
myResource.save().execute(cb);
myResource.save().withParams(params).execute(cb);
```

#### Delete

```js
let params = {
    name: 'Smith',
    age: 22
};
myResource.delete().execute(cb);
myResource.delete().withParams(params).execute(cb);
```


## Users

The Javascript SDK can also help you manage Users for your site.

#### Login

```js
var user = {
    email: 'my@email.com',
    password: 'my-super-secret'
};
oopsie.login(user, (err) => {
    if (err) {
        // We are not logged in!
        return;
    }
    // We are logged in!
});
```

#### Register

```js
var user = {
    email: 'my@email.com', 
    password: 'my-super-secret', 
    auths:['User'],
    firstname: 'Andreas',
    lastname: 'Andersson'
};

oopsie.register(user, (err) => {
    if (err) {
        // We are not logged in!
        return;
    }

    // We are logged in!
});
```

#### Logout

```js
oopsie.logout((err) => {
    if (err) {
        // We are not logged out!
        return;
    }
    // We logged out!
});
```

#### Refresh

```js
oopsie.refresh((err) => {
    if (err) {
        // We didnt manage to refresh the users session.
        return;
    }
    // We refreshed the session for your user.
});
```

#### Me

```js
oopsie.me((err, me) => {
    if (err) {
        // Something went wrong!
        return;
    }
    // We can inspect the logged in user, email etc.
});
```