## Exercise 2.4: Create an SAP Build Process

   In this exercise, we will create a new process in SAP Build. In this process, there will be a UI that lets users create a shopping cart with a product and a quantity. Upon the submission of this shopping cart, there will be a condition in the process that checks whether only one piece of the product is requested. In case it is, the request is automatically approved. If a bigger number is requested, an approval step in the process will be carried out, that an entitled person will find in the person's inbox. The person will then either decline or approve the request. In case the request is approved, the action that adds a new shopping cart entry invoking the RAP service that we built earlier.

   1. Let's start to create the process. Switch back to the lobby (Lobby entry is on the top left). Select *Create* and then *Create* in the menu.

   ![ProcessCreate](../ex2/images/ProcessCreate.png)

   2. Choose *Automated Process* and press *Next*.

   ![ProcessCreatePickPr](../ex2/images/ProcessCreatePickPr.png)

   3. Choose *ProcessÜ and press *Next*.

   ![ProcessCreatePickPr2](../ex2/images/ProcessCreatePickPr2.png)

   4. Provide a name like *ShoppingCart###Process* where *###* is again your group number. Press *Next*. 

   ![ProcessCreateName](../ex2/images/ProcessCreateName.png)

   5. Check in the summary if everything is right and then press *Create*.

   ![ProcessCreateSummary](../ex2/images/ProcessCreateSummary.png)

   6. In the new process project, you are immediately taken to a pop up in order to create a process within the process project. Add a name like *ShoppingCart###Process* and press *Create*. 

   ![ProcessCreateProcess](../ex2/images/ProcessCreateProcess.png)

   7. A canvas opens for your new process. In this early stage, there is not much in it. Let's start with adding a trigger. As the name implies, this is what triggers the process and is its starting point. Press *Add a Trigger*.

   ![ProcessAddTrigger](../ex2/images/ProcessAddTrigger.png)

   8. Select *Submit a Form*. There are a number of ways to start a process. For example it can be started by an API call or it can be started when a certain event occurs (e.g. the creation of a Sales Order in S/4HANA). In our case, we want to create a start UI, a form that when it is submitted, will start the process. Press *Submit a Form*.

   ![ProcessAddTriggerForm](../ex2/images/ProcessAddTriggerForm.png)

   9.  Select *Create a New Form*

   ![ProcessAddTriggerFormBlank](../ex2/images/ProcessAddTriggerFormBlank.png)

   10. Come up with a name for your form, e.g. *ShoppingCartForm*. Press *Create*.

   ![ProcessAddTriggerFormName](../ex2/images/ProcessAddTriggerFormName.png)

   11. On the process canvas, press the *...* button on the trigger and invoke the *Open Editor* button. This will let us define what is on the new form.

   ![ProcessAddTriggerFormEdit](../ex2/images/ProcessAddTriggerFormEdit.png)

   12. On the editor, choose the *H1* button on the left to create a new headline. Write *New Shopping Cart* into it. Then invoke *T* on the left side to create a new input field. Call it *Product*. Create another input field and call it *Quantity*. Press *Save*.

   ![ProcessAddTriggerFormFields](../ex2/images/ProcessAddTriggerFormFields.png)

   13. Now let's add a condition to automatically approve the new shopping cart request when the quantity is only 1. For this press the *+* button under the trigger.

   ![ProcessAddCondition](../ex2/images/ProcessAddCondition.png)

   14. Select *Controls and Events*.

   ![ProcessAddCondition2](../ex2/images/ProcessAddCondition2.png)

   15. Select *Condition*

   ![ProcessAddCondition3](../ex2/images/ProcessAddCondition3.png)

   16. Select the condition on the canvas and press *Open Condition Editor* on the right panel.

   ![ProcessAddConditionName](../ex2/images/ProcessAddConditionName.png)

   17. Place the cursor into the first field on the left. Then choose the *Quantity* field.

   ![CreateCondition](../ex2/images/CreateCondition.png)

   18. Select *is not equal to* in the middle field and type *1* in the value field on the right. Press *Apply*.

   ![CreateCondition2](../ex2/images/CreateCondition2.png)

   19. On the process canvas press *Save*. As a next step let's create an approval. For this invoke the *+* button in the *if* branch of the condition.

   ![AddApproval](../ex2/images/AddApproval.png)

   20. Select *Approval*.

   ![AddApproval2](../ex2/images/AddApproval2.png)

   21. Select *Blank Approval* 

   ![AddApproval3](../ex2/images/AddApproval3.png)

   22. Assign a name like *ShoppingCartApproval*. Mark the *Based on a form* checkbox and select your *ShoppingCartForm*. This means that the approval step uses the same form that we have created for the start UI. In turn this means that the approver will see the same screen as the requester in order for the approver to decide.

   ![AddApprovalForm](../ex2/images/AddApprovalForm.png)

   23. Select the approval in the canvas and then place the cursor in the *Subject* field. Write the text *Approve Shopping Cart for * and then select the *Product* field on the left. Now move to the *Recipients* section and write the name of your user into the *User* field, so *lowcodeuser+0###@gmail.com* with your group number *###*.

   This means that all the requests for the shopping cart will end up in your users inbox for approval. In a real world scenario it will not make sense of course that the same user that later on might create a request is also the user that approves the request, for our testing puposes it makes sense though. 

   ![AddApprovalFormParams](../ex2/images/AddApprovalFormParams.png)

   14. Switch to the *Inputs* tab. Assign *Product* to the *Product* field and *Quantity* to the *Quantity* field. This will ensure that the original field from the from in the start UI will also be populated into the approval form and so the approver can see the values. Press *Save*.

   ![AddApprovalInput](../ex2/images/AddApprovalInput.png)

   15. We need to make sure that the process ends, in case the approver rejects the request. For this press *+* under the *Reject* branch.

   ![AddReject](../ex2/images/AddReject.png)

   16. Select *Controls and Events*.

   ![AddRejectEnd](../ex2/images/AddRejectEnd.png)

   17. Select *End*. Press *Save*. 

   ![AddRejectEnd2](../ex2/images/AddRejectEnd2.png)

   18. Now let's add the invocation of the action to create a new shopping cart entry in case the request is approved. Press *+* just over the *End* node.

   ![AddAction](../ex2/images/AddAction.png)

   19. Select *Action*.

   ![AddAction2](../ex2/images/AddAction2.png)

   20. Select *Browser All Actions*.

   ![BrowseActions](../ex2/images/BrowseActions.png)

   21. Select the *Post Add new entity to ....* and press *Add* 

   ![AddActionNewEntity](../ex2/images/AddActionNewEntity.png)

   22. Select the new action node on the canvas. Place the cursor in the *Destination Variable* field and select *+ Create new Destination Variable*.

   ![AddActionDestinationVariable](../ex2/images/AddActionDestinationVariable.png)

   23. Come up with a name for your variable, e.g. *sc###*, where *###* is your group number. The variable could be used later in order to provide different destination names for different environments like a development, a test and a productive one. It will not really play a role in the exercise, but it needs to be created. Press *Create*.

   ![CreateDestinationVariable](../ex2/images/CreateDestinationVariable.png)

   24. Switch to the *Inputs* tab. Scroll to the *OrderedItem* field and place the cursor in it. Select *Product* on the left. Now scroll to the *OrderQuantity*, place the cursor in it and select *Quantity* on the left. As in the approval step, this makes sure that the *Product* and *Quantity* fields from the start UI are going to be bound to the API call as well and thus, the value that the user entered in the start UI are passed to the action and via the action to the RAP API. Press *Save*. 

   ![ActionMapProperties](../ex2/images/ActionMapProperties.png)

   25. The final canvas should look similar to the one on this screenshot. Next up we need to release and deploy the process. Press *Release* on the top right.

   ![ReleaseProcess](../ex2/images/ReleaseProcess.png)

   26. A pop up comes up that shows the release version for the project and and optional note for the release. Press *Relelase*.

   ![ReleaseProcess2](../ex2/images/ReleaseProcess2.png)

   27. On the next screen you will see an editable version of the process where you could then carry out further changes to the process. However, we want to switch to the currently released version. Press the *Show project version* link.

   ![ShowVersion](../ex2/images/ShowVersion.png)

   28. Now let's deploy the released version. Press *Deploy*. 

   ![DeployProcess](../ex2/images/DeployProcess.png)

   29. On the pop up choose the *Public* envrionment and press *Deploy*. 

   ![ChooseEnvironment](../ex2/images/ChooseEnvironment.png)

   30. For the current deployment, we need to fill the destination variable that we defined before with a concrete destination. Choose the *ShoppingCart###* one and press *Deploy*.

   ![SelectDestinationVariable](../ex2/images/SelectDestinationVariable.png)

  

# Summary
You have now built a process with Build Process Automation that includes a start UI, a condition, an approval step and the invocation of an action which in turn creates a new shopping cart entry usind the ABAP Cloud based RAP OData service. The process is deployed and can be used and tried out.
         
You can continue with the next exercise - **[Exercise 2.5: Test thhe process, the approval and the invocation of the RAP API ](../ex2.5/README.md)**
