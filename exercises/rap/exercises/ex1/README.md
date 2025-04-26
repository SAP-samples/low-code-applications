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

1. Open the lobby https://lcapteched.eu10.build.cloud.sap/lobby 
   
   Use the user that the instructors have given you and which contains the three digit group number. The password has also been given to you by the instructors

   In the Lobby press the *Create* button and choose *Create*

   ![lobby](images/Lobby.png)

2. In the wizard that comes up, choose the *Application* Tile and press *Next*

   ![Wizard-App](images/Wizard-App.png)

3. On the next step of the wizard choose *Full Stack*

   ![Wizard-Fullstack](images/Wizard-Fullstack.png)

4. On the next step choose *Full Stack ABAP* and press *Next*

   ![Wizard-ABAP](images/Wizard-ABAP.png)

5. Now select the system *H1* and under *Package* select *New* to create a new package. Type *ZLCOAL* as a superpackage and *ZSHOPPINGCARTXXX* as the name for your package. *XXX* needs to be replaced by your group number. Type in a description for you package, e.g. *Shopping Cart for User XXX*. Press *Next*.

   ![Wizard-Package](images/Wizard-Package.png)

6. Select *Create new transport request* and provide a description like *ShoppingCartXXX*, where *XXX* again is you shopping cart number. Press *Next*

   ![Wizard-Transport](images/Wizard-Transport.png)

7. Provide a name for your project *ShoppingCartXXX*, where XXX is replaced by your group number.

   ![Wizard-Project](images/Wizard-Project.png)

8. In the Summary you can review all you choices. Press *Create* if everything is fine.

   ![Wizard-Summary](images/Wizard-Summary.png)

The following points 9. - 11. might or might not pop up after you pressed create. This very much depends on whether Eclipse has been opened before and what happened for your user. Don't worry if any of these pop ups come up and you immediately are at step 12., this is fine.

9. Possibly your browser now asks whether Eclipse should be openend. If it does press *Open Eclipse*. The ABAP Development Tools, which are based on Elipse should bow be openend.

   ![OpenEclipse](images/OpenEclipse.png)

10. Possibly you are now asked whether a command shoud be executed. if this happens, press *OK*

   ![ADT-CommandCheck](images/ADT-CommandCheck.png)

11. Possibly you are asked whether you want to open an existing project or create a new one. Choose *Create a new project from the link* 

   ![ADT-NewProjectCheck](images/ADT-NewProjectCheck.png)

12. In this step, your new ABAP project is connected to your BTP ABAP Environment instance. The ABAP Service Instance Service URL should already be prefilled 

   ![ADT-ServiceInstance](images/ADT-ServiceInstance.png)

13. To log on press *Open Logon Page in Browser*. This will open a browser tab and after a couple of seconds it should say that you are logged on. Back in the ABAP Development tools you should then see the next wizard step already.

   ![ADT-Logon](images/ADT-Logon.png)

14. In this step you finalize the connection. You can take over the project name that is suggested to you and press *Finish*

   ![ADT_create_project](images/ADT_create_project.png)

15. In this next step you could already create a new ABAP Restful Programming Model (RAP) service. However, in order to do so, you would need to base it on something, e.g. a data base table. In our case we don't have such a base yet, we need to first create it. Therefore, press *Cancel* to terminate this step

   ![GenerateService](images/GenerateService.png)

16. On the left hand side in the *Project Explorer* add your new package to the *Favorite Packages* section. In order to do so, select *Favorite Packages* and press the right mouse button. In the menu select *Add package*

   ![AddFavoritePackage](images/AddFavoritePackage.png)

17. Start typing *ZSHOP* and in the list of packages that comes up, choose the one that you just created, with XXX as your group number

   ![SelectPackage](images/SelectPackage.png)

18. Select this package in the tree in the project explorer. Once again invoke the right mouse button and choose *New->Other ABAP Repository Objec*

   ![InitiateDBTable](images/InitiateDBTable.png)

19. Type *database" to filter and then select *Database Table* and press *Next*

   ![FIlterDatabase](images/FIlterDatabase.png)

20. Provide the name *ZDBSHOPCARTXXX* with XXX being your group number for the database table. Choose a description for your table. Then press *Next*    

   ![SpecifyDBTable](images/SpecifyDBTable.png)

21. Choose the tranport that you have already created and select it. Press *Finish*

   ![DBTransport](images/DBTransport.png)

22. As a result a new editor is opened, it already contains a stub for your new database table which represents shopping cart data. Now let's add some properties to your table. Copy the below properties. Make sure that you replace the XXX with your group number

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

23. Save and activate your chenages, press the according button.

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




