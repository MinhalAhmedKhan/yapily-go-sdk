# Constraints

## Overview

The constraints endpoints can be used to retrieve institution specific data requirements and rules that will apply when performing other operations.

### Available Operations

* [GetPaymentConstraintsRulesByInstitution](#getpaymentconstraintsrulesbyinstitution) - Get Payment Constraints Rules
* [GetAccountConstraintsRulesByInstitution](#getaccountconstraintsrulesbyinstitution) - Get Data Constraints Rules

## GetPaymentConstraintsRulesByInstitution

Retrieve institution specific constraints for payment authorisation and submission requests

### Example Usage

<!-- UsageSnippet language="go" operationID="getPaymentConstraintsRulesByInstitution" method="get" path="/institutions/constraints/payments" -->
```go
package main

import(
	"context"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/operations"
	"log"
)

func main() {
    ctx := context.Background()

    s := yapily.New(
        yapily.WithSecurity(components.Security{
            Username: yapily.Pointer(""),
            Password: yapily.Pointer(""),
        }),
    )

    res, err := s.Constraints.GetPaymentConstraintsRulesByInstitution(ctx, operations.GetPaymentConstraintsRulesByInstitutionRequest{
        InstitutionIds: []string{
            "<value 1>",
            "<value 2>",
            "<value 3>",
        },
        InstitutionCountryCode: "<value>",
        PaymentType: operations.PaymentTypeInternationalPayment,
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfPaymentConstraints != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                              | Type                                                                                                                                   | Required                                                                                                                               | Description                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                                  | [context.Context](https://pkg.go.dev/context#Context)                                                                                  | :heavy_check_mark:                                                                                                                     | The context to use for the request.                                                                                                    |
| `request`                                                                                                                              | [operations.GetPaymentConstraintsRulesByInstitutionRequest](../../models/operations/getpaymentconstraintsrulesbyinstitutionrequest.md) | :heavy_check_mark:                                                                                                                     | The request object to use for the request.                                                                                             |
| `opts`                                                                                                                                 | [][operations.Option](../../models/operations/option.md)                                                                               | :heavy_minus_sign:                                                                                                                     | The options for this request.                                                                                                          |

### Response

**[*operations.GetPaymentConstraintsRulesByInstitutionResponse](../../models/operations/getpaymentconstraintsrulesbyinstitutionresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIResponseError     | 400, 401, 404                  | application/json;charset=UTF-8 |
| apierrors.APIResponseError     | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## GetAccountConstraintsRulesByInstitution

Get Data Constraints Rules against an Institution for Account Authorisation requests

### Example Usage

<!-- UsageSnippet language="go" operationID="getAccountConstraintsRulesByInstitution" method="get" path="/institutions/constraints/data" -->
```go
package main

import(
	"context"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"log"
)

func main() {
    ctx := context.Background()

    s := yapily.New(
        yapily.WithSecurity(components.Security{
            Username: yapily.Pointer(""),
            Password: yapily.Pointer(""),
        }),
    )

    res, err := s.Constraints.GetAccountConstraintsRulesByInstitution(ctx, []string{}, "<value>", nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfDataConstraints != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                                                         | Type                                                                                                                                                              | Required                                                                                                                                                          | Description                                                                                                                                                       |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                                                             | [context.Context](https://pkg.go.dev/context#Context)                                                                                                             | :heavy_check_mark:                                                                                                                                                | The context to use for the request.                                                                                                                               |
| `institutionIds`                                                                                                                                                  | []`string`                                                                                                                                                        | :heavy_check_mark:                                                                                                                                                | Unique Id(s) of the `Institution`(s) to retrieve the Data Constraints for. Multiple institutionIds need to be separated by `,`                                    |
| `institutionCountryCode`                                                                                                                                          | `string`                                                                                                                                                          | :heavy_check_mark:                                                                                                                                                | Country code of the `Institution`(s). Ensure that the country code matches the respective institutionIds; any mismatch will result in an HTTP 404 error response. |
| `endpointPath`                                                                                                                                                    | `*string`                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                | The path on the API that is associated with the operation for which constraints are to be retrieved                                                               |
| `endpointMethod`                                                                                                                                                  | [*operations.GetAccountConstraintsRulesByInstitutionEndpointMethod](../../models/operations/getaccountconstraintsrulesbyinstitutionendpointmethod.md)             | :heavy_minus_sign:                                                                                                                                                | The HTTP method that is associated with the operation for which constraints are to be retrieved                                                                   |
| `opts`                                                                                                                                                            | [][operations.Option](../../models/operations/option.md)                                                                                                          | :heavy_minus_sign:                                                                                                                                                | The options for this request.                                                                                                                                     |

### Response

**[*operations.GetAccountConstraintsRulesByInstitutionResponse](../../models/operations/getaccountconstraintsrulesbyinstitutionresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIResponseError     | 400, 401, 404                  | application/json;charset=UTF-8 |
| apierrors.APIResponseError     | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |