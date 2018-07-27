---
layout: post
title: "Own your own identity + simple branded tokens to make blockchain projects whole"
---

We are already through [OST's](https://ost.com) Alpha III Challenge. OST lets people easily create their own branded token with a dashboard all setup to get info on transactions, users, and with lots of options.  I'm currently building an integration for OST and [uport](https://www.uport.me/) so OST users can log in with one account they control and interact with different dapp ecosystems.


## Status Update
This week we finished up our [uport-connect](https://github.com/uport-project/uport-identity) integration.  Now you can log in with a uport button which generates QR codes and allows the user to verify. This week we've also spent some time putting the [OST api]() which we will be focusing on together.  Most of the next week will be figuring out what parts of each OST project the user will be able to access and interact with.

![uport button](https://i.imgur.com/LgFv07S.png)


## Challenges
We can get info on a user in each project like this:
```
ost_balance_object = ost_sdk.services.balances # initializes the balance object

ost_balance_object.get({id: 'd66a40d0-b2fa-4915-b6d2-46bbe644278a'}).to_json   # Fetch the user's balance
```

But each user will have a different ID in each application, and there are different keys to get information from them all.  It would be nice if a _user_ could paste in the token info and be able to add it to their uport identity.  But I'm not sure if that is possible yet, I think that admins may have to paste in a key somewhere to be able to make calls and get all the info needed to fill out the data on each user that logs in with my integration.
