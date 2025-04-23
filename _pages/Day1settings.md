---
title: WxCC Day 1 Settings Tweaks
date: 2025-03-18
layout: post
---

# THIS PAGE IS CURRENTLY UNDER CONSTRUCTION

This page contains a list of recommended setup tweaks for Webex Contact Centre that the CCEP team use during our <a href="https://collabtoolbox.cisco.com/trials/managed-trials" target="_blank">managed customer trials.</a>

# Desktop Experience —> Idle/Wrap-up Codes:

<ul>
<li>Change default Idle code to “New Sign In” and remove the description</li>

<li>Add Idle Codes - On Phone Call, Lunch, Meeting, 15 Minute Break, Supervisor Escalation Path, Meeting</li>

<li>Change default Wrap Up Code to “No Wrap Up Selected” / remove description</li>
</ul>

# Tenant Settings —> Desktop

<img style="border: 1px solid grey;" src="/assets/images/Day1settings/Desktop.png" height="200" />

—Inactivity Timeout enabled, set duration to 480 Minutes

—Enable End Call - turn slider ON

—RONA Timeout for Telephony - 12 seconds

—Webex App - Turn State Synchronization ON

——Set On a Call to “On Phone Call” idle code

——Set all others to “Do Not Sync”

User Management —> Sites

—Change Site Name from Site-1 to customer name

User Management —> Teams

—Add new team, call it “IT Service Desk”, select Parent Site, select Agent Based

Customer Experience —> Queues

—Open the default Inbound Queue

—Rename it “IT Service Desk - New User”

—Remove Description

—Scroll Down to Contact Routing Settings and click on the pencil icon under the group, uncheck the default team and check “IT Service Desk” team, save

—Verify “Permit Monitoring” turned on

—Verify “Pause/Resume Enabled” turned on

—Set Maximum time in Queue to 86400

—Set Default Music in Queue to defaultmusic_on_hold_cisco_opus

—SAVE

—COPY the queue you just modified, rename it to “IT Service Desk - Password”, all other settings remain the same

User Management —> Teams

—Open the default team that the system created

—Slide the “active” slider to off (upper right)

—Click trash can to delete

Customer Experience —> Business Hours

—Create Working Hours, give it an appropriate name, example “M-F0800-1800_Eastern”

—Set schedule / define working hours

Tenant Settings —> Integrations

—Webex Contact Center -> Set Up

—Name Connector “API_RW”

—Read-Write Access

—I Authorize

Customer Experience—> Flows

—Import the following flows:

——Outdial

——Courtesy_Call_Back

——IT_Service_Desk

——CC_Status_Changer_GlobalVarialbe

—Open all flows that you imported, make necessary changes, publish flows

Customer Experience —> Channels

—Update Default Inbound Telephony Channel

——Rename to IT Service Desk

——Remove Description

——Set Routing Flow to IT_Service_Desk

——Set Version Label to Live

——Set Music on Hold to defaultmusic_on_hold_cisco_opus

——save

——Add Support number (if you have PSTN available)

—Update Outdial Entry Point-1 outbound Telephony Channel

——Remove Description

——Set routing flow to “Outdial”

——Set Version Label to Live

——Set Music on Hold to defaultmusic_on_hold_cisco_opus

——Set Outdial Queue to “Outdial Queue-1”

——save

Outdial Calling Config

Desktop Experience —> Outdial ANI

—Create Outdial ANI

—Name it “OutdialANI”

—Add phone number to list / name it

—Create

Desktop Experience —> Address Book

—Create Address Book

—Name it “AddressBook”

—Add entry such as Cisco TAC - 8005532447

Desktop Experience —> Desktop Profiles

—Open Agent-Profile & Agent-Profile(Auto WrapUp)

—Set Screen Popups to enabled

—Collaboration Tab

—Set State Synchronization to enabled

—Dial plans tab

—Outdial set to enabled

—Outdial Entry Point “Outdial Entry Point-1”

—Address Book “AddressBook”

—Outdial ANI “OutdialANI”

—Set Dial Plan to enabled

—Select Dial Plan “Any Format” and “US”

CJDS is an API-first service that enables organizations to:

- `Listen`: Integrate with any data source or third-party applications to listen to disparate data sources (_e.g. customer
  called Support_).
- `Identify`: Create a dynamic customer profile capturing propensity drivers, such as a customer's preferred mode of communication or preferred language (_e.g. how many times has the customer contacted us in the last week in each channel?_).
- `Analyze`: Apply different aggregation techniques to all customer data collected (_e.g. What is the CSAT score of the customer interaction? Is he using telephony,chat or other channel to contact?_).
- `Act`: Use the data and insights within CJDS to dynamically change the flow within Webex Contact Center Flow Control and personalize the customer experience at a granular level. These insights are visible to customer-facing teams in real time through Agent Desktop. (_e.g. bypass normal queue when customer calls for the third time in 24 hours and offer premium support_).

