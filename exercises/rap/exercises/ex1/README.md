[Home ](../../README.md)  

# Exercise 1: Create an ABAP Package form the SAP Build Lobby

In this exercise, you will create an ABAP project from the Build Lobby

> **Reminder:**   
> Don't forget to replace all occurences of the placeholder **`###`** with your group ID in the exercise steps below.    
> If you don't have a group ID yet, please check with your instructor.    

## Exercise 1.1: Create Package with language version ABAP for Cloud Development


<!--
   
   1. In ADT, again the **Project Explorer** right-click on the package **`ZLOCAL`**, and select **New** > **ABAP Package** from the context menu. 

   ![package](images/220_create_package.png)

   
   2. Maintain the required information (`###` is your group ID):
       - Name: **`Z_ONLINESHOP_###`**
       - Description: _**`Online Shop ###`**_
       - Select the box **Add to favorites package**
       
      Click **Next >**.

   ![package](images/230_create_package.png).

-->

![lobby](images/Lobby.png)
![Wizard-App](images/Wizard-App.png)
![Wizard-Fullstack](images/Wizard-Fullstack.png)
![Wizard-ABAP](images/Wizard-ABAP.png)
![Wizard-Package](images/Wizard-Package.png)
![Wizard-Transport](images/Wizard-Transport.png)
![Wizard-Project](images/Wizard-Project.png)
![Wizard-Summary](images/Wizard-Summary.png)
![OpenEclipse](images/OpenEclipse.png)
![ADT-CommandCheck](images/ADT-CommandCheck.png)
![ADT-NewProjectCheck](images/ADT-NewProjectCheck.png)
![ADT-ServiceInstance](images/ADT-ServiceInstance.png)
![ADT-Logon](images/ADT-Logon.png)
![ADT_create_project](images/ADT_create_project.png)

![GenerateService](images/GenerateService.png)



![AddFavoritePackage](images/AddFavoritePackage.png)
![SelectPackage](images/SelectPackage.png)
![InitiateDBTable](images/InitiateDBTable.png)
![FIlterDatabase](images/FIlterDatabase.png)
![SpecifyDBTable](images/SpecifyDBTable.png)

![DBTransport](images/DBTransport.png)


zdbshopcartXXX where XXX is your group number

```CDS
@EndUserText.label : 'Shopping Cart Table'
@AbapCatalog.enhancement.category : #NOT_EXTENSIBLE
@AbapCatalog.tableCategory : #TRANSPARENT
@AbapCatalog.deliveryClass : #A
@AbapCatalog.dataMaintenance : #RESTRICTED
define table zdbshopcartXXX {

  key client              : abap.clnt not null;
  key order_uuid          : sysuuid_x16 not null;
  order_id                : abap.numc(8) not null;
  ordered_item            : abap.char(40) not null;
  order_quantity          : abap.numc(4);
  requested_delivery_date : abap.dats;
  @Semantics.amount.currencyCode : 'zdbshopcartXXX.currency'
  total_price             : abap.curr(11,2);
  currency                : abap.cuky;
  overall_status          : abap.char(30);
  sales_order_status      : abap.char(30);
  salesorder              : abap.char(10);
  bgpf_status             : abap.int1;
  bgpg_process_name       : abap.char(32);
  manage_sales_order_url  : abap.char(255);
  notes                   : abap.char(100);
  created_by              : abp_creation_user;
  created_at              : abp_creation_tstmpl;
  last_changed_by         : abp_lastchange_user;
  last_changed_at         : abp_lastchange_tstmpl;
  local_last_changed_at   : abp_locinst_lastchange_tstmpl;

}
```
![DBActivate](images/DBActivate.png)


![InitiateGenerateRAP](images/InitiateGenerateRAP.png)
![GenerateUIService](images/GenerateUIService.png)
![UIServiceName](images/UIServiceName.png)
![UIServiceAssets](images/UIServiceAssets.png)
![UIServiceGenerationPreview](images/UIServiceGenerationPreview.png)
![UIServiceTransport](images/UIServiceTransport.png)



![PublishRAPService](images/PublishRAPService.png)
![Preview](images/Preview.png)
![FEPreview](images/FEPreview.png)
![PreviewCreate](images/PreviewCreate.png)
![PreviewCreated](images/PreviewCreated.png)




![aaa](images/aaa.png)
![aaa](images/aaa.png)
![aaa](images/aaa.png)
![aaa](images/aaa.png)
![aaa](images/aaa.png)




