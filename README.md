# Campus-Eats-DB-Project <!-- omit in toc -->

Final project for ITCS 3160 at UNCC for David Benton, Andrew Quinn, Chris Donohue, Matthew Lewis, Hari Dhimal based on the Campus Eats system

## Table of Contents <!-- omit in toc -->

- [Introduction](#introduction)
- [Use Case for Rating System](#use-case-for-rating-system)
  - [Business Rules](#business-rules)
- [EERD](#eerd)
  - [EERD Narrative](#eerd-narrative)
- [MySQL Queries](#mysql-queries)
- [Stored Procedures](#stored-procedures)
- [Web/App Implementation or Description of Future Work](#webapp-implementation-or-description-of-future-work)
- [MySQL dump](#mysql-dump)
- [PPT Video](#ppt-video)

## Introduction

This project defines a database for managing a food ordering and delivery system for a University using a relational database. This database is based on work by Dhananjay Arora, Akshay Babu, Sumit Kawale, Prashant Madaan for an earlier semester of this class and is being used with permission. As part of this assignment, we are extending the model to include a rating system for the drivers and restaurants as well as creating business rules for the system. This rating system allows customers to leave ratings for both drivers and restaurants, look at the average ratings for specific drivers/restaurants, and review their order history along with the ratings they left with them.

## Use Case for Rating System

![Use Case Diagram For Campus Eats Database](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/images/CampusEats_UseCAse.jpg)

### Business Rules

1. The project illustrates the rating system of both deliver drivers and the restaurants
2. Our rating system captured under whole number (1-5)
3. Customers can rate the restaurant and/or driver for each order. 
4. Customers can access their own transaction information.
5. We will keep track of driver and the restaurant average rating for each month

## EERD

![EERD For Campus Eats Database](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/images/CampusEats_EERD.png)

The full data dictionary is available in [DB Data Dictionary.md](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/DB%20Data%20Dictionary.md)  
Screenshots of the data can be found here [Data Screenshots](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/Data%20Screenshots.md)

### EERD Narrative

This database is based on the relationships between each entity in the CampusEats system, specifically the relationships between drivers, restaurants, people, and their ratings. Each person may be a member of staff, faculty, or a student. People are allowed to rate both drivers and restaurants. These ratings are then associated with the individual drivers and restaurants. A person is also able to make orders. When a person places an order, it is associated with a particular delivery, as well as a driver, a location, and the restaurant that will prepare the order. This allows the system to identify who will deliver the order, where they will deliver it, who will be preparing it, as well as the delivery number with which it is associated. A vehicle is associated with each delivery as well, which identifies the vehicle that will be driven to deliver the order.

## MySQL Queries

We have created two views to make it easier for administrators to serve order history to customers and delivery history to drivers.

### Order History <!-- omit in toc -->

To find the order history, we access data from many tables. This allows us to show where the order was delivered to, the name of the driver that delivered it, the rating the customer has given the driver, the restaurant they ordered from, the rating they have given the restaurant, and the total cost of the order. This allows them to see the orders that the liked and the orders they didn't like allowing customers to make educated decissions as to where they would like to order from next. You can find a portion of the view's output in the [Data Screenshots](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/Data%20Screenshots.md) file.

When looking to optimize this query, we utilized the `EXPLAIN` command in MySQL. This allowed us to look at the execution plan for the query and enables us to find areas that could be sped up by creating a new index.

![EXPLAIN for Order History](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/images/explain_order_history.png#order_history-view)

In this case, there was not any performance to be gained by adding a new index as this query rellied on the indexes we had already created for the primary and foreign keys of our database. If we had decided to sort the view by a value other than the `person_id`, it may have been beneficial.

### Delivery History <!-- omit in toc -->

Much like the order history, the delivery history view required accessing many tables. We wanted to show the order id, the car they drove to deliver the meal, when they delivered it, the restaurant they delivered from, the total cost of the delivery, adn the rating they received for it. This allows drivers to see the work that they have done for this company. It can also help driver track their improvement, estimate their earnings, and understand what the most profitable restaurant to drive for is. A portion of the output for the view can be seen in the [Data Screenshots](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/Data%20Screenshots.md#deliver_history-view) file.

As with the first view, we looked to optimize this query. Instead of using the `EXPLAIN` command, we utilized the execution analysis tools that are built into MySQL Workbench. This allowed us to easily go between the results and the execution order to understand the choices the program was making.

![EXPLAIN for Delivery History](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/images/explain_delivery_history.png)

Again, since we were utilizing primary and foreign key columns to do the joining and sorting, we had already created indexes at the suggestion of MySQL Workbench. Since every step of the execution plan had an index associated with it, adding another index would have been detrimental.

## Stored Procedures

### Driver Rating <!-- omit in toc -->

Our first stored procedure takes a driver ID as input and calculates their average rating based on the number of stars they have received. Below is an example with a driver_id of 1:

![Driver Rating Example](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/images/stored_driver_rating.png)

### Restaurant Rating <!-- omit in toc -->

The second stored procedure is much like the first. It takes a restaurant ID and calculates their average rating based on the  number of stars.

![Restaurant Rating Example](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/images/stored_restaurant_rating.png)

These procedures allow an application to interface with the program by requesting the rating of a specific driver or restaurant to help users choose where they plan to order food from. The driver ratings could potentially be used to identify the performance of a driver and determine if there should be disciplinary action or commendations for the driver.

## Web/App Implementation or Description of Future Work

Above, we have described several use cases for our views and stored procedures. If we create a customer facing interface in the future, there are a couple more things we would want to have. To start out, we would want a stored procedure for creating a rating for orders. This would make it easy to add new ratings as there would be no need to write SQL code, you would only need to call the procedure with the required parameters. We would also want functionality to allow customers to request their order history. We would simply use the view we have written for it and use a `WHERE` clause to show the customer only the orders that they were involved in. A similar process would be done for the drivers. Our current stored procedures would be used as described in their respective sections.

## MySQL dump

The current dump of the database is located in the [DB Dump](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/db%20code/DB%20Dumb%2012102020.sql) file. This file contains the database schema, the create statements, insert statements, and the SQL code for the stored procedures and views.

## PPT Video
