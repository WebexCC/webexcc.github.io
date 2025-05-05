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

As you can see in this sample flow, the green line represents the name of the branch you created, and then there's two addition error handling outcomes (what they connect to, is not important right now; we'll get to that later):

- `onInvalidChoice` is for when there is no error in your code, but the output the script gave, did not match any of your branches.
- `onError` is for when your code threw an error and therefore failed to finish executing

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/bare-bones-outcomes.png" height="300" />

### Branching

The Evaluate node has a built in branching mechanism, such that you do not need to connect the success outputs of the Evaluate node to the input of a Branch node.

In the following screenshot, I have created an additional branch called "Alternate," and I am connecting each success branch to its own path for further processing.

**Note**: You cannot connect two success branches to the same next node, they must connect to unique nodes.

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/bare-bones-second-outcome-1.png" height="300" />

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/bare-bones-second-outcome-2.png" height="300" />

# Handling Input and Output

Moving beyond a bare bones script, you might want to work with input data, and output data. Below we will cover the basics of input and output.

## Input Data

By default, you can use other node's variables, just like you do in most other nodes. In this example, my inbound webhook is looking for a JSON payload with a key named "input" in it, and my Evaluate node can reference it as follows:

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/input-node-variable.png" height="300" />

If I want to test my code, and provide a sample input data, I can do that like this, and notice how my `person` variable now contains the input value:

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/input-node-variable-test.png" height="300" />

I can also reference Custom Variable in the usual way as well:

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/custom-variable.png" height="300" />

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/custom-variable-as-input.png" height="300" />

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/custom-variable-as-input-test.png" height="300" />

## Output Data

While the result of the outcome from the Evaluate step (e.g., 0 = Success), is natively available by way of the Node's Output Variables:

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/node-outcome-variable.png" height="300" />

It's not an easy place to pass anything meaningful, or more than a simple piece of data; therefore, the use of Custom Variabes (for those of you coming from WxCC Flow Designer, these are like Flow Variables), is a great place to store just about anything you want, regardless of the overall outcome of the script (e.g., 0 = Success).

For example, the custom variable I show just above, I can use it in the script, as follows:

**Note**: I do not use the `$(variable)` syntax here, as I am not trying to convert the variable to its value, rather, I am storing new data inside of it.

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/custom-variable-as-output.png" height="300" />

I felt the best way to show you that the custom variable was actually modified, I would show you the node execution in the debugger.

<img style="border: 1px solid grey;" src="/assets/images/Evaluate/custom-variable-as-output-debug.png" height="300" />
