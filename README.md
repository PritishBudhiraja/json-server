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

Send data with the range of values.
http://localhost:3000/products?price_gte=2000&price_lte=6000

**gte** means greater that equals to && **lte** means less than equal to.
price_lte means applying lte property on price attribute

**ne** is the operator stands for not equal so
http://localhost:3000/products?price_ne=4000 will give all the values whose price is not equal to 4000

**like** operator: http://localhost:3000/products?category_like=^f all category that starts with f.

If want to filter and search for a string then go with q=stringToSearch
http://localhost:3000/products?q=in It will go through all elements and all lines in db.json and return the results with having substring in in it.

For getting all the reviews corresponds to their products, like JOINS in SQL.
http://localhost:3000/products?\_embed=reviews
**\_embed** keyword is used to show all the review in a nested manner

If want to to do the reverse that get the product for a particular review we use **\_expand** keyword.
http://localhost:3000/reviews?\_expand=product

For Indivsual review we can go with this: http://localhost:3000/reviews/1?\_expand=product

For Indivsual Product we can go with this: http://localhost:3000/products/1?\_embed=reviews

For adding data in the db.json file JSON Server supports that.
Open thunder client add http://localhost:3000/products/
in Body add the JSON Body.
{
"id": 11,
"title": "Product 11",
"category": "electronics",
"price": 4000,
"description": "This is description about product 11"
},
It will append the JSON in db.json

import axios from "axios";

let headersList = {
"Accept": "_/_",
"User-Agent": "Thunder Client (https://www.thunderclient.com)",
"Content-Type": "application/json"
}

let bodyContent = JSON.stringify( {
"id": 11,
"title": "Product 11",
"category": "electronics",
"price": 4000,
"description": "This is description about product 11"
});

let reqOptions = {
url: "http://localhost:3000/products/",
method: "POST",
headers: headersList,
data: bodyContent,
}

let response = await axios.request(reqOptions);
console.log(response.data);

In PUT request the same steps need to follow but in we need to send the entire JSON of the specific product that need to be updated.

import axios from "axios";

let headersList = {
"Accept": "_/_",
"User-Agent": "Thunder Client (https://www.thunderclient.com)",
"Content-Type": "application/json"
}

let bodyContent = JSON.stringify( {
"id": 11,
"title": "Product 11",
"category": "Champions",
"price": 4000,
"description": "This is description about product 11"
});

let reqOptions = {
url: "http://localhost:3000/products/1/",
method: "PUT",
headers: headersList,
data: bodyContent,
}

let response = await axios.request(reqOptions);
console.log(response.data);

If we need to update and send only one property then we need to use PATCH instead of PUT.
The price will change to 8000 when single PATCH request is made.
{
"price": 8000
}
