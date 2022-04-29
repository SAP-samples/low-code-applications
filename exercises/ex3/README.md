# Exercise 3 - Create a service (API)

After the creation of the data model ( persistence layer ) we will now select what to expose to the outside world as an API. This API can then be consumed by UI apps, workflows, etc. .For this we will add several entities to a service. CAP will expose this service automatically as a full blown OData service.

Go back to the **Home** tab in the Application Studio.

You home tab displays the two entities in your model and the corresponding sample data. You can easily navigate back to the Data Model Editor by clicking on of the entities if you like.

On **Home** add a new "Service" (it is actually a service entity). 

The Service Editor appears and asks you to create a service. Choose  **LCAPXXX.Capex** as a **Type** where again XXX is the number of your user. Then the **Name** should be automatically filled with **Capex** derived from the type. In the list of properties you can see all of them selected, leave it like this and confirm with a click on **Create**.

What you have now done is exposed your data model **Capex** as a service entity **Capex** 1:1. In technical (CAP) terms you have created a service entity as a projection on the Capex entity.

![](/exercises/ex3/images/LCAP_32.png)

Add another entity and repeat the step to create another service entity. This time select the type **LCAPXXX.Category** and find the name **Category** after selection. Click **Create**

Again we have exposed our **Category** data model 1:1. The types of service entities make a lot of sense if for example you want to create a new UI form to maintain Capex data and in the UI's **Category** field you want to expose a value help / dropdown of all the categories. Then you need 2 different entities.

However, there are also use cases where you just want to display the data in a list or a form, where the users are not interested in the technical details, e.g. that the category "monitors" has a key "3". In other words you don't want to directly expose the underlying data model structure. To do this we create a third service entity and "flatten" the model.

Again add an entity. As a type choose **LCAPXXX.Capex** again. This time however, overwrite the name to become **CapexFlat**. In the list of properties below
- uncheck **category** (this gets rid of the association)
- check **name** (this adds the name property of the association to the service entity directly)

![](/exercises/ex3/images/LCAP_33.png)

After this your editor should look like this: 

![](/exercises/ex3/images/LCAP_34.png)

Please note that the associations will be provided automatically, based on the definition in the data model.

Close the Service Editor and navigate back to "Home" tab.

You should have two entities in the Date Model and three service entities in the Service box.

## Summary
You have now added a service to your project. Essentially, this service will expose your data model as an OData V4, RESTful API to your application.

Continue to - [Exercise 4](../ex4/README.md)
