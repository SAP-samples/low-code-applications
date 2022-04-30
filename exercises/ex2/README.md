# Exercise 2 - Add some sample data

We will now populate our data model with some sample data so that we can test our service. Note, that even though it says sample data, the data can be of two types:
- fixed values that are part of you application and should be deployed along with the application. An example could be the data for **Category** if there is only a fixed set of categories that cannot be changed
- sample data that is really only used to test the services and applications that you create and that should not be part of a productive deployment

On the **Home** screen add **Sample Data**. Choose **Create** and **Category**.

An editor will appear. Change the **Mock Data** switch to **Off** and enter 3 as the number of rows. 

Now enter the following data:

| ID | Name |
| ----------- | ----------- |
| 1 | Office Supplies | 
| 2 | Computers |
| 3 | Monitors |

![](/exercises/ex2/images/LCAP_22.png)  

Now return to the **Home** tab and add some more sample. This time choose **Create** and **API_Business_Partner.A_BusinessPartner**

This time change the **Mock Data** switch to **On** and enter 3 as the number of rows.  Now there are 3 entries created and the data with it, you should see something like this:

![](/exercises/ex2/images/LCAP_23.png)  

With respect to the Business Partner we have a special situation: It gets its data from the S/4 HANA Cloud system. So we would not need to have sample data even for testing later, we could get data even for testing from the backend, the set up automatically created the connnectivity to the backend. Indeed, when it comes to testing, there will be 2 options, either use the backend ("live") data or the sample data. The latter comes in handy during development when one does not want to get to the backend each time and play around with data.

We have now added the sample data that we need. We could have of course also added sample data for the Capex entity as well, but in this project we rather create its data with the resulting application.

## Summary

We have now added some sample data to two data models that we can later use to test the service we are going to create.

Continue to - [Exercise 3](../ex3/README.md)
