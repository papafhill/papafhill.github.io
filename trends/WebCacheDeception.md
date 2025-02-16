---
layout: post
title: "Web Cache Deception: Vuln Trend Analysis"
description: "Vulnerability Trend Analysis - Web Cache Deception"
date: 2025-02-14
categories: tools
permalink: /trends/WebCacheDeception/
---
# UNDER CONSTRUCTION

# Critter Spotlight: Web Cache Deception

I have heard from multiple places in the last few months that Web Cache Deception (CWE-525) is a vulnerability to keep an eye on in 2025.  Let's take a closer look and see whether the word on the street holds water.

## What is Web Cache Deception?

When it comes to certain data, the origin server needs to be picky about what data they want to handle every request themselves and what data they want to have help serving to the client.  It makes sense that dynamic data, that is user-specific content, sensitive information, and XYZ to name a few, the server wants to handle all that, and they don't want that information stored outside their system.  On the other hand, static data that any user could request the origin server would prefer to serve that once and not be bothered with the same request for a set amount of time.

This is where caching can come in extremely valuable, as it takes request load off the origin server and puts the burden elsewhere.  Namely, CDNs or Content Delivery Networks are servers that help speed up delivery time of content to the client by helping the origin server manage requests.  When they receive a request, they run a number of checks before passing the content to the end user.  If the content passes certain tests, then it will be cached for other users to receive straight from the CDN rather than from the origin server.

However, this is where things can get jumbled. If the CDN doesn't fully validate the requested content, or if it misinterprets the dynamic content as static, it can store the requested sensitive data in the cache.

To draw a breif connection in caching behavior; ISP DNS servers like to cache DNS record requests aggressively.  If I make a `dig` request using my personal ISP, they will generally cache that data to reduce the volume of dig requests they have to handle.  In a similar way, finding how the cache server operates on your target is important. 


## Examples in Action



## Impact

Web cache deception can lead to Account Takeover and/or leaking of PII, PHI, or other sensitive data.  That said, the attack still requires user interaction, and the Scope is almost always Unchanged.  This puts web cache deception at a solid 8.8 - High on the CVSS scoring system.

The highest impact on record was a Critical reported by Spaceraccoon, AKA Eugene Lim, that was a vulnerability found on Shopify.  The payout was a whopping $40,000 for this find and is the highest disclosed web cache deception bounty to date.

One tool I'm growing to enjoy is HackerOne's CWE Discovery charts.  For CWE-525 it looks like the average severity came in as a Medium over 11 reports in the last 12 weeks of the date of this analysis.

## Is This A Trend?

+ Is this widespread? ....

It doesn't feel like this is a trend, at least for smaller corporations that don't have to serve a large amount of similar, static requests.

+ Added to Web Security Academy on August 13, 2024, this vulnerability is ....

My conclusion: Web cache deception is a worth while vulnerability to consider from a security perspective depending on cache behavior on your applications and the data being stored/served.  This is especially true for large corporations with massive attack surface, as breaches of this nature could have severe concequences and the likelihood of using CDNs to cache data is all but garaunteed.

### Learning Material
Disclosed Reports:
+ 
+ 

Bounty Hunter Information
+ 
+ [NahamSec's Blog](https://www.nahamsec.com/posts/high-value-web-security-vulnerabilities-to-learn-in-2025) - Web Cache Deception: A Growing Threat


Labs
+ [Portswigger - Web Security Academy](https://portswigger.net/web-security/web-cache-deception)
