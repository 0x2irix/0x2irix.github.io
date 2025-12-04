---
title: Race condition leads to Community-plan limit bypass
published: 2025-12-04
description: ''
image: 'race.jpg'
tags: [bugs, web, business logics]
category: 'bugs'
draft: false 
lang: ''
---


### **السَّلَامُ عَلَيْكُمْ وَرَحْمَةُ اللهِ وَبَرَكَاتُهُ**

This write-up explains how I could bypass the free-plan site limit using race condition  in the pipeline-creation flow allows multiple pipelines to be created concurrently, permitting a Community-plan account to exceed the plan limit and obtain features reserved for higher-tier plans.

## **First: What is a race condition?**

A race condition occurs when the outcome of a process depends on the unpredictable order in which multiple threads or processes access and modify shared resources. This can lead to unexpected and potentially erroneous results, or even security vulnerabilities. Essentially, it’s a “race” to access a resource, and the order in which they arrive determines the outcome.

## Free Plan vs Pro Plan

![2025-12-04 01_11_20-Race condition leads to Community-plan limit bypass.png](2025-12-04_01_11_20-Race_condition_leads_to_Community-plan_limit_bypass.png)

when you see the policy of free plan you find only have 20 pipelines can create it

we try to use race condition to create more than 20

### Add Pipeline request

![2025-12-04 01_16_41-WhatsApp Video 2025-11-05 at 19.42.58_3335af7d.mp4 - VLC media player.png](2025-12-04_01_16_41-WhatsApp_Video_2025-11-05_at_19.42.58_3335af7d.mp4_-_VLC_media_player.png)

send request to repeater and add it to group then duplicate it

![2025-12-04 01_20_54-WhatsApp Video 2025-11-05 at 19.42.58_3335af7d.mp4 - VLC media player.png](2025-12-04_01_20_54-WhatsApp_Video_2025-11-05_at_19.42.58_3335af7d.mp4_-_VLC_media_player.png)

## **Impact**

- Bypasses plan restrictions and business logic.
- Allows free users to access paid functionality without authorization.
- Potential platform abuse through the creation of excessive endpoints.

## HackerOne proof

First: HackerOne Triager accept the report and change status to **triage and pending bounty**

![Screenshot 2025-12-04 012441.png](Screenshot_2025-12-04_012441.png)

But internal team closed my report to info which say the business logic is out of the scope and my report is duplicated to my report (same report id but is lay)

![Screenshot 2025-12-04 012441.png](Screenshot_2025-12-04_012441.png)

Scope of App

is un predictable which most of logic bugs is out of the scope

![2025-12-04 01_33_57-.png](2025-12-04_01_33_57-.png)