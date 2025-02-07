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

Result: **`2025-02-06T21:09:02.712Z[UTC]`**

<!-- {%endraw%} -->

<img src="/assets/images/Pebbleplayground/now.png" height="400" />

## Epoch (Seconds since January 1, 2970 12:00am)

Returns the current date and time in epoch format.

<!-- {%raw%} -->

Expression: **`{{ now() | epoch }}`**

Result: **`1738876452`**

<!-- {%endraw%} -->

<img src="/assets/images/Pebbleplayground/NowEpoch.png" height="400" />

## Epoch for Static Date and Time

Gives the epoch timestamp of a specific date.

<!-- {%raw%} -->

Expression: **`{{ "December 10, 2023 00:00" | epoch(format="MMMM d, yyyy HH:mm") }}`**

Result: **`1702166400`**

<!-- {%endraw%} -->

<img src="/assets/images/Pebbleplayground/epochofdate.png" height="400" />

## Day of Week

Returns the name of the current day of the week.

<!-- {%raw%} -->

Expression: **`{{ now() | epoch(inMillis=true) | date("EEEE") }}`**

Result: **`Thursday`**

<!-- {%endraw%} -->

<img src="/assets/images/Pebbleplayground/currentday.png" height="400" />

## Tomorrow's Day of Week

Returns the name of the day of the week for tomorrow.

<!-- {%raw%} -->

Expression: **`{{ (now() | epoch(inMillis=true) + 86400000) | date("EEEE") }}`**

Result: **`Saturday`**

<!-- {%endraw%} -->

<img src="/assets/images/Pebbleplayground/Tomorrow.png" height="400" />

## Elapsed Days

Returns the number of days between now and a given date.

<!-- {%raw%} -->

Expression: **`{{ (now() | epoch / 86400) - ("October 1, 2023 00:00" | epoch(format="MMMM d, yyyy HH:mm") / 86400) }}`**

Result: **`495`**

<!-- {%endraw%} -->

<!--img src="/assets/images/Pebbleplayground/daysbetween.png" height="400" -->

## Elapsed Milliseconds

Returns the number of Ms between now and a given date.

<!-- {%raw%} -->

Expression: **`{{ now() | epoch(inMillis=true) - "October 1, 2023 00:00" | epoch(inMillis=true, format="MMMM d, yyyy HH:mm") }}`**

Result: **`42753373824`**

<!-- {%endraw%} -->

<img src="/assets/images/Pebbleplayground/msbetweendate.png" height="400" />

## Pseudo-Random Numbers

### Option 1

Returns a single digit number that seems random. Behind the scenes, we are using the modulus operator to divide our epoch in ms by 10, and return the remainder. You can use 100 for a 2 digit number, 1000 for a 3 digit number, and so on.

<!-- {%raw%} -->

Expression: **`{{ now() | epoch(inMillis=true) % 10 }}`**

Result: **`5`**

<!-- {%endraw%} -->

<img src="/assets/images/Pebbleplayground/randnum1.png" height="400" />

### Option 2

This second example returns a random number between a lower bound and an upper bound: 90 and 180, in this example. Useful for "Randomising" the start offset of music on hold, so you don't play the same 10 second clip of music repeatedly, Burning the same 10 seconds of Cisco Opus into a callers mind, driving them insane in the process.

<!-- {%raw%} -->

Expression: **`{{ ((now() | epoch(inMillis=true) % 1000 / 1000.0) * (180 - 90) + 90) | numberformat("#") }}`**

Result: **`106`**

<!-- {%endraw%} -->

<img src="/assets/images/Pebbleplayground/randnum2.png" height="400" />

## Queue Time Threshold

QTime should be a variable set right after the queue contact node in the flow using a simple now() Epoch. VMTimeout is an integer that can be loaded from a global variable. The above statement will allow you to evaluate true or false if a person has been queueing longer than the specified VM Timeout.

<!-- {%raw%} -->

Expression: **`{{ now() | epoch - QTime > VMTimeout }}`**

Result: **`true`**

<!-- {%endraw%} -->

<!--img src="/assets/images/Pebbleplayground/Vmtimeout.png" height="400" -->
