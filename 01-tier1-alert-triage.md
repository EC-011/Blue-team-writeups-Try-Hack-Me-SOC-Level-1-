# How I'd Triage an Alert as a Tier 1 SOC Analyst

**Date:** [25/10/2026]
**Based on:** TryHackMe SOC Level 1 (intro to SOC, alert triage)
**Skills shown:** alert triage, prioritisation, escalation, documentation

## Intro
 What are the SOC - they consist of a team of security professionals, that have the roles of monitoring, preventing, detecting, investigating and responding to threats within a company. 
 

## The scenario
> SIEM alert: 6 failed logins for "j.smith" in 4 minutes, then a successful
> login from a country the user has never logged in from. Time: 02:14 AM.

Using what I've learnt, this type of alert can be considered suspicious as theirs been multiple login attempts made for "j.smith" and the thew attempts are form a location the user has never logged in from at 2am, this could be a false positive depending ( may be away accessing their account and forgot their password or not )  on the circumstances but as a soc L1 I would Open the alert and start an investigation to gather more information as its showing suspicious tendency's .  


## First steps: gathering context
My first step would be to understand who is the account related to within the company and the access privileges the account has.

Once confirmed I would then proceed to check the account's data ,auth logs , login history , location of previous logins and confirm it with a check list containing , Was their a successful login?, Did it pass or fail MFA, the time zone of the attempted login dose it match were their expected to be ?, and are their any other failed login attempts.

I would use this information and try to match the login attempt for "j.smith" to gauge its activity , finding answers to question like , are they working out of hours , are they scheduled to be working from a different country for business, have they recently changed their password , did anything suspicious happen before the login attempts 

- How would I prioritise it, and why?
  
- Depending on the information being discovered i would check the most critical ones first as in ,
- Have they had a successful login attempt, if yes then i would need to act quickly and escalate the issue ( hight priority) to the l2 soc while giving them the details found and determine the level of access they have via the account privileges
- Did it pass MFA, if yes then theirs another escalating issue that needs to be passed on to L2 and tracked , If MFA failed or wasn’t completed, the login may not have fully succeeded, so it’s lower priority, though still worth noting

## Two possible outcomes
**A. False positive:** 

If it turns out based on the information found that it was indeed "j.smith" logging in at that time from a different location then it would be considered a false positive , but this would only be after quickly verifying this information, via checking their schedule and contacting them using a trusted channel.  

**B. True positive:** 
In the worst case scenario it can be broken down into multiple factors which would result in a true positive.

Evidence- if we get confirmation that "j.smith" says it wasn’t them,  the IP has a bad reputation, other accounts were hit from the same IP, or there’s odd activity after login (new mailbox rules, a new MFA device, large downloads).

in this case if they are true then its immediate action to escalate to L2, recommend containment (reset the password, revoke sessions, disable the account if needed), and check whether other accounts were targeted. Note that L1 recommends and L2 or IR usually carries it out.


## The escalation call

 When I'd close it,
The ticket would be closed if im able to confirm and verify that the activity detected was "j.smith" in this case its a false positive


 when I'd escalate to L2
The ticket would be escalated after verifying that it was not "j.smith" and by checking if the attempted log in was successful and still happening 

- My handover note: who, what, when, what I checked, what I think, what I recommend
  Esclating it to the L2 SOC i would give them a short but informative note on what i found and the issue at hand ( An example below)

  ## Example Handover note
**To L2:** j.smith (Finance, standard user): 6 failed logins then a
successful login at 02:14 from a country with no login history. MFA
[passed/failed], IP [flagged/clean], no contact with the user yet.
**Assessment:** Likely compromised account, medium-high confidence.
**Recommend:** Reset password, revoke sessions, review activity since
02:14, and check other accounts for the same IP.


## The business side
False positive's can be seen as a good thing since it means its not a breach or an attack but too many of them over a period of time creates fatigue, meaning that as a l1 soc if theirs so many alerts and tickets , I would be overwhelmed and might possibly be unable to see a critical attack since theirs a overflow hence why setting up Tuning rules and making documentation of past issues is necessary to help mitigate the overflow issue , so when a real attack is their I'm able to see it and deal with it quickly and accordingly .

## What I found hard / what's next
The hardest part was balancing speed with thoroughness. Working through alerts quickly is important, but checking properly before closing or escalating takes judgement. Next I’ll practise on real alerts in Splunk and write up a hands-on investigation.
