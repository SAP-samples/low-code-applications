# Exercise 3 - Create a service (API)

After the creation of the data model ( persistence layer ) we will now select what to expose to the outside world as an API. This API can then be consumed by UI apps, workflows, etc. .For this we will add several entities to a service. CAP will expose this service automatically as a full blown OData service.

## Create new service entities

Go back to the **Home** tab in the Application Studio.

Your home tab displays the two new entities and the external one in your model and the corresponding sample data. You can easily navigate back to the Data Model Editor by clicking on of the entities if you like.

On **Home** add a new **Service** (it is actually a service entity). 

The Service Editor appears and asks you to create a service. Choose  **LCAPXXX.Capex** as a **Type** where again XXX is the number of your user. Then the **Name** should be automatically filled with **Capex** derived from the type. In the list of properties you can see all of them selected, leave it like this and confirm with a click on **Create**.

What you have now done is exposed your data model **Capex** as a service entity **Capex** 1:1. In technical (CAP) terms you have created a service entity as a projection on the Capex entity.

![](/exercises/ex3/images/LCAP_32.png)


Add another entity and repeat the step to create another service entity. This time select the type **LCAPXXX.Category** and find the name **Category** after selection. Click **Create**

Again we have exposed our **Category** data model 1:1. The types of service entities make a lot of sense if for example you want to create a new UI form to maintain Capex data and in the UI's **Category** field you want to expose a value help / dropdown of all the categories. That's actually what we are going for! In such a case you need a different entity for what you want to present in the value help and that's why we expose **Category** as well.

Add a third entity, this time choose **API_BUSINESS_PARTNER.A_BusinessPartner**. The Business Partner entity comes with a lot of properties though, a lot of these we don't really need for our application and therefore, we don't want to expose them all in the new service. Therefore, we will just select some of them. To get to this, first uncheck the first entry in the list, the **<all properties>** property. Now select the properties:
- **Business Partner**
- **FirstName**
- **LastName**

![](/exercises/ex3/images/LCAP_33.png)

## Enable Draft Editing for Capex 

There is an important part we still have to do for the particular **Capex** entity: Mark it for **Draft Editing**. This means that the service entity supports storing incomplete or wrong data in a draft which is only exposed to the user that created the entity while the entity is not active and not visible for other users. This is an important UX feature: If there are applications where there are mandatory fields or validations for a field (e.g. an email field should contain a valid email address) and the user is not able to resolve these issues before the timeout of the operation (for example because the user needs to attend a meeting before finsihing) without a draft mode, all the data would get lost. Drafts make sure that all the data that is entered gets saved in a draft and only when the data is complete and validated the data is turned into a real active object. 

Activate **Draft Editing** for the **Capex** entity by marking the corresponding checkbox on the property panel:

![](/exercises/ex3/images/LCAP_34.png)

You can also see the 3 service entities that you created and the associations in the above picture.

Please note that the associations will be provided automatically, based on the definition in the data model.

Close the Service Editor and navigate back to **Home** tab.

You should have two entities in the Date Model and three service entities in the Service box.

## Summary
You have now added a service to your project. Essentially, this service will expose your data model as an OData V4, RESTful API to your application.

Continue to - [Exercise 4](../ex4/README.md)
