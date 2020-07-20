---
Title: Amazon Web Service
category: Installing the bot
order:1
---

<img class="doc-img" src="{{ site.baseurl }}/images/AWS/AWS.PNG" alt="Amazon Web Service" style="width:75px;
float: right;"/>

This wlakthrough will take you through the steps required to host the bot externally using a VPS. 
For this, we recommend the use of [Amazon Web Service](aws.amazon.com)
You must first have a Personal Account with them before continuing with this walkthrough.


### Creating a New Instance
Before you can run a program through AWS, you must first create an EC2 Instance. To do this, Navigate to the "Services" tab in the top left
and select EC2.
<img src="{{ site.baseurl }}/images/AWS/Select_EC2.PNG" alt="Select the EC2 option" style="float:right;"/>

From here, you can click the Orange "Launch Instance" button, to start setting up your instance.
<img src="{{ site.baseurl }}/images/AWS/Launch_Instance.PNG" alt="Launch Instance" style="float:right;"/>

You will be given many different options for which option to run, our suggestion is that you choose the "Ubuntu Server 18.04 LTS (HMV) service 
and this walkthrough will be catered to that option.
<img src="{{ site.baseurl }}/images/AWS/Free_Tier_Ubuntu.PNG" alt="Ubuntu 18.04 EC2" style="float:right;"/>

From here, click "Review and Launch", then "Launch" your instance. You will recieve a pop-up, asking you to "Select an existing key pair or create a new key pair."
Here, you will need to select "Create a new key pair" from the drop-down box, and give it a name. THen download your key, and click "Launch Instances."
Note: It is suggested that you save this key in multiple places to prevent it being lost, as once you Launch your instance, there is no way to get a new key without creating a new Instance.
<img src="{{ site.baseurl }}/images/AWS/Create_New_Key_Pair".PNG" alt="Create A Key Pair" style="float:right;"/>

