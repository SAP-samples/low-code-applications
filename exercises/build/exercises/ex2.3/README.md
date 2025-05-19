## Exercise 2.3: Create Actions from the Shopping Cart API

1. In the lobby select *Actions* on the left and then press *Add* to create a new action.

   ![ActionsInLobby](../ex2/images/ActionsInLobby.png)

2. On the dialog choose the tile *ABAP RESTful Application Programming Model* as an API Source

   ![RAPAction](../ex2/images/RAPAction.png)

3. Find your service *ShoppingCart###* (with ### being you unique number) and select it.

   ![ActionShoppingCart](../ex2/images/ActionShoppingCart.png)

4. Browse through the possible actions you can create from your service and press *Next*

   ![InspectActions](../ex2/images/InspectActions.png)

5. Give your new action project the name *ShoppingCart###Actions* and a description *Actions for API Shopping Cart ###* (with ### again your reference number). Press *Create*

   ![ActionProject](../ex2/images/ActionProject.png)

6. Now select the actions you want to create. Look for the name of your entity (like *ZC_DBSHOPPINFCART###*) and select both the *Get entities* and the *Add new entity* ones and press *Add*

   ![SelectActions1](../ex2/images/SelectActions1.png)

   ![SelectActions2](../ex2/images/SelectActions2.png)

7. Test the Get Action: Select it on the left hand side. Select the *Test* tab, select your *ShoppingCart###* destination and press *Test*

   ![TestGetAction](../ex2/images/TestGetAction.png)

8. After a short while you should see a result like this (with the entry that you created earler on in the Fiori elements preview application that you created)

   ![TestGetActionResult](../ex2/images/TestGetActionResult.png)

9. Now select the *Post* action on the left hand side. On the right hand side on the *Input* tab, select the *OrderUuid* property and switch off the *Mandator* switch. This is, because the API doesn't really need the *OrderUuid* to be passed, if there is none available, the RAP service creates one automatically

   ![ActionAddNewEntity](../ex2/images/ActionAddNewEntity.png)

10. Now select the *isActiveEntity* property, switch the *Mandatory* switch to *Off*, also set the value to *true*. This is related to the draf concepts, which means that in a UI when users edit an object it is constantly saved even in unfinished, inconsistent states. However, it is only saved for the current user in a draft state, all other users don't see the object in its unfinished state, they either see no object or the last active version. Only if the user finally saves the valuated object it changes from draft to active state. In our case, we want to add entities using the action in a way that all these entities are immediately active.
   
   ![ActionAddNewEntityActive](../ex2/images/ActionAddNewEntityActive.png)
  
11. APIs that carry out changing operations normally need a so-called CSRF token from the server for security reasons. Without going deeper into what the mechanics behind this security measure are, we need such a token in our case as well. In order to make the action framework to generate one, press the settings button in the upper right corner and switch the *Enable CSRF* to on and press *Save*.

   ![ActionEnableCSRF](../ex2/images/ActionEnableCSRF.png)

12. Now let's test the action again. Switch to the *Test* tab and select your *ShoppingCart###* destination.


   ![ActionAddDestination](../ex2/images/ActionAddDestination.png)

13. Fill in some made-up product name value of your choice for the *OrderedItem* and some *OrderQuantity*. Then press *Test* that you can see in the screenshot above.

   ![ActionEnterValues](../ex2/images/ActionEnterValues.png)

14. After a couple of seconds you should see the result in the lower part of the screen. A JSON representing the data that was just posted and is now persisted on the database should be shown, it indicates a successful invocation of the API

   ![ActionNewEntity](../ex2/images/ActionNewEntity.png)

15. After the successful test, we need to release the current version of the action to make it possible for others to consume it. Press the *Release* button on the upper right of the screen.

   ![ActionRelease](../ex2/images/ActionRelease.png)

16. A pop up comes up, indicating the current release version and an optional description for this version. Press *Release*.

   ![ActionReleaseVersion](../ex2/images/ActionReleaseVersion.png)

16. The now released version of the actions can now be published for others to consume. Press the *Publish* button on the upper right.

   ![ActionPublish](../ex2/images/ActionPublish.png)

17. Confirm with the *Publish* button. 

   ![ActionPublishOk](../ex2/images/ActionPublishOk.png)

18. You should now see a published version of the actions.

   ![ActionPublished](../ex2/images/ActionPublished.png)



# Summary
This concludes the creation of an action project which consumes some parts of the ABAP RAP API for shopping carts that you created earlier. This action project can now be consumed within a SAP Build Process, that we are going to create in the next chapter
      
You can continue with the next exercise - **[Exercise 2.4: Create an SAP Build Process](../ex2.4/README.md)**
