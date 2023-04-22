# Exercise 5 - Preview your service and application

We now have a running service and a UI application on top of it, we can now preview both without having to deploy to the cloud. Actually, we could have done that already earlier, at the point where we had created the service. However, to save some time, we are only doing it here to preview all that we have done so far in one go.

## Preview with Sample Data

On the **Home** screen you find a **Preview** button in the upper right corner. There are 2 options: **With Sample Data** and **With Live Data**. We will try both of them out. 

First we will choose **With Sample Data**. This option only uses the sample data that we have created in an earlier setp. It uses this sample data for the category as well as for the business partner. Remember the business partner comes with automatic connectivity to an S/4 HANA Cloud system and data for the service could retreived from there as well. With the sample option however, the data is served from our local business partner data that we generated.

![](/exercises/ex5/images/LCAP_51.png)  

A **Task Preview** tab will pop up in the lower part of the screen preparing the preview. After a couple of seconds a new browser tab will be opened and you will see a screen like this:

![](/exercises/ex5/images/LCAP_52.png)  

( If you don't get a new tab, please check whether there is a blocker running in your browser. If so, please allow the domain of the Business Application Studio to open a new tab )

From here you can navigate to the various artifacts of your project. You can see to all things concerning the service on the right, for example to the metadata resource of your API and check out the three service entities we created and of which we alread populated two with sample data.

Click on the button next to **Categroies** to open the API which provides the list of Capex entires in your database in a new browser tab. 

![](/exercises/ex5/images/LCAP_52_2.png) 

The data is queried and exposed using OData V4. Please note that this service is run from an in-memory database that is automatically spun up for you during the preview, so any modification to the data will not persisted.

Now do the same for **A_BusinessPartner**. This will show you something like this:

![](/exercises/ex5/images/LCAP_53.png)  

The data might not be formatted in such a nice way as you can see it on the above picture where a browser plug in formatted it. However, you will essentially see a similar JSON structure and the data in it reflects what we had generated as sample data for the business partner. The JSON adheres to the OData V4 specification.

Now switch back to the Application Preview tab and press on the **My List Report** tile. A new browser tab will be opened and it contains our Fiori elements list report application. It will look like this:

![](/exercises/ex5/images/LCAP_54.png)  

There are no entries in this list as we have neither provided sample data for the capex entity, not have we created any data ourselves yet. Let's change that. Press the **Create** button on the upper right above the empty list.

You will then see the form as we created it, it has 2 sections, a dropdown for the categories and a value help for the business partner. Check the dropdown for its contents and select an entry:

![](/exercises/ex5/images/LCAP_55.png) 

Now also press the value help for the business partner. It will show you the 3 generated entries from the sample data:

![](/exercises/ex5/images/LCAP_56.png) 

Again pick one of them. Then back in the form enter some data for the other fields like **firstname** and **lastname**, **totalcost** and **description**.

Notice how it says "Draft saved" in the bottom right corner of the screen everytime you have entered a value in one of the fields. As stated before, the data that is entered by you will be persisted in a draft which is only available to you and noone else until you finally press **Create** which will only save your data as a real object only when all the validations are without errors and all the mandatory values have been provided.
 
![](/exercises/ex5/images/LCAP_57.png) 

Now press the **<** button in the upper left corner of the screen next to the SAP sign. This will take you back to the list page. Press **Go** and you should see the entry that you just created.

![](/exercises/ex5/images/LCAP_58.png) 

## Preview with Live Data

Now switch back to the tab that has the Business Application Studio with your project. We will now look at the second version of the preview which uses the live data. This time for the business partner the data is actually fetched from the S/4 HANA Cloud system instead from the sample data. For the categories though, where there is no backend connection still the sample data will be shown.

To get there first press the **Stop Preview** button. 

![](/exercises/ex5/images/LCAP_59.png) 

The button changes to become a **Preview** button. This time select the **With Live Data** option. After some seconds again the **Application Development Preview Page** comes up and looks like the one before. However if you again press the rightmost button next to **A_BusinessPartner** you will get a lot more data than before, it is the real business partner data from the S/4 backend:

![](/exercises/ex5/images/LCAP_510.png) 

Similarly if you follow all the steps in your **My List Report** application like before you will get the backend data in the buisness partner value help:

![](/exercises/ex5/images/LCAP_511.png) 

You can play around with the already built in filters for the data as well.

## Summary
We have now previewed our new application without any deployment.

Continue to - [Exercise 6](../ex6/README.md)
