# MongoDB & Mongoose

[<- Go Back](buildingsite.md)

## What's a database?
* A **database** is an organized collection of data
* This data can be organized by any criteria
* Using a database we can read, create, update and delete data

### Database types
* Now a day we can find different types of databases that fulfill different projects needs
* We can split the big database family into two big categories: **Relational** or **No relational or NoSQL**
* The **Relational** are known as SQL databases (as they use SQL as query language)
* NoSQL databases are **No relational**
* Each database type will have pros and cons when reading, creating, updating or deleting values
* We need to choose the right database for our job and know why we're going to use it
* In this course section we'll learn MongoDB that's a NoSQL database

### Relational Databases assets
* [What is a Relational Database?](https://www.youtube.com/watch?v=iKK3P11OCyM)
* [Khan Academy - Intro to SQL: Querying and managing data](https://www.khanacademy.org/computing/computer-programming/sql)
* [SQL for Beginners. Learn basics of SQL in 1 Hour](https://www.youtube.com/watch?v=7Vtl2WggqOg)
* [W3 Schools](https://www.w3schools.com/sql/)

### NoSQL
* NoSQL (**N**ot **O**nly **SQL**) is the given name for databases that are not relationals
* In this database family we can find different types of databases like `key/value, document oriented, grapsh or big tables`
* All this databases are prepare to horizontaly scale (this means that we can add more databases servers if we need so)
* In some cases we can even use a simple computer (not much hardware) to solve a business problem
* Martin Fowler gave a great [Introduction to NoSQL talk](https://www.youtube.com/watch?v=qI_g07C_Q5I&t=340s) where he explains all this concepts
* This talk is a must to understand this subject
* Also, you can read on [his blog](https://martinfowler.com/nosql.html) about it

## MongoDB
* MongoDB is a NoSQL document oriented database
* This database a;low us to store data in JSON format
* It has a flexible schema, this means that we can change/update our documents structure whenever we need it
* This becomes helpful as we develop and we don't have the final data structure
* MongoDB also it's prepared to horizontal scale in a easy way
* As we learned JavaScript we'll use a database engine that allows us to keep on using this language to store our data

### Install MongoDB
* To use MongoDB locally we need to download & install it
* Open the documentation to [Install MongoDB Community Edition](https://docs.mongodb.com/v3.2/administration/install-community/) and choose your OS MongoDB version
  * [Windows](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/)
    * For Windows, execute the downloaded installer, follow all the default wizard steps and MongoDB will be installed on the following path `C:\Program Files\MongoDB\Server\3.4\.`
    * To be able to access MongoDB from anywhere in the terminal we need to configure our environments variables
      * [Windows 10 & 8](https://dangphongvanthanh.wordpress.com/2017/06/12/add-mongos-bin-folder-to-the-path-environment-variable)
      * [Windows 7](https://groups.google.com/forum/#!topic/mongodb-user/ct-GnmstUSE)
  * [Mac](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/)
    * For Mac, use [Homebrew](https://brew.sh/) to install MongoDB
  * [Linux](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-linux/)
