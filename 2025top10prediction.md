---
layout: default
title: "OWASP Top 10 - 2025 Predictions"
description: "Predicting OWASP Top 10 - 2025"
date: 2025-02-18
categories: trends
permalink: /trends/2025top10prediction/
---
# UNDER CONTSTRUCTION

This article is still a work in progress...

# OWASP 2025 - Predicting the Top 10 List
## It's Been A While...

Since September 2021 we haven't had an OWASP Top 10 released.  They typically release a new Top 10 every four years judging by past behavior with the most recent being 2021 and then 2017 before that.

As of July 2024, [according to OWASP themselves](https://www.owasptopten.org/), we could be looking at an update to this list in early 2025, which could be any day now!

## What Is OWASP Top 10 and How Does It Works?

OWASP 2017 was purely almost exclusively on incidence rate, or how many applications tested did that security category impact.  The higher the incidence, the higher up the list that vulnerability category would appear.  In 2021, they introduced impact into this calculation saying Exploitability was given 60% credence and Impact 40%.  This seems subjective to my untrained eye, but my opinion on how this could be improved will be saved for another post.  The gist from OWASP on why do this is pure statistical incidence rates ignore the broader trends with development of mitigations along with rising technology and the introduction of new vulnerabilities.

Overall, the Top 10 list is a solid resource in understanding what vulnerabilities are ubiquitous in the AppSec world, and knowing how to read the report and update your approach to AppSec around this information will help to find impactful vulnerabilities.

## What's Happened Since 2021?
### More AI
It's unavoidable, and even some software engineers will admit that they can't do their jobs when ChatGPT isn't working.  AI has changed so much already, but one notable change is that coding new applications, features, and tools has increased exponentially.  I still believe humans are far superior to AI and will continue to be, but having a companion that can churn out the scaffolding of code for you to then wire up with the more complex logic needed to make it shine makes the difference between 

The down side to this is a programmer can get by without knowing a lot of important fundamentals in programming and can be over reliant on the AI's ability to make sound coding decisions.

### More Repos, More Problems
Again, AI isn't helping us here.  One can churn out lots of code and stuff it into their GitHub profile.  
CI/CD is still king, and quickly

## My Best Guestimation of 2025's Top Ten
### Downgrades
Injections A03:2021 slid down the list two spots from A01:2017, and this was after adding the massive volume of XSS to this category.  I can see this trend continuing with the improvement of automated scanners and AI driven monitoring.  The bar was raised on injection attacks and I can see this trend continuing.

Broken Authentication dropped from the number two spot down to number seven.  This continues to be a popular weakness to test for.  However, increased efforts to 

### Upgrades

As some weaknesses are shored up, other weaknesses rise up to take their place.  This could be from increased scrutiny and testing has unearthed new techniques for exploitation, or it could just be by the very nature of the other weaknesses dropping down the list.  Either way, here are my thoughts on what categories will be making their way up the list this time around.

SSRF, to me, seems very similar to the root causes of Broken Access Control weaknesses - for example Path Traversal (CWE-35) vulnerabilities.  In essence, we are requesting the application to make a request to the server, exploiting a trusted relationship and using a field that lacks proper access controls to see beyond the field.  Without proper access controls, such as deny by default, this attack succeeds.  The root cause is similar between the two vulnerabilities.  For this reason I see SSRF A10:2021 being combined with A0

+ Speculations on what might get combined?
  - SSRF w/ Broken Access Control - This category feels in line with Path Traversal (CWE-35) vulnerabilities.  In essence, we are telling the application to tell the server it wants resource sent to it or an action performed.  Without proper access controls, such as deny by default, this attack succeeds.  The root cause is similar between the two vulnerabilities.
+ What's the List?

### My Top Ten 2025 Prediction

Disclaimer: this is purely a guess, I have no numbers to back this up on.  The list below is based on hunches and hearsay over the last two years.

1. Broken Access Control (w/ SSRF Added)

  If SSRF is added to this category, I can't imagine it losing its footing at the number one spot. Access to privileged data and functionality is critical, and any application with privileges (which every application has an owner/admin) is potentially vulnerable to this. There is also a tedium to testing Access Controls that makes it hard to automate.
2. Cryptographic Failures

  This is still a main focus for a lot of hunters.  The question of how a key or secret is generated and whether the algorithms used to encrypt or the encoding process can be deciphered is something that remains largely in the minds of the attackers.  If implemented poorly this is more security by obscurity and seasoned threat actors and researchers can see through that.
3. Security Misconfiguration

  
4. Insecure Design

  As secure frameworks are more ubiquitous and 
5. Injection

  This category isn't getting any lovin', down two spots from 2021.  This is due in large part from all the frameworks and coding standards, the automated tools and AI monitoring systems, and the improvement of WAFs and CSPs helping to keep the client and server safe.  However, this remains the starting point for bug bounty hunters and a lot of notable hunters advise learning these vulnerabilities early and get a large volume of bugs that fall into this category.  I'd guess over 20% of all bugs reported fall into Injection attacks.
6. Vulnerable and Outdated Components

  Holding fast to the sixth spot, 
7. Software and Data Integrity Failures

  I feel silly not bumping this higher up the list after the disastrous CrowdStrike error, which is estimated to have cost more than $5 billion from Fortune 500 companies alone.  
8. Identification and Authentication Failures

  I can imagine this sliding down, having drop fived spots from 2017 to 2021.  This trend of improved framework standardization will likely 
9. Leaving For Community Survey

  OWASP has shown it is sensitive to community perspective.  There may be something in the industry that is on everyone's mind that will make an appearance.  I'm surely hoping so!
10. Security Logging and Monitoring Failures

  AI is helping to empower monitoring and logging efforts.  Being that this category is more subjective and was added in 2017 and 2021 because the community surveyed insisted this was an issue.  

## Closing Thoughts

The are many variables to security and coming up with the most objective list is a monumental task that is prone to have errors and shortcomings.

One such shortcoming I could see lack of consideration for cost of impact and ability to combine weaknesses.  With AI being widely available, I could see this being leveraged to investigate reports that showcase multiple weaknesses being chained to deliver maximal impact.  In a similar way so SSRF being placed as A10:2021, this was included because the community survey highlighted the critical risk this weakness exploited, even though incidence rates were so low.  I think there is a great opportunity for the security community to consider the true impact low severity weaknesses when combined with other weaknesses.

In conclusion, I'm excited to see what 2025 brings and how the Top Ten shapes up.  
