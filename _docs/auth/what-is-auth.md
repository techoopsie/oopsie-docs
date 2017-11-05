---
title: What is Authorization?
permalink: /docs/what-is-auth/
---

*Authorizaton Models* acts like templates for you applications and sites telling the site how to handle authorization for you resources. By default two Auths always exist, Admin and User. Admin will always have all rights on all resources and can't be changed. The User auth has NONE initially as the default permission but can be changed, either on the *Authorization Model* or later on a specific *Resource*. All users registered on a site will get the *User* auth, hence the NONE permission (if you haven't changed it of course). You can see *Auths* like a group or role of *[Users](/docs/users)* if you like.

You can create as many models you want and also alter existing models. If any model is used by an *Application Model* it will be updated accordingly. This will not affect any deployed site using the altered auth model since the site has a copy from the verions of the released application.

##### Auth Permissions #####

<img src="/img/permissions.png" width="450">

> ***Remember!*** The permission set on the *Auths* are inital (defult) permission when added to a resource and can individually on each resource be alterer to use another permission. This means that two different resource with same Auth, e.g. Staff Auth, can have different permissions. Very powerful feature!
