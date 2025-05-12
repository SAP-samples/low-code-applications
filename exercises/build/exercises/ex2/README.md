# Exercise 2: Create Actions in SAP Build to access the Onlineshop API

From this exercise on, we will switch to SAP Build Process Automation on the  Business Technology Platform (BTP).

In this exercise we will create Actions in SAP Build that access the Shopping Cart API on the BTP ABAP Environment from the previous chapter. There will be 2 actions, one to read all the shopping cart entries and another one that creates a new shopping cart entry. 

To create such Actions we need to prepare one thing first:
-Create a destination in BTP to create the secure connectivity in the BTP subaccount to the Shopping Cart API on the BTP ABAP Environment from the previous chapters

## Exercise 2.1: Create a Destination in a BTP subaccount to access the Shopping API

We will now create the destination in a BTP subaccount to our Shopping Cart API on the BTP ABAP Environment from the previous chapter. The destination will ensure secure connectivity.

1. In a browser open the [destinations (new) view in the BTP Cockpit](https://emea.cockpit.btp.cloud.sap/cockpit/?idp=lcap.accounts.ondemand.com#/globalaccount/47ae62c5-c35b-48a4-99b1-eee46b5b62bf/subaccount/f65e327c-d9e9-44cd-8d7b-e4e7ea8db474/destinationsnew). If you need to log on, log on with the user and the password that the instructors have given you

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

   ![ProcessCreate](images/ProcessCreate.png)
   ![ProcessCreatePickPr](images/ProcessCreatePickPr.png)
   ![ProcessCreatePickPr2](images/ProcessCreatePickPr2.png)
   ![ProcessCreateName](images/ProcessCreateName.png)
   ![ProcessCreateSummary](images/ProcessCreateSummary.png)
   ![ProcessCreateProcess](images/ProcessCreateProcess.png)
   ![ProcessAddTrigger](images/ProcessAddTrigger.png)
   ![ProcessAddTriggerForm](images/ProcessAddTriggerForm.png)
   ![ProcessAddTriggerFormBlank](images/ProcessAddTriggerFormBlank.png)
   ![ProcessAddTriggerFormName](images/ProcessAddTriggerFormName.png)
   ![ProcessAddTriggerFormEdit](images/ProcessAddTriggerFormEdit.png)
   ![ProcessAddTriggerFormFields](images/ProcessAddTriggerFormFields.png)
   ![ProcessAddCondition](images/ProcessAddCondition.png)
   ![ProcessAddCondition2](images/ProcessAddCondition2.png)
   ![ProcessAddCondition3](images/ProcessAddCondition3.png)
   ![ProcessAddConditionName](images/ProcessAddConditionName.png)
   ![CreateCondition](images/CreateCondition.png)
   ![CreateCondition2](images/CreateCondition2.png)
   ![AddApproval](images/AddApproval.png)
   ![AddApproval2](images/AddApproval2.png)
   ![AddApproval3](images/AddApproval3.png)
   ![AddApprovalForm](images/AddApprovalForm.png)
   ![AddApprovalFormParams](images/AddApprovalFormParams.png)
   ![AddApprovalInput](images/AddApprovalInput.png)
   ![AddReject](images/AddReject.png)
   ![AddRejectEnd](images/AddRejectEnd.png)
   ![AddRejectEnd2](images/AddRejectEnd2.png)
   ![AddAction](images/AddAction.png)
   ![AddAction2](images/AddAction2.png)
   ![BrowseActions](images/BrowseActions.png)
   ![AddActionNewEntity](images/AddActionNewEntity.png)
   ![AddActionDestinationVariable](images/AddActionDestinationVariable.png)
   ![CreateDestinationVariable](images/CreateDestinationVariable.png)
   ![ActionMapProperties](images/ActionMapProperties.png)
   ![ReleaseProcess](images/ReleaseProcess.png)
   ![ReleaseProcess2](images/ReleaseProcess2.png)
   ![ShowVersion](images/ShowVersion.png)
   ![DeployProcess](images/DeployProcess.png)
   ![ChooseEnvironment](images/ChooseEnvironment.png)
   ![SelectDestinationVariable](images/SelectDestinationVariable.png)
   ![SwitchToProcess](images/SwitchToProcess.png)
   ![CopyProcessLink](images/CopyProcessLink.png)
   ![ProcessStartUI](images/ProcessStartUI.png)
   ![SuccessfulSubmit](images/SuccessfulSubmit.png)
   ![NavToInbox](images/NavToInbox.png)
   ![Approval](images/Approval.png)
   ![FioriPreview](images/FioriPreview.png)
   ![PreviewResult](images/PreviewResult.png)








## Summary  
 
