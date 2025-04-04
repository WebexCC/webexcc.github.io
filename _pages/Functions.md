---
title: Functions
date: 2025-04-02
layout: post
---

**Functions** are a forthcoming feature of Webex CC, which allows for custom Javascript or Python code blocks to be added into Flows, much like how Subflows work.  E.g., Input and Output variables.

# Random Number Generator

If you need a random number generated in your Flow, you could use the following Function to pick a random number between two bounds: a lower bound, and an upper bound (e.g., a number between 1 and 10).

Input Variables:
* lower_bound (integer), e.g., 1
* upper_bound (integer), e.g., 10

Output:
* random_number (integer) via `$.random_number`, e.g., 7

Javascript:
```javascript
export const handle = async (request, response) => {
    const { lower_bound, upper_bound } = request.inputs;
    
    let random_number = -1;
    if (lower_bound >= 0 && upper_bound > lower_bound) {
        random_number = Math.floor(Math.random() * (upper_bound - lower_bound + 1) + lower_bound);
    }
    
    response.data = {"random_number": random_number};
    
    return response;
}
```


# Regex Pattern Matcher

If you need to see if some input from the caller matches a specific pattern, like when the caller inputs an extension of phone number via Collect Digits, and you want to make sure it's within a valid input range, you could use this needle in the haystack search feature, to valid good input.

Input Variables:
* needle (String), e.g., 6125551212
* haystack (String), e.g., [2-9]..[2-9]......

Output:
* match (boolean) via `$.match`, e.g., True

Javascript:
```javascript
export const handle = async (request, response) => {
    const { needle, haystack } = request.inputs;
    try {
        const regex = new RegExp(haystack);
        response.data = {"match": regex.test(needle)};
    } catch (error) {
        response.data = {"match": false};
    }
    return response;
}
```
