---
title: Functions
date: 2025-04-02
layout: post
---

**Functions** are a feature of Webex CC, which allows for custom Javascript or Python code blocks to be added into Flows, much like how Subflows work. E.g., Input and Output variables.

# DNIS Data Map

If you have ever used a Case activity on the `NewPhoneContact.DNIS`, to then set starting variables for things like: which queue to send the call to, which voicemail extension to divert the call to, etc., then this function could replace your Case activity, and save you quite a few Set Variable activities, streamlining your Flow.

In the example below, I am only mapping three DNIS, but you can map several thousand DNIS, and within each DNIS mapping, I am only storing a Queue ID, and a Priority, but you can store so much more data, to include: Business Hours ID, Skill Names, TTS Messages, etc.

Input Variables:

- input (String), e.g., `NewPhoneContact.DNIS`

Output:

- output (JSON), via `$.output` e.g., `{"queue_id": "some queue id here", ...}`

Javascript:

~~~ javascript
export const handle = async (request, response) => {
    const { input } = request.inputs;

    const data = {
        "+16125551000": {"queue_id": "7ab606fe-0443-42db-9013-2e9e87edfeed", "priority": 1},
        "+16125551001": {"queue_id": "7ab606fe-0443-42db-9013-2e9e87edfeed", "priority": 10},
        "+17635552000": {"queue_id": "467eae08-261d-4f32-b49b-2f1ae5d02cbe"}
    };

    response.data = {"output": data[input] || ""};

    return response;
}
~~~

# Random Number Generator

If you need a random number generated in your Flow, you could use the following Function to pick a random number between two bounds: a lower bound, and an upper bound (e.g., a number between 1 and 10).

Input Variables:

- lower_bound (integer), e.g., 1
- upper_bound (integer), e.g., 10

Output:

- random_number (integer) via `$.random_number`, e.g., 7

Javascript:

```
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

If you need to see if some input from the caller matches a specific pattern, like when the caller inputs an extension or phone number via Collect Digits, and you want to make sure it's within a valid input range, you could use this "needle in the haystack" search feature, to validate good input.

Input Variables:

- needle (String), e.g., 6125551212
- haystack (String), e.g., [2-9]..[2-9]......

Output:

- match (boolean) via `$.match`, e.g., True

Javascript:

```
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
