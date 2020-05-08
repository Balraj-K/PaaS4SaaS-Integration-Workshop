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

-   This will take you to the Integrations portion of Oracle Integration from where we can build integrations between Applications. 

-   We will first create connections to all the application we plan on connecting to in our integration. In our case a connection to Oracle Cloud ERP and Oracle Autonomous Data Warehouse. 

-   Now select **Connections** from the menu on the left to take you to the connections page. Once on the **Connections** page click on the **Create button** on the top right corner. 

![](./images/ConnectionsPage.png " ")

-   In the search bar type in **ERP** and select **Oracle ERP Cloud**

![](./images/SearchForERPConnector.png " ")

- Click on the select button. 

![](./images/SelectERPConnector.png " ")

-   You will be prompted to enter a name for the connection you are trying to make. Enter **ERP Cloud** in the name section and the Identifier will autogenerate. Leave the role as **Trigger and Invoke**. Click the **Create Button**.

![](./images/ERPDetails.png " ")

-   We now have to input the credentials for our Oracle ERP Cloud connection. This consists of a connection URL and a security credential. Here the Security credentials are for the user you use to log into ERP Cloud. Please note that the capabilities of the adapter will change according to what roles and responsibility the user has been assigned. For example : If your user doesn't have privileges within the ERP system to view Order Information, you will not be able to use the corresponding APIs with the adapter. 

-   First click on the **Configure Connectivity Button** to enter connection URL. 

![](./images/ERPConnectandSecure.png " ")

![](./images/ERPConnection1.png " ")

-  Enter connection URL for ERP and click the **OK Button** at the bottom. 

![](./images/ERPConnection2.png " ")

-   Click on the **Configure Security Button** to enter security credentials

![](./images/ERPConnectandSecure.png " ")

-   Enter security credentials and click the **OK Button** at the bottom. 

![](./images/ERPSecurity.png " ")

-   Scroll to the top and click on the **Test Button** and then the **Save Button**. 

![](./images/SaveERPAdapter.png " ")

### **STEP 2**: Create a Connection to Oracle Autonomous Data Warehouse
-   Click on the **Create button** on the top right corner. 

![](./images/ConnectionsPage.png " ")

-   Enter **ADW** in the Search bar and select **Oracle ADW**.

![](./images/SearchforADW.png " ")

-   Select the ADW Option

![](./images/SelectADW.png " ")

-   You will be prompted to enter a name for the connection you are trying to make. Enter **ADW ERP** in the name section and the Identifier will autogenerate. Leave the role as **Trigger and Invoke**. Click the **Create Button**.

![](./images/ADWDetails.png " ")

-   Click on the **Configure Connectivity Button** to enter connection properties.

![](./images/ADWSelectConnectivity.png " ")

-   Enter value for the **Service name** field. You can get this from the Wallet in the **tnsnames.ora** file. Then click on the **OK Button**.

![](./images/ADWInputConnection.png " ")

-   Click on the **Configure Security Button** to enter security credentials. 

![](./images/ADWSelectSecurity.png " ")

-   Upload your wallet file and enter all the security details. Then click on the **OK Button**.

![](./images/ADWInputSecurity.png " ")

-   Scroll to the top and click on the **Test Button** and then the **Save Button** 


## Part 3. Create Integration

-   Click on **Integrations** from the menu on the left hand side. Click on the  **Create Button** on the top right corner to create a new Integration. 

![](./images/CreateIntegration.png " ")

-   Select App driven Orchestration. 

![](./images/SelectAppDriven.png " ")

-   An Integration Details page will pop up. Enter a **Name** for your Integration. The identifier will auto-generate. The other fields can be left as is. Click the **Create Button** in the bottom.

![](./images/IntegrationDetails.png " ")


### **STEP 1**: Add and Configure Rest Adapter

-   You will be taken to a canvas where you can drag and drop the connections that you have configured and map data between applications. It is also possible to create complex logic using the action icons such as for-loops, switch statements, error handling etc. 

-  Click on the **'+' Icon** to add your first adapter. In the search bar type in 'sample' to bring up the **Sample Rest Endpoint** connection. This is a rest adapter configured to be a trigger. Using a Rest trigger will expose the integration that we build as a Rest API. 

