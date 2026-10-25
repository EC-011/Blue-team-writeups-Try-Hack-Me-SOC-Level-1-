# How I'd Triage an Alert as a Tier 1 SOC Analyst

**Date:** [25/10/2026]
**Based on:** TryHackMe SOC Level 1 (intro to SOC, alert triage)
**Skills shown:** alert triage, prioritisation, escalation, documentation

## Intro
 What are the SOC 

 SOC L1 
 

## The scenario
> SIEM alert: 6 failed logins for "j.smith" in 4 minutes, then a successful
> login from a country the user has never logged in from. Time: 02:14 AM.

What looks suspicious? What could be innocent?

## First steps: gathering context
- Who is the user, and is the account privileged?
- What data would I check? (auth logs, login history, IP reputation, other alerts)
- How would I prioritise it, and why?

## Two possible outcomes
**A. False positive:** what evidence confirms it, and what I'd do.
**B. True positive:** what evidence points to compromise, and what I'd do.

## The escalation call
- When I'd close it, and when I'd escalate to L2
- My handover note: who, what, when, what I checked, what I think, what I recommend

## The business side
1-2 lines on false-positive fatigue and why documenting decisions matters.

## What I found hard / what's next
One honest line, plus a pointer to the next write-up.
