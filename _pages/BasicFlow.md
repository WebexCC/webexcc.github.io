---
title: Configure Basic Call Flow
date: 2024-01-27
layout: post
---

## Webex Contact Center Initial Setup & Basic Flow Build

## Important Links:  
  
Webex Control Hub: <https://admin.webex.com>

WxCC Agent/Supervisor Desktop:

<https://desktop.wxcc-us1.cisco.com/>

<https://desktop.wxcc-eu1.cisco.com/>

<https://desktop.wxcc-eu2.cisco.com/>

WxCC User Guides :
<https://www.cisco.com/c/en/us/support/customer-collaboration/webex-contact-center/series.html>

# Set up users & add Webex Calling licenses

Log into Webex Control Hub: <https://admin.webex.com>

### Create New User:

Under Management on the left, click users, then in the upper right click
Manage Users, then click on Manually Add or Modify Users. Follow through
the prompts as you would normally to add a Wx/WxC user.

![newuser](/assets/images/BasicFlow/newuser.png)

When you get to the license/service selection screen for the user, make
sure they are set with the correct licenses. For WxCC Users, make sure
they are Webex Calling Professional and select the agent type (Standard,
Premium, Premium with Supervisor).

![addlicense](/assets/images/BasicFlow/licensecalling.png)
![addlicense2](/assets/images/BasicFlow/licensecc.png)

On the next screen, make sure the agent has an extension, or a phone number, or both and Calling Plan is selected.

![usercalling](/assets/images/BasicFlow/assignnumber.png)

### Existing Users: Edit Licenses to add WxCC

If a user whom WxCC services are to be added already exists in the org,
simply edit their license to add the features. Click on the user under
the user list, when the user details load, click “Edit Licenses”. Follow
the same steps as above to make sure the user has WxC Professional and
WxCC Premium Agent, with either agent or supervisor and then click save.
You may have to assign an extension/phone number to the agent if they
didn’t have one already.

### Activate Users

Users who are added in Control Hub will not show up in WxCC until they
are activated, even if you hit the Synchronize Users button.

To activate, the user must click on the email they received and create a
password if not on SSO. This is only applicable to new users in Control
Hub.


### Access Contact Center Configuration

Webex Contact Center configuration is accessed from Control hub. Once
you log into Control hub at <https://admin.webex.com> simply navigate to
Contact Center under the left hand menu under Services. This will bring
you to the Contact Center Overview landing page.

![contactcenter](/assets/images/BasicFlow/CCconfig.png)

Note about Multimedia Profile
> 
> The default profiles that exist in this section will be sufficient for
> getting started. Additional profiles can be created, or the existing
> profiles can be modified to fit the needs of your environment.

Note about Sites
> 
> In WxCC, you can optionally create a new site to section off users
> (generally for different physical locations). For the purposes of this
> documentation, **we recommend keeping all of your users located in one
> site**. There are certain features and functions that do not cross
> site boundaries. For example, a user must be tied to ONE site and a team
> must be tied to ONE site. If user Amy is tied to site Chicago, and the
> team Helpdesk is tied to site Denver, Amy can NOT be associated with the
> team Helpdesk.

# Create Skill Definitions & Skill Profiles

Skills will be integrated into a skill profile, and these can be used to
define who gets a call initially, when/if the call is relaxed, etc.

### Skill Definitions

1. Under “User Management” click Skill Definitions
2. Click on Create Skill Definition
3. Name the skill something meaningful
4. Add a more detailed description
5. Set the type – For the example, we will use Proficiency
6. Service Level Threshold is not necessary, but feel free to set it to any value for reporting
7. Click Create
8. Repeat as needed
![skilldefinition](/assets/images/BasicFlow/skilldefinition.gif)

### Skill Profile

1. Under “User Management” click Skill Profile
2. Click on Create Skill Profile
3. Name the skill profile something meaningful such as Agent-A-Skills
4. Describe the skill profile
5. Select the skills & the values for each skill. For Proficiency, 0 is
  low skilled, 10 is Expert
6. Click Create
7. Repeat as needed
![skillprofile](/assets/images/BasicFlow/skillprofile.gif)

### Create Idle/Wrap Up Codes

Codes are used for reporting purposes. Create as many as needed. Idle
codes are for when an agent is not available, and wrap up codes are tied
to interactions once they are complete.

1. Under **Desktop Experience** click **Idle/Wrap-up Codes**
2. Click **Create Idle/Wrap-up Code**
3. Name the code (i.e. Lunch Break)
4. Describe the code
5. If this is your default code, select the button for Make it **Default**
6. Select **Code type** from the drop down box
7. Click **Create**
8. Repeat as needed
![wrapupcode](/assets/images/BasicFlow/wrapupcode.gif)

### Modify existing Desktop Profile

Desktop profiles are assigned to agents so that they can have the
correct Aux Codes, DN Validation, Outdial, etc. The existing profiles
are sufficient to begin with. If you wish to make changes to one of the
existing profiles, follow these steps:

1. Under **Desktop Experience** click **Desktop Profiles**
2. Click on the profile you wish to modify
3. Go thru the various tabs and make the changes you wish to adjust
![desktopprofile](/assets/images/BasicFlow/desktopprofile.gif)


### Create Teams

Teams are groups of agents that can be assigned to a call queue. The
more complex of an environment may mean more teams.

1. Under **User Management** click **Teams**
2. Click **Create Team**
3. Name your team (i.e. ACME-Anvil-Experts)
4. Describe your team
5. Select Parent Site
6. Make sure to select **Agent Based** radio button – Capacity Based Teams
  are legacy
