PRACTICE JOINS:

1) SELECT *
    FROM Invoice i
    JOIN InvoiceLine il ON il.invoiceId = i.invoiceId
    WHERE il.UnitPrice > 0.99;

2)  SELECT i.invoicedate, c.firstname, c.lastname, i.total
    FROM customer c
    JOIN invoice i ON c.customerid = i.customerid

3)    SELECT c.firstname, c.lastname, e.firstname, e.lastname
    FROM customer c
    join employee e ON c.supportrepid = e.employeeid

4) SELECT al.title, ar.name
FROM album al
join artist ar ON al.artistid = ar.artistid

5) SELECT pt.Trackid
FROM PlaylistTrack pt
JOIN Playlist p ON p.playlistid = pt.playlistid 
WHERE p.Name = 'Music';

6)  SELECT t.name
from track t
join playlisttrack pt ON t.trackid = pt.trackid
where pt.playlistid = 5;

7) SELECT t.name, p.name
FROM track t
join playlisttrack pt ON t.trackid = pt.trackid
join playlist p ON pt.playlistid = p.playlistid;

8) SELECT t.name, a.title
FROM genre g
join track t ON t.genreid = g.genreid
join album a ON a.albumid = t.albumid
where g.name = "Alternative"


NESTED QUERIES:

1)  UPDATE customers
set fax = null
where fax is not null

2)  UPDATE customers
set company = "Self"
where fax is null

3)  UPDATE customer
SET lastname = "Thompson"
where firstname = "Julia" and lastname = "Barnett"

4)  UPDATE customer
SET supportrep = 4
where email = "luisrojas@yahoo.cl"

5) UPDATE track
SET composer = "The darkness around us"
where genreid = (select genreid FROM genre where name = "Metal") 
and composer = null

GROUP BY

1) SELECT  count(*), g.name
FROM track t
JOIN genre g ON g.genreid = t.genreid
GROUP BY g.name

2)  SELECT  count(*), g.name
FROM track t
JOIN genre g ON g.genreid = t.genreid
where g.name = "Pop" or g.name = "Rock"
GROUP BY g.name

3)  SELECT  count(*), a.name
FROM album al
JOIN artist a ON a.artistid = al.artistid
GROUP BY a.name

DISTINCT

1)  SELECT DISTINCT composer FROM track

2)  SELECT DISTINCT billingpostalcode FROM invoice

3)  SELECT DISTINCT company FROM customer

DELETE ROWS

select * from practice_delete where type = "bronze"
delete from practice_delete where type = "bronze"
delete from practice_delete where type = "silver"
delete from practice_delete where value = 150 


Sim

/* create table users (
	userid integer PRIMARY KEY,
  	name	varchar(20),
  	email	text
)
 */
/*  insert into users (name, email) 
 values
 	("josh", "email@gmail.com")
    ("kyle", "otheremail@gmail.com")
    ("sam", "newemail@gmail.com") */
    
/*  create table products (
   prodid integer PRIMARY KEY,
   name varchar(40),
   price integer
  ) */
  
/*   insert into products (name, price)
  values 
  		("shoes", 50),
  		("phone", 400),
        ("cup", 20) */
/* select * from products */
/* drop table products */

/* create table orders (
  order_id integer,
  user_id integer,
  product_id integer,
  FOREIGN KEY(user_id) REFERENCES users(userid),
  FOREIGN KEY(product_id) REFERENCES products(prodid)
  ); */
/*   drop table orders */
 
/*  INSERT INTO orders(order_id, user_id, product_id)
 values 
 		(1,2,1),
        (1,2,2),
        (2,3,3) */
 
 
/* select * from orders where order_id = 1 */

/* select * from orders  */

/* select sum(p.price) 
from products p
JOIN orders o ON o.product_id = p.prodid
where order_id = 1 */


/* SELECT p.name, p.price
from orders o
join users u ON o.user_id = u.userid
JOIN products p ON p.prodid = o.product_id
where u.userid = 2 */

/* SELECT COUNT(o.order_id)
from orders o
join users u ON o.user_id = u.userid
JOIN products p ON p.prodid = o.product_id
where u.userid = 3 */
 

