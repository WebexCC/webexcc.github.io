---
title: Enable Virtual Agent
date: 2024-01-13
layout: post
---

## Cisco Native Virtual Agent for voice channel (NEW!!)

**Webex Connect Bot Builder** is a Cloud AI platform that offers native conversational omni-channel virtual agent service to customers via a Cisco Contact Center AI (CCAI) solution. The CCAI solution orchestrates and automates voice-based and digital interactions with the end users. To use the Webex, Connect Bot Builder, you need to provision the Webex Connect digital services for your organization.

# Task 1. Dashboard overview

1. From the Control Hub, navigate to **Contact Center > Overview**
2. On the **Quick Links** section click on **Webex Connect Bot Builder.**
![4.1](/assets/images/NativeVA/4.1.png)

3. On the top of the Dashboard, you will see two type of bots available: **Q&A bots and Task bots.**
![4.2](/assets/images/NativeVA/4.2.png)

4. **Q&A Bots** are knowledge-driven bots whose knowledge base consists of a series of possible questions (with their alternative syntax) and related answers. Q&A bot is available for Digital Channel.
5. **Task Bots** enable multi-turn conversations where a bot can obtain relevant data from users to perform the task at hand. Task Bot  is available for Voice and Digital Channel.

6. On the left side there also modules for **Knowledge , Analytics** and **Help**. Under **Knowledge** you can add Knowledge bases and configure them with your bots.
![4.3](/assets/images/NativeVA/4.3.png)

7. In the Analytics module you can monitor the bot activity by selecting the bot from the list, specify Data range and other options.
![4.4](/assets/images/NativeVA/4.4.png)

8. The Help module directs you to the Webex Bot Builder documentation page.
![4.5](/assets/images/NativeVA/4.5.png)

# Task 2. Create Task Bot

Task bots augment the no-code bot-building capabilities of Webex Bot Builder. Task bots enable multi-turn conversations where a bot can obtain relevant data from users to perform the task at hand. In this lab we would see how to build these Bot to deliver the customer experiences.

1. Select **Task** bots and click on create **New Task Bot**.
![4.6](/assets/images/NativeVA/4.6.png)

2. On the following page you can see that you can utilize some of the prebuild Virtual Agents.

3. To see that **Intents** and **Utterances** that are prebuild, click on the **Details** button or the **Appointment Booking** Bot.

4. After the review, select the **Appointment Booking** prebuild agent for this lab. Then click on **Next**.
![4.7](/assets/images/NativeVA/4.7.png)

5. Add your attendee ID (CL_IDxxx) to the name, **Allow feedback** and click on **Import**.
![4.8](/assets/images/NativeVA/4.8.png)

6. Now make your bot live by clicking **Make Live** option

7. Enter text “Test”
![4.9](/assets/images/NativeVA/4.9.png)

8. Now open your Webex Contact Center flow CL_{YourID}_WxCC_DialogflowCX

9. Enable Edit

10. Select **Virtual Agent V2** activity and select the Task Bot that you just created.

11. Go to the settings, in the **Contact Center AI config** switch from currently selected **Google Dialogflow CX** connector to **Cisco native Virtual Agent** connector by selecting **Webex CCAI Config**.

12. Once selected, you will notice all the Native Task Bots under Virtual Agent.

13. Select your BOT created in previous step named with your ID.

14. **Validate** and **Publish** the flow.
![4.10](/assets/images/NativeVA/4.10.png)

15. Call the inbound dial number that is configured with your Entry Point / Channel to book an appointment.

16. You should see that bot is well configured to answer to your question and collect the information from you.

17. At the end ask to **speak with an agent** and the call will be moved to the Sales queue as this is **default** routing configured in the **Case activity** in the WxCC flow.
![4.11](/assets/images/NativeVA/4.11.png)
