# Lab 300: Integrating Cloud ERP with OIC (INTERNAL ONLY)

<!-- Comment out table of contents
## Table of Contents
[Introduction](#introduction)
-->

## Introduction

*In addition to the workshop*, feel free to watch the walk-through companion video by clicking on the following link:
[Lab 400 Walkthrough Video](<INSERT LINK HERE>)

### Objectives

### Required Artifacts

### Extra Resources
-   To learn more about Oracle Integration, feel free to explore the capabilities by clicking on this link: [OIC Documentation](https://docs.oracle.com/en/cloud/paas/integration-cloud/index.html)
-   To learn more about , Oracle ERP Cloud feel free to explore the capabilities by clicking on this link: [ERP Cloud](https://go.oracle.com/LP=85331?elqCampaignId=48423&src1=ad:pas:go:dg:erp&src2=wwmk160606p00030c0001&SC=sckw=WWMK160606P00030C0001&mkwid=%7cpmt%7ce%7cpdv%7cc%7c&GOOGLE&oracle+erp+cloud&Cj0KCQjw7qn1BRDqARIsAKMbHDaSJX4r2woRQrLHIFTCk3imWrf6ORbhp3f1czxUvvxVTsz8Votd7TQaAhggEALw_wcB&gclid=Cj0KCQjw7qn1BRDqARIsAKMbHDaSJX4r2woRQrLHIFTCk3imWrf6ORbhp3f1czxUvvxVTsz8Votd7TQaAhggEALw_wcB&gclsrc=aw.ds)


## Part 1. Create a process application

### **STEP 1**: Get started making your process


![](./images/1.png " ")

-   Navigate to the **OIC console** sign-in page provided by your lab facilitator. Enter the provided username & password. **If you do not have the URL or the credentials, please contact your lab facilitator.**

- Click 'Processes' on the left menu

![](./images/2.png " ")

- Now click on 'Process Applications'.

![](./images/3.png " ")

- Click the create button on the top right.

![](./images/4.png " ")

- Click create on the 'Create an Application' box

![](./images/5.png " ")

- Give your process a name and then hit create on the left

![](./images/6.png " ")

- Click the 'create a structured process' on the left, and then start with a form.

![](./images/7.png " ")

- Click form on the right, and enter 'OrderApproval' in the name box. 

![](./images/8.png " ")

- Your prcoess looks like this, click start. 

![](./images/9.png " ")

- Click open properties. 


![](./images/11.png " ")

- This window will appear below.

![](./images/10.png " ")

- Click the plus sign to create a new form.

![](./images/12.png " ")

- Give your form the name 'OrderEntryForm.'


### **STEP 2**: Create your process form


![](./images/form1.png " ")

- This is the screen you'll be greet with to create your form, you can see it opened a new tab on the screen. 

![](./images/form2.png " ")

- Drag the select from the right to the screen.

![](./images/form3.png " ")

- For the properties, scroll down to the options source section, and input these static options.

![](./images/60.png " ")

- Drag another and place it to its right. 

![](./images/form4.png " ")

- For payment terms, do the same and input these values.

![](./images/61.png " ")

- Click your select box and give it the following Name & Label. 

![](./images/form5.png " ")

- Drag a date action from the right and place it to the right of your Payment select box. 

![](./images/form6.png " ")

- Now drag a tab le from the right and place that below your select boxes.

![](./images/form7.png " ")

- Click on your table, on the left side of the screen you can see its properties. 

![](./images/form10.png " ")

- Enter Name, Quantity, Unit Price for the columns. 

![](./images/form11.png " ")

- Drag a select field from the right. 

![](./images/form12.png " ")

- Now place it under the Name column.

![](./images/form13.png " ")

- Give the select box the following Name, Label, and Binding.

![](./images/form14.png " ")

- Scroll down on the properties box and enter these options Names and Options Values.

![](./images/form15.png " ")

- Now drag an 'Input Text' action to be underneath the Quantity field. 

![](./images/form16.png " ")

- Click the input text box and give it the same Name, Label, and Binding. 

![](./images/form19.png " ")
- Now drag a Mondy action from the right and place it under the Unit Price column. 

![](./images/form20.png " ")

- Configure the Name, Label, and Binding for the Money box. 

![](./images/form21.png " ")

- Mark the unit price 'Read Only' check box.


![](./images/form25.png " ")

- Drag another Money field from the right to below your table.

![](./images/form26.png " ")

- Configure the same Name, Label, and Binding. 

![](./images/form22.png " ")


- Now you can press save, and close the 'OrderEntryForm' tab to return to the process designer.


### **STEP 3**: Finish creating your process

![](./images/13.png " ")

- From the right, click the drop down next to gateways, and drag & drop an Exclusive gateway to the right of the start action. 

![](./images/14.png " ")

- Now click the blue box to the left of start, then the pencil icon. 

![](./images/15.png " ")

- Type in customer. 

![](./images/16.png " ")

- Now we have the personnas configured for our process, a customer submitting the order, and a process owner to review relevant orders. Now, drag and drop an 'Approve' action from the right, under Human, and place it in the Process Owner section of the screen.

![](./images/17.png " ")

Click the user task and open the properties. 

![](./images/18.png " ")

Click the magnify glass to the right of form. 

![](./images/19.png " ")

Select the OrderEntryForm you previously created. 

![](./images/20.png " ")

Now click the exclusive gateway, and then click the cursor. 

![](./images/21.png " ")

Drag and drop the line from the gateway to the user task. 

![](./images/22.png " ")

Place another eclusive gateway to the right of the user task. 

![](./images/23.png " ")

Drag and drop a cursor from the user task to the new exclusive gateway. 

![](./images/24.png " ")

Under the system action on the right, drag and drop a Nofity task to the right of exclusive gateway. 

![](./images/25.png " ")

Open its properties. 

![](./images/26.png " ")

- INSERT 

![](./images/28.png " ")

- Now click the line between Exclusive gateway & User task.

![](./images/29.png " ")

Click the pencil. Then click the pencil to the right of the condtion box. 

![](./images/30.png " ")

Enter this logic, you can highlight the totalPrice field, press 'Insert Into Expression' and then add ' > 12000. This will route the integration to need human approval if the total price is over $12,000. We hardcoded a value of $15,000 previously in order to ensure you will need the human approval.

- Your process is coming along well, in the next steps we will add the itnegration to your process and complete its devleopment.  

### **STEP 4**: Add the integration to the process, Test the Process Application

![](./images/31.png " ")

- Drag and Drop the Integration action to the right of Exclusive Gateway. 

![](./images/32.png " ")

- Click on it and open the properties.

![](./images/33.png " ")

- Click the plus sign and select the integration you previously developed, our's is named 'CreateSalesOrderERP'.

![](./images/34.png " ")

- Your integration should look like this.

![](./images/35.png " ")

- Your screen might be getting crowded, you can drag and drop the 'End' action to the right to have more room.

![](./images/36.png " ")

- Now, drag and drop another Notify action to the right of your integration.

![](./images/37.png " ")

- Configure its properties to have your email in the 'To' box and the same subject & body. 

![](./images/38.png " ")

- Drag and drop a cursor from the new notification task to the End box. 

![](./images/39.png " ")

- Drag and drop the cursor from 'Exclusive gateway 1' to the integration.

![](./images/41.png " ")

- Click the line and then the pencil. Then click the checkbox next to 'Conditional Flow'.

![](./images/42.png " ")

- Click the pencil to the right of the condition box. 

![](./images/43.png " ")

Click 'TaskOutcomeDataObject' then Insert Into Express. Complete the expression by adding '== "REJECT"'.

![](./images/44.png " ")

- Now to clean up our labels, click the exclusive gateway and rename it to 'Price Routing' or the label of your choice.

![](./images/45.png " ")

- Do the same to the second gateway. 

![](./images/46.png " ")

- You can do the same to the notification tasks. 

![](./images/48.png " ")

- Your Process should now resemble this.

![](./images/49.png " ")

- Click the start icon and open the properties. Give it a title. 

![](./images/50.png " ")

- Now click the integration and open its data association.

![](./images/51.png " ")



![](./images/62.png " ")

- Enter these hardcoded values for the respective fields on the right. These hardcoded values will vary for each ERP system, but these are the mandatory fields the API requires to create a new order.

![](./images/64.png " ")

![](./images/63.png " ")

- On the bottom, drag your table data object from the left, and map it to the orderItems table on the right.

![](./images/66.png " ")

- You will see this warning. Press the box in between.


![](./images/67.png " ")

- Change the condition to add.

![](./images/69.png " ")

- Create a new transformation.

![](./images/65.png " ")

- This is what it should look like on your mapper now

![](./images/70.png " ")

- Map the fields from your form table to the fields in the Fusion table like so.

![](./images/48.png " ")

- Your process is complete and should like this now. 

![](./images/71.png " ")

- Click publish, add a comment, then click the publish button.

![](./images/72.png " ")

- After hitting publish, press activate in the blue box, then 'Try in Test Mode' in the green box.

![](./images/73.png " ")

- Press activate, leave the checkbox as is.

![](./images/74.png " ")

- You should see this confirmation

![](./images/75.png " ")






- Map the data objects from the form to the fields that are submitted to the integration.

![](./images/52.png " ")

- Press save and test.

### **STEP 5**: Test your Process:

- Click on **Create Order** in **My Apps** section.

![](./images/87.png " ")

- Select **EXW** for Incoterms, **Net 60** for Payment terms, input a PO date. Click on the blue + icon. Add **Vario tablet** as the table name, quantity is **3** and unit price **300**. Click **Submit**

![](./images/78.png " ").

- Since the condition to forward the order to the Process owner isn't satisfied the integration will be directly called. You can view Integration status from the monitoring section underneath integration as mentioned in the previous labs.

![](./images/81.png " ").

![](./images/82.png " ").

![](./images/83.png " ").

![](./images/84.png " ").

- Test the process again. Enter quantity and net price such that total is over $15,000 and submit. 

![](./images/86.png " ").

- Select **My Tasks** from the menu on the right. 

![](./images/90.png " ").

- Select your process. 

![](./images/91.png " ").

- You can view your process details. Note that when you are reviewing your process you are reviewing it as a proces owner. Once you review your process details you can approve/reject 

![](./images/92.png " ").

- Go to **Processes** on the menu.

![](./images/93.png " ").

- You can view your end process flow here to see if it was succesful.

![](./images/94.png " ").

![](./images/95.png " ").



## Summary

-   In this lab, you developed an OIC process application that calls the previous integration you built. Together, this gives you an order entry form that performs as if natively part of your ERP Cloud implementation.

-   **You are finished with all of the labs!**

[Back to top](#introduction)


