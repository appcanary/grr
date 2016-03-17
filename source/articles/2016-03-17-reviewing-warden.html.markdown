---
title: Reviewing warden
date: 2016-03-17
tags: Great Ruby Review, warden, No bugs found
author: team
published: true
layout: post
---

[warden](https://github.com/hassox/warden)
Latest version reviewed: 1.2.3

Summary: No exploitable vulnerabilities found.

Notes from researcher:
Based on the foregoing, Warden appears to be robustly safe for production - while it has not been updated since 2014, the development team is extremely cautious in allowing new pull requests. As a final note, Warden is very thoroughly commented, which makes the codebase very accessible for review.

The warden library is a Rack middleware designed for building higher-order authentication solutions. It is the basis of the popular Devise authentication library.

Dylan focussed his attention across four main attack surfaces: safe serialization, safe dynamic method calls, and the correct usage of symbols and regular expressions.

Warden avoids any serialization issues by virtue of simply not deserializing user-controlled data. Whenever it dynamically calls methods, it is always careful to first sanitize input prior to passing it along. Symbol usage within Warden, which in Ruby versions prior to 2.2 can cause DoS attacks, is carefully regulated. Similarly, Dylan was unable to find any logic errors in warden's usage of regular expressions.

Finally, Dylan was unable to find a way to exploit any uses of eval, shell injection (system calls are simply not used) or file or method generation.