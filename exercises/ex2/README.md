# Exercise 2 - Add some sample data

We will now populate our data model with some sample data so that we can test our service. Note, that even though it says sample data, the data can be of two types:
- fixed values that are part of you application and should be deployed along with the application. An example could be the data for **Category** if there is only a fixed set of categories that cannot be changed
- sample data that is really only used to test the services and applications that you create and that should not be part of a productive deployment

On the "Home" screen add **Sample Data**. Choose "Create" and "Category".

An editor will appear. Change the **Mock Data** switch to **Off** and enter 3 as the number of rows. 

Now enter the following data:

| ID | Name |
| ----------- | ----------- |
| 1 | Office Supplies | 
| 2 | Computers |
| 3 | Monitors |

![](/exercises/ex2/images/LCAP_22.png)  

Now return to the **Home** tab and add some more sample. This time choose "Create" and "Capex"

This time change the **Mock Data** switch to **On** and enter 3 as the number of rows.  Now there are 3 entries created and the data with it, you should see something like this:

![](/exercises/ex2/images/LCAP_23.png)  

Note how the ID field this time is a read only field. This is because it is of type UUID and noone can bexpected to create or change such an ID, the system will always generate it for you.

You can now leave the data like it is or overwrite it with some nice values and make use of some more built in functionality of the sample data editor:

| ID | DESCRIPTION | COSTCENTER | TOTALCOST | FIRSTNAME | LASTNAME | CATEGORY_ID |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| < generated number > | Office Chairs | 10010 | 3000 | Tom | Teller | 1 |
| < generated number > | Notebooks | 10020 | 15000 | Fred | Fresh | 2 |
| < generated number > | 27 inch Flatscreens | 10031 | 5000 | Greg | Guang | 3 |

Note how in the **CATEGORY_ID** fields there is a value help that shows you all the categories that you have maintained before:

![](/exercises/ex2/images/LCAP_24.png)  

We have now added all the sample data

## Summary

We have now added some sample data to both data models that we can later use to test the service we are going to create.

Continue to - [Exercise 3](../ex3/README.md)
