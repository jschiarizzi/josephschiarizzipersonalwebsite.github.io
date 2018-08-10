---
layout: post
title: "OST Alpha III POC"
---

My Submission for the OST alpha III hackathon is here: [https://uport-ost.glitch.me/](https://uport-ost.glitch.me/)

![header](https://i.imgur.com/xyUlWlM.png)

[Simple Token (OST) is a project](https://ost.com/) to make it easy for people to create their own branded blockchain tokens.  I really like the idea of making utility tokens easier to use, having trackable analytics dashboards built in, and spreading useful applications of this tech.  There are lots of chances to experiment with what OST could be used for today.  That's why I'm building an integration with [uPort](https://www.uport.me/) and OST.

The connection between uport and OST will help bridge the gap between hundreds of different token economies and verify who you are within/between a token's community.

[More info on my ideas for this project in OSTaIII Post 1](./2018-07-21-Own-your-own-identity-plus-OST.md)

## Final Product

![finale](https://i.imgur.com/P3SwX9O.png)

This project allows users to log in with uPort, see their balance of IVNT, and send tokens to other users who have added their userIDs from OST to their uPort profile.

This does not quite get up to my original goal (*Allow users to use uPort to log into multiple OST token apps with 1 whole (non-fragmented) identity.*) due to some technical constraints which will be further discussed below.

## Wallet Features

I used the balance inquiry features in OST's new javascript SDK.
It's setup like this:

~~~javascript
const ostObj = new OSTSDK({apiKey: apikey, apiSecret: ostsecret, apiEndpoint: apiEndpoint});
var ost_ledger_object = ostObj.services.ledger;

ost_balance_object.get({id: globalUser.OST.IVNT.userID}).to_json
~~~
This first two lines create a ledger object. The last line uses a users ID, which is saved in uport and requested, to get the balance of the user.


## Flow Design

![uport flow diagram](https://developer.uport.me/diag1a-fcb6d01dc49e48c491272ac0ea4fca0f.svg)
1. Browser displays QR code with URI
2. Browser starts polling Chasqui using the sessionId to check if Mobile has posted the address & any other info required by the 3rd party app.
3. Mobile scans QR code, displays card asking the user to share their address (and, optionally, other relevant data)
4. If user consents: Mobile grabs sessionId from URI, posts address & data to the Chasqui API using the sessionId
5. Browser grabs the address & data from Chasqui, removes QR code from UI

![uport SSO](https://i.imgur.com/HNOkNBl.png)


## Project Weaknesses & Challenges

Originally I had wanted users to be able to log in with uPort to any token.  However, the API calls to make transfers are dependent on userIDs, and a private key, which vary between OST tokens.  A further step in this project could be to allow OST token creators to use uPort for sharing their keys for API calls safely, or interacting with the OST token smart contracts directly. Because of this, the key value for my IVNT token is hard coded (securely)

It was a challenge to make OST API calls outside of their (very well documented and powerful) javascript libraries.  Perhaps if I come back to this project I will make it easier to add more tokens.  For now, I can only manually add supported tokens myself, as the website admin.  However, I can only make 1 OST token project so we are limited to IVNT tokens today.

## Successes

![qrcode uport](https://i.imgur.com/yy8aiC6.png)

It was fun to work with uPort, I think it is an important next step in the progression of web3.  I hope the web will move away from google and facebook owning our identities towards a decentralized solution where I can own my own identity.
