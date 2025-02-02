To get started with the YugaByte DB YSQL tutorial you'll need to complete the prerequisites below.

## Step 1: Download and Install YugaByte DB

The latest instructions on how to get up and running are on our Quickstart page here:

https://docs.yugabyte.com/latest/quick-start/

## Step 2: Download Northwind

The Northwind database is a sample database that was originally created by Microsoft and used as the basis for their tutorials in a variety of database products for decades. The Northwind database contains the sales data for a fictitious company called “Northwind Traders,” which imports and exports specialty foods from around the world.  The Northwind database is an excellent tutorial schema for a small-business ERP, with customers, orders, inventory, purchasing, suppliers, shipping, employees, and single-entry accounting. 

The dataset consists of 14 tables and the table relationships are showcased in the entity relationship diagram below:

![](https://static.packt-cdn.com/products/9781782170907/graphics/0907EN_02_09.jpg)

The dataset contains the following:

* **Suppliers:** Suppliers and vendors of Northwind
* **Customers:** Customers who buy products from Northwind
* **Employees:** Employee details of Northwind traders
* **Products:** Product information
* **Shippers:** The details of the shippers who ship the products from the traders to the end-customers
* **Orders** and **Order_Details:** Sales Order transactions taking place between the customers & the company

The Northwind database has since been ported to a variety of non-Microsoft databases including PostgreSQL. In this section we are going to walk you through how to install the PostgreSQL-compatible version of Northwind onto the YugaByte DB distributed SQL database.

You can download the Northwind database that is compatible with YugaByte DB from our GitHub repo. Here’s the two files you’ll need:

* [northwind_ddl.sql](https://raw.githubusercontent.com/YugaByte/yugabyte-db/master/sample/northwind_ddl.sql) which creates tables and other database objects
* [northwind_data.sql](https://raw.githubusercontent.com/YugaByte/yugabyte-db/master/sample/northwind_data.sql) which loads the sample data into Northwind

## Step 3: Enter the YSQL shell

Next run the ysqlsh command to enter the PostgreSQL shell.

```$ ./bin/ysqlsh  --echo-queries
ysqlsh (11.2)
Type "help" for help.
postgres=#
```

## Step 4: Create the Northwind Database

```
CREATE DATABASE northwind;
```

Confirm we have the Northwind database by listing out the databases on our cluster.

```
postgres=# \l
```

Switch to the Northwind database.

```
postgres=# \c northwind
You are now connected to database "northwind" as user "postgres".
northwind=# 
```

## Step 5: Build the Northwind Tables and Objects

```
northwind=# \i /Users/yugabyte/northwind_ddl.sql
```
We can verify that all 14 of our tables have been created by executing:

```
northwind=# \d
```

## Step 6: Load Sample Data into Northwind

Next, let’s load our database with sample data.

```
northwind=# \i /Users/yugabyte/northwind_data.sql
```

Let’s do a simple SELECT to pull data from the customers table to verify we now have some data to play with.

```
northwind=# SELECT * FROM customers LIMIT 2;
```

## Step 7: Get Started with the YSQL Tutorial

That’s it! You are ready to start the [YSQL Tutorial](https://github.com/YugaByte/yugabyte-db/wiki/YSQL-Tutorial:-Fundamentals).

_**Note:** These instructions last tested with YugaByte DB 1.3_