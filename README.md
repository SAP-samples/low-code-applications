# Create an Extension with SAP Build containing the BTP ABAP Environment and SAP Build Process Automation

## Description

This repository contains the material for the workshop "Create an Extension with SAP Build containing the BTP ABAP Environment and SAP Build Process Automations"  
We will create a new service using the ABAP RESTful Application Programming Model (RAP) using the ABAP Cloud Programming Model on a BTP ABAP Environment and then create a process using SAP Build Process, both on the SAP Business Technology Platform (BTP). 

## Overview

This session covers the basic app development steps using the ABAP Development Tools (ADT) to create a new OData service based on the ABAP RESTful Application Programming Model (RAP) on the BTP ABAP Environment. This service will then be used in a new process that will be created using SAP Build Process Automation that runs on the SAP Business Technology Platfrom (BTP). You will learn how this kind of Fusion Development, i.e. creating extensions that are based on different technologies and / or use different tools, creates an overall Extension Solution.  

## The use case

The goal is to create a UI from which a user can order a product with a quantity. This request for an order will go through an approval of an entitled person. If the order request is approved, a new shopping cart object is created for the order and this in turn creates a sales order in S/4HANA.

In order to achieve this goal, there are several steps involved:
- you will create a new OData service on the BTP ABAP environment for the shopping cart.
- you will create a process with a start UI for ordering the product, an approval step and an action which triggers a call of the shopping cart OData request in order to create a new shopping cart

## Requirements

To carry out the exercises of this repository, you need to
- install the ABAP Development Tools (ADT) for the ABAP development parts
- have a browser ready, preferably Google Chrome, to access the SAP Build

The users for the development environment during the course are email addresses which are provided to you by the hosts.

Go to [Getting Started - Preparation](exercises/ex0/README.md) to find out the installation details, URLs, then start with the first exercise.

## Exercises

- [Getting Started - Preparation](exercises/ex0/README.md)
- [Part 1 - ABAP Cloud based RAP OData Service BTP ABAP Environment ](exercises/rap/README.md)
- [Part 2 - SAP Build Process Automantion](exercises/build/exercises/ex2/README.md)

Start the exercises [here](exercises/rap/exercises/ex1/README.md).
 
## How to obtain support!

Support for the content in this repository is available during the actual time of the session by the hosts. 

## Contributing
If you want to contribute, please check the [CONTRIBUTING.md](CONTRIBUTING.md) documentation for contribution guidelines.

## Code of conduct

SAP adopts the Contributor's Covenant 2.0 across our open source projects to ensure a welcoming and open culture for everyone involved ([Code of Conduct](CODE_OF_CONDUCT.md)).

## License
Copyright (c) 2025 SAP SE or an SAP affiliate company. All rights reserved. This project is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSES/Apache-2.0.txt) file.
