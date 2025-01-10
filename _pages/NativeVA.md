

# Exercise 2.4: Cisco Native Virtual Agent for voice channel (NEW!!)

**Webex Connect Bot Builder** is a Cloud AI platform that offers native conversational omni-channel virtual agent service to customers via a Cisco Contact Center AI (CCAI) solution. The CCAI solution orchestrates and automates voice-based and digital interactions with the end users. To use the Webex, Connect Bot Builder, you need to provision the Webex Connect digital services for your organization. 

**In this lab** you will configure Virtual Agent Voice for Webex Contact Center using Cisco's native Conversation AI solution powered by Webex Connect Bot Builder. 

## Task 1. Dashboard overview.


1. From the Control Hub, navigate to **Contact Center > Overview**
2. On the **Quick Links** section click on **Webex Connect Bot Builder.** </li>
 
![4.1](/assets/images/NativeVA/4.1.png)
<br> 
  <li>On the top of the Dashboard, you will see two type of bots available: <b>Q&A bots and Task bots.</b> 
  <br> 
<img src="../assets/4.2.png"> <br>
<br> 
<ul>
  <li><b>Q&A Bots</b> are knowledge-driven bots whose knowledge base consists of a series of possible questions (with their alternative syntax) and related answers. Q&A bot is available for Digital Channel.</li>
  <li><b>Task Bots</b> enable multi-turn conversations where a bot can obtain relevant data from users to perform the task at hand. Task Bot  is available for Voice and Digital Channel.</li>
</ul></li>
  <li>On the left side there also modules for <b> Knowledge , Analytics</b>  and <b> Help</b> . Under <b>Knowledge</b>  you can add Knowledge bases and configure them with your bots. 
<br> 
<img src="../assets/4.3.png"> <br>
<br> 
<ul>
  <li>In the Analytics module you can monitor the bot activity by selecting the bot from the list, specify Data range and other options. </li>
<br> 
<img src="../assets/4.4.png"> <br>
<br> 
  <li>The Help module directs you to the Webex Bot Builder documentation page.</li>
<br> 
<img src="../assets/4.5.png"> <br>
<br> 
</ul></li>
</ol> 

## <span style="color: #049fd9;">Task 2. Create Task Bot.</span>

Task bots augment the no-code bot-building capabilities of Webex Bot Builder. Task bots enable multi-turn conversations where a bot can obtain relevant data from users to perform the task at hand. In this lab we would see how to build these Bot to deliver the customer experiences. 

<ol>
  <li>Select <b>Task</b> bots and click on create <b>New Task Bot.</b> </li>
<br> 
<img src="../assets/4.6.png"> <br>
<br> 
  <li>On the following page you can see that you can utilize some of the prebuild Virtual Agents.
  <ul>
  <li>To see that <b>Intents</b> and <b>Utterances</b> that are prebuild, click on the <b>Details</b> button or the <b>Appointment Booking</b> Bot.  </li>
  <li>After the review, select the <b>Appointment Booking</b> prebuild agent for this lab. Then click on <b>Next.</b> </li>
</ul></li>
<br> 
<img src="../assets/4.7.png"> <br>
<br> 
  <li>Add your attendee ID (CL_IDxxx) to the name, <b>Allow feedback</b> and click on <b>Import.</b> </li>
<br> 
<img src="../assets/4.8.png"> <br>
<br> 
  <li>Now make your bot live by clicking <b>“Make Live”</b> option
  <br>
  Enter text “Test”</li>
<br> 
<img src="../assets/4.9.png"> <br>
<br> 
  <li>Now open your Webex Contact Center flow CL_{YourID}_WxCC_DialogflowCX
  <ul>
  <li>Enable Edit</li>
  <li>Select <b>Virtual Agent V2</b> activity and select the Task Bot that you just created. </li>
  <li>Go to the settings, in the <b>“Contact Center AI config”</b> switch from currently selected <b>Google Dialogflow CX</b> connector to <b>Cisco native Virtual Agent</b> connector by selecting <b>Webex CCAI Config.</b> </li>
  <li>Once selected, you will notice all the Native Task Bots under Virtual Agent.</li>
  <li>Select your BOT created in previous step named with your ID. </li>
  <li><b>Validate</b> and <b>Publish</b> the flow. </li>
