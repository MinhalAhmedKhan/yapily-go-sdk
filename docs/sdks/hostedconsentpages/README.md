# HostedConsentPages

## Overview

Hosted Consent Pages endpoints for data products

### Available Operations

* [CreateHostedConsentRequest](#createhostedconsentrequest) - Create Hosted Consent Request
* [GetHostedConsentRequest](#gethostedconsentrequest) - Get Hosted Consent Request

## CreateHostedConsentRequest

Used to initiate a consent request using Yapily Hosted Pages.

### Example Usage: 400 Error Response

<!-- UsageSnippet language="go" operationID="createHostedConsentRequest" method="post" path="/hosted/consent-requests" example="400 Error Response" -->
```go
package main

import(
	"context"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/types"
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

    res, err := s.HostedConsentPages.CreateHostedConsentRequest(ctx, components.CreateHostedConsentRequest{
        InstitutionIdentifiers: components.InstitutionIdentifiers{
            InstitutionCountryCode: "GB",
        },
        UserSettings: &components.UserSettings{
            Language: yapily.Pointer("en"),
            Location: yapily.Pointer("GB"),
        },
        RedirectURL: "https://tpp-application.com",
        OneTimeToken: yapily.Pointer(false),
        AccountRequest: &components.HostedAccountRequest{
            TransactionFrom: types.MustNewTimeFromString("2020-01-01T00:00:00Z"),
            TransactionTo: types.MustNewTimeFromString("2021-01-01T00:00:00Z"),
            ExpiresAt: types.MustNewTimeFromString("2025-01-01T00:00:00Z"),
        },
    }, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfCreateHostedConsentRequest != nil {
        // handle response
    }
}
```
### Example Usage: Create Hosted Consent Request

<!-- UsageSnippet language="go" operationID="createHostedConsentRequest" method="post" path="/hosted/consent-requests" example="Create Hosted Consent Request" -->
```go
package main

import(
	"context"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/types"
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

    res, err := s.HostedConsentPages.CreateHostedConsentRequest(ctx, components.CreateHostedConsentRequest{
        UserID: yapily.Pointer("ca412fdf-5a30-43a2-88b7-5964a24a8e55"),
        ApplicationUserID: yapily.Pointer("string"),
        InstitutionIdentifiers: components.InstitutionIdentifiers{
            InstitutionID: yapily.Pointer("modelo-sandbox"),
            InstitutionCountryCode: "GB",
        },
        UserSettings: &components.UserSettings{
            Language: yapily.Pointer("en"),
            Location: yapily.Pointer("GB"),
        },
        RedirectURL: "https://tpp-application.com/",
        OneTimeToken: yapily.Pointer(false),
        AccountRequest: &components.HostedAccountRequest{
            TransactionFrom: types.MustNewTimeFromString("2023-07-01T00:00:00.000Z"),
            TransactionTo: types.MustNewTimeFromString("2023-08-01T00:00:00.000Z"),
            ExpiresAt: types.MustNewTimeFromString("2023-11-01T00:00:00.000Z"),
            FeatureScope: []components.FeatureEnum{
                components.FeatureEnumAccounts,
                components.FeatureEnumAccount,
                components.FeatureEnumAccountBalances,
                components.FeatureEnumAccountTransactions,
                components.FeatureEnumIdentity,
            },
        },
    }, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfCreateHostedConsentRequest != nil {
        // handle response
    }
}
```
### Example Usage: Create Hosted Consent Request Response

<!-- UsageSnippet language="go" operationID="createHostedConsentRequest" method="post" path="/hosted/consent-requests" example="Create Hosted Consent Request Response" -->
```go
package main

import(
	"context"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/types"
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

    res, err := s.HostedConsentPages.CreateHostedConsentRequest(ctx, components.CreateHostedConsentRequest{
        InstitutionIdentifiers: components.InstitutionIdentifiers{
            InstitutionCountryCode: "GB",
        },
        UserSettings: &components.UserSettings{
            Language: yapily.Pointer("en"),
            Location: yapily.Pointer("GB"),
        },
        RedirectURL: "https://tpp-application.com",
        OneTimeToken: yapily.Pointer(false),
        AccountRequest: &components.HostedAccountRequest{
            TransactionFrom: types.MustNewTimeFromString("2020-01-01T00:00:00Z"),
            TransactionTo: types.MustNewTimeFromString("2021-01-01T00:00:00Z"),
            ExpiresAt: types.MustNewTimeFromString("2025-01-01T00:00:00Z"),
        },
    }, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfCreateHostedConsentRequest != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `ctx`                                                                                          | [context.Context](https://pkg.go.dev/context#Context)                                          | :heavy_check_mark:                                                                             | The context to use for the request.                                                            |
| `body`                                                                                         | [components.CreateHostedConsentRequest](../../models/components/createhostedconsentrequest.md) | :heavy_check_mark:                                                                             | N/A                                                                                            |
| `subApplication`                                                                               | `*string`                                                                                      | :heavy_minus_sign:                                                                             | The sub-application ID to which event type is being subscribed to                              |
| `opts`                                                                                         | [][operations.Option](../../models/operations/option.md)                                       | :heavy_minus_sign:                                                                             | The options for this request.                                                                  |

### Response

**[*operations.CreateHostedConsentRequestResponse](../../models/operations/createhostedconsentrequestresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401                       | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## GetHostedConsentRequest

Used to get details of a hosted consent request

### Example Usage: 401 Error Response

<!-- UsageSnippet language="go" operationID="getHostedConsentRequest" method="get" path="/hosted/consent-requests/{consentRequestId}" example="401 Error Response" -->
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

    res, err := s.HostedConsentPages.GetHostedConsentRequest(ctx, "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfGetHostedConsentRequest != nil {
        // handle response
    }
}
```
### Example Usage: Get Hosted Consent Request Response

<!-- UsageSnippet language="go" operationID="getHostedConsentRequest" method="get" path="/hosted/consent-requests/{consentRequestId}" example="Get Hosted Consent Request Response" -->
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

    res, err := s.HostedConsentPages.GetHostedConsentRequest(ctx, "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfGetHostedConsentRequest != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                         | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `ctx`                                                             | [context.Context](https://pkg.go.dev/context#Context)             | :heavy_check_mark:                                                | The context to use for the request.                               |
| `consentRequestID`                                                | `string`                                                          | :heavy_check_mark:                                                | Unique Identifier of the consent request                          |
| `subApplication`                                                  | `*string`                                                         | :heavy_minus_sign:                                                | The sub-application ID to which event type is being subscribed to |
| `opts`                                                            | [][operations.Option](../../models/operations/option.md)          | :heavy_minus_sign:                                                | The options for this request.                                     |

### Response

**[*operations.GetHostedConsentRequestResponse](../../models/operations/gethostedconsentrequestresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 401, 404                       | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |