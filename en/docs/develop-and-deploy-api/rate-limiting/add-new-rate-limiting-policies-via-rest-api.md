# Add Rate Limiting Policy via the REST API Interface

!!! Tip
    
    To get familiar with the concept of Rate Limiting, see [Rate Limiting Overview](../../../develop-and-deploy-api/rate-limiting-policy-overview).

You need to define the Rate Limiting Policies in the API payload when creating an API using the REST API Interface. You can define either API-level or Operation-level Rate Limiting Policies. Let's get familiar with the [API-level](#api-level) and [Operation-level (Resource-Level)](#operation-level-resource-level-rate-limiting) configurations and also the [configuration definitions](#configuration-definitions).

## API-Level Rate Limiting

**Sample code snippets**

The following is a sample code snippet that defines how you can define Rate Limiting policies at the API-level within an API definition.

```
"apiRateLimit": {
    "requestsPerUnit": 5,
    "unit": "Minute"
},
```

??? note "Sample API definition"
    
    The following in a sample API definition with an API-Level Rate Limiting Policy defined in it.
    ```
    name: "PizzaAPIPolicies",
        context: "/pizzaAPIPolcies/1.0.0",
        'version: "1.0.0",
        endpointConfig: {"production_endpoints": {"url": "https://localhost"}},
        operations: [
            {
                "target": "/menu",
                "verb": "GET",
                "authTypeEnabled": true,
                "throttlingPolicy": 1000
            }
        ],
        apiRateLimit: {
            "requestsPerUnit": 10,
            "unit": "Minute"
        }
    ```

## Operation-Level (Resource-Level) Rate Limiting

**Sample code snippets**

The following is a sample code snippet that defines how you can define Rate Limiting policies at the Operation-level within an API definition.

```
"operationRateLimit": {
    "requestsPerUnit": 10,
    "unit": "Minute"
}
```

??? note "Sample API definition"
    
    The following in a sample API definition with an Operation-Level Rate Limiting Policy defined in it.
    ```
    name: "PizzaAPIPolicies",
        context: "/pizzaAPIPolcies/1.0.0",
        'version: "1.0.0",
        endpointConfig: {"production_endpoints": {"url": "https://localhost"}},
        operations: [
            {
                "target": "/menu",
                "verb": "GET",
                "authTypeEnabled": true,
                "throttlingPolicy": 1000,
                "operationRateLimit": {
                    "requestsPerUnit": 10,
                    "unit": "Minute"
                }
            }
        ]
    ```

## Configuration definitions

The following are the configurations that you need when defining Rate Limiting Policies to an API when working with the REST API interface.

<table>
<thead>
  <tr>
    <th><b>Configuration</b></th>
    <th><b>Description</b></th>
  </
</thead>
<tbody>
  <tr>
    <td><code>apiRateLimit</code></td>
    <td>Used to define API-Level Rate Limit Policies within the OpenAPI Specification (OAS) that you use to define the API.</td>
  </tr>
  <tr>
    <td style="white-space: nowrap;"><code>operationRateLimit</code></td>
    <td>Used to define Operation-Level Rate Limit Policies within the OpenAPI Specification (OAS) that you use to define the API.</td>
  </tr>
  <tr>
    <td><code>requestsPerUnit</code></td>
    <td>This defines the number of API requests that are allowed per unit.<br><b>Example</b>:<br> If <code>unit</code> is Minutes and <code>requestsPerUnit</code> is 5, then only 5 API requests are allowed per Minute.</td>
  </tr>
  <tr>
    <td><code>Unit</code></td>
    <td>Defines the measurement unit used to define Rate Limits.<br><b>Possible Values:</b> <code>Minutes</code>, <code>Hours</code>, <code>Days</code><br><b>Example:</b> If <code>unit</code> is Minutes, then how many API requests are allowed per Minute.</td>
  </tr>
</tbody>
</table>