</ul></li>
<br> 
<img src="../assets/4.10.png"> <br>
<be>
<li>Call the inbound dial number that is configured with your Entry Point / Channel to book an appointment. 
<ul>
  <li>You should see that bot is well configured to answer to your question and collect the information from you. </li>
  <li>At the end ask to <b>speak with an agent</b> and the call will be moved to the Sales queue as this is <b>default</b> routing configured in the <b>Case activity</b> in the WxCC flow.</li>
</ul></li>
<br> 
<img src="../assets/4.11.png"> <br>
<be>
</ol>


## <span style="color: #049fd9;">Task 3. Understand the bot configuration modules. </span>

<ol>
  <li>By clicking on <b>Preview</b>, you can interact with the bot on the chat window and test if this is working as suspect or some configurations need to be corrected. </li>
<br> 
<img src="../assets/4.12.png"> <br>
<br> 
  <li>The bot supports <b>multiple languages</b>. While on Settings module click on <b>Language</b> and add <b>English</b> language from the drop-down, <b>if the language is not there</b>. 
  <ul>
  <li>Click on <b>Update bot.</b> </li>
</ul></li>
<br> 
<img src="../assets/1Picture2.gif"> <br>
<br> 
  <li>On the <b>Training module</b> you can see the <b>Intents</b> and their configurations : <b>Intent Name</b>, <b>count of Utterances</b>, and <b>Response name</b> etc. </li>
<br> 
<img src="../assets/1Picture3.png"> <br>
<br> 
  <li>Open the <b>“Talk to an agent”</b> intent you can see the option to add more <b>utterances</b> and configure the <b>response.</b> </li>
<br> 
<img src="../assets/1Picture4.png"> <br>
<br> 
  <li>Generate more utterances using AI.
  <be>
  <b>Click</b> on <b>Generate</b> options. This allows us to cover possible options a customer can use to reach this option in a conversation.  
  <ul>
  <li>Provide the description for the utterances. Like <b>“Reach an agent”</b></li>
  <li>Select the number of variants enter <b>8</b> </li>
  <li>Click on <b>Generate.</b> </li>
  <li>Save the <b>Intent</b></li>
  <li>Go Back by clicking the arrow next to the intent <b><-Talk to an agent.</b> </li>
</ul></li>
<br> 
<img src="../assets/1Picture5.gif"> <br>
<br>    
  <li>Now we need to train the BOT to start using modified Intent. 
  <ul>
  <li>Click on <b>NLU Engine</b> </li>
  <li>Select the <b>Engine</b> option: Mindmeld (Other options: RASA -BETA, Swiftmatch)</li>
  <li>Click <b>Update</b></li>
  <li>Click on <b>Train BOT</b> on the right top corner and provide a comment like "test".</li>
  <li>Status next to <b>Training data</b> would show <b>Training</b> and then switch to <b>Trained</b>  </li>
  <li>Click <b>Make Live</b></li>
</ul></li>
<br> 
<img src="../assets/1Picture6.png"> <br>
<br> 
  <li><b>Entities</b> are the variables that bot uses store the collected information form the users. For example:  you can see the Entities with name <b>preferred appointment data</b> with Entity type as <b>Day.</b></li>
<br> 
<img src="../assets/1Picture7.png"> <br>
<br> 
  <li>To add the <b>Entities</b> to the <b>training phrases,</b> go back to <b>Intents</b> and select <b>Book appointment</b> intent. </li>
<br> 
<img src="../assets/1Picture8.png"> <br>
<br> 
  <li>Add utterance with text “I want to see the doctor on the weekend”.</li>
