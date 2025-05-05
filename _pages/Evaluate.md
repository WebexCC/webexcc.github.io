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

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/bare-bones.png" height="200" />

As you can see in the above example:

- I am typing `0;` as the script itself, which, is how you return output. You do not need the keyword `return` as you might be used to in vanilla JS.
- I have one branch created called "Success" (the name is up to you)
- I set the output value for that branch to match what the script is outputing

# Bare Bones Testing

There is a code testing function within the node, and if you click test, then click test again, it will either show you some output, or an error.

In my case, if I test the bare bones script, I can see that the output is `0` and the matched branch is "Success".

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/bare-bones-test.png" height="200" />
