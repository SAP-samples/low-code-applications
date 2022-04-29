# Exercise 1.5 - Reference an S/4 HANA CLoud Service in your Data Model

In this exercise, we will add an S/4 service, the Business Partner to our project and associated with our Capex model

## Exercise 1.5.1 Discover an S/4 HANA Cloud Service and add it to your Data Model

On **Home** press "+" on the **External Data Models** tile. This opens the so-called **Service Center** on the left hand side.

There you can see a choice of **SAP Systems**. Technically these are destinations to OData Services in your backend system that an administrator has set up for you. These can be services from an S/4 HANA system or from other SAP backend systems.

In the lower part of the screen you can also see that there are APIs from **SAP API Business Hub** available. However, unlike the ones that are under **SAP Systems** these don't come with connectivity to the backends, so we stick with **SAP Systems**.

Choose **API_BUSINESS_PARTNER**

You can now see the details of the chosen Service, its entities and the properties for each entity, as well general data about the service.

![](/exercises/ex1.5/images/LCAP_151.png)

Press on the **Add Data Model** in the upper right corner of the screen.

This adds the chosen Service to you project. 

Return to **Home**, after a couple of seconds the new Service will show up, its 36 entities are shown.

![](/exercises/ex1.5/images/LCAP_152.png)

You can now close the left pane of the service center by clicking the highlighted button in the image above

## Exercise 1.5.2 Associate a Business Partner Entity with the Capex Entity

On **Home** under **Data Models** press on the **Capex** entry to get back into the graphical modeler.

Here invoke the **Add Relationship** function on **Capex** again. 

![](/exercises/ex1.5/images/LCAP_153.png)

This is to create a new association to a Business Partner entity. However, we don't see the Business Partner on the canvas. This is because it is in another namespace than our own Capex and Category entities.

Therefore, drag the end of line of the relationship to an empty space on the canvas and click the mouse button.

A new dialog will come up. From the dropdown choose **Target Entity Type** **API_BUSINESS_PARTNER-A_BusinessPartner**. Change the suggested **Property Name** to **BusinessPartner**. Leave all the other suggestions (**Association** and **To-One**) as they are and press **Create**

![](/exercises/ex1.5/images/LCAP_154.png)

You will now see the final data model:

![](/exercises/ex1.5/images/LCAP_155.png)


## Summary

You've now added a reference to a data model / service in an S/4 HANA Cloud backend system to your new data model.

Continue to - [Exercise 2](../ex2/README.md)

