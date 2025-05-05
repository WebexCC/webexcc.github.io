---
title: Evaluate
date: 2025-05-05
layout: post
---

**Evaluate** is a node within a Webex Connect flow, which allows you to execute Javascript code.

While similar to Functions in WxCC Flow Designer, the Evaluate node runs on the [Rhino JS Engine](<https://en.wikipedia.org/wiki/Rhino_(JavaScript_engine)>), and therefore, [is not compatible](https://mozilla.github.io/rhino/compat/engines.html) with more common Javascript programming features and concepts.

With this in mind, you likely cannot use typical AI code generation tools, even the built-in one inside of Webex Connect. You might have success with the results, but you also might be fighting an unwinnable battle.

# Bare Bones Script

The most basic script you could possibly write, returns a value of any type, and also has one output branch, which matches your return value, and is given some kind of label.

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/bare-bones.png" height="300" />

As you can see in the above example:

- I am typing `0;` as the script itself, which, is how you return output. You do not need the keyword `return` as you might be used to in vanilla JS.
- I have one branch created called "Success" (the name is up to you)
- I set the output value for that branch to match what the script is outputing

## Bare Bones Testing

There is a code testing function within the node, and if you click test, then click test again, it will either show you some output, or an error.

In my case, if I test the bare bones script, I can see that the output is `0` and the matched branch is "Success".

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/bare-bones-test.png" height="300" />

## Bare Bones Outcomes

As you can see in this sample flow, the green line represents the name of the branch you created, and then there's two addition error handling outcomes:

- `onInvalidChoice` is for when there is no error in your code, but the output the script gave, did not match any of your branches.
- `onError` is for when your code threw an error and therefore failed to finish executing

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/bare-bones-outcomes.png" height="300" />

**TIP**: You cannot connect more than one successful outcome branches to the same node. See the below screenshot for how I handle a second successful outcome branch. The top route for "Success" goes to one node, while the second route for "Alternate" goes to another node; they both cannot go to the same node.

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/bare-bones-second-outcome-1.png" height="300" />

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/bare-bones-second-outcome-2.png" height="300" />
