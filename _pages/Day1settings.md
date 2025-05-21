---
title: WxCC Day 1 Settings Tweaks
date: 2025-03-18
layout: post
---

This page contains a list of recommended setup tweaks for Webex Contact Centre that the CCEP team use during our <a href="https://collabtoolbox.cisco.com/trials/managed-trials" target="_blank">managed customer trials.</a>
<BR><BR>
Unless stated otherwise, all settings should be carried out from Control Hub, under the Contact Center Menu.

![Control Hub Menu Area](/assets/images/Day1settings/CH_WxCCPage.png)

# Desktop Experience —> Idle/Wrap-up Codes:

<ul>
<li>Change default Idle code to “New Sign In” and remove the description</li>

<li>Add Idle Codes - On Phone Call, Lunch, Meeting, 15 Minute Break, Supervisor Escalation Path, Meeting</li>

<li>Change default Wrap Up Code to “No Wrap Up Selected” / remove description</li>
</ul>

# Tenant Settings —> Desktop

<ul>
<li>Inactivity Timeout enabled, set duration to 480 Minutes</li>
<li>Enable End Call - turn slider ON</li>
<li>RONA Timeout for Telephony - 12 seconds</li>
<li>Webex App - Turn State Synchronization ON</li>
<li>Set On a Call to “On Phone Call” idle code</li>
<li>Set all others to “Do Not Sync”</li>
</ul>

# User Management —> Sites

<ul>
<li>Change Site Name from Site-1 to customer name</li>
</ul>
# User Management —> Teams
<ul>
<li>Add new team, call it “IT Service Desk” or similar, select Parent Site, select Agent Based</li>
</ul>

# Customer Experience —> Queues

<ul>
<li>Open the default Inbound Queue</li>

<li>Rename it to something appropriate to your use case</li>

<li>Remove Description</li>

<li>Scroll Down to Contact Routing Settings and click on the pencil icon under the group, uncheck the default team and check “IT Service Desk” team you created earlier, save</li>

<li>Verify “Permit Monitoring” turned on</li>

<li>Verify “Pause/Resume Enabled” turned on</li>

<li>Set Maximum time in Queue to 86400</li>

<li>Set Default Music in Queue to <a href="https://www.youtube.com/watch?v=KC_NwHDpbFo" target="_blank">defaultmusic_on_hold_cisco_opus</a></li>
</ul>

# User Management -> Teams

<ul>
<li>Open the default team that the system created </li>

<li>Slide the “active” slider to off (upper right)</li>

<li>Click trash can to delete</li>
</ul>

# Customer Experience —> Business Hours

<ul>
<li>Create Working Hours, give it an appropriate name, example “M-F0800-1800_Eastern” </li>

<li>Set schedule / define working hours </li>
</ul>

# Tenant Settings —> Integrations

<ul>
<li>In the Webex Contact Center panel, choose "Set Up"</li>

<li>Name Connector “API_RW”</li>

<li>Read-Write Access</li>

<li>Authorize and finish</li>
</ul>
