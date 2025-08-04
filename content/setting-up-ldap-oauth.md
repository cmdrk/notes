---
title: Setting up Identity services for my home lab
---

## Background

_What is Man? A miserable little pile of secrets_
    - André Malraux

I'm going to be honest with you, I thought that quote was from Dracula in the
Castlevania video game series. I was pleasantly surprised to learn it is
actually from the French novelist André Malraux, and I feel considerably more
erudite and learned for attributing the quote to him instead. I also considered
a pithy segue into how the attribution of that quote resonates in some
fundamental way with Identity Services, but I'll spare you and get right to it.

For setting up [[open-ondemand|Open OnDemand]], I needed to create some
identity services in my lab. This seemed like a good opportunity to take a
second look at some technologies I've considered but ultimately passed over at
$JOB for various reasons. 

There's a wonderful presentation by William Brown about Kanidm (see below), in which he
covers a bit of the history of identity management systems. One of the things
that I recall from William's talk is that there's a sort of schism between
identity and auth services, with traditional enterprises relying on Active
Directory, LDAP, Kerberos and so on, while small, little-known startups like
Google and Twitter developed web-centric authentication and authorization
systems that would evolve into modern standards like OpenID and OAuth2.

For modern research computing environments, there's a need to support both.
Traditional identity services are essential to shared UNIX environments, while
(arguably) more modern technologies like OAuth2 are a requirement for providing
services like Jupyter, Open OnDemand, etc.

For my home lab, I've decided to check out a simplified LDAP implementation
called [LLDAP](https://github.com/lldap/lldap) (yes, so light they say it
twice). 


## LLDAP setup on Debian 12

## Dex
Most of my experience is with [Keycloak](https://www.keycloak.org/), the open
source upstream of [Red Hat Single
Sign-On](https://access.redhat.com/products/red-hat-single-sign-on/). While I
think Keycloak is an excellent technology at scale, I wanted to roll with
something a bit more simple this time around.

## Kanidm Presentation
![](https://www.youtube.com/watch?v=8IaxnSAggkI)
