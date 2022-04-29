# Accelerate Application Development with Low-Code in the SAP Business Application Studio

## Description

This repository contains the material for the workshop "Accelerate Application Development with Low-Code in the SAP Business Application Studio".  
We will create an application with the new Low-Code perspective of the SAP Business Application Studio. 

## Overview

This session covers the basic app development steps using the SAP Business Application Studio perspective for Low-Code development in order to create a new application which is based on the backend on SAP's Cloud Application Programming Model (CAP) and on the frontend on SAP Fiori elements which in turn builds on SAP UI5. The application is deployed to the Business Technology Platform (BTP). 

## The use case

In this session we will enable of Capital Expenditures (CAPEX) process. Capital expenditures have a deep effect on the Profit & Loss balance sheet of a company.
CAPEX is about providing budget for buying & maintaining fixed / integral assets (FA/IA). 
CAPEX cost also includes upgrades or repairs of assets to improve the life span of “useful assets” (e.g. vehicles, laptops, phones).

So, normally users would register for such an expenditure by filling out and submitting a form with the details for the intended purchase or the repairs and the expected costs. 
This will then start a workflow where a manager can decide to approve or reject the CAPEX request. This is what we will develop in this session.

To achieve this, we will create a new backend service using the Cloud Application Programming Model (CAP), and a web application based on Fiori elements with which users can create CAPEX requests as well as list all the CAPEX requests. Other parts of the process, a workflow for the approval process including a task UI based on the Mobile Development Kit (MDK) are not in the scope of this tuorial for time reasons, but it can be done with LCAP in Business Application Studio as well.

## Requirements

The local requirement is to preferably use the Google Chrome browser to access the SAP Business Application Studio. 

The users for the development environment during the course are email addresses which are provided to you by the hosts.

## Exercises

The exercises are divided into two parts. In part one we use the new Low-Code perspecitive in the Buesiness Application Studio to create an API service including persistence on SAP BTP. This includes already some applications using Fiori Elements. In part two, we will create a mobile app using SAP AppGyver.

### Part 1: Create a backend service and a list report UI in Business Application Studio
- [Getting Started - Preparation Part 1](exercises/ex0/README.md)
- [Exercise 1 - Create a data model with the SAP Business Application Studio ](exercises/ex1/README.md)
- [Exercise 2 - Add some sample data ](exercises/ex2/README.md)
- [Exercise 3 - Create a service ](exercises/ex3/README.md)
- [Exercise 4 - Create a List Report UI Application ](exercises/ex4/README.md)
- [Exercise 5 - Preview your service and application ](exercises/ex5/README.md)

### Part 2: Deploy and use your application on SAP's Business Technology Platform
- [Exercise 6 - Deploy your service and application ](exercises/ex6/README.md)
- [Exercise H — Test the app and the scenario](exercises/exH/README.md)

Start the exercises [here](exercises/ex0/README.md).

## How to obtain support

Support for the content in this repository is available during the actual time of the session by the hosts. 

## License
Copyright (c) 2022 SAP SE or an SAP affiliate company. All rights reserved. This project is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSES/Apache-2.0.txt) file.
