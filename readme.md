# Aws Synthetics to monitor Websites

## Scope

* Implement Synthetics function using Node.JS
* Include unit tests using mocha
* Test url's provided in env vars for response and status code
* Record snapshot of every test to S3 bucket with a TTL calculated based on an env var
* Insert new record into DynamoDb table `website-test`
```
Timestamp (pk)
Samples: [
  {
    "url": "https://www.google.ca",
    "responseTime": 356,
    "httpStatus": 200
  }
]
Status: success | failure
```
* Record in the DynamoDB to be stored with ttl calculated based on env var
* Each test considered a failure when response time exceeds an env var value
* Overall test is considered a failure when more than X percent of tests fail
* Env vars:
```
urls: ["https://www.google.ca","https://www.msn.com"]
failureThreshold: 50 <-- percent
responseThreshold: 10000 <-- milliseconds
```
* Include bash scripts to provision: S3, DynamoDB (the lowest throughput), and synthetics function
* Document the deliverable using markdown