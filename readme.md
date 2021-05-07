# Test for node
> This is a description of the test for node js
## Instructions for installing
There are no node modules being used.
Only do a `git clone` and cd into the project folder.
And run `npm run start` or `node app.js`

### Data
	A JSON file is present and has some data in it
	1. origin_addresses
	2. destination_addresses
	3. rows
	4. elements
	5. distance
	6. duration
    7. customers
__*origin_addresses*__ is an array of addresses with length **n = 5** which comprises of 5 addresses. First addresses is an address of a store. and rest 4 are the customers that have placed an order from that store.

	[store, customerA, customerB, customerC, customerD]

__*destination_addresses*__ is a array of length **m = 4** which are the addresses of the customers.

	[customerA, customerB, customerC, customerD]
__*rows*__ is an array of objects with size **n** and it contains distance from each origin to each destination. 

	rows:[	{elements:[...]},//Distances of each customer from the store
	 		{elements:[...]},//Distancs of each customer from customerA
			{elements:[...]},//Distancs of each customer from customerB
			{elements:[...]},//Distancs of each customer from customerC
			{elements:[...]} //Distancs of each customer from customerA	]
Visually this means 


__*elements*__ inside each __*rows*__ object is an array of size **m** which contains some distances.

if __*i*__ is an arbitrary index in __*rows*__ then __*elements*__ will have this data

		[   
		{distance,duration,status},//Distance of origin_addresses[i] to destination_addresses[0]
		{distance,duration,status},//Distance of origin_addresses[i] to destination_addresses[1]
		{distance,duration,status},//Distance of origin_addresses[i] to destination_addresses[2]
		{distance,duration,status} //Distance of origin_addresses[i] to destination_addresses[3]		]

### Problem
1. The route from the stores to customers are being calculated as of right now and so are the delivery charges. We need to find out if there is a customer close to last customer that was assigned a route such that the total distance of the route does not exceed the max route length which has been already determined in code as __*maxRouteLength*__.
2. To calculate the delivery charges for each route

### Current Result

    [
       {
          "totalLength":"3147 meters from Store.",
          "route":[
             {
                "customer":"customerC",
                "deliveryCharges":1,
                "path":"3147 meters from Store to customerC."
             }
          ]
       },
       {
          "totalLength":"7374 meters from Store.",
          "route":[
             {
                "customer":"customerD",
                "deliveryCharges":2,
                "path":"7374 meters from Store to customerD."
             }
          ]
       },
       {
          "totalLength":"7374 meters from Store.",
          "route":[
             {
                "customer":"customerA",
                "deliveryCharges":2,
                "path":"7374 meters from Store to customerA."
             }
          ]
       },
       {
          "totalLength":"8021 meters from Store.",
          "route":[
             {
                "customer":"customerB",
                "deliveryCharges":2,
                "path":"8021 meters from Store to customerB."
             }
          ]
       }
    ]

### Ideal Result

    [
       {
          "totalLength":"5.5 miles from Store.",
          "route":[
             {
                "customer":"customerC",
                "deliveryCharges":1,
                "path":"2.0 mi From Store to customerC."
             },
             {
                "customer":"customerD",
                "deliveryCharges":2,
                "path":"3.6 mi from customerC To customerD"
             },
             {
                "customer":"customerA",
                "deliveryCharges":1,
                "path":"1 ft from customerD To customerA"
             }
          ]
       },
       {
          "totalLength":"4.45 miles from Store.",
          "route":[
             {
                "customer":"customerB",
                "deliveryCharges":2,
                "path":"5.0 mi From Store to customerB."
             }
          ]
       }
    ]

`Bonus points if you can serve the results to a route using express`

## Expected files
You can create a new git repo for the solution or create a zip of the solution files.
:rocket: Happy coding
