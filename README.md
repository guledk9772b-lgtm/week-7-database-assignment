# Week 7 Assignment: Database Design and Normalization

## Overview
This repository contains SQL solutions for **Week 7: Database Design and Normalization**. The goal of this assignment is to eliminate data redundancy and improve data integrity by transforming unnormalized and partially normalized tables into **First Normal Form (1NF)** and **Second Normal Form (2NF)**.

## Repository Structure
* `answer.sql` — Contains the SQL DDL and DML statements (`CREATE TABLE` and `INSERT INTO`) for Questions 1 and 2.
* `README.md` — Documentation summarizing the normalization steps and schema design.

## Solutions Summary

### Question 1: Achieving First Normal Form (1NF)
* **Problem:** The `ProductDetail` table violated 1NF because the `Products` column stored multiple comma-separated values in a single cell.
* **Solution:** Created `ProductDetail_1NF` with atomic values so each row represents a single product per order, defined with a composite primary key `(OrderID, Product)`.

### Question 2: Achieving Second Normal Form (2NF)
* **Problem:** In `OrderDetails`, `CustomerName` depended only on `OrderID` rather than the full composite primary key `(OrderID, Product)`, creating a partial dependency (`OrderID -> CustomerName`).
* **Solution:** Decomposed the table into two relations:
  * **`Orders`** (`OrderID` PK, `CustomerName`) — Stores order-level customer details.
  * **`OrderItems`** (`OrderID`, `Product` Composite PK, `Quantity`) — Stores line-item product quantities and references `Orders(OrderID)` via a foreign key.

## How to Run
1. Open **MySQL Workbench** (or any SQL client) and connect to your database server.
2. Select or create a target database schema (e.g., `CREATE DATABASE normalization_db; USE normalization_db;`).
3. Open `answer.sql` and execute the script.
