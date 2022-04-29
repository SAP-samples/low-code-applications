# Exercise 5 - Preview your service and application

We now have a running service and a UI application on top of it, we can now preview both without having to deploy to the cloud. Actually, we could have done that already earlier, at the point where we had created the service. However, to save some time, we are only doing it here to preview all that we have done so far in one go.

On the **Home** screen you find a **Preview** button in the upper right corner. Choose the **With Sample Data** option.

A **Task Preview** tab will pop up in the lower part of the screen preparing the preview. After a couple of seconds a new browser tab will be opened and you will see a screen like this:

![](/exercises/ex5/images/LCAP_52.png)  

( If you don't get a new tab, please check whether there is a blocker running in your browser. If so, please allow the domain of the Business Application Studio to open a new tab )

From here you can navigate to the various artifacts of your project. You can see to all things concerning the service on the right, for example to the metadata resource of your API and check out the three service entities we created and populated already with sample data.

Click on the highlighted button next to "Capex" to open the API which provides the list of Capex entires in your database in a new browser tab. The data is queried and exposed using OData V4. Please note that this service is run from an in-memory database that is automatically spun up for you during the preview, so any modification to the data will not persisted.

![](/exercises/ex5/images/LCAP_53.png)  

Now switch back to the Application Preview tab and press on the "My List Report" tile. A new browser tab will be opened and it contains our Fiori elements list report application. Press on the **Go** button on the right and you should see a list like this:

![](/exercises/ex5/images/LCAP_54.png)  

If you press on one of the entries in the list, you will be taken to the corresponding object page. If you have followed all the steps in the previous exercise it looks like this, it has 2 sections. If you skipped the last part it will look slightly different but all fields are present:

![](/exercises/ex5/images/LCAP_55.png)  

Now switch back to the Application Preview tab. If you now were to do any changes in your project, service or UI application, the preview would automatically be updated, including the UI application

## Summary
We have now previewed our new application without any deployment.

Continue to - [Exercise 6](../ex6/README.md)
