# Aws Synthetics to monitor Websites

## Scope

* Implement Synthetics function using Node.JS
* Include unit tests using mocha
* Test url's provided in env vars
* Record snapshot of every test to S3 bucket with a TTL calculated based on env var
* Insert new record into DynamoDb table `website-test` with 1 read/write per second
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
* Each test considered a failure when response time exceeds an env var
* Overall test is considered a failure when more than X percent of tests failed
* Env vars:
```
urls: ["https://www.google.ca","https://www.msn.com"]
failureThreshold: 50 <-- percent
responseThreshold: 10000 <-- milliseconds
```
* Include bash scripts to deploy: S3, DynamoDB, and synthetics function
* Document the deliverable using markdown