# Campus-Eats-DB-Project <!-- omit in toc -->

Final project for ITCS 3160 at UNCC for David Benton, Andrew Quinn, Chris Donohue, Matthew Lewis, Hari Dhimal based on the Campus Eats system

## Table of Contents <!-- omit in toc -->

- [Introduction](#introduction)
- [Use Case for Rating System](#use-case-for-rating-system)
- [EERD](#eerd)
- [MySQL Queries](#mysql-queries)
- [Stored Procedures](#stored-procedures)
- [Web/App Implementation or Description of Future Work](#webapp-implementation-or-description-of-future-work)
- [MySQL dump](#mysql-dump)
- [PPT Video](#ppt-video)

## Introduction

This project defines a database for managing a food ordering and delivery system for a University. This database is based on work by Dhananjay Arora, Akshay Babu, Sumit Kawale, Prashant Madaan for an earlier semester of this class and is being used with permission. As part of this assignment, we are extending the model to include a rating system for the drivers and restaurants. 

## Use Case for Rating System

![Use Case Diagram For Campus Eats Database](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/images/CampusEats_UseCAse.jpg)

### Business Rules

1)    The project illustrates the rating system of both deliver drivers and the restaurants
2)    Our rating system captured under whole number (1-5)
3)    Customers can rate the restaurant and/or driver for each order. 
4)    Customers can access their own transaction information.
5)    We will keep track of driver and the restaurant average rating for each month

## EERD

![EERD For Campus Eats Database](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/images/CampusEats_EERD.png)

The full data dictionary is available in [DB Data Dictionary.md](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/DB%20Data%20Dictionary.md)  
Screenshots of the data can be found here [Data Screenshots](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/Data%20Screenshots.md)

### EERD Narrative:
This database is based on the relationships between each entity in the CampusEats system, specifically the relationships between drivers, restaurants, people, and their ratings. Each person may be a member of staff, faculty, or a student. People are allowed to rate both drivers and restaurants. These ratings are then associated with the individual drivers and restaurants. A person is also able to make orders. When a person places an order, it is associated with a particular delivery, as well as a driver, a location, and the restaurant that will prepare the order. This allows the system to identify who will deliver the order, where they will deliver it, who will be preparing it, as well as the delivery number with which it is associated. A vehicle is associated with each delivery as well, which identifies the vehicle that will be driven to deliver the order.

## MySQL Queries

## Stored Procedures

## Web/App Implementation or Description of Future Work

## MySQL dump

The current dump of the database is located in the [DB Dump](https://github.com/bentondavidl/Campus-Eats-DB-Project/blob/main/db%20code/DB%20Dumb%2012012020.sql) file.

## PPT Video
