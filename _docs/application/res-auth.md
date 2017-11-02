---
title: Resource Auth
permalink: /docs/res-auth/
---

All *[Resources](/docs/resources)* have an authorization config attached to them. This menas that you can fine tune how your users access the data on a resource level. E.g. the registry of *Customers* the *staff* at your comapny should have access right to all  *customer* data, but the customers themselves should only be able to read and write their own data.

With *[Authorization Models](/docs/what-is-auth)* you can create specific *Authorizations* with different default *Permissions*. Below is a screenshot of how the above example could look like when configures on a resource called *Customers*.

### CHANGE PIC ###

<img src="/img/res-auth-tab.png" width="350">

Let us explain what we see here:

With the swipe button you turn on and off the authorization of the resource. Default is on since with autorization off the resource will be fully open to anyone on the internet. So, be careful with this setting.

## TALK ABOUT USER ##

Under the auth swipe button we see a list of *Authorizations*. You can see these as groups or roles if you like. Two auths are always present, Admin and User, and you can read more about these in the *[Authorization Models](/docs/what-is-auth)* section. The *auths* are initially configured with the default *permission* as set by the *Auhtorization Model* used by the *Application*. You can change the *permission* if you aren't satisfid with the default. The Admin auth is locked though, this since users in Admin should always have access to everything.