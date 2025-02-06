---
title: Pebble Playground
date: 2025-01-30
layout: post
---

**Pebble Playground** is a collection of useful pebble expressions for use in Webex Contact Centre flows.

# Working with Dates and Time

This section contains time related expressions and functions, useful for processing hold times, days of week, etc.

## Current Date and Time
Return the current date and time.

<!-- {%raw%} -->
Expression: **`{{ now() }}`**
Result: **`2025-01-30T12:42:45.760Z[UTC]`**
<!-- {%endraw%} -->

<img src="/assets/images/Pebbleplayground/now.png" height="400" />

<!-- {%raw%} -->

**`{{now()|epoch}}`**

<!-- {%endraw%} -->

Returns the current date and time in epoch format.

<img src="/assets/images/Pebbleplayground/NowEpoch.png" height="400" />

<!-- {%raw%} -->

**`{{ now() | epoch(inMillis=true) | date("EEEE") }} `**

<!-- {%endraw%} -->

Returns the name of the current day.

<img src="/assets/images/Pebbleplayground/currentday.png" height="400" />

<!-- {%raw%} -->

**`{{(now() | epoch(inMillis=true)+86400000) | date("EEEE")}}`**

<!-- {%endraw%} -->

Returns the name of tomorrow.

<img src="/assets/images/Pebbleplayground/Tomorrow.png" height="400" />

<!-- {%raw%} -->

**`{{ "December 10, 2023 00:00" | epoch(format="MMMM dd, yyyy HH:mm") }}`**

<!-- {%endraw%} -->

Gives the epoch timestamp of a specific date.

<img src="/assets/images/Pebbleplayground/epochofdate.png" height="400" />

<!-- {%raw%} -->

**`{{(now() | date("MM-dd-yyyy HH:mm:ss", existingFormat="yyyy-MM-dd'T'HH:mm:ss.SSS'Z'", timeZone="America/Chicago") | epoch(format='MM-dd-yyyy HH:mm:ss')  - ('10-01-2023 00:00:00' | epoch(format='MM-dd-yyyy HH:mm:ss'))) / (606024)}}`**

<!-- {%endraw%} -->

Returns the number of days between now and a given date.

<img src="/assets/images/Pebbleplayground/daysbetween.png" height="400" />

<!-- {%raw%} -->

**`{{(now() | epoch(inMillis=true)) -  ('10-19-2022 16:18:03.779' | epoch(format='MM-dd-yyyy HH:mm:ss.SSS', inMillis=true))}}`**

<!-- {%endraw%} -->

Returns the number of Ms between now and a given date.

<img src="/assets/images/Pebbleplayground/msbetweendate.png" height="400" />

<!-- {%raw%} -->

**`{{now() | epoch(inMillis=true) % 10}}`**
Or
**`{{(((now() | epoch(inMillis=true)) % 1000 / 1000.0) * (180 - 90) + 90) | numberformat("#")}}`**

<!-- {%endraw%} -->

Returns a single digit number that seems random. Behind the scenes, we are using the modulus operator to divide our Epoch in Ms by 10 and return the remainder. Use 100 for a 2 digit number, and 1000 for a 3 digit number and so on. The second statement returns a random number between 90 and 180.Useful for "Randomising" the start offset of music on hold, so you don't play the same 10 second clip of music repeatedly, Burning the same 10 seconds of Cisco Opus into a callers mind, driving them insane in the process.

<img src="/assets/images/Pebbleplayground/randnum.png" height="400" />

<!-- {%raw%} -->

**`{{now() |epoch() - QTime > VMTimeout}}`**

<!-- {%endraw%} -->

QTime should be a variable set right after the queue contact node in the flow using a simple now() Epoch. VMTimeout is an integer that can be loaded from a global variable. The above statement will allow you to evaluate true or false if a person has been queueing longer than the specified VM Timeout.

<img src="/assets/images/Pebbleplayground/Vmtimeout.png" height="400" />
