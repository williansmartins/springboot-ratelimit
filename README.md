# springboot-ratelimit
Poc about Rate Limit using Springboot and bucket4j

## Test
## successful request
```
$ curl -v -X POST http://localhost:9001/api/v1/area/triangle \
    -H "Content-Type: application/json" -H "X-api-key:FX001-99999" \
    -d '{ "height": 15, "base": 8 }'

< HTTP/1.1 200
< X-Rate-Limit-Remaining: 9
{"shape":"triangle","area":60.0}

## rejected request
$ curl -v -X POST http://localhost:9001/api/v1/area/triangle \
    -H "Content-Type: application/json" -H "X-api-key:FX001-99999" \
    -d '{ "height": 15, "base": 8 }'

< HTTP/1.1 429
< X-Rate-Limit-Retry-After-Seconds: 299
{ "status": 429, "error": "Too Many Requests", "message": "You have exhausted your API Request Quota" }
```