A comprehensive summary of the feature is available in the [Developer Portal](https://developer.webex-cx.com/documentation/guides/journey---getting-started), where you can find all the vital information & step-by-step guide to enable JDS for the first time in your own tenant.

## Provision JDS

1. `Fill out` this [form](https://app.smartsheet.com/b/form/7776df72239e47d0bbb73a392e32927f) to have CJDS provisioned for your tenant enabled, as it **not** enabled by default. If applicable, please work together with your Customer Success Manager (CSM) to ensure a smooth process and enablement. Post the initial request, the Cisco team will provision the CJDS instance within 72 hours.

2. When JDS is provisioned for the tenant, `Customer Journey Data` tab appears in the Control Hub.

3. You can set how long to retain data that's captured for CJDS. We recommend that you keep a minimum of 180 days to make sure that there are sufficient end-user journey data. By default, data is retained for 365 days.

   a. Sign in to Control Hub and go to `Customer Journey Data` > `Settings`.

   b. Enter the **number of days** that you want to retain data in CJDS.

4. Click `Save`.

![jdsprov](/assets/images/JDS/Provision_JDS.gif)

> `Note:` JDS is already provisioned in the provided lab tenant, so you do not need to perform them. You may follow the above steps when provisioning for your own tenant.

## Setup Desktop Customer Journey Widget

The customer Journey widget provides a single pane of glass view to the customer’s journey across all channels and applications, giving you the necessary contextual data for a more personalized customer experience and reducing average handling time.

### Create a journey project and Activate Webex Contact Center connector

Journey `projects` help organizations manage multiple data sources. Each journey project has a unique identifier which is required to leverage CJDS APIs payloads. Note that `project IDs` in Control Hub are referred to as `workspace IDs` in APIs.
Jouney project may be activated with the `Webex Contact Center connector`. This allows the journey project to capture all customer events and send it to CJDS from Contact Center. Once the connector is activated in one project, it cannot be activated in another. **At any point in time, it can be enabled for only one project.**

1. Sign in to **Control Hub** and go to `Customer Journey Data > Journey projects`.

2. You can use the default Sandbox Project or click `Create a Journey Project`.

3. Enter a **name** and a **description** for the journey project.

4. Select the journey `project` that you created in previous step.

5. Toggle the `Activate` connector in the Webex Contact Center section to ON.

![jdsactivateconnector](/assets/images/JDS/jds_activate_connector.gif)

### Add User Identities to a Journey Project

1. Select the journey `project` for which connector was activated.

2. Select `Identities`. Click on `Add identities`.

3. Download the sample **template**.

4. In the downloaded CSV file, add the Customer identities [First Name,Last Name,Email Addresses,Phone Numbers,Customers Ids].

   - Each customer identity must have **at least** an email address, phone number, or customer ID or else the CSV file will return an error.
   - If you want to add **multiple** email addresses, phone numbers or customer IDs, you need to **use the pipe “|” delimiter** between them. For example, try to add your phone number both with and without a plus sign.
   - For the **Id column**, make sure to leave each row `empty`. When you upload the CSV file, this field will auto-generate.

   ![jdscreatedcsv](/assets/images/JDS/jds_created_csv.png)

5. Upload the **CSV file** that you created for customer identities, and then click `Next`.

6. If the CSV file is valid, a window appears to show you if the import was successful. Once you're done, select `Close`. You should see a list of all the uploaded customer identities.

![jdsuploadidentities](/assets/images/JDS/jds_upload_ids.gif)

### Enable Customer Journey Widget on an Agent Desktop

1. We recommend adding JDS to your existing desktop layout using a code snippet. You can get the relevant code [here](https://github.com/CiscoDevNet/cjaas-widgets/blob/main/CustomerJourney/README_VERSION_10.0.0.md#how-to-add-the-cjds-widget-into-an-existing-desktop-layout).

Here is a screenshot of the block in place (notice it is after `IVR_TRASNCRIPT` and before `WXM_JOURNEY_TAB`).

![JDSWidgetCode](/assets/images/JDS/JDS_Widget_Code.png)

Alternatively, Download this [Desktop Layout JSON file](/assets/desktoplayouts/JDS10_AIAssistant.json) which includes the JDS widget and AI Assistant.

2. Sign in to Control Hub and go to `Contact Center > Desktop Layouts`.

3. Create a `New Layout`.

4. Assign an `Agent Team`.

5. Upload the Desktop Layout JSON file that you downloaded or created in **step 1**.

6. Click `Save`.

![jdsuploadwidget](/assets/images/JDS/jds_upload_widget.gif)

### View Customer Journey Widget on an Agent desktop

1. Login as an Agent into `Agent Desktop`. Ensure that the **desktop layout** of the Agent's Team has the JDS widget configured as per the previous steps.

2. On **Accepting** an incoming request, the `CJDS Widget` will appear in the desktop. If you are using AI Agent, it may load the IVR Transcript by default. Navigate to the 'Customer Journey' tab to see it.

The widget displays insights such as the number of times the customer has called or was contacted across all channels during a given duration. It also displays the journey history with default information such as `wrap-up code`, `queue name`, `agent ID` etc., and also allows to customize the event history with options such as third-party (non Webex CC) events and custom icons.

The `progressive profile` allows for alignment of different phone numbers and emails under one profile, ensuring accurate and comprehensive interaction data.

![JDSWidgetDesktop](/assets/images/JDS/jds_desktop_widget.gif)

Once JDS is set up and configured, we recommend using the <a href="https://github.com/TeamCCEP/JDSContactResolver" target="_blank">contact resolver subflow</a> to retrieve customer details into variables in existing flows. This allows you to do things like greet callers by name, channel switch to Email, SMS etc, and a variety of other activities based around knowing your customer.

There is a great <a href="https://github.com/WebexSamples/webex-contact-center-api-samples/tree/main/customer-journey-samples/cjds-postman-example" target="_blank">Postman Collection</a> available that gives many API's that you can use to show examples of overdue payment notifications in WxCC Agent desktop. You will need to set up postman with the relevant OAuth token using <a href="https://app.vidcast.io/share/6b54f08d-0cd2-481f-979b-c8643c1d6a13" target="_blank">this guide</a>

![Overdue Payment Notification](/assets/images/JDS/JDSPayments.png)