7. Select the appropriate **skill profile**, **Multimedia profile**, and the
  agents who are part of this team (Skill & Multimedia profiles are
  optional and can be assigned directly to agent)
8. Click **Create**
9. Repeat as needed
![createteam](/assets/images/BasicFlow/createteam.gif)

### Enable Users for WxCC

> NOTE User Intervention Required 
> This step cannot be completed until the users have activated their Webex accounts. You may need to wait until the user has performed this step.

Log into Control hub, go to Contact Center, click on **Contact Center
Users** under **User Management**. From here, you can see the status and
contact center status of the user. To use WxCC, the user will need to
have WxCC enabled. Click on a user - this will bring you into the user
settings.

Edit each user and change the following settings:

1. Verify Contact Center is set to **ON**
2. **Site** should be **Site-1** or appropriate site
3. Verify the correct **Desktop Profile**
4. Verify the correct **Multimedia Profile**
5. If using skills, select the appropriate **Skill Profile**
6. Select the appropriate team(s) they will be a part of
7. Click **Save**
8. Repeat for all users as needed
![enablewxccusers](/assets/images/BasicFlow/enablewxccusers.gif)


# Create a Queue

Queues are virtual containers for contacts to be held until they can be
answered by an available agent. Calls can be routed either by Longest
Available Agent, or Skills Based. 
> Queue Routing Type cannot be changed once a queue is created. If you need to adjust the type later, you will need to create a new queue.

1. Under **Customer Experience** click **Queues**
2. Click **Create Queue**
3. Name your queue
4. Describe your queue
5. Select Queue Type **Inbound Queue**
6. Select the channel type **Telephony**
7. For Queue Routing Type select Skills Based or Longest Available Agent
> If SBR, for Agent Selection select Best Available Agent or Agent available longest
8. Add groups of agents by clicking **Create Group**
9. Select Team(s) to participate in then press save
10. Select options from advanced settings.
11. Permit **Service monitoring** for supervisor monitoring
12. Service Level Threshold can be set to `120`
13. Max Time in Queue can be set to `86400`
14. Default Music on Hold set to `defaultmusic_on_hold.wav`
15. Click Create
16. Repeat as needed
![createqueue](/assets/images/BasicFlow/createqueue.gif)


# Create a Flow

A flow is essentially a call script and will dictate where the call goes
once it enters the system. This work will be done from the flow
designer.

1. Under “Customer Experience” click Flows
2. Click “Manage Flows” drop down and **“Create Flow”**
3. Click **"Flow Template"**, select **"Simple Inbound Call to Queue"** and click Next
3. Name your flow to start building it (ex. CCEPInboundFlow) and click **Create Flow**.
4. Flow Builder will be opened and you will see new flow. This Flow will be using TTS (Text to Speach) technology to announce messages.
5. Select your Incoming Queue in the **Queue** node
6. **Validate** and **Publish** your flow
![createflow](/assets/images/BasicFlow/createflow1.gif) 

# Localization change of Text-to-Speach (TTS) service

To Localize TTS to your county specific language, you will need to check supported languages [here](https://help.webex.com/en-us/article/ntkjqhw/Text-to-Speech-(TTS)-in-Webex-Contact-Center)

1. Add following Global Variables into the flow: `Global_VoiceName` and `Global_Language` into the flow
2. Drag Set Variable Node to the flow and assign variables `Global_VoiceName` and `Global_Language` according to your requirement (in example: `Global_VoiceName = en-GB-Colton` and `Global_Language = en-GB`
3. Select your Incoming Queue in the **Queue** node
4. **Validate** and **Publish** your flow
![globalTTSvariable](/assets/images/BasicFlow/globalTTSvariable1.gif) 

>Note
>
> 1. During CCEP Trials, a TTS Connector will be provided for the trial
> 
> 2. Feel free to experiment with various flow objects

One of Flow examples that you might get:
![flow](/assets/images/BasicFlow/flow.png)

# Create Channels (Entry Point with phone number mapping)

Channels (Entry Points) are points where calls enter the CC. A support
number will point a phone number/DID to the Entry Point

1. Under **Customer Experience** click Channels
2. Click **Create Channel**
3. Name your entry point (ex. CCEP)
4. Describe your entry point
5. Select **Channel Type** as **Inbound Telephony**
6. Set **Service Level Threshold** to `120`
7. Select the **Routing Flow** you had created earlier in the drop down (ex. CCEPInboundFlow)
8. Select **Version label** as **Latest**
8. Select **Music on Hold** as `defaultmusic_on_hold.wav`
9. Under **Support number**, press **Add**
10. Select **Webex Calling Location** and Select **Support Number**. Click check mark
11. Click Create
![createchannel](/assets/images/BasicFlow/createchannel.gif)

# Testing your configuration

1. Log your agent into the WxCC Agent Desktop according to the location of your tennant:
  US based tennant: <https://desktop.wxcc-us1.cisco.com/>
  EU based tennant: <https://desktop.wxcc-eu1.cisco.com/>
2. Select the correct extension/phone number and team from Station
  Credentials
3. Once logged in, change status to “Available” (Green)
4. Call the phone number of your entry point mapping that you configured earlier. This should deliver the call to the agent if all is configured correctly.

Additional Notes

> For time-of-day routing, please use the business hours object. This is configured in Control Hub, under Contact Center - Business Hours

> Once you have a Business Hours list created, you can utilize a “Business Hours” object in the flow designer. It is located at the bottom of the Flow Control Objects menu

> Routing strategies should no longer be used for Time of Day routing.
