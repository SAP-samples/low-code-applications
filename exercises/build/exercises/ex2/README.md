# Exercise 2: Create "actions" in SAP Build to access the Onlineshop API

This exercise will be conducted in SAP Build Process Automation on the SAP Business Technology Platform (BTP).

In this exercise, we will create Actions in SAP Build that access the Shopping Cart API on the SAP BTP ABAP Environment that has been developed in the previous chapter. There will be 2 actions, one to read all the shopping cart entries and another one that creates a new shopping cart entry. 

Then we will create a process using SAP Build Process Automation. The process will consist of 
- a start UI which a user can use to order a product with a quantity
- a condition that checks whether the quantity is 1. If it is, the condition auto approves the product order. If it isn't there will be an approval setp
- am approval step where an approver (e.g. a manager) gets the order of the user in the approver's inbox and can either approve or reject the order request
- an action step in which approved order requests invoke the call of the ABAP Cloud based RAP API. The call creates a new shopping cart in the BTP ABAP environment.

When this is finished, you will test the process from start to finish.

Now let's start with creating the actions that are needed for the process. To create such actions, we need to prepare two things first:
- Create a destination in SAP BTP to create the secure connectivity in the SAP BTP subaccount to the Shopping Cart API on the SAP BTP ABAP Environment from the previous chapters
- Register this destination to be used for sctions

You can continue with the first exercise - **[Exercise 2.1: Create a destination in an SAP BTP subaccount to access the Shopping API](../ex2.1/README.md)**


