---
layout: post
title: "uport + OST integration update 3"
---

Wow there is only another week left in this hackathon!  Time flies when you're building.

If you have not read my previous updates check them out here: [One](http://josephschiarizzi.com/2018/07/Own-your-own-identity-plus-OST/), [Two](http://josephschiarizzi.com/2018/07/ost-uport-50-percent/).  They explain why I have been building this project, my motivation, and the over all goals.  I think the integration between uport and OST is worth the time.

This will be a quicker update since I've been extra busy this week.  Hopefully the integration between uport will be complete this weekend, with another more substantial update to come in a few days.

## What progress did you make on your Alpha III POC this week?
This week we wrote the API calls that will be made to OST for each project a suser adds to their uport profile. We've written it for the generic case, so any OST project can be added and users will be able to log in with uport to interact with multiple OST projects at once.

Calls look like this and are made in javascript:

***Balances***
~~~javascript
GET - https://sandboxapi.ost.com/v1.1/balances/user-Id-ABC123?api_key=99999999&request_timestamp=1526525211&signature=signature-string

ost_balance_object = ost_sdk.services.balances # initializes the balance object

ost_balance_object.get({id: 'd66a40d0-b2fa-4915-b6d2-46bbe644278a'}).to_json   # Fetch the users balance
~~~

For each different OST project the user ID will be different per person. By storing that for each of _our_ users we can combine the identities across platforms.

We can also see a list of transactions.

***Transactions***
~~~javascript
GET - https://sandboxapi.ost.com/v1.1/transactions/?api_key=123456789&limit=5&page_no=1&request_timestamp=1526452463&signature=abc123
~~~

Each project will have a different API key that can saved.

More on how to generate signatures [here](https://dev.ost.com/docs/api_authentication.html).

## What did you learn/issues you had to overcome?
The most important issue right now is securing the user IDs for each person, and controlling who owns them.

Another issue that I'm planning on for this week is figuring out how to authenticate the API calls from someone else's OST project. Perhaps there can be an admin login where one can securing add their keys so people using their project will be able to use our product more easily?

## What are you planning for the next week?
In the next week we are bringing it home! Time to make the final integrations and combine the identity functions described in post 1 and 2, with the Api calls described here.

Follow me on [twitter](https://twitter.com/cupojoseph) to keep up with the progress.
