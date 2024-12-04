# MongoDB Aggregation Pipeline Error: Handling Missing Foreign Key References

This repository demonstrates a common error in MongoDB aggregation pipelines: incorrect handling of missing or invalid foreign key references during joins using the `$lookup` operator.  The pipeline attempts to aggregate sales data by product category, but fails when encountering orders with missing or invalid `product_id` fields.

The `bug.js` file contains the erroneous pipeline. The `bugSolution.js` file provides a corrected version using `$lookup` and `$ifNull` to handle such scenarios effectively, avoiding unexpected errors and ensuring accurate aggregation results.

## How to Reproduce

1. Clone the repository.
2. Configure a MongoDB connection string.
3. Run the provided JavaScript files (using your preferred MongoDB client/driver).
4. Observe that `bug.js` causes an error whereas `bugSolution.js` successfully processes the data.

## Solution

The key to fixing this is using error handling and conditional logic to handle cases where a matching document in the foreign collection might not be found.   The `$ifNull` operator is crucial here.