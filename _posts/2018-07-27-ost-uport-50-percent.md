---
layout: post
title: "uport + OST integration halfway update"
---

We are already through [OST's](https://ost.com) Alpha III Challenge. OST lets people easily create their own branded token with a dashboard all setup to get info on transactions, users, and with lots of options.  **Goal**: I'm currently building an integration for OST and [uport](https://www.uport.me/) so OST users can log in with one account they control and interact with different dapp ecosystems.


## Status Update
Already made is our uport connect button for Single Sign On (SSO) using a decentralized identity. Cool stuff!

![uport button](https://i.imgur.com/LgFv07S.png)

This week we finished up our [uport-connect](https://github.com/uport-project/uport-identity) integration.  Now you can log in with a uport button which generates QR codes and allows the user to verify. This week we've also spent some time putting the [OST api]() which we will be focusing on together.  Most of the next week will be figuring out what parts of each OST project the user will be able to access and interact with.

## Why build this?
Why did I join this challenge? Why do I think this is worth the time to make?

Google and Facebook own monopolies on our identities.  uPort is fighting back, and I think that what they are going for, own your own identity solutions, is a great goal that I want to support.  At the same time OST is making it easier and more user friendly for people to interact with utility tokens with a wide range of apps already being built as part of this challenge.

## Challenges
We can get info on a user in each project like this:
```
ost_balance_object = ost_sdk.services.balances # initializes the balance object

ost_balance_object.get({id: 'd66a40d0-b2fa-4915-b6d2-46bbe644278a'}).to_json   # Fetch the user's balance
```

But each user will have a different ID in each application, and there are different keys to get information from them all.  It would be nice if a _user_ could paste in the token info and be able to add it to their uport identity.  But I'm not sure if that is possible yet, I think that admins may have to paste in a key somewhere to be able to make calls and get all the info needed to fill out the data on each user that logs in with my integration.


## Next
Next is adding support for users to sign transactions using their uport identity.  There are some great docs on how to do this, but not something I have built before. That should make it even more fun.  Users must be able to sign transactions in order to transfer tokens between each other, and interact with the smart contract which gets deployed for each OST project.