![](./images/SelectSameRest.png " ")

-   You will be taken to the page to configure Rest the Rest Endpoint. Enter **Request** for a name and click the **Next Button**

![](./images/Rest1.png " ")

-   Enter **/order** in the relative URI column. Select **POST** from the dropdown as the action you want to perform on the endpoint. Check boxes to **configure a request payload** and **configure to receive response**. Then click the **Next Button**.

![](./images/Rest2.png " ")

-   Select **JSON Sample** from the dropdown in the request payload format.

![](./images/Rest3.png " ")

-   Click on **enter sample JSON inline**.

![](./images/Rest4.png " ")

-   Enter the following Payload in the textbox and click the **OK Button**. This is the structure of the request payload format you want your API to have. 

```JSON
{
  "TransactionIdentifier" : "Creekside Warehouse-14073",
  "BuyingPartyName" : "Pinnacle Technologies",
  "BuyingPartyContactName" : "Isaac Nelson",
  "BusinessUnitName" : "US1 Business Unit",
  "ShipToPartyIdentifier" : "A100000000409220",
  "ShipToPartyName" : "Pinnacle Technologies",
  "BillToCustomerName" : "Pinnacle Technologies",
  "ShipToPartySiteIdentifier" : "A300000048361113",
  "BillToAccountSiteUseIdentifier" : "A300000048361115",
  "OrderItems" : [ {
    "ProductId" : "AS46336",
    "Quantity" : 3
  }, {
    "ProductId" : "AS46336",
    "Quantity" : 3
  } ]
}

```

![](./images/Rest5.png " ")

-   Click the **Next Button**.

![](./images/Rest4.png " ")

-   Select **JSON Sample** from the dropdown in the response payload format.

![](./images/Rest6.png " ")

-   Click on **enter sample JSON inline**.

![](./images/Rest7.png " ")

-   Enter the following Payload in the textbox and click the **OK Button**. This is the structure of the response payload format you want your API to have. 

```JSON
{
  "orderNumber" : "A11231",
  "orderStatus" : "Success"
}
```

![](./images/Rest8.png " ")

-   Click the **Next Button**.

![](./images/Rest6.png " ")

-   Review the Summary and click **Done**.

![](./images/Rest9.png " ")

### **STEP 2**: Add and Configure Cloud ERP Adapter

-   Hover over the grey line  below the Rest Adapter. A **+ Icon** will pop up and then you can click on it.

![](./images/SelectERPAdapter.png " ")

-   Type in **ERP Cloud** or whatever name you gave your ERP connection and select it.

![](./images/TypeERPCloud.png " ")

-   Input a name for the connection, **CreateERPOrder** and click the **Next Button**.

![](./images/ERPBasicInfo.png " ")

-   Select the first action and click the next button. 

![](./images/ERPAction.png " ")

-   Select **Services** from the **Browse By** dropdown.

![](./images/ERPOperation.png " ")

-   Type in **Order** in the search bar, select **OrderImportService** from the list and then select **createOrders** from the drop down menu. Then click **Next**. 

![](./images/ERPCreateOrder.png " ")

-   Review the summary and click **Done**.

![](./images/ERPSummary.png " ")


### **STEP 3**: Add and Configure ADW Adapter

-   Hover over the grey arrow underneath the ERP cloud adapter. Click on the **+ Icon** and enter the ADW connection name. Select the ADW connection. 

![](./images/ADW1.png " ")

-   In the configuration wizard input the name as **DataWarehouse**. From the operations drop down select **Perform an Operation on Table**. 

![](./images/ADW2.png " ")

-   Select **Insert** as the operation and click **Next**.

![](./images/ADW3.png " ")

-   Select **ADMIN** from the schema drop down. Table type can be left as **Table**. From the table list search for the table you want to input data into. In our case it is the **Orders** table. Select **Orders** and click the **single arrow pointing to the left**.

![](./images/ADW4.png " ")

-   Click **Import Tables Button**.

![](./images/ADW5.png " ")

-   Select **TransactionIdentifier** as the primary key. Then click **OK**. This will take you to the previous screen where you can click the **Next Button**.

![](./images/ADW6.png " ")

-   Review Summary and click **Done**.

![](./images/ADW7.png " ")

## Part 3. Map Data

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