<br> 
<img src="../assets/1Picture9.png"> <br>
<br> 
  <li>Scroll down on utterances and Looking at your just added utterance you can see that <b>weekend</b> is marked with different color. </li>
  <li>System automatically detect it as the <b>time</b> and configure as the <b>Entity.</b> </li>
<br> 
<img src="../assets/1Picture10.png"> <br>
<br> 
  <li>If you want manually to specify any part of the <b>utterance</b> as the <b>parameter</b>, you can highlight it and option will <b>popup</b> to select the entity from the available list. 
  <ul>
  <li>Review the video below, no need to update. </li>
</ul></li>
<br> 
<img src="../assets/1Picture11.gif"> <br>
<br>
  <li>The <b>Response modules</b> has the template configures. 
  <ul>
  <li>There are some Default templates that you can customize but cannot delete or rename.</li>
  <li>There are also custom templates that you can add to the list. </li>
  <li>The response can be delivered over multiple channels and on this module you can configure if this should be for Voice or/and any available Digital Channel. </li>
  <li>On the right side you can see the response types. It could be text, code, audio file, etc.</li>
<br> 
<img src="../assets/1Picture12.png"> <br>
<br>
</ul></li>
  <li>Click on <b>Welcome message</b> default response template. 
  <ul>
  <li>Select Voice Channel.</li>
  <li>Modify the Text Variant, for example type “Welcome to Cisco Live! How can I assist you?"</li>
  <li>Update and Make it Live. </li>
  <li>Place the test call to your Channel to test that change was applied. </li>
</ul></li>
<br> 
<img src="../assets/New15.gif"> <br>
<br>
  <li>On the <b>Testing</b> module you can test if the phrases will be trigger the <b>Response Templates</b> or you need to modify your Intents. 
  <ul>
  <li>For example if you want to test message “Agent” against Response template <b>Agent handover,</b> the test will be successful as we have the <b>Talk to an agent</b> intent configured properly. </li>
</ul></li>
<br> 
<img src="../assets/1Picture14.gif"> <br>
<br>
  <li>If the <b>BOT encounter an error</b>, fallback intent, bad feedback or poor intent configuration you can see the details in the <b>Curation</b> module. 
  <ul>
  <li>Make a note of count under <b>Fallback</b></li>
</ul></li>
  <li>Click on <b>Preview</b> and enter <b>“Test”</b>. 
  <ul>
  <li>It will trigger response related to the <b>Fallback Intent</b> as “test” phrase is not specified in any intent. </li>
  <li>You can also <b>downvote</b> this response and add <b>comment.</b> </li>
</ul></li>
<br> 
<img src="../assets/1Picture15.png"> <br>
<br>
  <li>Go back to <b>Curation module or Refresh</b>. You should see that <b>Fallback intent</b> was detected with count went up by 1, as well as <b>Downvoted</b> count incremented. 
    <ul>
  <li>Click on <b>Fallback</b> block </li>
  <li>Click <b>Decrypt</b> </li>
</ul>
</li>
<br> 
<img src="../assets/1Picture16.png"> <br>
<br>
  <li>You should see options to add <b>“test”</b> phrase to an <b>existing Intent, create new intent</b> for it or just <b>ignore</b> this message.
<br> 
<img src="../assets/1Picture21.png"> <br>
<br>
  <ul>
  <li>For now just ignore it. </li>
  <li>But for the production environment this is the place where you can improve your agent response by adding or modifying the intents. </li>
</ul></li>
<br> 
<img src="../assets/1Picture17.png"> <br>
<br>
  <li>Under the <b>Session module</b> you can find all the <b>transcript</b> related to the bot interactions. </li>
<br> 
<img src="../assets/1Picture18.png"> <br>
<br>
  <li>The History <b>Module</b> contains information about your: 
  <ul>
  <li>Bot trainings with Intent updates as well as the Audit Logs.</li>
</ul>
</li>
<br> 
<img src="../assets/1Picture19.png"> <br>
<br>
<img src="../assets/1Picture20.png"> <br>
<br>
<img src="../assets/2024-05-20_12h11_44.png"> <br>
<br>
</ol>
