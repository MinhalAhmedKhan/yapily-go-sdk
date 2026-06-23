# HostedVRPPages

## Overview

Hosted Variable Recurring Payment Pages endpoints for payments products

### Available Operations

* [PostHostedCommercialVrpRequest](#posthostedcommercialvrprequest) - Create Hosted Commercial VRP request
* [GetHostedCommercialVrpRequest](#gethostedcommercialvrprequest) - Get Hosted Commercial VRP request

## PostHostedCommercialVrpRequest

Used to initiate a Commercial VRP request using Yapily Hosted Pages.

### Example Usage: 401 Error Response

<!-- UsageSnippet language="go" operationID="postHostedCommercialVrpRequest" method="post" path="/hosted/vrp-requests/commercial" example="401 Error Response" -->
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

    res, err := s.HostedVRPPages.PostHostedCommercialVrpRequest(ctx, operations.PostHostedCommercialVrpRequestRequest{
        ApplicationUserID: "<id>",
        InstitutionIdentifiers: operations.InstitutionIdentifiersRequest{},
        ControlParameters: components.HostedVrpControlParameters{
            MaxAmountPerPayment: components.Amount{
                Amount: 10.0,
                Currency: "GBP",
            },
            PeriodicLimit: components.PeriodicLimit{
                Frequency: "<value>",
                TotalMaxAmount: components.Amount{
                    Amount: 10.0,
                    Currency: "GBP",
                },
            },
        },
        InitiationDetails: &components.HostedVrpInitiationDetails{
            Payer: &components.Payer{
                Name: yapily.Pointer("John Doe"),
                AccountIdentifications: []components.AccountIdentification{
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                Address: &components.Address{
                    Country: yapily.Pointer("GB"),
                },
            },
            UltimatePayer: &components.VrpUltimatePayer{
                AccountIdentifications: []components.AccountIdentification{
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                Address: &components.Address{
                    Country: yapily.Pointer("GB"),
                },
            },
            Payee: &components.Payee{
                Name: "Jane Doe",
                AccountIdentifications: []components.AccountIdentification{
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeAccountNumber,
                        Identification: "71518920",
                    },
                },
                Address: &components.Address{
                    Country: yapily.Pointer("GB"),
                },
                MerchantID: yapily.Pointer("24589303"),
                MerchantCategoryCode: yapily.Pointer("0742"),
            },
            UltimatePayee: &components.VrpUltimatePayee{
                AccountIdentifications: []components.AccountIdentification{
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                Address: &components.Address{
                    Country: yapily.Pointer("GB"),
                },
            },
        },
        RedirectURL: "https://petty-celsius.org",
        RiskDetails: components.HostedVrpCommercialRiskDetails{
            PaymentContextCode: "<value>",
            PaymentPurposeCode: "<value>",
            CategoryPurposeCode: "<value>",
            MerchantCustomerID: "<id>",
            IsPayeePrepopulated: false,
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```
### Example Usage: Create Hosted Commercial VRP Response

<!-- UsageSnippet language="go" operationID="postHostedCommercialVrpRequest" method="post" path="/hosted/vrp-requests/commercial" example="Create Hosted Commercial VRP Response" -->
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

    res, err := s.HostedVRPPages.PostHostedCommercialVrpRequest(ctx, operations.PostHostedCommercialVrpRequestRequest{
        ApplicationUserID: "<id>",
        InstitutionIdentifiers: operations.InstitutionIdentifiersRequest{},
        ControlParameters: components.HostedVrpControlParameters{
            MaxAmountPerPayment: components.Amount{
                Amount: 10.0,
                Currency: "GBP",
            },
            PeriodicLimit: components.PeriodicLimit{
                Frequency: "<value>",
                TotalMaxAmount: components.Amount{
                    Amount: 10.0,
                    Currency: "GBP",
                },
            },
        },
        InitiationDetails: &components.HostedVrpInitiationDetails{
            Payer: &components.Payer{
                Name: yapily.Pointer("John Doe"),
                AccountIdentifications: []components.AccountIdentification{
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                Address: &components.Address{
                    Country: yapily.Pointer("GB"),
                },
            },
            UltimatePayer: &components.VrpUltimatePayer{
                AccountIdentifications: []components.AccountIdentification{
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                Address: &components.Address{
                    Country: yapily.Pointer("GB"),
                },
            },
            Payee: &components.Payee{
                Name: "Jane Doe",
                AccountIdentifications: []components.AccountIdentification{
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeAccountNumber,
                        Identification: "71518920",
                    },
                },
                Address: &components.Address{
                    Country: yapily.Pointer("GB"),
                },
                MerchantID: yapily.Pointer("24589303"),
                MerchantCategoryCode: yapily.Pointer("0742"),
            },
            UltimatePayee: &components.VrpUltimatePayee{
                AccountIdentifications: []components.AccountIdentification{
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                Address: &components.Address{
                    Country: yapily.Pointer("GB"),
                },
            },
        },
        RedirectURL: "https://petty-celsius.org",
        RiskDetails: components.HostedVrpCommercialRiskDetails{
            PaymentContextCode: "<value>",
            PaymentPurposeCode: "<value>",
            CategoryPurposeCode: "<value>",
            MerchantCustomerID: "<id>",
            IsPayeePrepopulated: false,
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                            | Type                                                                                                                 | Required                                                                                                             | Description                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                | [context.Context](https://pkg.go.dev/context#Context)                                                                | :heavy_check_mark:                                                                                                   | The context to use for the request.                                                                                  |
| `request`                                                                                                            | [operations.PostHostedCommercialVrpRequestRequest](../../models/operations/posthostedcommercialvrprequestrequest.md) | :heavy_check_mark:                                                                                                   | The request object to use for the request.                                                                           |
| `opts`                                                                                                               | [][operations.Option](../../models/operations/option.md)                                                             | :heavy_minus_sign:                                                                                                   | The options for this request.                                                                                        |

### Response

**[*operations.PostHostedCommercialVrpRequestResponse](../../models/operations/posthostedcommercialvrprequestresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIResponseError     | 401                            | application/json;charset=UTF-8 |
| apierrors.APIResponseError     | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## GetHostedCommercialVrpRequest

Used to get details of a Commercial VRP request

### Example Usage

<!-- UsageSnippet language="go" operationID="getHostedCommercialVrpRequest" method="get" path="/hosted/vrp-requests/commercial/{requestId}" example="Get Hosted Commercial VRP Response" -->
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

    res, err := s.HostedVRPPages.GetHostedCommercialVrpRequest(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `requestID`                                              | `string`                                                 | :heavy_check_mark:                                       | Unique Identifier of the Commercial VRP request          |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetHostedCommercialVrpRequestResponse](../../models/operations/gethostedcommercialvrprequestresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIResponseError     | 400, 403, 404                  | application/json;charset=UTF-8 |
| apierrors.APIResponseError     | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |