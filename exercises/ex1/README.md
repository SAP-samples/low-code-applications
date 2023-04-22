# Exercise 1 - Create a data model with the SAP Business Application Studio

In this exercise, we will use the new low-code perspective in the SAP Business Application Studio to create a service that persists our business data and exposes the data as an OData service for our consuming applications later on.
We will also test the service and see whether it runs or not.

## Exercise 1.1 Launch Low-Code Perspective

Open your browser and launch the so-called "lobby" using the following URL:
```URL
https://lcapteched2021-applicationdevelopment.lcnc.cfapps.eu10.hana.ondemand.com/
````
You should see the central entry for low-code / no-code development on SAP BTP.

![](/exercises/ex1/images/lobby_01.png)

Click on the "Create" button and select "Business Application". A dialog appears where you can enter the following name for your project. As we plan to deploy our project it is important to stick to the naming convention here.  

**DO NOT USE YOUR OWN PROJECT NAME**  

Name your project   
```
LCAPXXX
```
Where XXX is your the user number that was assigned to you. Please make sure that you got a user number assigned by the speakers / moderators, don't make up your own number to avoid clashes with the deployments of others. So if your user number is for example **008** your project name is **LCAP008**

You can provide any descriptive text if you want.  
Confirm with a click on **Create**.

After the SAP Business Application Studio has created your environment you should see a screen like this (depending on whether your dev space has already started, this might take several minutes to come up). Make sure you select the "Home" tab:
![](/exercises/ex1/images/LCAP_01.png)

Now we can build our project and use SAP-opinionated technologies such as CAP (Cloud Application Programming Model), Fiori Elements, MDK (Mobile Development Kit) and Workflow for our purposes without thinking about how to structure our project and being able to concentrate on the tasks to solve rather than spending time to think about project setup and wiring up technologies.

In the next step we will create a data model.

## Exercise 1.2 Create a Data Model

We will first create our persistence by adding a data model to our project. You can use the **Data Models** tile for that.

Create your first data model ( = entity ) which is the one that contains all the properties that should pop up in the UI apps to create and view registrations for expenditures. Note that the ID property as a key is already created for you for convenience reasons. One can choose to keep it or change / delete it, we keep it.

Entity Name: Capex

| Property Name | Property Type | Key Property
| ----------- | ----------- | - |
| ID | UUID | X |
| costcenter | String |   |
| description | String |   |
| totalcost | Integer |   |
| firstname | String |   |
| lastname | String |   |

![](/exercises/ex1/images/LCAP_02.png)


We will now add another entity. This time we will create a **Category** entity, which will contain some categories in which a Capex request will fall.

Entity Name: Category

| Property Name | Property Type | Key Property
| ----------- | ----------- | - |
| ID | Integer | X |
| name | String |   |

Again, the **ID** property is created for you. This time however, make sure you change its property type from **UUID** to **Integer**.

Now the data model will look like this:

![](/exercises/ex1/images/LCAP_03.png)

We will now create an relationship (association) between the entities to indicate of which category a capex request is.

Click on the header area of the **Capex** entity and click "Add Relationship" in the menu that appears:

![](/exercises/ex1/images/LCAP_04.png)

Associate your **Capex** entity with the **Category** entity and take over the suggested values (like **Category** and the target entity type **LCAPXXX.Category** where XXX is your user's number) for that.

![](/exercises/ex1/images/LCAP_04_2.png)

Our data model is now complete an should look like this:

![](/exercises/ex1/images/LCAP_08.png)
 
## Summary

You've now created a data model including persistence in CAP (Cloud Application Programming model) that can be later used to be deployed to the SAP HANA database we will use. Note that you have not seen any CAP related commands or syntax.

Continue to - [Exercise 1.5](../ex1.5/README.md)

