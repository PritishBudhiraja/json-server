# json-server

Repository to learn and get the Findings of the JSON Server

http://localhost:3000/products
All Products Array can be seen.
Its a get request to access all data of Products

http://localhost:3000/reviews
All Review Array can be seen.
Its a get request to access all data of Review

If want single item then http://localhost:3000/products/1
It will give the single item that has id = 1 and it will return an object.

If we want to filter it out the properties we need to send the query parameters.
http://localhost:3000/products?category=electronics
It will send all the Objects which has category as electronics

To filter out the nested properties we go with the dot operator.
http://localhost:3000/products?category=electronics&discount.type=shipping

Sort the data of db.json we can do via

By default Ascending: http://localhost:3000/products?\_sort=price
For desc: http://localhost:3000/products?\_sort=price&\_order=desc

If we want to sort on multiple enteties.
http://localhost:3000/products?\_sort=price,category&\_order=desc,asc
It will sort first by price in desc order then those have same price it will sort by category in asc order

If we want to make our data paginated we can use the \_page and & \_linit values
http://localhost:3000/products?\_page=2&\_limit=2

It will give the products at page 2 with 2 items as limit is 2.
