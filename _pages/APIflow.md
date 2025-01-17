---
title: API request in the call flow
date: 2024-01-15
layout: post
---

# Task 1. Create Data to query via API

> Note. This step has to be done in order to create dummy data.

1. Open portal [mockapi.io](mockapi.io)
2. Get authenticated
3. Create new project  
![mockapicreateproject](/assets/images/APIflow/mockapicreateproject.png)
4. Specify name and clice **Create**.  
![mockapicreateprojectname](/assets/images/APIflow/mockapicreateprojectname.png)
5. Click **New resource** to create new data and provide name of resource and data you would like to have. In our case we will have the following data:
	* id
	* title -> random.words
	* pin -> finance.pin  
![mockapispecifydata](/assets/images/APIflow/mockapispecifydata.png)
6. Click **Create**
7. Generate 30 random cases as on the screenshot and edit them.  
![mockapigeneratedata](/assets/images/APIflow/mockapigeneratedata.png)
8. Click **Data** and edit it.
	* edit **id** to be with 5 digit 
	* specify **pin** easily to remember, as it is for the demo
	* Click **Update**  
![mockapieditdata](/assets/images/APIflow/mockapieditdata.png) 
9. Test it with Postman.  
	![postmanget](/assets/images/APIflow/postmanget.png) 

# Task 2. Add to Flow pin check and your case title

Add the following algorithm to the flow to check details of your case.
![wxccflow](/assets/images/APIflow/wxccflow.png) 

1. Menu. 
2. CED **Collect caseid**. 
3. Set Global Variable **caseid** (for Reporting)
4. Send "HTTP Request".  
![apirequest](/assets/images/APIflow/apirequest.png)
5. Specify path to variables. Path can be checked with [https://jsonpath.com/](https://jsonpath.com/)
![variablepath](/assets/images/APIflow/variablepath.png)
6. CED **Collect PIN** with TTS "If you are calling for the case {{title}}, please enter PIN"
7. Check Condition **Check PIN** with experssion like on the screenshot ` {{CollectDigits_pincheck.DigitsEntered == pin}} `.  
![pincondition](/assets/images/APIflow/pincondition.png). 
8. Play message with good or bad authentication.
