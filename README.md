# Security Orchestration Automation and Response Lab

## Objective

The objective of this lab is to create a SOAR (Security Orchestration, Automation, and Response) playbook that automates the detection and response to a malicious event. In this case the playbook will use a LimaCharlie detection rule that triggers when the Lazagne credential harvester is executed on a client on the network. Once triggered, Tines will automatically send a message over Slack and email, including key identifiers of the attack as well as information about the compromised system. Additionally, a user prompt will provide the option to either isolate the infected machine from the network or keep it connected. If the machine is isolated, a confirmation will be sent to verify the successful isolation of the infected computer.

### Diagram

![Soar_Edr_project](https://github.com/user-attachments/assets/25305a3e-c0f3-4bba-9a8c-4d56d39830c1)

### Skills Learned

- Understanding of design and implementation of SOAR Playbooks.
- Enhanced knowledge in writing Detection rules for LimaCharlie.
- Intermediate Knowledge in Tines Automation.
- Enchanced skills in Workflow Automation.
- Gained Practical knowledge of Security Awareness and Endpoint Isolation.

### Tools Used

- LimaCharlie: For Endpoint detection and response (EDR) as well as creating and implementing  
               detection rules. Also used for Endpoint Isolation.
- Tines: For Orchestrating Automated Workflows
- Slack/Email: Recieve real time alerts

## Explanation

![Screenshot (579)](https://github.com/user-attachments/assets/0fa5a038-83df-4dd8-99c2-5341a96d148d)

To begin I installed a LimaCharlie Sensor on my computer, Just for clarification in the example I will be using my Domain Controller as the test computer. But during the actual Isolation I will be using a client computer on the domain because I didn't want to isolate my domain controller.

--------------------------------------
![Screenshot (580)](https://github.com/user-attachments/assets/4a8b86e1-4a0a-4fab-a2fb-65dea99d28ff)

The Domain controller that's part of the githubdomain has been connected to LimaCharlie as a sensor.

--------------------------------------

![Screenshot (584)](https://github.com/user-attachments/assets/2f3601c0-ad21-4491-853a-724911fbac1c)

This allows access to running processes, file systems, autorunning apps, and loads of other options. But most useful is the timeline allowing access to a second by second recording of what is happening on the system.

--------------------------------------
![Screenshot (594)](https://github.com/user-attachments/assets/298c3d1f-b1fe-4344-930e-e027c3c8f28c)

I'm now going to install our dangerous application LaZagne.exe (The link to the github will be provided at the bottom)

---------------------------------------

![Screenshot (600)](https://github.com/user-attachments/assets/a4f06256-ebb8-4da7-92cc-0f629465265c)

I open up a command prompt and run LaZagne.exe to generate an event so we have something to build our detection rule off of.

--------------------------------------
![Screenshot (603)](https://github.com/user-attachments/assets/b1b58cc3-46f4-4b7f-bda9-b09ba0560b09)

Heading to timeline and searching for LaZagne I can see a new process, expanding the event details

--------------------------------------
![Screenshot (604)](https://github.com/user-attachments/assets/9d587e28-c394-4a8c-accb-8e1daa0a8922)

We are given access to more verbos information, including the File Path the program is located, what was typed into command line and even what username the event happened on.

--------------------------------------
![Screenshot (606)](https://github.com/user-attachments/assets/019e3f77-7d23-4274-9ef3-ff3f1cfa1d7b)

Now that I have some information to work with I can begin building my detection rule by selecting create custom rule.

--------------------------------------
![Screenshot (631)](https://github.com/user-attachments/assets/815e6323-17c9-4f80-93f1-1c414fa6f3c3)

This is the [LINK](https://github.com/karamkamal1/SOAR_EDR_Lab/blob/5d0ef10d401d3ed197858aeff8ad22dad64baaaf/Detection_Rule.md) to the rule.

--------------------------------------
![Screenshot (638)](https://github.com/user-attachments/assets/51556df1-6557-43f8-8948-90384de0e9a1)

Now that I have my rule built I will create an event using LaZagne for our rule to detect.

--------------------------------------
![Screenshot (639)](https://github.com/user-attachments/assets/4a144b7e-62fa-400f-a8d2-03888b6b4722)

Heading back to LimaCharlie under detections I can see two events were triggered, both from running LaZagne on our machine.

--------------------------------------
![Screenshot (644)](https://github.com/user-attachments/assets/f95f2d63-8217-475c-9a7b-5f2c2e8aaa2d)

Now i'll head to slack to create a channel for us to recieve our detection alerts on.

-------------------------------------
![Screenshot (652)](https://github.com/user-attachments/assets/5fb5cab7-7a2d-4789-bd85-7e1b1bb1ed03)

I'll create a new channel called Alerts

--------------------------------------
![Screenshot (653)](https://github.com/user-attachments/assets/3239d14b-6109-4917-a2d1-f87108f7a899)

New channel created

---------------------------------------
![Screenshot (655)](https://github.com/user-attachments/assets/1e7b99cd-1eb7-4f42-9b82-055fac2244fe)

I'll now head to Tines to begin to create the automation workflow

---------------------------------------
![Screenshot (659)](https://github.com/user-attachments/assets/7e0ec828-a959-4a97-9ae0-e4180e24951c)

Our new empty playbook now's the fun part.

--------------------------------------
![Screenshot (661)](https://github.com/user-attachments/assets/ad51ba96-6466-4a9c-8682-5b01917021e3)

First i'll add a webhook to recieve our detection output from LimaCharlie. To do that i'll copy the webhook url and head to LimaCharlie.

------------------------------------
![Screenshot (663)](https://github.com/user-attachments/assets/16932b62-0e90-43f0-9214-cbd424555827)

In LimaCharlie I am going to add a new output.

------------------------------------

![Screenshot (666)](https://github.com/user-attachments/assets/4c7ef42b-3dd2-45ea-9c1c-8232fc72070c)

In Destination Host I'll add our Tines webhook URL linking our Tines webhook with our LimaCharlie Detections

-------------------------------------
![Screenshot (676)](https://github.com/user-attachments/assets/e38e74fd-28be-4eb8-9a4c-ba1d26471129)

Next we need to link Slack to Tines to be able to recieve alerts in our Alert Channel. To do this I'll install the Tines app on slack.

--------------------------------------
![Screenshot (680)](https://github.com/user-attachments/assets/95cbf60a-3760-4e55-b5fc-df3830362f60)

Now i'll head back to Tines and add a new Slack Credential to have authorization to send messages to slack. 


--------------------------------------
![Screenshot (682)](https://github.com/user-attachments/assets/d5b1461e-62a0-4bf9-98ca-278b7e36109c)


I'll select slack from our dropdown list and go through the prompts to connect.

--------------------------------------
![Screenshot (685)](https://github.com/user-attachments/assets/2f4364f5-8e1f-4834-aa99-0f9b95ae935d)

We now have our new Slack Credential.

--------------------------------------
![Screenshot (687)](https://github.com/user-attachments/assets/f9b9e8e8-2d81-4e20-87b5-d3d1a1250e0c)


I'll head back to the workbook and add a Send Message Slack Template, I'll copy the Slack Alert Channel ID and paste it into the Slack send message template.

--------------------------------------
![Screenshot (693)](https://github.com/user-attachments/assets/2465d7a1-6ba0-4603-985b-794135e4e8cf)

I'll now click test. If everything is working we should recieve the message Hello, World in our slack channel. You can see the message that's going to be sent in the message box.

--------------------------------------

![Screenshot (694)](https://github.com/user-attachments/assets/cef80800-9133-4321-8eda-5b098881ac36)

The message was recieved in the correct channel. Everything seems to be linked and I'm on the right track.

--------------------------------------

![Screenshot (698)](https://github.com/user-attachments/assets/d329f7d2-fc13-4411-9f6e-d9c63177c7d6)

I will now add a send email action to our workbook, and click test.

--------------------------------------

![Screenshot (699)](https://github.com/user-attachments/assets/bc230493-37d8-402f-932d-94dd2bf60978)

The email was successfully recieved.

---------------------------------------

![Screenshot (700)](https://github.com/user-attachments/assets/40ad31fe-a3a4-4891-a0e9-449d3d272265)

Now I will move on to creating the user prompt, giving a yes or no option to isolate the machine. To do this I add a pages that will be named User Prompt. Pages creates a webpage to add the Yes or No prompt on.

---------------------------------------

![Screenshot (704)](https://github.com/user-attachments/assets/6513f2d0-63c1-4521-a1c7-3fbc419ee2b6)

The User Prompt page has been added, and and has been connected to our detection webhook.

---------------------------------------

![Screenshot (709)](https://github.com/user-attachments/assets/b19bdff0-aa7e-4a76-bea1-f8e382c21c3d)

On the page I add a Submit Button, I will also add a Boolean allowing us to assign a true and false value to the yes and no buttons.

---------------------------------------

![Screenshot (722)](https://github.com/user-attachments/assets/c4726fc9-0c4b-417a-a664-4be32ec1f849)

I will now find and copy the paths I would like to copy from the event to display for the user.

---------------------------------------

![Screenshot (725)](https://github.com/user-attachments/assets/aacd627a-cd5b-4bed-88a2-6d6a8342fffd)

This is the list of Paths I will be using and their corresponding information. 

--------------------------------------
![Screenshot (735)](https://github.com/user-attachments/assets/dad48d97-1f56-4ad7-8d1a-12159d8d8d5f)

I will paste these paths to the Message portion of our Slack send message build. I'll Select test.

-------------------------------------

![Screenshot (739)](https://github.com/user-attachments/assets/88bf7a97-928d-4c76-b601-bbe284894844)

Awesome the Slack message was sent all of our selectged event information.

-------------------------------------

![Screenshot (740)](https://github.com/user-attachments/assets/d8e976f1-6c9e-41b2-a010-0b1f4384d773)

I will now add labels to each event path so it's a little more user friendly and easier to read. I will also add it to the Message section of our splunk message build.

-------------------------------------

![Screenshot (747)](https://github.com/user-attachments/assets/932441cd-82f8-4ced-a13b-4257d34e4fdd)

Now the Slack maessage is a lot easier to read.

-------------------------------------

![Screenshot (750)](https://github.com/user-attachments/assets/54718e7a-12d0-4a79-a060-9e66c3079672)

I will now add the paths to my send email action.

-------------------------------------

![Screenshot (754)](https://github.com/user-attachments/assets/d477c980-5a0b-43e2-aed7-3d7da9250b04)

The email message must be formatted in html.

-------------------------------------

![Screenshot (756)](https://github.com/user-attachments/assets/023fb204-3530-4416-831c-81ace1f2ea99)

Now when I recieve an email it includes all the required fields in a user friendly way.

--------------------------------------

![Screenshot (760)](https://github.com/user-attachments/assets/b831e7de-9be6-449c-abdd-f69dbbff10eb)

I will add the paths to the user prompt page as well.

-------------------------------------

![Screenshot (763)](https://github.com/user-attachments/assets/27e6b629-99ce-4eca-9547-26736d00460c)

I select visit webpage and I select a recent event. 

--------------------------------------

![Screenshot (764)](https://github.com/user-attachments/assets/99db5483-4270-40f1-b745-2d030d23dc97)

Now when I view the page we can see all our event information, alongside our Yes and No boolean and Submit Button. Pretty cool !

--------------------------------------

![Screenshot (765)](https://github.com/user-attachments/assets/2d8903c8-e67a-4760-8562-0fe662f08e10)

I will now add our triggers which will process our true and false boolean and perform an action.

-------------------------------------

![Screenshot (773)](https://github.com/user-attachments/assets/5ff67ace-6bfa-4a14-8924-099f72173d83)

The first trtigger will be named no. The Rules field will include a path to the yes or no button selection. In this case the user selects No so we can attribute that button press to false.


-----------------------------------

![Screenshot (780)](https://github.com/user-attachments/assets/94e67d88-0143-41cf-bda8-78eddcd89728)

I will now add a slack send message action to send a message notifying of the Computer name and that it was not isolated.


----------------------------------

![Screenshot (785)](https://github.com/user-attachments/assets/d3b50df7-209c-4843-82ba-76986334681d)

Now when the user selects No a message is sent to Slack.

---------------------------------

![Screenshot (786)](https://github.com/user-attachments/assets/7e7aeab3-eb9a-45b0-aaf6-fdd6ed1fb34e)

I am going to add another trigger for when Yes is pressed on the user prompt.

---------------------------------

![Screenshot (796)](https://github.com/user-attachments/assets/78167f8d-1e84-4c2b-8f44-c9dea8a6c906)

I will name it yes and give it the same rool as the no prompt equal to true.

---------------------------------

![Screenshot (799)](https://github.com/user-attachments/assets/8cefda03-7bf7-41a9-9d1b-e17cd981b2f3)

I will add a LimaCharlie Isolate Sensor Template. To isolate our infected computer.
The Sensor ID must also be added.

--------------------------------
![Screenshot (800)](https://github.com/user-attachments/assets/4f8a1e76-0798-4b7a-80dc-ab49a3ad059d)

I will copy the sensor ID path.

-------------------------------
![Screenshot (801)](https://github.com/user-attachments/assets/f2053c6a-2296-4380-8242-1ca269973077)

I'll paste the Sensor ID path into the URL. To recap when a user clicks the Yes button in the user prompt, it will trigger the yes trigger getting our LimaCharlie Isolate Sensor HTTP Request to isolate our infected computer from the network. 

-------------------------------
![Screenshot (805)](https://github.com/user-attachments/assets/649cac0c-0a77-41ca-bc97-9eb1c2249360)


To authenitcate the LimaCharlie Isolate sensor request a credential needs to be added. There is no preset credential so text credential at the top must be selected. 

-------------------------------

![Screenshot (813)](https://github.com/user-attachments/assets/418714b6-d08e-449a-8470-d9e0fcd6e32c)

I will name the credential LimaCharlie, and in the value line you will add the API for LimaCharlie which can be found under access managment on the LimaCharlie Dashboard.

-------------------------------

![Screenshot (815)](https://github.com/user-attachments/assets/9ac53bc4-ac6a-4488-a1b3-e4c23ce3bb34)


Click Connect on LimaCharlie under Credentials.

--------------------------------

![Screenshot (817)](https://github.com/user-attachments/assets/0178283d-44b9-4044-8f5c-7012b2fc0157)


I will also copy my slack send message template, change the message to "The Computer <Computer Name> Was Successfully Isolated, and connect it to the Isolate sensor Http Request.

---------------------------------

![Screenshot (819)](https://github.com/user-attachments/assets/aaf06a87-3cc1-4751-9f66-2ad46140e2f4)

You can choose to add another Lima Charlie HTTP request to get the isolation status. This is extra and I will not be including the isolation status in the confirmation message.

---------------------------------

![Screenshot (824)](https://github.com/user-attachments/assets/39a9cc2a-cda6-405e-b534-b34c29be373c)

I will also connect the Slack and Email Send Request to the User Prompt page so I can include the user prompt URL in the Slack Message and the email. I also added the user prompt URL path to the Slack and Email Message with the Label of Choose To Isolate.

--------------------------------
![Screenshot (826)](https://github.com/user-attachments/assets/0857dcee-bff2-4cef-8243-005033d8eb09)

Everything is now configured. I will show on the LimaCharlie dashboard that network access is allowed for our connected sensor/computer.

---------------------------------
![Screenshot (825)](https://github.com/user-attachments/assets/9c976160-eaea-4c2d-a749-ec51103ebfd2)


I will now execute LaZagne.exe on our computer.

----------------------------------
![Screenshot (827)](https://github.com/user-attachments/assets/e41c83a6-04d2-426d-b055-8ccc8b5b641f)

A message is sent to Slack In the Laert channel with all of our important event information and a link to our prompt allowing the choice to isolate or not. AWESOME !!

-----------------------------------
![Screenshot (828)](https://github.com/user-attachments/assets/de9349be-76cb-4d30-a6ea-f4f7ad4104f3)

An email is also sent with the same information.


--------------------------------------
![Screenshot (829)](https://github.com/user-attachments/assets/345636c0-475b-42df-afa0-9258de4d8bc0)


Clicking on the Choose To Isolate Link we are taken to our user prompt. I will select Yes to Isolate the computer.


---------------------------------------
![Screenshot (830)](https://github.com/user-attachments/assets/5b50b607-745d-48a4-9b58-a7016b225ac1)


The Computer is now Isolated. That's super cool !

---------------------------------------
![Screenshot (831)](https://github.com/user-attachments/assets/9d7a05f2-71d1-4d3e-bb8e-bf0b69ab566e)

A message is also sent to our slack channel letting us know our computer was successfully isolated. Everything is configured and everything works (:

----------------------------------------
