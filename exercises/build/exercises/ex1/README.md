# Exercise 1: Create Actions in SAP Build to access the Onlineshop API

From this exercise on, we will switch to SAP's Business Technology Platform (BTP) on which SAP's solution for citizen developers, SAP Build run.

In this exercise we will create Actions in SAP Build that accesses the Onlineshop API on S/4 HANA from the previous chpater. There will be 2 actions, one to read all the onlineshop entries and another one that creates a new onlineshop entry. 

To create such Actions we need to prepare 2 things first:
- create a destination in BTP to create the secure connectivity from a BTP subaccount to the Onlineshop API on S/4 HANA from the previous chapters
- download the OData metadata document of the Onlineshop API from the previous chapter

## Exercise 1.1: Create a Destination in a BTP subaccount to access the Onlineshop API

We will now create the destination in a BTP subaccount to our Onlineshop API in the S/4 HANA system from the previous chapter. The destination will ensure secure connectivity.

1. In your ABAP Development Tools under **Business Services** -> **Service Bindings** -> **ZUI_ONLINESHOP_O4_###** copy the **Service URL**, it should be `/sap/opu/odata4/sap/zui_onlineshop_o4_###/srvd/sap/zui_onlineshop_###/0001/`

![serviceurl](images/105.png)

2. In a browser open the [destinations view in the BTP Cockpit](https://emea.cockpit.btp.cloud.sap/cockpit/#/globalaccount/47ae62c5-c35b-48a4-99b1-eee46b5b62bf/subaccount/f65e327c-d9e9-44cd-8d7b-e4e7ea8db474/destinations)

3. Press the `New Destination` button.

4. Fill in the following:

    |  Porperty   | Value |
    |  :------------- | :------------- |
    |  Name   | Onlineshop_### |
    |  Type   | HTTP |
    |  Description   | Onlineshop_### on S4H |
    |  URL   | http://s4h:443 + the copied Onlineshop URL (e.g. /sap/opu/odata4/sap/zui_onlineshop_o4_###/srvd/sap/zui_onlineshop_###/0001/) |
    |  Proxy Type   | OnPremise |
    |  Authentication   | BasicAuthentication |
    |  Location ID   | CALCC |
    |  User   | lowcode### |
    |  Password   | ######xx |

5. Then press the `New Property` button and add 
`sap.applicationdevelopment.actions.enabled` with value `true`

6. Press the `New Property` button again and add 
`sap.processautomation.enabled` with value `true`

![destination](images/100.png)

7. Press `Save`

8. Press `Check Connection`: You should get a pop up that says `Connection to "Onlineshop_###" successful`

## Exercise 1.2: Download the OData metadata document of the Onlineshop API

In this exercise we will download the OData metadata document to a file to later use it for a definiton of an Action for SAP Build.

1. In your ABAP Development Tools you should still have the service bidning ( under **Business Services** -> **Service Bindings** -> **ZUI_ONLINESHOP_O4_###** ) open , this time, click on **Service URL**:

![serviceurl](images/110.png)

2. A browser window opens. The URL will look like this: 

        https://YY.YYY.YYY.YY:44301/sap/opu/odata4/sap/zui_onlineshop_o4_300/srvd/sap/zui_onlineshop_300/0001/?sap-client=100 

    Delete the `?sap-client=100` at the end and instead add `$metadata`, so the URL looks like this:

        https://YY.YYY.YYY.YY:44301/sap/opu/odata4/sap/zui_onlineshop_o4_300/srvd/sap/zui_onlineshop_300/0001/$metadata

    Press `return` to load the metadata document

4. Right Mouse Click on the browser window and select `View Page Source` and press `Ctrl + A` + `Ctrl + C` (`Command + A` + `Command + C` on Mac) 

5. Open a text editor on your computer, paste the copied content using `Ctrl + V` (`Command + V` on Mac) and save the file as `Onlineshop_###_metadata.xml` to a location of your liking on your computer

## Exercise 1.3: Create Actions from the Onlineshop API

1. Open the [lobby](https://lcapteched.eu10.build.cloud.sap/lobby) in the browser with

        User: lowcodeuser+0###@gmail.com
    
        PW: XXXXXXX

    that is provided by the instructors by the workshop (note this is not the same user as for the ABAP development tools, it is a BTP user)

2. Press `Create`

![lobby](images/150.png)

3. Select `Build an Automated Process`

![lobby](images/155.png)

4. Select `Actions`

![lobby](images/160.png)

5. As Project Name choose `Onlineshop###Action`. Use the `Browse` button to locate the metadata file that you have saved in the previous step on your computer. Press `Create` 

6. Expand the entry `onlineshop` and select both, the `POST /onlineshop Add new entry to onlineshop` and the `Get /onlineshop Get entities from onlineshop`. Press `Add`

![lobby](images/165.png)

![lobby](images/170.png)

7. The 2 actions are now visible, select the `POST` one. In the right upper corner press the `Settings` button that looks like a gear wheel.

![lobby](images/175.png)

8. Sewitch `Enable CSRF` to `yes` and press `Save`

![lobby](images/180.png)

9. To test the action, select the destination that you have created before `Onlineshop_###`. In the input fields below, write `AS02` for the `product` and a number into the `quantity` field. Press `Test`.

![lobby](images/185.png)

![lobby](images/190.png)

10. The result should look like this:

![lobby](images/195.png)

3. 

## Exercise 1.4: Test Actions from the Onlineshop API