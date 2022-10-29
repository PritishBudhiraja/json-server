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
