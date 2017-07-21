---
title: 5 Protocols For Event-Driven API Architectures
date: 2017-07-21 12:00:00
tags: [Event-Driven,全栈,Node]
---

原文：[5 Protocols For Event-Driven API Architectures](http://nordicapis.com/5-protocols-for-event-driven-api-architectures/)

The internet is a system of communication, and as such, the relationship between client and server, as well as server to server, is one of the most oft-discussed and hotly contested concepts. **event-driven architecture** is a methodology of defining these relationships, and creating systems within a specific set of relationships that allow for extensive functionality.

In this piece, we’re going to discuss 5 common event-driven methods — **WebSockets**, **WebHooks**, **REST Hooks**, **Pub-Sub**, and **Server Sent Events**. We’ll define what they fundamentally are and do, and how API providers go about using them. Additionally, we’ll provide some pros and cons on each to make choosing a solution for your platform easy and intuitive.

## What is an Event-Driven Architecture?

Event-driven architectures establish an event that can be consumed and reacted to. But what is an event?

An event is essentially any significant **change** from one state to another, such as the change from having no messages in your inbox to have a new message in your inbox. This state can be reacted to **internally** (such as when the email program in question realizes a new message has been received), **externally** (when a user sees a notification for a new message), or used to **generate another event** (for instance, the message tally increases by one).

Event-driven architectures are appealing to API developers because they function very well in **asynchronous** environments. By crafting APIs that **trigger** certain functions on new event delivery, API systems don’t have to inherently wait for synchronous delivery or real time communication. This is hugely beneficial, as eliminating the need to constantly poll endpoints frees resources from otherwise wasteful purposes, reducing both general hardware requirements and call-specific overhead.

For this reason, event-driven architectures are very, very popular, and lead to improved power, bandwidth, and co-processing than other solutions and architectures such as polling and other poll-centric derivatives.

## 5 Types of Event-Driven Protocols for APIs

### 1: WebSockets

**WebSockets** are an interesting event-driven solution, because, for most browsers, they’re actually baked into the application itself. Essentially, WebSocket is a protocol that provides full-duplex communication on a single TCP connection. It was standardized by the Internet Engineering Task Force as [RFC 6455](https://tools.ietf.org/html/rfc6455), and the WebSocket API in Web IDL was later standardized under the W3C banner.

While the protocol itself is meant to be used between **web browsers** and **servers**, the protocol can be used in any case where there is a client-server relationship. The protocol itself is based upon TCP, with the additional HTTP interpretation statement that is considered an “Upgrade request” to allow for interoperability.

#### Pros
Because WebSocket is expressly designed for browser operation, it boasts extremely **low overhead** for what it actually does. By establishing a **full-duplex** conversation using a standardized methodology, connection both to and from the two entities can take place simultaneously, resulting in lower overhead and better throughput.

Additionally, the fact that these communications take place over TCP 80/443 means that environments that traditionally block non-web based applications for security reasons can still handle this protocol, as firewalls allow communication to and from this port.

Perhaps the strongest argument for the use of WebSockets are the fact that they are standardized and **natively supported** by all major browsers, ranging from Microsft Edge to Opera, from Firefox to Chrome. This means that any web application that ties into it will be interactable within the vast majority of both browser-based and browser-independent gateways and applications.

#### Cons
WebSockets have one distinct major failing — while it might have support for HTTP-like functionality, **it is not HTTP** whatsoever. This has implications, especially when considering optimizing in HTTP such as caching, proxying, etc., that haven’t quite become apparent.

Because WebSockets are relatively new, having been only officially standardized in 2011, the industry is still understanding what the side effects mean. Most applications that use WebSockets are designed specifically for everything that a WebSocket is — what has yet to be seen, however, is whether or not this solution is better in the long-run than any stateless solution currently available.

There is of course the fact that, as with other architectures on this list, WebSockets create an “always on” connection during the duration of data transfer. While this is fine for many uses such as media streaming and live stream calculations, it also essentially means that, for WebSockets, there is no scalability. Ports have hardcoded limitations and bandwidth, and thus in order to “scale”, you must add additional ports to match the maximum load. In stateless systems, this is less of an issue, as requests can wait and be made in such a way as to be independent on the state of the server itself.

### 2: WebHooks
**WebHooks** are a similar concept to the WebSocket. They primarily function using **custom callbacks**, or code that is passed as an argument to another chunk of code and executed at a specified point in time. Essentially, a WebHook is a glorified system of “if this, then do”, allowing for users independent of the event firing to craft a custom response to that event within their own system.

The term was coined by [Jeff Lindsay](https://twitter.com/progrium) in 2007, and quickly became popular amongst users who wished to create automated responses to exterior behaviors. A great example of this would be a developer pushing a new item to GitHub, which causes an event. A user has a system tied into the URI of a WebHook. When the push is published, the user’s system utilizes the URI of the WebHook to integrate the push into a larger build, thereby creating a compiled component.

#### Pros
WebHooks function a lot like WebSockets, but they’re different in some key areas. First and foremost, WebSockets are primarily designed for browser-based communications, and while they can be used regardless in any client-server communication, they do not behave well in a **server-to-server** setup.

WebHooks, on the other hand, work very well in server-to-server systems due to how they operate. Because the system essentially functions as the aforementioned “if this then do”, servers can be configured to tie into pre-formed URIs at any time and execute a given function whenever that event is triggered.

Additionally, WebHooks have the unique benefit of being **based upon HTTP**, unlike WebSockets. This means that the system can be integrated without utilizing any new infrastructure, allowing speedy adoption and relatively simple setup.

#### Cons
The problem with WebHooks is that a lot of their functionality can already be placed on the arguably more powerful REST architectural approach. While adopting event-driven architecture is often a requirement of the service being built, it’s a hard sell when it can be mirrored in REST while also giving the wealth of options that REST gives to the user.

These RESTful solutions such as [RestMS](http://www.restms.org/) are essentially simply message querying services, though, and do require additional infrastructure, which may or may not be doable considering the purpose of the application.

Additionally, WebHooks can be **resource intensive** to both the client and the server. If the client needs to notify many servers that an event has occurred, and a server needs to listen to a great deal of clients notifying of this change, you can very quickly run into a situation where your network grows uncontrollably. While HTTP does scale quite well, this is a definite negative to consider.

However, there are also ways to build a [message queuing service](https://en.wikipedia.org/wiki/Message_queuing_service) on top of HTTP—some RESTful examples include [IronMQ](https://www.iron.io/platform/ironmq/) and RestMS.

### 3: REST Hooks
Speaking of RESTful examples, **REST Hooks** is essentially “hooking” baked into REST itself. Defined as an initiative from [Zapier](http://resthooks.org/docs/), this is a subject [we’ve covered before](http://nordicapis.com/stop-polling-and-consider-using-rest-hooks/) — hooks are collated to a single target URL as a subscription, which pings the resource requester when a change is noted.

This approach is a response to the practice of **polling**, in which a client constantly checks for changes to a resource. Under the REST Hooks paradigm, the client instead waits for a change, and reacts to it. To put it simply, this is a WebHook in REST.

#### Pros
REST Hooks are obviously super powerful in the correct context — being able to passively receive a resource rather than dedicating processing power to constant polling frees up a lot of the client-side cost.

Perhaps the strongest argument for REST Hooks though, is the fact that it’s **so easy** and **intuitive** to use. While WebHooks utilize HTTP and thus do not need new architecture to set up, they are also limited by the fact that they are built upon HTTP, and can thus be somewhat complex to set up properly and use effectively.

REST Hooks, though, are **subscription based**, and as such, are simply usable by subscribing. This makes it a very easy to use solution while providing a lot of the usability and effectiveness of more complex systems.

#### Cons
Of course, every solution has its negatives, and REST Hooks are no different. It could be viewed that REST Hooks actually fly in the face of what REST is — [session free and stateless](http://nordicapis.com/defining-stateful-vs-stateless-web-services/). REST Hooks essentially create consistent polling, it’s just moved the polling from one side to another.

Then, there’s the arguable problem that REST Hooks might be doing something that has already been solved. Some would argue that TCP already does most of what REST Hooks is trying to do, and simply layering more solutions on top of HTTP to get what TCP already does is a poor approach.

### 4: Pub-Sub
**Pub-Sub** is a slightly different approach. Referred to by its full name as **publish-subscribe**, the concept is where events are published to a class without knowledge of the client subscribing to the class. Basically, a user will join one or more classes, and then will receive event updates without regard or knowledge to the event publisher.

The main difference here is one of conscious choice of provider — in the other solutions noted herein, a user consciously communicates with a given server or provider and receives events as pre-determined. Under the Pub-Sub scheme, the user only specifies which class they wish to be part of and what events they are interested in receiving. From there, they receive these events when one is pushed out.

A way this is often framed in internet discussions is in the frame of a **radio channel**. Record companies, or publishers, issue audio to the station, which then broadcasts this audio to listeners, or subscribers. Pub-sub is the middleman radio station here — listeners don’t know who gave the station the music, nor do the companies know who the listeners are. It is this segmentation that is baked into the pattern.

When we talk about Pub-Sub, we need to keep in mind that we’re actually talking about two different things. Pub-Sub can mean the methodology and general concept in programming terms, but it can also mean specific provider solutions based upon that methodology. For instance, Google’s [Cloud Pub/Sub](https://cloud.google.com/pubsub/docs/overview) is an implementation of the general methodology within their cloud service, and allows for asynchronous many-to-many pub-sub relationships as stated above.

#### Pros
A huge benefit of Pub-Sub is the fact that it’s **loosely coupled**, and thus is extremely scalable and flexible. The only thing the event-provider is doing is generating the content — each other step is done through a separated middleman, and so the content is easily scaled and modulated to the architecture and design of the solution.

Additionally, Pub-Sub lends itself very well to **testing**. A subscriber is narrowly limited to a set of events that they have requested under a class, so if a failure occurs, this natural segmentation informs the provider as to where the fault is, and which class of users is experiencing the fault.

#### Cons
Unfortunately, decoupling is also a huge disadvantage for this pattern. By being a **middleman**, Pub-Sub cannot effectively notify the provider that a message has been sent, and the listener is separated from the event and thus may not know if a message wasn’t sent that should have been. Harkening back to the radio explanation, a listener will never know if a song was meant to play on a channel or if the channel is out of range, and once the record executives hand off the music, they’ve got no idea if the user received the songs without direct feedback from them.

Additionally, while the system is extensible and flexible, instability does occur with high traffic load as subclass after subclass might be constructed to handle further segmentation. This of course leads to the aforementioned instability in addition to increased complexity.

You must keep in mind that while the relationship between the publisher and subscriber in this model may be beneficial, it also comes with its own difficulties when these relationships need to be modulated. While you can certainly work around this, at this point, you’re fighting the very basis of the pattern, rather than any secondary natures — you’re trying to make dehydrated water, and fighting against the nature of a pattern suggests the pattern to be inherently poor.

> Also read: [Building a Backend for Frontend (BFF) For Your Microservices](http://nordicapis.com/building-a-backend-for-frontend-shim-for-your-microservices/)

### 5: Server Sent Events
**Server Sent Events**, or SSE, is a communication protocol much like WebSockets, but with the implication of **unidirectional data**. In this architecture, the server is consistently sending updates to the client as an automatic process. This was standardized under HTML5 by the [W3C](https://www.w3.org/TR/2009/WD-eventsource-20091029/), and is thus compatible with any solution that is likewise compatible with HTML5.

> Of note is that there is a competing standardization from the [Web Hypertext Application Technology Working Group](https://whatwg.org/) – this is a relic from movement away from “HTML5” and into what WHATWG is calling “HTML Living Standard”. The general working consensus is that, WHATWG’s standardization is prioritized in the rare cases of divergent standards. This could become more of an issue as time marches forward, given that WHATWG was created due to a perceived lack of interest from W3C towards evolving HTML, but for the time being, either standard is generally acceptable.
While simple in theory, Server Sent Events are anything but simple when considering benefits and drawbacks.

#### Pros
SSE is **not bidirectional** in its communications — the server is issuing the events in a steady, predictable method. This is hugely beneficial to applications which do not need the two-way communications baked into WebSockets or other such solutions, as this means **lower bandwidth**, and an allowance for the connection to be temporary rather than always-on during the duration of data transfer. By its nature, the data is being transferred one way, and thus there is no need to wait for data to be returned.

Additionally, at least in theory, SSE is easier to set up in complex situations. You only have to worry about data traveling one direction via one system, thus reducing complexity dramatically. There is no need to define a message exchange protocol, no need to specify data duration or wait times, no need to support bilateral messaging — the single direction saves a lot of complexity.

#### Cons
That simplicity could be where SSE fails for particular use cases. SSE is a very poor solution for situations that require **bidirectional communication**, and while this seems obvious, it would surprise many developers to see how many systems actually depend on bidirectional communication for simple functionality.

While much of this can be fixed with workarounds, a developer’s goal in choosing an event-driven protocol should be to find one that works out of the box, not to find a solution that might work if configured properly and given secondary systems upon which to depend.

There is also the issue of **security** and authentication. While two-way systems can easily use authentication methodologies, SSE handles this using **header forwarding**. While headers can be manipulated and overridden in many languages and applications, the EventSource object in JavaScript does not natively support this, which would cause many adoptees some major headaches.

Finally, there is a concern over loss of efficiency with **over transmitting** data. A two-direction system can determine when a client or server disconnects, but SSE can only determine that a client has disconnected after attempting a full data transmission and receiving a noted failure. Because of this, data can be lost rather quickly, and with many failed connections, this loss can mount dramatically over time.

## Conclusion
There is no one event-driven solution that works in every use case. While many would argue that event-driven solutions should be REST based, which suggests REST Hooks as the answer, many others would argue that it is entirely situational, and that REST is not always the silver bullet it’s touted to be.

If you are building for scalability with low overhead in a browser environment, **WebSockets** are a great solution. Conversely, if you’d like those same benefits but are working in a non-browser system, then **WebHooks** should be your approach. **REST Hooks** are not only great for RESTful services, they’re also much easier to set up than either, and thus are great in low-time high-rush situations. **Pub-Sub** can be great if you need to enforce a division between client and server, and this can further be established and controlled in an even stronger way with **Server Sent**.

Simply put, the best solution will be the one that fits your specific situation and build — any of these solutions, given the correct system, is a great solution. To that end, each solution has a very specific use case.

## TLDR Comparison Table
| PROTOCOL | RELATED TO | STANDARD BODY | NOTES |
| ------ | ------ | ------ | ------ |
| WebSockets | TCP, HTTP-like | IETF, W3C | Two-way communication over TCP<br>Designed for web browsers & web servers<br>Good for lower overhead scenarios<br>Supported in all major browsers |
| Webhooks | URI, HTTP | - | User defined “HTTP callbacks”<br>Triggered by an event HTTP<br>Requests are made to Webhook URI<br>Enables real-time event triggering|
| REST Hooks | HTTP | Zapier | Lightweight subscription layer<br>Manipulated by a REST API<br>Essentially a WebHook in REST |
| Pub-Sub | - | - |Client subscribes to classes<br>Bidirectional<br>Middleman layer between client and server<br>Loose coupling|
| Server Sent | HTTP, HTML5 , DOM | WHATWG, W3C |Server constantly sends updates to the client<br>Unidirectional push notifications as DOM events|
