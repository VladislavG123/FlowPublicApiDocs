# Rate limiter

The system is aimed to prevent incorrect use of the API. Requests made with frequency higher than indicated in the table
will be rejected with error 429. The values apply to each instance.

## Allowed number of requests#

- For all methods limit is 500 requests per second