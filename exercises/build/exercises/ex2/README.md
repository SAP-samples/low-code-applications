# Exercise 2: Create "actions" in SAP Build to access the Onlineshop API

This exercise will be conducted in SAP Build Process Automation on the SAP Business Technology Platform (BTP).

In this exercise, we will create Actions in SAP Build that access the Shopping Cart API on the SAP BTP ABAP Environment that has been developed in the previous chapter. There will be 2 actions, one to read all the shopping cart entries and another one that creates a new shopping cart entry. 

To create such actions, we need to prepare one thing first:
- Create a destination in SAP BTP to create the secure connectivity in the SAP BTP subaccount to the Shopping Cart API on the SAP BTP ABAP Environment from the previous chapters

## Exercise 2.1: Create a destination in an SAP BTP subaccount to access the Shopping API

We will now create the destination in a BTP subaccount to our Shopping Cart API on the SAP BTP ABAP Environment from the previous chapter. The destination will ensure secure connectivity.

1. In a browser, open the [destinations (new) view in the BTP Cockpit](https://emea.cockpit.btp.cloud.sap/cockpit/?idp=lcap.accounts.ondemand.com#/globalaccount/47ae62c5-c35b-48a4-99b1-eee46b5b62bf/subaccount/f65e327c-d9e9-44cd-8d7b-e4e7ea8db474/destinationsnew). If you need to log on, log on with the user and the password that the instructors have given you.

2. Press the *Create* button. On the pop up select 'From Scratch* and press *Create*

   ![NewDestinationFromScratch](images/NewDestinationFromScratch.png)

3. Fill in the following:

    |  Porperty   | Value |
    |  :------------- | :------------- |
    |  Name   | ShoppingCart### |
    |  Type   | HTTP |
    |  Description   | Shopping Cart API ### |
    |  URL   | https://3f652f6e-fef3-4c3a-8b7f-0ffd0f835d54.abap.eu10.hana.ondemand.com/sap/opu/odata/sap/Z_SHOPPINGCART_###_O2_API |
    |  Proxy Type   | Internet |
    |  Authentication   | BasicAuthentication |
    |  User   | INBOUND_USER_TECHEDLCAP |
    |  Password   | !!Password that is provided to you by the instructors!! |

    where *###* is your group number again (beware this has to be replaced in 3 values in the above list)    

   ![NewDestination](images/NewDestination.png)

4. Under *Additional Properties* press *Add Property* and add
`sap.applicationdevelopment.actions.enabled` with value `true`

5. Under *Additional Properties* press *Add Property* again and add
`sap.processautomation.enabled` with value `true`

6. Under *Additional Properties* press *Add Property* again and add
`sap.build.usage` with value `RAP`

7. Press *Create*

   ![PropertiesForDestination](images/PropertiesForDestination.png)

8. Back on the list of the destinations, select your new destination and press *Check Connection*. It should bring up a success messate

   ![DestinationCheck](images/DestinationCheck.png)

## Exercise 2.2: Enable the destination for Actions

1. Go to lobby https://lcapteched.eu10.build.cloud.sap/lobby. Select *Control Tower* on the left and select the *Destinations* tile on the right

   ![RegisterDestination](images/RegisterDestination.png)

2. Press *Add* to add a new destination

   ![RegisterDestinationAdd](images/RegisterDestinationAdd.png)

3. Search for your new destination *ShoppingCart###*, select it in the list and press *Next*

   ![RegisterDestinationSelect](images/RegisterDestinationSelect.png)

4. Select *All Environments* and press *Add Destination* 

   ![RegisterDestinationEnv](images/RegisterDestinationEnv.png)

## Exercise 2.3: Create Actions from the Shopping Cart API

1. In the lobby select *Actions* on the left and then press *Add* to create a new action.

   ![ActionsInLobby](images/ActionsInLobby.png)

2. On the dialog choose the tile *ABAP RESTful Application Programming Model* as an API Source

   ![RAPAction](images/RAPAction.png)

3. find your service *ShoppingCart###* (with ### being you group number) and select it.

   ![ActionShoppingCart](images/ActionShoppingCart.png)

4. Browse through the possible actions you can create from your service and press *Next*

   ![InspectActions](images/InspectActions.png)

5. Give your new action project the name *ShoppingCart###Actions* and a description *Actions for API Shopping Cart ###* (with ### again your group name). Press *Create*

   ![ActionProject](images/ActionProject.png)

6. Now select the actions you want to create. Look for the name of your entity (like *ZC_DBSHOPPINFCART###*) and select both the *Get entities* and the *Add new entity* ones and press *Add*

   ![SelectActions1](images/SelectActions1.png)

   ![SelectActions2](images/SelectActions2.png)

7. Test the Get Action: Select it on the left hand side. Select the *Test* tab, select your *ShoppingCart###* destination and press *Test*

   ![TestGetAction](images/TestGetAction.png)

8. After a short while you should see a result like this (with the entry that you created earler on in the Fiori elements preview application that you created)

   ![TestGetActionResult](images/TestGetActionResult.png)

9. Now select the *Post* action on the left hand side. On the right hand side on the *Input* tab, select the *OrderUuid* property and switch off the *Mandator* switch. This is, because the API doesn't really need the *OrderUuid* to be passed, if there is none available, the RAP service creates one automatically

   ![ActionAddNewEntity](images/ActionAddNewEntity.png)

10. Now select the *isActiveEntity* property, switch the *Mandatory* switch to *Off*, also set the value to *true*. This is related to the draf concepts, which means that in a UI when users edit an object it is constantly saved even in unfinished, inconsistent states. However, it is only saved for the current user in a draft state, all other users don't see the object in its unfinished state, they either see no object or the last active version. Only if the user finally saves the valuated object it changes from draft to active state. In our case, we want to add entities using the action in a way that all these entities are immediately active.
   
   ![ActionAddNewEntityActive](images/ActionAddNewEntityActive.png)
  
11. APIs that carry out changing operations normally need a so-called CSRF token from the server for security reasons. Without going deeper into what the mechanics behind this security measure are, we need such a token in our case as well. In order to make the action framework to generate one, press the settings button in the upper right corner and switch the *Enable CSRF* to on and press *Save*.

   ![ActionEnableCSRF](images/ActionEnableCSRF.png)

12. Now let's test the action again. Switch to the *Test* tab and select your *ShoppingCart###* destination.


   ![ActionAddDestination](images/ActionAddDestination.png)

13. Fill in some made-up product name value of your choice for the *OrderedItem* and some *OrderQuantity*. Then press *Test* that you can see in the screenshot above.

   ![ActionEnterValues](images/ActionEnterValues.png)

14. After a couple of seconds you should see the result in the lower part of the screen. A JSON representing the data that was just posted and is now persisted on the database should be shown, it indicates a successful invocation of the API

   ![ActionNewEntity](images/ActionNewEntity.png)

15. After the successful test, we need to release the current version of the action to make it possible for others to consume it. Press the *Release* button on the upper right of the screen.

   ![ActionRelease](images/ActionRelease.png)

16. A pop up comes up, indicating the current release version and an optional description for this version. Press *Release*.

   ![ActionReleaseVersion](images/ActionReleaseVersion.png)

16. The now released version of the actions can now be published for others to consume. Press the *Publish* button on the upper right.

   ![ActionPublish](images/ActionPublish.png)

17. Confirm with the *Publish* button. 

   ![ActionPublishOk](images/ActionPublishOk.png)

18. You should now see a published version of the actions.

   ![ActionPublished](images/ActionPublished.png)

   This concludes the creation of an action project which consumes some parts of the ABAP RAP API for shopping carts that you created earlier. This action project can now be consumed within a SAP Build Process, that we are going to create in the next chater

## Exercise 2.4: Create an SAP Build Process

   In this exercise we will create a new process in SAP Build. In this process there will be a UI that lets users create a shopping cart with a product and a quantity. Upon the submission of this shopping cart, there will be a condition in the process that checks whether only one piece of the product is requested and if it is, the request is automatically approved. If a bigger number is requested an approval step in the process will be carried out, that an entiteld person will find in the person's inbox. The person will then either request or approve the request and in the case the request is approved, the action that adds a new shopping cart entry invoking the RAP service that we built earlier.

   1. Let's start to create the process. Switch to the lobby back to the lobby (Lobby entry is on the top left). Select *Create* and *Create* in the menu

   ![ProcessCreate](images/ProcessCreate.png)

   2. Choose *Automated Process* and press *Next*.

   ![ProcessCreatePickPr](images/ProcessCreatePickPr.png)

   3. Choose *ProcessÜ and press *Next*.

   ![ProcessCreatePickPr2](images/ProcessCreatePickPr2.png)

   4. Provide a name like *ShoppingCart###Process* where *###* is again your group number. Press *Next*. 

   ![ProcessCreateName](images/ProcessCreateName.png)

   5. Check in the summary if everything is right and then press *Create*.

   ![ProcessCreateSummary](images/ProcessCreateSummary.png)

   6. In the new process project, you are immediately taken to a pop up in order to create a process within the process project. Add a name like *ShoppingCart###Process* and press *Create*. 

   ![ProcessCreateProcess](images/ProcessCreateProcess.png)

   7. A canvas opens for your new process. In this early stage, there is not much in it. Let's start with adding a trigger. As the name implies, this is what triggers the process and is its starting point. Press *Add a Trigger*.

   ![ProcessAddTrigger](images/ProcessAddTrigger.png)

   8. Select *Submit a Form*. There are a number of ways to start a process. For example it can be started by an API call or it can be started when a certain event occurs (e.g. the creation of a Sales Order in S/4HANA). In our case, we want to create a start UI, a form that when it is submitted, will start the process. Press *Submit a Form*.

   ![ProcessAddTriggerForm](images/ProcessAddTriggerForm.png)

   9.  Select *Create a New Form*

   ![ProcessAddTriggerFormBlank](images/ProcessAddTriggerFormBlank.png)

   10. Come up with a name for your form, e.g. *ShoppingCartForm*. Press *Create*.

   ![ProcessAddTriggerFormName](images/ProcessAddTriggerFormName.png)

   11. On the process canvas, press the *...* button on the trigger and invoke the *Open Editor* button. This will let us define what is on the new form.

   ![ProcessAddTriggerFormEdit](images/ProcessAddTriggerFormEdit.png)

   12. On the editor, choose the *H1* button on the left to create a new headline. Write *New Shopping Cart* into it. Then invoke *T* on the left side to create a new input field. Call it *Product*. Create another input field and call it *Quantity*. Press *Save*.

   ![ProcessAddTriggerFormFields](images/ProcessAddTriggerFormFields.png)

   13. Now let's add a condition to automatically approve the new shopping cart request when the quantity is only 1. For this press the *+* button under the trigger.

   ![ProcessAddCondition](images/ProcessAddCondition.png)

   14. Select *Controls and Events*.

   ![ProcessAddCondition2](images/ProcessAddCondition2.png)

   15. Select *Condition*

   ![ProcessAddCondition3](images/ProcessAddCondition3.png)

   16. Select the condition on the canvas and press *Open Condition Editor* on the right panel.

   ![ProcessAddConditionName](images/ProcessAddConditionName.png)

   17. Place the cursor into the first field on the left. Then choose the *Quantity* field.

   ![CreateCondition](images/CreateCondition.png)

   18. Select *is not equal to* in the middle field and type *1* in the value field on the right. Press *Apply*.

   ![CreateCondition2](images/CreateCondition2.png)

   19. On the process canvas press *Save*. As a next step let's create an approval. For this invoke the *+* button in the *if* branch of the condition.

   ![AddApproval](images/AddApproval.png)

   20. Select *Approval*.

   ![AddApproval2](images/AddApproval2.png)

   21. Select *Blank Approval* 

   ![AddApproval3](images/AddApproval3.png)

   22. Assign a name like *ShoppingCartApproval*. Mark the *Based on a form* checkbox and select your *ShoppingCartForm*. This means that the approval step uses the same form that we have created for the start UI. In turn this means that the approver will see the same screen as the requester in order for the approver to decide.

   ![AddApprovalForm](images/AddApprovalForm.png)

   23. Select the approval in the canvas and then place the cursor in the *Subject* field. Write the text *Approve Shopping Cart for * and then select the *Product* field on the left. Now move to the *Recipients* section and write the name of your user into the *User* field, so *lowcodeuser+0###@gmail.com* with your group number *###*.

   This means that all the requests for the shopping cart will end up in your users inbox for approval. In a real world scenario it will not make sense of course that the same user that later on might create a request is also the user that approves the request, for our testing puposes it makes sense though. 

   ![AddApprovalFormParams](images/AddApprovalFormParams.png)

   14. Switch to the *Inputs* tab. Assign *Product* to the *Product* field and *Quantity* to the *Quantity* field. This will ensure that the original field from the from in the start UI will also be populated into the approval form and so the approver can see the values. Press *Save*.

   ![AddApprovalInput](images/AddApprovalInput.png)

   15. We need to make sure that the process ends, in case the approver rejects the request. For this press *+* under the *Reject* branch.

   ![AddReject](images/AddReject.png)

   16. Select *Controls and Events*.

   ![AddRejectEnd](images/AddRejectEnd.png)

   17. Select *End*. Press *Save*. 

   ![AddRejectEnd2](images/AddRejectEnd2.png)

   18. Now let's add the invocation of the action to create a new shopping cart entry in case the request is approved. Press *+* just over the *End* node.

   ![AddAction](images/AddAction.png)

   19. Select *Action*.

   ![AddAction2](images/AddAction2.png)

   20. Select *Browser All Actions*.

   ![BrowseActions](images/BrowseActions.png)

   21. Select the *Post Add new entity to ....* and press *Add* 

   ![AddActionNewEntity](images/AddActionNewEntity.png)

   22. Select the new action node on the canvas. Place the cursor in the *Destination Variable* field and select *+ Create new Destination Variable*.

   ![AddActionDestinationVariable](images/AddActionDestinationVariable.png)

   23. Come up with a name for your variable, e.g. *sc###*, where *###* is your group number. The variable could be used later in order to provide different destination names for different environments like a development, a test and a productive one. It will not really play a role in the exercise, but it needs to be created. Press *Create*.

   ![CreateDestinationVariable](images/CreateDestinationVariable.png)

   24. Switch to the *Inputs* tab. Scroll to the *OrderedItem* field and place the cursor in it. Select *Product* on the left. Now scroll to the *OrderQuantity*, place the cursor in it and select *Quantity* on the left. As in the approval step, this makes sure that the *Product* and *Quantity* fields from the start UI are going to be bound to the API call as well and thus, the value that the user entered in the start UI are passed to the action and via the action to the RAP API. Press *Save*. 

   ![ActionMapProperties](images/ActionMapProperties.png)

   25. The final canvas should look similar to the one on this screenshot. Next up we need to release and deploy the process. Press *Release* on the top right.

   ![ReleaseProcess](images/ReleaseProcess.png)

   26. A pop up comes up that shows the release version for the project and and optional note for the release. Press *Relelase*.

   ![ReleaseProcess2](images/ReleaseProcess2.png)

   27. On the next screen you will see an editable version of the process where you could then carry out further changes to the process. However, we want to switch to the currently released version. Press the *Show project version* link.

   ![ShowVersion](images/ShowVersion.png)

   28. Now let's deploy the released version. Press *Deploy*. 

   ![DeployProcess](images/DeployProcess.png)

   29. On the pop up choose the *Public* envrionment and press *Deploy*. 

   ![ChooseEnvironment](images/ChooseEnvironment.png)

   30. For the current deployment, we need to fill the destination variable that we defined before with a concrete destination. Choose the *ShoppingCart###* one and press *Deploy*.

   ![SelectDestinationVariable](images/SelectDestinationVariable.png)

   The process is now deployed and can be used and tried out.

## Exercise 2.5: Test thhe process, the approval and the invocation of the RAP API 

   In this section we will test the process. First we will fill out a new shopping cart request and submit it. Then we will put ourselves into the shoes of the approver and enter the approver's inbox. Then we will approve the request and check whether this resulted in the proper invocation of the action and in turn the shopping cart RAP API on ABAP.

   1. As a first step we need to get a URL for the start UI. For thi, switch to the *Overview* tab of the process. Click the link of the *ShoppingCart###Process*.

   ![SwitchToProcess](images/SwitchToProcess.png)

   2. Back on the canvas, select the trigger and then on the right hand side copy the *public* link. 

   ![CopyProcessLink](images/CopyProcessLink.png)

   3. Switch to a new browser tab and paste the URL that you just copied. The start UI comes up. Enter a product name and a quantity of your likining and the press *Submit*.

   ![ProcessStartUI](images/ProcessStartUI.png)

   4. After a couple of seconds you will see a message telling you that you successfully submitted the form.

   ![SuccessfulSubmit](images/SuccessfulSubmit.png)

   5. Now that the shopping cart request was submitted, we switch to the approver person in order to approve or reject the shopping cart. For this, switch back to the browser tab with the SAP Build Lobby. Invoke the *Inbox* button which you find as the second on the left on the top of the lobby screen.

   ![NavToInbox](images/NavToInbox.png)

   6. In your inbox on the left side a task should be shown which is the approval for the shopping cart that you just submitted. Click on it to bring up the details on the right. You should see the form with the values that were submitted. Press *Approve*.

   ![Approval](images/Approval.png)

   7. Now let's check whether the invocation of the action and the RAP API was successful after the approval. For this, switch back to the ABAP developer tools again and the service binding of the UI service. Press *Preview* to bring up the Fiori UI with all the shopping cart entries.

   ![FioriPreview](images/FioriPreview.png)

   8. Press *Go*. Your new enntry should come up in the list

   ![PreviewResult](images/PreviewResult.png)

   This concludes the test of the process end to end.


## Summary  
 
 This concludes this hand on workshop! You have created a shopping cart OData API with the ABAP Restful Programming Model (RAP) using ABAP Cloud on the BTP ABAP Environment. You have made this API available for consumption outside of the ABAP Envrionment. You have created SAP Build actions from the RAP API. Then you created an SAP Build Process which consists out of several steps: A start UI to create a shopping cart for a product and a quantity, a condition that auto approvs when the quantity is only 1, an approval step for approvers to approve or reject shopping carts with quantities other than 1 and an invocation of an action that creates a shopping cart entry by calling the RAP API. At the end you tested the entire process.

 
