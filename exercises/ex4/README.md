# Exercise 4 - Create a List Report UI Application based on Fiori elements

After the creation of the service with several entities, we will create a list report with an object page based on the Fiori elements technology.

## Create a new UI Application

Go back to the **Home** tab in the Application Studio. (Note: If you accidentally closed all the tabs you can find your **Home** tab by clicking on the **Project Explorer** icon on the left hand-side and click **Home**.)

Press **+**  under **User interfaces**

![](/exercises/ex4/images/LCAP_41.png)

Now enter a display Name **My List Report** or another name of your liking. The **application name** should be defaulted with a technical version of your display name without spaces, so it becomes for example **MyListReport**.

![](/exercises/ex4/images/LCAP_42.png)

In the next step you can choose the technology you want to use to create your new UI app. You have a choice between "template based, responsive application" representing Fiori elements (FE) and "Mobile centric, freestyle application" representing the Mobile Development Kit (MDK). Choose **Template based, responsive application** on the left.

![](/exercises/ex4/images/LCAP_43.png)

Some background that you can choose to skip reading:
Both create responsive apps that can be used on mobile devices and on desktops, however it is fair to say that with FE users rather start with desktops and MDK apps rather with mobile. Both adhere to templates, however in the MDK case it is a copy template that can be changed in whatever way the user wants to. FE is more restricted with respect to changes to the template, however the resulting app always adheres to the newest Fiori guidelines and comes with a lot of functionality out of the box.

**Press Next**

Next up you have a choice of templates, choose the **List Report Object Page**.

![](/exercises/ex4/images/LCAP_44.png)

As a last step choose the (service) entity on which the new app should be created. Choose **Capex**.

![](/exercises/ex4/images/LCAP_45.png)

And there you go, with just 4 steps you have created a complete UI app on top of your service entity. After some seconds you will see the new UI app showing up in the **User Interface** box on the **Home** tab. After some more seconds an editor pops up to the side which shows the pages that are generated for the UI app, the so-called page map.

![](/exercises/ex4/images/LCAP_46.png)

We now have a fully functional list report and and object page. Both pages are automatically populated with all the fields from our CapexFlat service entity apart from the ones that don't make sense: the ID field which contains a UUID is not included, as showing UUIDs to humans is not a good user experience.

While we could now already start testing our UI application and would get a nice application, we will optimize the UI at a couple of places.

## Adjust the List Page of your UI Application

Click **list Report** Page in the page map.

![](/exercises/ex4/images/LCAP_47.png)

You can now see the details of this page. Expand the **Columns** under **Table** and see the properties of your service entity. Drag and drop the **firstname** and **lastname** fields from their position at the end to the top spots, so it looks like this:

![](/exercises/ex4/images/LCAP_48.png)

We will now add more columns for our list than were generated. We will add the associations to the business partner and the category. For this hover the **Columns** entry with your mouse, a **+** sign will come up on the right. Press it and select **Add Basic Columns**

![](/exercises/ex4/images/LCAP_48_2.png)

In the dialog's dropdown that now shows up select the **BusinessPartner** property and the **name** of the **category**, then close the dropdown and press **Add**. This will close the dialog and add the 2 new columns to the list

![](/exercises/ex4/images/LCAP_48_3.png)

## Adjust the Object Page of your UI Application and add Value Helps

Now press **Page Map** on the upper part of the editor to be taken back to the page map. Now edit the **Object Page**. Expand the **Fields** under **Form** in the **General Information** section. You can now see all the properties that were automaticlly added to the form. 

For both, the associtation properties for the categoy and the business partner, we now want to change the label and enable value helps for them. 

To do this, first select property **category_id**, then in the panel that opens on the right, under **Label** change the text to **category**. Then below under **Display Type** select **Value Help**

![](/exercises/ex4/images/LCAP_49.png)

On the dialog, choose **name** for **Value Description Property** and then under **Text Arrangement** choose **Text Only**. Leave the **Display as Dropdown** option switched on and press **Apply**

![](/exercises/ex4/images/LCAP_49_2.png)

With this we have chosen to make to category field a dropdown (because it has a small number of entries the list doesn't get too long), to only show the name of the category and not its id. With the **Text Arrangement** option it would have been possible to also show its id in different orders of name and id.

After you have closed the dialog, still on the panel under **Text** select **category/name**. This makes sure that not only the list in the dropdown only shows the name and not an id but also in the field when an entry was selected.

Now we will also carry out similar steps for the Business Partner. Only this time we will create a full blown value help instead of a dropdown because we expect the list of business partners from the backend to be too huge to handle in a dropdown.

Select property **BusinessPartner_BusinessPartner**, then in the panel on the right, under **Label** change the text to **BusinessPartner**. Then below under **Display Type** select **Value Help** again.

On the dialog, switch the **Display as Dropdown** option off, then press **Add Cokumn** and select **FirstName**. Then do the same and add **LastName**. Finally press **Apply**

![](/exercises/ex4/images/LCAP_49_3.png)

Let's finally do some rearrangement of the page. In it's current stage all the fields are displayed in one section. Let's nor create a second one and move the first and last name of the requestor for Capex into it.

Go to the **Sections** entry and press the **+** button on the right to add a new section.

Choose **Form Section** and enter a new label **Requestor**

![](/exercises/ex4/images/LCAP_410.png)

Now drag the **firstname** and **lastname** fields from their position in the form under **Fields** in the form of the new **Requestor** section

![](/exercises/ex4/images/LCAP_411.png)

Close the Page Editor and navigate back to **Home** tab.

## Summary
You have now added a new UI application to your project

Continue to - [Exercise 5](../ex5/README.md)
