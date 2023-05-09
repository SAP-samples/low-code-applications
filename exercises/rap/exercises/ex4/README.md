
# Exercise 4: Create a Web API for the Onlineshop

In this exercise we create an additional service. In the exercise before we created an Onlineshop service that we can use for a Fiori elements application which supports drafts (the ability to save UI entries in an unfinished or wrong state for the current user, in order to allow the user to correct the entry later. The entry will only become visible when the entry was finally corrected and saved). These kind of services are not suitable to be called from other places than UIs, for example processes. As we later on want to create a process we will now add a second service for web API usage. 

For this we need to add acouple of artefacts on top of the already existing ones.

## Exercise 4.1: Create a new data defintion

1. In your project open the context menu on **Core Data Services** -> **Data Definitions** and selected **New Data Definition**

![new_dd](images/100.png) 

2. Use the name `TAPI_ONLINESHOP_###` 

![new_dd](images/110.png) 

3. Overwrite the contents of the generated data definition like this

<pre lang="ABAP">
@AccessControl.authorizationCheck: #CHECK
@Metadata.allowExtensions: true
@EndUserText.label: 'Projection View for ZR_ONLINESHOP_###'
define root view entity ZAPI_ONLINESHOP_###
  provider contract transactional_query
  as projection on ZR_ONLINESHOP_###
{
  key OrderUUID,
  OrderID,
  Product,
  Quantity,
  LocalLastChangedAt
}
</pre>

3. Save and Activate your change

## Exercise 4.2: Create a new behavior definition

1. In your project open the context menu on **Core Data Services** -> **Behavior Definition** and selected **New Behavior Definition**

![new_dd](images/120.png) 

2. Choose the Implementation Type `Projection` and Root Entity `ZAPI_ONLINESHOP_###`. Press `Next` and then `Finish`

![new_dd](images/130.png) 

3. In the generated code get rid of the `use draft` line and all the lines that start with `use action`

![new_dd](images/140.png) 

4. add `alias onlineshop` as an alias, the code should look like this:

<pre lang="ABAP">
projection;
strict ( 2 );

define behavior for ZAPI_ONLINESHOP_### alias onlineshop
{
  use create;
  use update;
  use delete;
}
</pre>

5. Save and Activate your change

## Exercise 4.3: Create a new Service definition

1. In your project open the context menu on **Core Data Services** -> **Service Definition** and selected **New Service Definition**

![new_dd](images/150.png) 

2. Choose Source Type `Definition` and Referenced Object `ZAPI_ONLINESHOP_###`

![new_dd](images/160.png) 

3. Add alias `as onlineshop`

<pre lang="ABAP">
@EndUserText.label: 'Service Defition Z_ONLINESHOP_###'
define service Z_ONLINESHOP_### {
  expose ZAPI_ONLINESHOP_### as onlineshop;
}
</pre>

4. Save and Activate your change

## Exercise 4.4: Create a new Service Binding

1. In your project open the context menu on **Business Services** -> **Service Bindings** and selected **New Service Bindings**

![new_dd](images/170.png) 

2. Choose the name `Z_ONLINESHOP_###`, the Binding Type `ODATA V4 - Web API` and the Serivce Definition `Z_ONLINESHOP_###`. Press `Next` and `Finish`

![new_dd](images/180.png) 

3. Save and Activate your changes

4. On the resulting UI press the `Publish`button, the result looks like this:

![new_dd](images/190.png) 

## Exercise 4.5: Test the API in the browser

1. Press on the link `Service URL` in the picture above.

2. Add `onlineshop` at the end of the URL in the browser, so it looks like this

https://YY.YYYY.YYY.YY:44301/sap/opu/odata4/sap/z_onlineshop_###/srvd_a2x/sap/z_onlineshop_###/0001/onlineshop

3. The result should look like this:

![new_dd](images/200.png)  

## Summary   

You have created a Web API next to the one that is suitable for a UI and you can now use this API in a SAP Build Process.

You can continue with the next exercise - **[Build Exercise 1: Create Actions in SAP Build to access the Onlineshop API](../../../build/exercises/ex1/README.md)**
