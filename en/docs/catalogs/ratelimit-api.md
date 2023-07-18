# RateLimitPolicy for API

The following define Rate Limiting Policies at the API-level within an API definition.

```
apiVersion: dp.wso2.com/v1alpha1
kind: RateLimitPolicy
metadata:
  name: sand-http-bin-ratelimit
spec:
  default:
    type: Api
    api:
      rateLimit:
        requestsPerUnit: 5
        unit: Minute
  targetRef:
    kind: HTTPRoute
    name: sand-http-route-http-bin-api
    group: gateway.networking.k8s.io
```