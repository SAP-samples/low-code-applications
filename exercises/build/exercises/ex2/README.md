# Exercise 2: Create a Process in SAP Build Process Automation based on the Onlineshop Service

In this chapter you will build a whole process in SAP Build Process Automation. It will contain a UI with a form with which users can create requests for products in our onlineshop. Depending on the quantity there will then be an approval step where a manager will have to approve or reject the onlineshop request. If the quantity is low, the request will automatically be approved. In case of an approval an action to create a new onlineshop entry based on the onlineshop service you have built in the S/4HANA system using ABAP Cloud. The result can then be seen in the Fiori elements preview application based on the onlineshop service.

Remember that whereever in this exercise you see `###` to replace it with your **group number** that was given to you by the instructors.

## Exercise 2.1: Create a new Process in SAP BUild Process Automation

You will create the project for a process.

1. Choose `Lobby`in SAP Build. Press `Create`. Select `Build and Automated Process` and then `Business Process`.

![lobby](images/100.png)

![lobby](images/110.png)

2. Choose `Onlineshop###Process` as your Project Name and press `Create`.

![lobby](images/120.png)

3. The process project is being created and your are prompted to create a process within this project. Choose `Onlineshop####` as a name, leave the identifier as suggested by the system.

![lobby](images/130.png)

## Exercise 2.2: Add a Form to the Process

You will create a UI form for the process, where users can request the order of a product with a quantitiy in the onlineshop.

1. On the canvas of the process, press `+` on the trigger step that the system has already generated for you. Choose `Formss` and `New Form`.

![lobby](images/140.png)

2. Choose `Onlineshop###Form` as a name and press `Create`.

![lobby](images/145.png)

The new form is now embedded into the trigger of the process.

3. On the form choose `Open Ediotr`.

![lobby](images/150.png)

You can now see a new canvas on which you can place a number of UI elements that make up your form. This is what users will see when they want to request a product in the onlineshop.

4. From the left side pane, choose `Headline 1` and drag it to the Canvas and drop it there. Write `Enter the product and the quantity that you want to order` into the headline. Now choose `Text` and drag and drop it to the canvas. Change the fields label to `Product`. Now choose `Number` and drag and drop it to the canvas. Change the fields label to `Quantity`. Finally, press `Save`.

![lobby](images/155.png)

## Exercise 2.3: Add an Approval step to the Process

![lobby](images/160.png)

![lobby](images/165.png)

![lobby](images/170.png)

![lobby](images/175.png)

![lobby](images/180.png)

![lobby](images/185.png)

![lobby](images/190.png)

![lobby](images/260.png)

![lobby](images/270.png)

![lobby](images/275.png)

![lobby](images/280.png)

![lobby](images/285.png)

![lobby](images/290.png)

![lobby](images/295.png)

![lobby](images/300.png)

![lobby](images/310.png)

![lobby](images/315.png)

![lobby](images/320.png)

![lobby](images/325.png)

![lobby](images/330.png)

![lobby](images/335.png)
