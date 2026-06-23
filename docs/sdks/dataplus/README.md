# DataPlus

## Overview

Data Plus endpoints enable our customers to enrich transaction data. 

### Available Operations

* [PostAccountsAccountIDTransactionsCategorisation](#postaccountsaccountidtransactionscategorisation) - Transactions and Enrichment
* [~~GetAccountsTransactionsCategorised~~](#getaccountstransactionscategorised) - Get Categorised Transactions (Deprecated) :warning: **Deprecated**
* [PostTransactionsCategorisation](#posttransactionscategorisation) - Enrichment
* [GetTransactionsCategorised](#gettransactionscategorised) - Get Enrichment Results
* [GetCategorisationAccountType](#getcategorisationaccounttype) - Get Enrichment Labels

## PostAccountsAccountIDTransactionsCategorisation

Trigger categorisation for transactions from [AIS (see Get Transactions endpoint)](/api-reference/getTransactions) in the specified time range.

### Example Usage: Example

<!-- UsageSnippet language="go" operationID="post-accounts-accountId-transactions-categorisation" method="post" path="/accounts/{accountId}/transactions/categorisation" example="Example" -->
```go
package main

import(
	"context"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/types"
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

    res, err := s.DataPlus.PostAccountsAccountIDTransactionsCategorisation(ctx, operations.PostAccountsAccountIDTransactionsCategorisationRequest{
        Consent: "{consentToken}",
        AccountID: "<id>",
        Body: &operations.PostAccountsAccountIDTransactionsCategorisationRequestBody{
            CountryCode: "GB",
            CategorisationType: "consumer",
            From: types.MustNewTimeFromString("2019-08-24T14:15:22Z"),
            Before: types.MustNewTimeFromString("2019-08-24T14:15:22Z"),
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfCreateTransactionsCategorisationRequest != nil {
        // handle response
    }
}
```
### Example Usage: Example 1

<!-- UsageSnippet language="go" operationID="post-accounts-accountId-transactions-categorisation" method="post" path="/accounts/{accountId}/transactions/categorisation" example="Example 1" -->
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

    res, err := s.DataPlus.PostAccountsAccountIDTransactionsCategorisation(ctx, operations.PostAccountsAccountIDTransactionsCategorisationRequest{
        Consent: "{consentToken}",
        AccountID: "<id>",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfCreateTransactionsCategorisationRequest != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                                              | Type                                                                                                                                                   | Required                                                                                                                                               | Description                                                                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                                                                  | [context.Context](https://pkg.go.dev/context#Context)                                                                                                  | :heavy_check_mark:                                                                                                                                     | The context to use for the request.                                                                                                                    |
| `request`                                                                                                                                              | [operations.PostAccountsAccountIDTransactionsCategorisationRequest](../../models/operations/postaccountsaccountidtransactionscategorisationrequest.md) | :heavy_check_mark:                                                                                                                                     | The request object to use for the request.                                                                                                             |
| `opts`                                                                                                                                                 | [][operations.Option](../../models/operations/option.md)                                                                                               | :heavy_minus_sign:                                                                                                                                     | The options for this request.                                                                                                                          |

### Response

**[*operations.PostAccountsAccountIDTransactionsCategorisationResponse](../../models/operations/postaccountsaccountidtransactionscategorisationresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401                       | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## ~~GetAccountsTransactionsCategorised~~

__Deprecated__. Retrieve categorised transactions by Categorisation ID.

Use the [other endpoint (`/transactions/categorisation/{categorisationId}`)](#operation/get-transactions-categorised) instead.

> :warning: **DEPRECATED**: This will be removed in a future release, please migrate away from it as soon as possible.

### Example Usage

<!-- UsageSnippet language="go" operationID="get-accounts-transactions-categorised" method="get" path="/accounts/{accountId}/transactions/categorisation/{categorisationId}" example="Example 1" -->
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

    res, err := s.DataPlus.GetAccountsTransactionsCategorised(ctx, operations.GetAccountsTransactionsCategorisedRequest{
        Consent: "{consentToken}",
        AccountID: "<id>",
        CategorisationID: "<id>",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfGetCategorisedTransactionsRequest != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                    | Type                                                                                                                         | Required                                                                                                                     | Description                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                                                        | :heavy_check_mark:                                                                                                           | The context to use for the request.                                                                                          |
| `request`                                                                                                                    | [operations.GetAccountsTransactionsCategorisedRequest](../../models/operations/getaccountstransactionscategorisedrequest.md) | :heavy_check_mark:                                                                                                           | The request object to use for the request.                                                                                   |
| `opts`                                                                                                                       | [][operations.Option](../../models/operations/option.md)                                                                     | :heavy_minus_sign:                                                                                                           | The options for this request.                                                                                                |

### Response

**[*operations.GetAccountsTransactionsCategorisedResponse](../../models/operations/getaccountstransactionscategorisedresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 404                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## PostTransactionsCategorisation

Trigger categorisation for transactions provided in the request.

### Example Usage

<!-- UsageSnippet language="go" operationID="post-transactions-categorisation" method="post" path="/transactions/categorisation" example="Example 1" -->
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

    res, err := s.DataPlus.PostTransactionsCategorisation(ctx, nil, &operations.PostTransactionsCategorisationRequestBody{
        CountryCode: "GB",
        CategorisationType: "consumer",
        Transactions: []operations.Transaction{
            operations.Transaction{
                ID: "06edf952-8d94-44ae-8d4e-a065b7e47300",
                Date: "2025-03-01T14:15:16Z",
                Amount: operations.Amount{
                    Value: -9900,
                    Currency: "GBP",
                },
                Description: "Shopping",
                CountryCode: "GB",
            },
            operations.Transaction{
                ID: "6a241cae-7c43-4058-bdbd-ff9d64e6c9df",
                Date: "2025-04-02T07:59:59Z",
                Amount: operations.Amount{
                    Value: 1000,
                    Currency: "USD",
                },
                Description: "Refund",
                CountryCode: "GB",
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfCreateTransactionsCategorisationRequest != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                     | Type                                                                                                                          | Required                                                                                                                      | Description                                                                                                                   |
| ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                         | [context.Context](https://pkg.go.dev/context#Context)                                                                         | :heavy_check_mark:                                                                                                            | The context to use for the request.                                                                                           |
| `subApplication`                                                                                                              | `*string`                                                                                                                     | :heavy_minus_sign:                                                                                                            | The sub-application ID to which event type is being subscribed to                                                             |
| `body`                                                                                                                        | [*operations.PostTransactionsCategorisationRequestBody](../../models/operations/posttransactionscategorisationrequestbody.md) | :heavy_minus_sign:                                                                                                            | N/A                                                                                                                           |
| `opts`                                                                                                                        | [][operations.Option](../../models/operations/option.md)                                                                      | :heavy_minus_sign:                                                                                                            | The options for this request.                                                                                                 |

### Response

**[*operations.PostTransactionsCategorisationResponse](../../models/operations/posttransactionscategorisationresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401                       | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## GetTransactionsCategorised

Retrieve categorised transactions by Categorisation ID.

Please [use webhooks](/introductionpages/data/data-plus/tutorial-categorisation/) to be notified when your transactions have been categorised and are ready for retrieval.

Note that when using the [Transactions and Categorisation endpoint](/api-reference/post-accounts-accountId-transactions-categorisation) this endpoint may also return any data specified by the [Get Account Transactions endpoint](/api-reference/getTransactions); this endpoint's docs mentions a non-exhaustive subset of such data.

### Example Usage

<!-- UsageSnippet language="go" operationID="get-transactions-categorised" method="get" path="/transactions/categorisation/{categorisationId}" example="Example 1" -->
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

    res, err := s.DataPlus.GetTransactionsCategorised(ctx, "<id>", nil, nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfGetCategorisedTransactionsRequest != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                                   | Type                                                                                                                                        | Required                                                                                                                                    | Description                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                                       | [context.Context](https://pkg.go.dev/context#Context)                                                                                       | :heavy_check_mark:                                                                                                                          | The context to use for the request.                                                                                                         |
| `categorisationID`                                                                                                                          | `string`                                                                                                                                    | :heavy_check_mark:                                                                                                                          | Unique identifier for transaction categorisation request                                                                                    |
| `subApplication`                                                                                                                            | `*string`                                                                                                                                   | :heavy_minus_sign:                                                                                                                          | The sub-application ID to which event type is being subscribed to                                                                           |
| `limit`                                                                                                                                     | `*int`                                                                                                                                      | :heavy_minus_sign:                                                                                                                          | __Optional__. The maximum number of transaction records to be returned. Must be between 100 and 1000. If not specified will default to 100. |
| `page`                                                                                                                                      | `*int`                                                                                                                                      | :heavy_minus_sign:                                                                                                                          | __Optional__. The page number to be returned. If not specified will default to 1.                                                           |
| `opts`                                                                                                                                      | [][operations.Option](../../models/operations/option.md)                                                                                    | :heavy_minus_sign:                                                                                                                          | The options for this request.                                                                                                               |

### Response

**[*operations.GetTransactionsCategorisedResponse](../../models/operations/gettransactionscategorisedresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 404                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## GetCategorisationAccountType

Returns the list of categories that can be returned for a specific account type (consumer or business).

### Example Usage: Example business

<!-- UsageSnippet language="go" operationID="get-categorisation-accountType" method="get" path="/transactions/categorisation/categories/{accountType}" example="Example business" -->
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

    res, err := s.DataPlus.GetCategorisationAccountType(ctx, "<value>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```
### Example Usage: Example consumer

<!-- UsageSnippet language="go" operationID="get-categorisation-accountType" method="get" path="/transactions/categorisation/categories/{accountType}" example="Example consumer" -->
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

    res, err := s.DataPlus.GetCategorisationAccountType(ctx, "<value>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                         | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `ctx`                                                             | [context.Context](https://pkg.go.dev/context#Context)             | :heavy_check_mark:                                                | The context to use for the request.                               |
| `accountType`                                                     | `string`                                                          | :heavy_check_mark:                                                | type of bank account (consumer or business)                       |
| `subApplication`                                                  | `*string`                                                         | :heavy_minus_sign:                                                | The sub-application ID to which event type is being subscribed to |
| `opts`                                                            | [][operations.Option](../../models/operations/option.md)          | :heavy_minus_sign:                                                | The options for this request.                                     |

### Response

**[*operations.GetCategorisationAccountTypeResponse](../../models/operations/getcategorisationaccounttyperesponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 404                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |