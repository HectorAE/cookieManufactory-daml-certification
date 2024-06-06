# Cookie Manufactory: my Daml Fundamentals Certification capstone project

Written by Hector Escobedo.

## Overview

This project implements the simplified business logic of a cookie manufactory. Customers can request cookies of different flavors. A baker may accept the request and then create and "deliver" a cookie to that customer, making them the owner. The customer may then eat the cookie.

## Template workflow and design

Using a service pattern similar to the AirlineService in the Daml Fundamentals courses, the customer Party listed in a service contract may exercise a nonconsuming choice to create a new CookiesRequest. They may independently create as many as they wish by reusing the service, so long as the list of requested cookies is not identical to an existing order. For each CookiesRequest, the baker can either accept it and exercise BakeCookies to create one or more new Cookie contracts owned by the customer, or reject it by exercising TurnDown with an optional explanation of reason. The customer may also exercise consuming choice Cancel to archive the CookiesRequest before the baker does anything, with no other side effects. Once the customer finally has a baked Cookie contract, they can exercise Eat to print a descriptive string to the trace and archive the contract and end the workflow.

## How to build and test

`daml test` will run all included tests.

`daml start` will run basic setup, allowing you to interact with the ledger in Daml Navigator as different users.

## License

This project is free and open source software, licensed under the Apache License, Version 2.0; please see `LICENSE.txt` for the full terms.
