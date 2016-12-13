# simple-sql-queries

For today we will be practicing inserting and querying data using SQL.

Here is a website that will let us write queries to interact with some data.  [http://jxs.me/chinook-web/](http://jxs.me/chinook-web/)

On the left are the Tables with their fields.  The right is where we will be writing our queries.  The bottom is where we will see our results.  

Any new tables or records that we add into the database will be removed after you refresh the page.  So if you're wondering where you data went, that may be why.

Use [www.sqlteaching.com](http://www.sqlteaching.com/) or [sqlbolt.com](http://sqlbolt.com/) as resources for the missing keywords you'll need.

## PERSON
1. Create a table called Person that records a person's Name, Age, Height, City, FavoriteColor, and Id.  Id should be an auto-incrementing id/primary key.  
2. Add 5 different people into the Person database.  Remember to not include the Id because it should auto-increment.
3. List the people in the Person table by Height from tallest to shortest (descending)

 CREATE TABLE person
(name VARCHAR(30),
 age INTEGER(2),
 height	DECIMAL(3,2),
 city VARCHAR(30),
 favoriteColor	VARCHAR(30),
 id integer primary key
);
  *INSERT INTO person (name, age, height,city,favoriteColor) VALUES ('Gabe Aboy', 23, 6.23,'Miami','Blue');
   INSERT INTO person (name, age, height,city,favoriteColor) VALUES ('John Hicks', 28,5.4,'Provo','Yellow');
   INSERT INTO person (name, age, height,city,favoriteColor) VALUES ('Gregory Yidi', 22, 5.11,'Miami','Black');
   INSERT INTO person (name, age, height,city,favoriteColor) VALUES ('Natalia Yidi', 21, 5.78,'Miami','Pink');
   INSERT INTO person (name, age, height,city,favoriteColor) VALUES ('Natasha Bald', 18, 5.5,'Manhattan','Green');*/


(For this database to create an auto incrementing field set it's type to INTEGER PRIMARY KEY AUTOINCREMENT)

  * List the people in the Person table by Height from shortest to tallest (ascending)
    select * from person order by height asc
  * List all the people in the Person table by oldest first
     select * from person order by age desc
  * List all the people in the Person table older than age 20.
     select * from person where age > 20
  * List all the people in the Person table that are exactly 18.
     select * from person where age = 18
  * List all Person that are less than 20 and older than 30.
     select * from person where age < 20 or age > 23
  * List all Person that are not 27 (Use not equals)
    select * from person where age != 21
  * List all Person where their favorite color is not red
    select * from person where favoriteColor !='Blue'
  * List all Person where their favorite color is not red or blue
     select * from person where favoriteColor !='Blue' and favoriteColor != 'Yellow'
  * List all Person where their favorite color is orange or green
     select * from person where favoriteColor ='Blue' or favoriteColor = 'Yellow'
  * List all Person where their favorite color is orange or green blue (use IN)
     select * from person where favoriteColor in ('Blue','Green')
  * List all Person where their favorite color is yellow or purple
 select * from person where favoriteColor in ('Blue','Green')


## ORDER
4. Create a table called Orders that records the productName, productPrice, Quantity, and personId  
CREATE TABLE orders
(productName VARCHAR(30),
productPrice INTEGER(2),
Quantity INTEGER(50),
personId integer primary key
);
INSERT INTO orders (productName, productPrice, Quantity) VALUES ('A', 100, 6.23);
INSERT INTO orders (productName, productPrice, Quantity) VALUES ('B', 200, 6.23);
INSERT INTO orders (productName, productPrice, Quantity) VALUES ('C', 150, 6.23);
INSERT INTO orders (productName, productPrice, Quantity) VALUES ('D', 250, 6.23);
INSERT INTO orders (productName, productPrice, Quantity) VALUES ('E', 75, 6.23);
5. Add 5 Orders to Order table

6. Select all the records from the Order table
      select * from orders
  * Calculate the total number of products Ordered
      select sum(Quantity) from orders
  * Calculate the total Order Price
      select sum(productPrice) from orders
  * Calculate the total Order Price By personId (If you only made orders for 1 person, go add more for the other people)
    select sum(productPrice * round(Quantity)) as total from orders
## Artists
7. Add 3 new Artists to the Artist table

 * Select the top 10 artists in reverse alphabetical order
  order by alpha desc
  SELECT * FROM ORDERS ORDER BY PRODUCTNAME DESC LIMIT 2
 * Select the top 5 artists in alphabetical order
  SELECT * FROM ORDERS ORDER BY PRODUCTNAME
 * Select all artists that start with the word Black
  SELECT * FROM ORDERS WHERE productName like 'A%'
 * Select all artists that contain the word Black
  SELECT * FROM ORDERS WHERE productName like '%A%'

## Employee
8. Add 2 new Employees to the Employee table

* List all Employee first and last names only that live in Calgary
  select * from person where city like '%Miami%'
   select * from person where city='Miami'
* Find the first and last name for the youngest employee
   select name from person order by age asc limit 1
* Find the first and last name for the oldest employee
   select name from person order by age desc limit 1
* Find everyone that reports to Nancy Edwards (Use the ReportsTo column)
   select * from person where name like '%Yid%'
* Count how many people live in Lethbridge
   select city, count(city) as dod from person where city = 'Miami'

## Invoice
9. Use the Invoice table for the following

* Count how many orders were made from the USA
   select sum(height) from person where city='Miami'
* Find the largest order total amount
   select max(age) from person
* Find the smallest order total amount
   select min(age) from person
* Find all orders bigger than $5
   select * from person where height>=5.7
* Count how many orders were smaller than $5
   select count( * ) from person where height>=5.7
* Count how many orders were in CA, TX, or AZ (use IN)
  select count(height) from person where city in ('Miami','Provo')
* Get the average total of the orders
  select avg(height) from person where city in ('Miami','Provo')
* Get the total sum of the orders
  select sum(height) from person where city in ('Miami','Provo')


## Copyright

© DevMountain LLC, 2016. Unauthorized use and/or duplication of this material without express and written permission from DevMountain, LLC is strictly prohibited. Excerpts and links may be used, provided that full and clear credit is given to DevMountain with appropriate and specific direction to the original content.
