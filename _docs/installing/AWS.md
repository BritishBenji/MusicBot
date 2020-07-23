---
Title: Amazon Web Service
category: Installing the bot
order:9
---

<img class="doc-img" src="{{ site.baseurl }}/images/AWS/AWS.PNG" alt="Amazon Web Service" style="width:75px;
float: right;"/>

This walkthrough will take you through the steps required to host the bot externally using a VPS. 
For this, we recommend the use of [Amazon Web Service](aws.amazon.com)
You must first have a Personal Account with them before continuing with this walkthrough.


### Creating a New Instance
Before you can run a program through AWS, you must first create an EC2 Instance. To do this, Navigate to the "Services" tab in the top left
and select EC2.

<img src="{{ site.baseurl }}/images/AWS/Select_EC2.PNG" alt="Select the EC2 option"/>

From here, you can click the Orange "Launch Instance" button, to start setting up your instance.

<img src="{{ site.baseurl }}/images/AWS/Launch_Instance.PNG" alt="Launch Instance"/>

You will be given many different options for which option to run, our suggestion is that you choose the "Ubuntu Server 18.04 LTS (HMV) service 
and this walkthrough will be catered to that option.

<img src="{{ site.baseurl }}/images/AWS/Free_Tier_Ubuntu.PNG" alt="Ubuntu 18.04 EC2"/>

From here, click "Review and Launch", then "Launch" your instance. You will recieve a pop-up, asking you to "Select an existing key pair or create a new key pair."
Here, you will need to select "Create a new key pair" from the drop-down box, and give it a name. Then download your key, and click "Launch Instances."
Note: It is suggested that you save this key in multiple places to prevent it being lost, as once you Launch your instance, there is no way to get a new key without creating a new Instance.

<img src="{{ site.baseurl }}/images/AWS/Create_New_Key_Pair.PNG" alt="Create A Key Pair" />

### Interacting with the Ubuntu Instance
Now that You have set up your Instance with AWS, we need to find a way to interact with it. This can be done with any form of SSH client, however, for this example, we'll be using PuTTY (which can be downloaded and installed from [here](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html))

With PuTTY installed, we first need to open PuTTYgen, this will allow use to change the public key Amazon provided us with into something PuTTY can interact with and use.
With the PuTTYgen program open, load an existing private key file using the "Load" button, and save it as a Public Key. To keep things simple, save this with the same filename as your original key, with the .ppk file extension.

<img src="{{ site.baseurl }}/images/AWS/PuTTYgen_UI.PNG" alt="PuTTYgen UI"/>

Once you have saved this, open PuTTY and AWS side by side. On your AWS window, find and copy your "Public DNS (IPv4)", and paste this into the "Host Name (or IP address)" text box with the prefix "ubuntu@" (example below)

<img src="{{ site.baseurl }}/images/AWS/Connect_IP.PNG" alt="PuTTY example"/>

Following on from this page, expand the "SSH" tab on the right hand side of the screen and click "Auth" 
Select your .ppk file using the "Browse..." option, then go back to the "Session" tab and click open. 
You will be brought to a black screen with text on it, you are now in your Ubuntu Workspace on your EC2 Instance.
Use the code below to install the bot to this Instance:

~~~ bash
# Install build tools
sudo apt-get install build-essential unzip -y
sudo apt-get install software-properties-common -y

# Install system dependencies
sudo apt-get update -y
sudo apt-get install git ffmpeg libopus-dev libffi-dev libsodium-dev python3-pip 
sudo apt-get upgrade -y

# Clone the MusicBot to your home directory
git clone https://github.com/Just-Some-Bots/MusicBot.git ~/MusicBot -b master
cd ~/MusicBot

# Install Python dependencies
sudo python3 -m pip install -U pip
sudo python3 -m pip install -U -r requirements.txt
~~~

### Configure the bot
From here, you are free to configure the bot, for those who aren't familiar with Ubuntu Terminal Syntax, the table below should give you a place to start alonside the [configuration](https://just-some-bots.github.io/MusicBot/using/configuration) page

|      Command     |                           Function                           |
|:----------------:|:------------------------------------------------------------:|
|        ls        | Shows you the files and directories in the current directory |
|  cd \<directory>  |             Takes you to the specified directory             |
| nano \<file_name> |                     Opens Ubuntu's editor                    |

### Running the bot
Once you have configured the bot, navigate to the main "MusicBot" directory, and run the command 
~~~ bash
screen -S <Any name you choose>
~~~
From here, you should run the command:
~~~ bash
python3 run.py
~~~
After a few seconds the bot will begin to run, press Ctrl + A to interact with screen, and then Ctrl + D to detach the screen and begin working on your main Ubuntu window again, then you're free to close the PuTTY client, your bot is now being run via Amazon Web Services.

