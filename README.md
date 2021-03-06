>There's no such thing as an original idea. Every idea worth having has been had thousands of times already.
> - [swombat](https://news.ycombinator.com/item?id=250793)

**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [NoFollow Enforcer](nofollow.md)
- [PyPi Notifier](pypi-notifier.md)
- [OpenBook](#user-content-openbook)
    - [Expectations](#user-content-expectations)
    - [Features](#user-content-features)
    - [Interface](#user-content-interface)
    - [Backend](#user-content-backend)
- [iStalk](#user-content-istalk)
    - [Idea](#user-content-idea)
    - [Interface](#user-content-interface-1)
    - [Collaborative Bookmarking](#user-content-collaborative-bookmarking)
- [Lightspeed for Chrome](#user-content-lightspeed-for-chrome)
- [Facebook Analytics](#user-content-facebook-analytics)
- [API for Workflowy](#user-content-api-for-workflowy)
- [Lettersafe](#user-content-lettersafe)
- [Email on top of keybase](#user-content-email-on-top-of-keybase)
- [Newsletters for GitHub](#user-newsletters-for-github)
- [Hacking via OAauth tokens](#user-content-hacking-via-oaauth-tokens)
    - [But OAuth tokens can be revoked](#user-content-but-oauth-tokens-can-be-revoked)
    - [Procedure](#user-content-procedure)
- [Pluggable Notify Daemon for linux](#user-content-notify-daemon-for-linux)
- [Licence](#user-content-licence)

## OpenBook
This is a privacy-awareness application that relies on the TrueCaller data-sharing model. It is meant to teach users that their privacy is not in their hands, but in the hands of those that they trust.

The idea itself is to let people browse facebook as someone else. This is done by note of the following points:

1. Facebook allows OAuth API access that allow your application to perform tasks as any user whose token you have.
2. To start using the service, you must "hand in your data" first. Just like TrueCaller uploads _your entire phonebook_ before you can use the app, openbook requires you to give us access to _your facebook account_ before you can use openbook.

### Expectations
This has massive privacy implications. People assume their facebook data (such as information on your about page) to be available to only people they have friended on facebook. However, it is also accessible to all applications you authorize, which is what we are exploiting basically. I expect the application to be banned and have its keys revoked within a day or two. If I were to make this, I'd rather not use my own facebook account for fear of getting it suspended.

### Features
Since the idea is to teach users about privacy, openbook will not ask for access to all data. It will probably use a harmless data-property that will essentially be made public to all users of the app. Currently, I'm thinking "No. of Friends", which is not always available to public if you've hidden your friend list. It is harmless enough to not cause any mayhem, and yet vital enough to just show that such _attacks are possible_.

### Interface
1. Homepage will be a simple FAQ on privacy-related matters and what the app does.
2. A login page
3. A search interface to search amongst all users using the app.
4. A profile page of any user, where you can see their data using someone else's token.

### Backend
Unlike facebook, which can directly access _any data_ on their servers, we are limited to using their API. Which means getting data for any user has now become a mapping problem. You need to know which tokens can access data of which user. This could be made possible by pre-mapping the users accessible via each token, and refreshing each token's list every week or so (as you make new friends).

This idea probably breaks lots of point in Facebook's ToS, but that doesn't mean it can't be built.

## iStalk
This is essentially a unified profile mechanism, where a user's identity is defined by all of their activity on various networks. While this has some cool sub-ideas (like correlating activity between various networks), the most important implication that arises is that it can be a perfect tool for stalking.

### Idea
iStalk lets you "follow" a person across various networks that they belong to. Some networks, like twitter are mostly public, and can be followed very easily. But other networks (like Facebook) are harder to follow by virtue of them requiring a "connection" between the two users. iStalk makes it easier for you by using your account on that network as a proxy-connect mechanism.

Basically, you give us your access tokens, and we use them to stalk someone for you.

### Interface
A profile creation page allows you to specify as much information as you have on the person. This includes their facebook, twitter, last.fm, github usernames for eg. Each integration you want has to first be verified by you granting us (iStalk) access to your account (via OAuth).

Once a profile has been created, we will continuously long-poll the service to fetch new information as and when it becomes available. Real-time notifications are delivered to you as the person's activity is tracked.

### Collaborative Bookmarking
There are a dozen bookmarking services out there, many of them quite well done. However, most services are focused on the idea that bookmarking is a lone-person habit, which someone does in isolation.

I've often described the idea as "dropbox for bookmarks". The core concept is to allow a bookmarking "tag/folder" to be shared with another user, two-way. This means any of the shared members can add/remove bookmarks from that folder.
All updates (addition/deletion/edits) are notified to every member in the group.

Bookmarking for Teams, in essence. Some good alternatives are [listed in this quora answer](https://www.quora.com/Hello-What-are-the-best-web-apps-for-sharing-bookmarks-across-a-team), which you should read and follow if you're interested in this.

## Lightspeed for Chrome
[Lightspeed](https://www.youtube.com/watch?v=wLnSLFrQDG8) is an experimental UI design (not implemented) for Firefox that focuses on making the New Tab page more functional by giving the browser a decent way to search across bookmarks, open tabs, and history.

It is a pretty neat idea (see the video linked above). My first thought on seeing the video was that most of that stuff could be done using the Chrome APIs for Chrome as well. Chrome does offer a way for an extension to override the new tab page, after all. 

The discussion on [HN](https://news.ycombinator.com/item?id=8151271) is also very good.

## Facebook Analytics
I like the analytics that WolframAlpha provides for Facebook. Except that they are not really that useful. I'd like an easy query interface that let me "filter" data points, and get back open-data via the Graph API. This means, for eg, getting the most liked music artist among a subset of my friends. The interface I'm thinking of right now is like Gapminder, which allows you to "play" the dataset as it evolves over time.

A recommendation engine built on top of my facebook data is a good idea, I think.

## API for Workflowy
Workflowy is a cool tool that I use for note-taking. It allows infinitely nested lists with @mention and #hashtag support. One thing it lacks currently is API for me to access my own data. I think workflowy is a great tool that could become a lot better if there were a way for developers to hook into it. (For example using workflowy as a data-backend for a todo-app).

## Lettersafe
My notes for lettersafe are on [workflowy](https://workflowy.com/s/5439f7a9-3762-f247-3e96-4d047b5d4ce0).

The idea was to build a zero-knowledge email storage. Kinda like lavabit, with a few minor changes. After thinking about it for months, and working on it for a few days, I gave up on the idea. I understand now that server-side email encryption can never be a good idea.

## Email on top of keybase
Keybase has a cool API. I wonder if its possible to build an actual email service on top of keybase?

## Newsletters for GitHub

A lot of github project owners would like to send out newsletters to all of their
stargazers. However, GitHub doesn't provide anything for that. An easy way would
be to integrate StarGazers with MailChimp, making sure that people can unstar
a project to unsubscribe from the mailing list.

Only the repo owners and collaborators (maybe) should have access to sending out
newsletters. For bonus points, you can replace mailchimp with your own solution.

This could even be monetized slightly for paying off your server costs: newsletter
access for projects with >1k stars (the mailers that would cost you money) cost
money to the repo owner as well.

So a tiny python package pays nothing to update its users about a new release, but
if Angular team wants to send out an update, that gets paid.

And finally, this should automatically subscribe you to any new GitHub releases in
any project you have starred. This is a missing feature that I think can be best
implemented by a third-party for now.

## Hacking via OAauth tokens
While pen-testing, once you've gained access to the target, it is often necessary to install a backdoor to mantain the access. While this is easily done in case of root access to the machine, this is not that easy if the target is an email account, lets say.

Many online services today (with data of considerable value) offer developers programmatic access to their data by use of APIs, which are usually authenticated via OAuth tokens. What I intend to build is a suite of applications (or a single large one) that allow you to use the application as another user, just by setting up an access token.

While this is certainly possible with existing tools (such as the Facebook Graph API Explorer), it is cumbersome and not user-friendly. The application will mimic the interface, usability, and looks of the actual application to let you maintain access easily enough.

### But OAuth tokens can be revoked
That is a good point, but one that fails in practice. A password change in most services does not trigger an automatic token revocation because that would leave a lot of developers and users unhappy. However, neither does any service warn you to check your approved applications (especially after a hacking attempt).

### Procedure
1. You gain access to someone's account.
2. You create an application (using a fake account or the victim's own account, so its not tied back to you)
3. You setup our app (direct deploy to Heroku)
4. You configure the app with the application credentials (app id, secret key)
5. You authenticate the victim's account against the app
6. You use the application to access the user's account

The account access will continue till the victim checks his/her approved applications. 

## Notify Daemon for Linux

Not another window manager daemon, because lots of them already exist and there
are already good APIs in almost all languages that make it easy to integrate with
all of them. However, Linux DEs are still missing an easy way for me to get notifications
about the thousands of little different things (such as build notifications).

The idea is to have a simple config where you can connect your bazillian accounts
via OAuth, and we will poll all your accounts and give you "clickable" notifications
for each of them. (GMail notifications might open your mail client if you click reply)

Keep it pluggable, otherwise its of no use.

## Licence
This work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/). Feel free to contribute via Pull Requests, or discuss ideas in Issues. Also feel free to use these ideas in making the Next Big Thing.
