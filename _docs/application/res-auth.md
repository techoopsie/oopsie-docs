---
title: Resource Auth
permalink: /docs/res-auth/
---

All *[Resources](/docs/resources)* have an authorization config attached to them. This means that you can fine tune how your users access the data on a resource level. E.g. the registry of *Customers* the *staff* at your comapny should have access right to all  *customer* data, but the customers themselves should only be able to read and write their own data.

With *[Authorization Models](/docs/what-is-auth)* you can create specific *Authorizations* with different default *Permissions*. Below is a screenshot of how the above example could look like when configured on a resource called *Customers*.

Let us explain what we see here:

With the swipe button you turn on and off the authorization of the resource. Default is on since with autorization off the resource will be fully open to anyone on the internet. So, be careful with this setting.

Under the auth swipe button we see a list of *Authorizations*. You can see these as groups or roles if you like. The *auths* are initially configured with the default *permission* as set by the *Auhtorization Model* used by the *Application*. You can change the *permission* if you aren't satisfied with the default value.

A word about the *Admin* and *User* auths. Two auths are always present in the resource auth tab, *Admin* and *User*. *Admin* auth is disabled for editing since users in *Admin* should always have read and write access to everything. All users registered in an oopsie site will always be added to the *User* auth. Therefore it should be considered a good practice to always have this auth set to permission *NONE* and create more suitable auths such as the Customer auth as shown in picture. You can read more about these special auths in the *[Authorization Models](/docs/what-is-auth)* section.