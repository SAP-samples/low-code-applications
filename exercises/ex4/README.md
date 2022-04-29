# Exercise 4 - Create a List Report UI Application based on Fiori elements

After the creation of the service with several entities, we will create a list report with an object page based on the Fiori elements technology.

Note that this will be a read only version of the application. For a list report that also allows the creation, editing and deletion of records, we need a so-called "draft enabled" service, which requires a slightly different service entity. 

Go back to the **Home** tab in the Application Studio. (Note: If you accidentally closed all the tabs you can find your "Home" tab by clicking on the "Project Explorer" icon on the left hand-side and click "Home".)

Add a new user interface

Now enter a display Name **My List Report** or another name of your liking. The **application name** should be defaulted with a technical version of your display name without spaces, add your user number **XXX** at the end of the application name, so it becomes **MyListReportXXX**, e.g. MyListReport001 if 001 is your user name. 

In the next step you can choose the technology you want to use to create your new UI app. You have a choice between "template based, responsive application" representing Fiori elements (FE) and "Mobile centric, freestyle application" representing the Mobile Development Kit (MDK). Choose template based, responsive application" on the left.

( Some background that you can choose to skip reading:
Both create responsive apps that can be used on mobile devices and on desktops, however it is fair to say that with FE users rather start with desktops and MDK apps rather with mobile. Both adhere to templates, however in the MDK case it is a copy template that can be changed in whatever way the user wants to. FE is more restricted with respect to changes to the template, however the resulting app always adheres to the newest Fiori guidelines and comes with a lot of functionality out of the box. )

Next up you have a choice of templates, choose the "List Report Object Page".

As a last step choose the (service) entity on which the new app should be created. Choose "CapexFlat".

And there you go, with just 4 steps you have created a complete UI app on top of your service entity. After some seconds you will see the new UI app showing up in the **User Interface** box on the **Home** tab. After some more seconds an editor pops up to the side which shows the pages that are generated for the UI app, the so-called page map.

![](/exercises/ex4/images/LCAP_46.png)

We now have a fully functional list report and and object page. Both pages are automatically populated with all the fields from our CapexFlat service entity apart from the ones that don't make sense: the ID field which contains a UUID is not included, as showing UUIDs to humans is not a good user experience.

If you are in a hurry or not interested in further details how to tweak the generated UI, you can skip the rest of this exercise and directly go to [Exercise 5](../ex5/README.md)

If you want to carry on here, edit "list Report" Page in the page map.

You can now see the details of this page. Expand the **Columns** under **Table** and see the properties of your service entity. Drag and drop the **firstname** and **lastname** fields from their position at the end to the top spots, so it looks like this:

![](/exercises/ex4/images/LCAP_48.png)

Now press **Page Map** on the upper part of the editor to be taken back to the page map. Now edit the **Object Page**. Expand the **Fields** under **Form** in the **General Information** section. Add a new section.

Choose **Form Section** and enter a new label **Requestor**

Now drag the **firstname** and **lastname** fields from their position in the form under **Fields** in the form of the new **Requestor** section

![](/exercises/ex4/images/LCAP_411.png)

Close the Page Editor and navigate back to "Home" tab.

## Summary
You have now added a new UI application to your project

Continue to - [Exercise 5](../ex5/README.md)
