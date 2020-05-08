# Lab 200: Create a Sales Order in Oracle Cloud ERP using Oracle Integration Cloud (INTERNAL ONLY)

<!-- Comment out table of contents
## Table of Contents
[Introduction](#introduction)
-->

## Introduction

This lab walks you through how to create an Integration in OIC to create a Sales Order in Oracle Cloud ERP and push data in an Oracle Autonomous Data Warehouse.  
*In addition to the workshop*, feel free to watch the walk-through companion video by clicking on the following link:
[Lab 200 Walkthrough Video](<INSERT LINK HERE>)



### Objectives
-   Understand the capabilities of Oracle Integration cloud and how to integration with Applications
### Required Artifacts
-   ERP Cloud Instance from 
-   Oracle Autonomous Data Warehouse instance with preconfigured Table and access to Wallet file with connection details.

### Extra Resources
-   To learn more about Oracle Integration Cloud (OIC), feel free to explore the capabilities by clicking on this link: [OIC Documentation](https://docs.oracle.com/en/cloud/paas/integration-cloud/)
-   To learn more about , Oracle ERP Cloud feel free to explore the capabilities by clicking on this link: [ERP Cloud](https://go.oracle.com/LP=85331?elqCampaignId=48423&src1=ad:pas:go:dg:erp&src2=wwmk160606p00030c0001&SC=sckw=WWMK160606P00030C0001&mkwid=%7cpmt%7ce%7cpdv%7cc%7c&GOOGLE&oracle+erp+cloud&Cj0KCQjw7qn1BRDqARIsAKMbHDaSJX4r2woRQrLHIFTCk3imWrf6ORbhp3f1czxUvvxVTsz8Votd7TQaAhggEALw_wcB&gclid=Cj0KCQjw7qn1BRDqARIsAKMbHDaSJX4r2woRQrLHIFTCk3imWrf6ORbhp3f1czxUvvxVTsz8Votd7TQaAhggEALw_wcB&gclsrc=aw.ds)


## Part 1. Gather Pre-requisite Information

### **STEP 1**: Obtain Oracle cloud ERP Information

-   Obtain Oracle cloud ERP connection URL. 

![](./images/ERP.png " ")

-   Usernames to Oracle cloud ERP environments are **bala.gupta** and **ava.clark**.

-   Obtain Password information used to log into your cloud environment.


### **STEP 2**: Obtain Oracle Autonomous Data Warehouse Information

You will need the following to be able to connect to the Oracle Autonomous Data Warehouse : 

-    Wallet file

-    Wallet password

-    Database user and password

-    Database service name

-    Create **table**

## Part 2. Create Connections

### **STEP 1**: Create Connection to Oracle Cloud ERP 

-   Log into Oracle Integration cloud and click on **Integrations** from the menu on the left hand side. 
![](./images/OIChome.png " ")

-   This will take you to the Integrations portion of Oracle Integration from where we can build integrations between Applications. Now select **Connections** from the menu on the left to take you to the connections page. 

![](./images/'Connections Page.png' " ")

-   In the chat window of the Digital Assistant type in **food expenses $15.46**. You will notice that the Digital Assistant recognizes that he wants to create a new expense and will prompt him to enter a few more details.

![](./images/da2.jpg " ")

-   The Digital Assistant will prompt you to enter:
    - The merchant's name: **Enter your favorite place to eat**
    - The date of the expense: **Enter a date of your choice** (example 3/23/20) 
    - The category of the expense: **Select Breakfast**

![](./images/da3.jpg " ")

![](./images/da4.jpg " ")

-   Once all the details have been filled in. The Digital Assistant confirms the expense line creation, but we would like to update the description. 

-   To update the description type in **Description is Lunch**

![](./images/da5.jpg " ")

-   Confirm your expense by entering the number given in the Digital Assistant's response. 

![](./images/da6.jpg " ")

### **STEP 2**: Create an Expense report using a receipt
-   One other way to create an expense report in a Digital Assistant is to upload an image of a receipt. The Digital Assistant uses key words scanned from the image to fill in the expense fields.

-   Download [sample receipt](./files/receipt.jpg)

-   **Upload** the image by selecting the icon to the left of the chat box and navigate to where you downloaded the sample receipt and **upload**. 

![](./images/da7.jpg" ")

-   The Digital Assistant will ask you to enter **the expense type** and select **lunch**

![](./images/da8.jpg " ")

-   The Digital Assistant will give you a summary of the expense and ask you to confirm by entering the **Confirmation Code** in the last message sent by the digital assistant. 

![](./images/da9.jpg " ")

-   To change the date of the last expense submitted, type in **modify the last expense**

-   Type in **Change date to last tuesday**. The Digital Assistant recognizes the correct date through natural language processing, then saves the change, and automatically submits the new expense.  

![](./images/da10.jpg " ")

-   Confirm by entering the **confirmation code** in the last message sent from the Digital Assistant. 

-   The Digital Assistant was able to retrieve data from ERP's Finance Module to create, retrieve, and update an expense report.  

## Part 3. Change persona

### **STEP 1**: Sign out kerry.lane

-   Click the top right icon and then click on **Sign Out**

![](./images/signout.jpg " ")

### **STEP 2**: Sign in using brian.joseph

-   Enter the username **brian.joseph** and the **password** you copied earlier in the workshop.

![](./images/signin-brian.jpg " ")

### **STEP 3**: Interact with the Digital Assistant 

-   We are going to switch to the perspective of a new hire. This new hire was told to procure a laptop and business cards through his employer's pre-built Digital Assistant that has been integrated with ERP Cloud Procurement module. **Click** on the **Digital Assistant** icon in the bottom right hand corner and type in **I need a new laptop**

![](./images/laptop.jpg " ")

-   The Digital Assistant will prompt you if you would like it to recommend a laptop based on your job role. Type in **Yes**.

-   Browse what is available by clicking on the **Yellow side arrow** and select **more details** on your favorite option.

![](./images/browse.jpg " ")

-   The Digital Assistant will provide you with more details and ask if you would like more details on any other laptops.

-   Type in **No**

![](./images/no.jpg " ")

-   The Digital Assistant will ask if you have made a choice. Type in **Yes** and select the **Laptop** you would like to procure.

![](./images/select.jpg " ")

-   The Digital Assistant will create the purchase requisition and route the req. to your manager for approval. 

![](./images/purchase.jpg " ")

-   The next thing we need to do is procure business cards. To do this type in **Order business cards**

-   The Digital Assistant will respond and give you a preview. Select **Tap here**.

-   Select **Tap here**

![](./images/bc.jpg " ")

-   This will open up a new tab where you can preview your business cards, select the quantity, and submit the order.

![](./images/wb-1.jpg " ")

-   Select the quantity you want to order and select submit. **Close** the tab and open up the tab where you are logged into *ERP Cloud**.

![](./images/wb-2.jpg " ")

-   The Digital Assistant will create the requisition, display the status of the order, and give you the requisition number.

![](./images/fin.jpg " ")

-   When a new tab opened up, the application you were viewing is what's called a **WebView**. A WebView is an application that enables structured data entry through UI element and is able to integrate with the Digital Assistant. The WebView can validate user input and can be built using Oracle Visual Builder Cloud Service, like the one seen earlier, Oracle JET, or React. 


## Part 3. Mobile Application and Oracle's AI Voice

### **STEP 1**: Initial Setup

-   Follow the steps [here](https://demo.oracle.com/apex/f?p=GO:PAGE:0:DSD:NO:1:ID:53992) to install on iOS or Andriod mobile device. 

### **STEP 2**: Interact with ODA

-   In this portion of the workshop we are going to get a few updates on the Finance Manager's account.

-   You can interact with the ODA by typing in the chat box or by clicking the microphone icon in the bottom right.

-   Press the microphone button and say **What is the account balance for cleaning?**

![](./images/mobile-1.jpg " ")

-   Press the microphone button and say **How much do we owe our suppliers office depot?**

![](./images/mobile-2.jpg " ")

-   Press the microphone button and say **Which account has the largest budget surplus?**

![](./images/mobile-3.jpg " ")

-   Press the microphone button and say **Which project has the highest margins?**

![](./images/mobile-4.jpg " ")

-   Oracle’s Digital assistant provides broad channel support like slack, teams, sms, mobile apps, text-to-speech, and speech to text capabilities. In this portion of the workshop Oracle's AI Voice is being used with no risky exposure to 3rd party api's.

## BONUS: Create a twilio, slack, and/or Facebook channel route to Demo Services ODA

-   [Click here](https://demo.oracle.com/apex/f?p=GO:PAGE:0:DSD:NO:1:ID:76473) to do so.


## Summary

-   In this lab, you requested a demo ERP Cloud instance and interacted with the pre-built Digital Assistant skill for ERP. Oracle Digital Assistant pre-built skills showcase easy, interactive, intuitive and meaningful information without the need to login and open ERP applications.


-   **You are ready to move on to the next lab!**

[Back to top](#introduction)

