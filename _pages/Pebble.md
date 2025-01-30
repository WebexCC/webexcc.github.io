---
title: Pebble Playground
date: 2025-01-30
layout: post
---

## Pebble Playground

**Pebble Playground** is a collection of useful pebble expressions for use in Webex Contact Centre flows.

# Time Expressions

This section contains time related expressions and functions, useful for processing hold times, days of week, etc.

<!-- {%raw%} -->

**`{{now()}}`**

<!-- {%endraw%} -->

Returns the current date and time.

<img src="/assets/images/Pebbleplayground/now.png" height="400" />

<!-- {%raw%} -->

**`{{now()|epoch}}`**

<!-- {%endraw%} -->

Returns the current date and time in epoch format.

<img src="/assets/images/Pebbleplayground/NowEpoch.png" height="400" />

<!-- {%raw%} -->

**`{{now() | date("EEEE", existingFormat="yyyy-MM-dd'T'HH:mm:ss.SSS'Z'")}}`**

<!-- {%endraw%} -->

Returns the name of the current day.

<img src="/assets/images/Pebbleplayground/currentday.png" height="400" />

<!-- {%raw%} -->

**`{{(now() | epoch(inMillis=true)+86400000) | date("EEEE")}}`**

<!-- {%endraw%} -->

Returns the name of tomorrow.

<img src="/assets/images/Pebbleplayground/Tomorrow.png" height="400" />

<!-- {%raw%} -->

**`{{ "December 10, 2023" | date("MM-dd-yyyy HH:mm:ss", existingFormat="MMMM dd, yyyy") | epoch(format='MM-dd-yyyy HH:mm:ss')}}`**

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

**`{{ now() | epoch(inMillis=true) % 10 }}`**

<!-- {%endraw%} -->

Returns a single digit number that seems random. Behind the scenes, we are using the modulus operator to divide our Epoch in Ms by 10 and return the remainder. Use 100 for a 2 digit number, and 1000 for a 3 digit number and so on. Useful for "Randomising" the start offset of music on hold, so you don't play the same 10 second clip of music repeatedly, Burning the same 10 seconds of Cisco Opus into a callers mind, driving them insane in the process.

<img src="/assets/images/Pebbleplayground/randnum.png" height="400" />
