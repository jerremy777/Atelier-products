# SPRINTS

### Learning to use PostgresQL
- [x] Complete getting started guide for pg module
  - There might be some knowledge I can glean from the setup that will be helpful to me when I begin to formulate my queries

- [x] Practice using VIEWS to query data
  - Views are basically queries
  - We query a query to get data from multiple tables

- [ ] After messing around with VIEWS check out creating a MATERILZIED VIEW

### Setting up the unoptimized get routes
- i.e. using JS to put data from multiple queries together before sending back to client

- [x] Structure a query so that I can make one lookup onto my db and get back the data I need in order to form the following structure:
```
product: {
  id: Number,
  campus: String,
  name: String,
  slogan: String,
  description: String,
  category: String,
  default_price: Number,
  created_at: Date,
  updated_at: Date,
  features: Array // -> Result of query for features
}
```

- [x] Structure a query so I can make one look up for the styles of a product ID. Styles should be returned in the following structure:
```
{
  "product_id": "1",
  "results": [
    {
      "style_id": 1,
      "photos": [{url: ''}, ...],
      "skus": {id: {}, ...},
    }, ...]
}
```

- [x] Setup the skus query to format the result as an object with keys being the sku id

- [x] With getStyleById completed, create a getStylesByProductId method and use it to create the completed getProductById method. This will be the completed getter for benchmarking

- [x] Create a get products method that takes in a page and count parameter and fetches `count` number of results per `page` and return a `page` of results as an array of product items.

- [ ] With all routes completed, deploy to AWS to take benchmarks.

### Practicing more complex queries:
- [x] Generate query for retrieving all the photos associated with a product:
`SELECT url FROM photos JOIN styles ON style_id = styles.id AND styles.product_id = 1;`
- [ ] Query for retrieving all skus associated with a product
- [ ] Can I get the product AND its features in one query?

### Testing:
- [x] Install a testing suite
  - Gonna use Jest
- [x] Complete Jest getting started guide
- [x] Create a test that tests the API for a response
  - Gonna use the 'request-promise' npm package
- [ ] Get some sample data from the HR API to test against
- [x] *Don't test the front-end*
- [x] This is very chicken/egg, but it makes sense:
  - Connect to the db (within the test suite)
  - Make a sample get request (to the server)
  - Test the response against querying from the database directly
  - *This is testing the server specifically*
- [x] Write unit tests for styles:
- [x] Complete the k6 getting started
  - [x] Write k6 scripts for local testing

### Plugging in the front-end:
- [ ] Change the routes on the front-end to communicate with my service
- [ ] Document any errors
- [ ] Add unit tests for any backend issues
- [ ] Fix the errors


### Normalize the 'category' column of product into a category id and table of categories
- Doing so will enable me to change the names of categories. i.e. shoes -> kicks.
- Can I run a query on the product table that does something like this:
  - Take the unique values of the category column and put them into another table, with an index that auto increments

