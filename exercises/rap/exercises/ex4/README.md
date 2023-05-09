
# Exercise 4: Create a Web API for the Onlineshop

## Exercise 4.1: 

1. 


 ![new_dd](images/100.png) 

  ![new_dd](images/110.png) 

2. Overwrite the contents of the generated data definition like this

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

4.

![new_dd](images/120.png) 

![new_dd](images/130.png) 

![new_dd](images/140.png) 

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

![new_dd](images/150.png) 

![new_dd](images/160.png) 

Add alias `as onlineshop`

<pre lang="ABAP">
@EndUserText.label: 'Service Defition Z_ONLINESHOP_300'
define service Z_ONLINESHOP_300 {
  expose ZAPI_ONLINESHOP_300 as onlineshop;
}
</pre>

Save and Activate your change

![new_dd](images/170.png) 

![new_dd](images/180.png) 

Activate

Publish

![new_dd](images/190.png) 

In Browser:

https://34.233.103.22:44301/sap/opu/odata4/sap/z_onlineshop_300/srvd_a2x/sap/zui_onlineshop_300/0001/onlineshop

![new_dd](images/200.png)  

## Summary   
You can continue with the next exercise - **[Build Exercise 1: Create Actions in SAP Build to access the Onlineshop API](../../../build/exercises/ex1/README.md)**
