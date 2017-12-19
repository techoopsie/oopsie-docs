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

### Script tag

To get latest:

```html
<script src="https://cdn.jsdelivr.net/npm/@techoopsie/oopsie/dist/oopsie.min.js"></script>
``` 

Or to get a specific version:

```html
<script src="https://cdn.jsdelivr.net/npm/@techoopsie/oopsie@<version>/dist/oopsie.min.js"></script>

<!-- For example -->
<script src="https://cdn.jsdelivr.net/npm/@techoopsie/oopsie@0.0.6/dist/oopsie.min.js"></script>
```


### Webpack

If you are using webpack you might need to add 

```
node: {
    fs: "empty"
}
```

to your webpack.config.js




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

// To get data in a View you can specify which View to use.
myResource.get().byView('MyView').withParams(params).execute(cb);

// If you want to change the limit, defaults to 100. Can be 0 to 1000.
myResource.get().limit(100).execute(cb);

// When relations exists you can expand them
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


## Users

If you have auth enabled on your site you can manage Users via the SDK.

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

To let Users register via the SDK you need to set this up in the Dashboard for your site. By default no Roles are allowed to register via the API and only the Admin for the Site can add Users in the Dashboard.

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

# Promises

Oopsie SDK follows nodejs callback pattern so you can use bluebird to promisefy the functions if you rather use promises then callbacks.

# Examples

Examples can be found in the *examples* folder. Each example will be in a subfolder and include everything needed to run the example. They need a working Oopsie site to run, and we will most likely provide them for you, but you can also create your own Site in the sandbox and try the examples against your own Site.

**NOTE: the examples are meant to give you a better understanding of how you can use Oopsie to store your data and handle your Users, they are not meant to be a beauty for the eye ;)**

**If you can't stand the awesome design of the examples, feel free to give us a pull request**
