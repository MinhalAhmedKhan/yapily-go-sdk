# HostedPaymentPages

## Overview

Hosted Payment Pages endpoints for payments products

### Available Operations

* [CreateHostedPaymentRequest](#createhostedpaymentrequest) - Create Hosted payment request
* [CreateHostedPaymentRequestLink](#createhostedpaymentrequestlink) - Create Pay By Link
* [GetHostedPaymentRequest](#gethostedpaymentrequest) - Get Hosted payment request

## CreateHostedPaymentRequest

Used to initiate a payment request using Yapily Hosted Pages.

### Example Usage: 400 Error Response

<!-- UsageSnippet language="go" operationID="createHostedPaymentRequest" method="post" path="/hosted/payment-requests" example="400 Error Response" -->
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

    res, err := s.HostedPaymentPages.CreateHostedPaymentRequest(ctx, components.CreateHostedPaymentRequest{
        InstitutionIdentifiers: components.InstitutionIdentifiers{
            InstitutionCountryCode: "GB",
        },
        UserSettings: &components.UserSettings{
            Language: yapily.Pointer("en"),
            Location: yapily.Pointer("GB"),
        },
        RedirectURL: "https://tpp-application.com",
        PaymentRequestDetails: components.HostedPaymentRequestDetails{
            PaymentIdempotencyID: "04ab4536gaerfc0e1f93c4f4",
            Reference: yapily.Pointer("Bill payment"),
            Type: components.PaymentTypeDomesticPeriodicPayment,
            Payee: components.Payee{
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
            Payer: &components.Payer{
                Name: yapily.Pointer("John Doe"),
                AccountIdentifications: []components.AccountIdentification{},
                Address: &components.Address{
                    Country: yapily.Pointer("GB"),
                },
            },
            AmountDetails: components.HostedAmountDetails{
                AmountToPay: 10.5,
                Currency: "GBP",
            },
        },
    }, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfCreateHostedPaymentRequest != nil {
        // handle response
    }
}
```
### Example Usage: Create Hosted Payment Request

<!-- UsageSnippet language="go" operationID="createHostedPaymentRequest" method="post" path="/hosted/payment-requests" example="Create Hosted Payment Request" -->
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

    res, err := s.HostedPaymentPages.CreateHostedPaymentRequest(ctx, components.CreateHostedPaymentRequest{
        UserID: yapily.Pointer("3ddf5dd0-aa48-4d0f-baa7-fa057e9e911d"),
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
        PaymentRequestDetails: components.HostedPaymentRequestDetails{
            PaymentIdempotencyID: "4289457hd38djoa783jw9qag3",
            Reference: yapily.Pointer("Test Payment"),
            Type: components.PaymentTypeDomesticPayment,
            Payee: components.Payee{
                Name: "Jane Doe",
                AccountIdentifications: []components.AccountIdentification{
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "123456",
                    },
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeAccountNumber,
                        Identification: "12345678",
                    },
                },
            },
            Payer: &components.Payer{
                Name: yapily.Pointer("John Doe"),
                AccountIdentifications: []components.AccountIdentification{
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "121212",
                    },
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeAccountNumber,
                        Identification: "87654321",
                    },
                },
            },
            AmountDetails: components.HostedAmountDetails{
                AmountToPay: 10.0,
                Currency: "GBP",
            },
        },
    }, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfCreateHostedPaymentRequest != nil {
        // handle response
    }
}
```
### Example Usage: Create Hosted Payment Request Response

<!-- UsageSnippet language="go" operationID="createHostedPaymentRequest" method="post" path="/hosted/payment-requests" example="Create Hosted Payment Request Response" -->
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

    res, err := s.HostedPaymentPages.CreateHostedPaymentRequest(ctx, components.CreateHostedPaymentRequest{
        InstitutionIdentifiers: components.InstitutionIdentifiers{
            InstitutionCountryCode: "GB",
        },
        UserSettings: &components.UserSettings{
            Language: yapily.Pointer("en"),
            Location: yapily.Pointer("GB"),
        },
        RedirectURL: "https://tpp-application.com",
        PaymentRequestDetails: components.HostedPaymentRequestDetails{
            PaymentIdempotencyID: "04ab4536gaerfc0e1f93c4f4",
            Reference: yapily.Pointer("Bill payment"),
            Type: components.PaymentTypeDomesticPeriodicPayment,
            Payee: components.Payee{
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
            Payer: &components.Payer{
                Name: yapily.Pointer("John Doe"),
                AccountIdentifications: []components.AccountIdentification{},
                Address: &components.Address{
                    Country: yapily.Pointer("GB"),
                },
            },
            AmountDetails: components.HostedAmountDetails{
                AmountToPay: 10.5,
                Currency: "GBP",
            },
        },
    }, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfCreateHostedPaymentRequest != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `ctx`                                                                                          | [context.Context](https://pkg.go.dev/context#Context)                                          | :heavy_check_mark:                                                                             | The context to use for the request.                                                            |
| `body`                                                                                         | [components.CreateHostedPaymentRequest](../../models/components/createhostedpaymentrequest.md) | :heavy_check_mark:                                                                             | N/A                                                                                            |
| `subApplication`                                                                               | `*string`                                                                                      | :heavy_minus_sign:                                                                             | The sub-application ID to which event type is being subscribed to                              |
| `opts`                                                                                         | [][operations.Option](../../models/operations/option.md)                                       | :heavy_minus_sign:                                                                             | The options for this request.                                                                  |

### Response

**[*operations.CreateHostedPaymentRequestResponse](../../models/operations/createhostedpaymentrequestresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401                       | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## CreateHostedPaymentRequestLink

Used to created a long lived payment request for Pay By Link

### Example Usage: 400 Error Response

<!-- UsageSnippet language="go" operationID="createHostedPaymentRequestLink" method="post" path="/hosted/payment-requests/links" example="400 Error Response" -->
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

    res, err := s.HostedPaymentPages.CreateHostedPaymentRequestLink(ctx, components.CreateHostedPaymentRequestLink{
        InstitutionIdentifiers: components.InstitutionIdentifiers{
            InstitutionCountryCode: "GB",
        },
        UserSettings: &components.UserSettings{
            Language: yapily.Pointer("en"),
            Location: yapily.Pointer("GB"),
        },
        RedirectURL: "https://tpp-application.com",
        PaymentRequestDetails: components.HostedPaymentRequestDetailsLink{
            Reference: yapily.Pointer("Bill payment"),
            Payee: &components.PayeeDetailsResponse{
                Name: yapily.Pointer("Jane Doe"),
                AccountIdentifications: []components.AccountIdentificationResponse{
                    components.AccountIdentificationResponse{
                        Type: components.AccountIdentificationTypeResponseSortCode.ToPointer(),
                        Identification: yapily.Pointer("401016"),
                    },
                    components.AccountIdentificationResponse{
                        Type: components.AccountIdentificationTypeResponseAccountNumber.ToPointer(),
                        Identification: yapily.Pointer("71518920"),
                    },
                },
                Address: &components.AddressResponse{
                    Country: yapily.Pointer("GB"),
                },
                MerchantID: yapily.Pointer("24589303"),
                MerchantCategoryCode: yapily.Pointer("5551"),
            },
            Payer: &components.PayerDetailsResponse{
                Name: yapily.Pointer("John Doe"),
                AccountIdentifications: []components.AccountIdentificationResponse{
                    components.AccountIdentificationResponse{
                        Type: components.AccountIdentificationTypeResponseSortCode.ToPointer(),
                        Identification: yapily.Pointer("401016"),
                    },
                },
                Address: &components.AddressResponse{
                    Country: yapily.Pointer("GB"),
                },
            },
            AmountDetails: &components.AmountDetailsResponse{
                Amount: yapily.Pointer[float64](10.0),
                Currency: yapily.Pointer("GBP"),
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfCreateHostedPaymentRequestLink != nil {
        // handle response
    }
}
```
### Example Usage: Create Hosted Payment Request

<!-- UsageSnippet language="go" operationID="createHostedPaymentRequestLink" method="post" path="/hosted/payment-requests/links" example="Create Hosted Payment Request" -->
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

    res, err := s.HostedPaymentPages.CreateHostedPaymentRequestLink(ctx, components.CreateHostedPaymentRequestLink{
        UserID: yapily.Pointer("3ddf5dd0-aa48-4d0f-baa7-fa057e9e911d"),
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
        PaymentRequestDetails: components.HostedPaymentRequestDetailsLink{
            Reference: yapily.Pointer("Test Payment"),
            ContextType: components.PaymentContextTypeResponseOther.ToPointer(),
            Type: components.PaymentTypeResponseDomesticPayment.ToPointer(),
            Payee: &components.PayeeDetailsResponse{
                Name: yapily.Pointer("Jane Doe"),
                AccountIdentifications: []components.AccountIdentificationResponse{
                    components.AccountIdentificationResponse{
                        Type: components.AccountIdentificationTypeResponseSortCode.ToPointer(),
                        Identification: yapily.Pointer("123456"),
                    },
                    components.AccountIdentificationResponse{
                        Type: components.AccountIdentificationTypeResponseAccountNumber.ToPointer(),
                        Identification: yapily.Pointer("12345678"),
                    },
                },
            },
            Payer: &components.PayerDetailsResponse{
                Name: yapily.Pointer("John Doe"),
                AccountIdentifications: []components.AccountIdentificationResponse{
                    components.AccountIdentificationResponse{
                        Type: components.AccountIdentificationTypeResponseSortCode.ToPointer(),
                        Identification: yapily.Pointer("121212"),
                    },
                    components.AccountIdentificationResponse{
                        Type: components.AccountIdentificationTypeResponseAccountNumber.ToPointer(),
                        Identification: yapily.Pointer("87654321"),
                    },
                },
            },
            AmountDetails: &components.AmountDetailsResponse{
                Currency: yapily.Pointer("GBP"),
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfCreateHostedPaymentRequestLink != nil {
        // handle response
    }
}
```
### Example Usage: Create Hosted Payment Request Response

<!-- UsageSnippet language="go" operationID="createHostedPaymentRequestLink" method="post" path="/hosted/payment-requests/links" example="Create Hosted Payment Request Response" -->
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

    res, err := s.HostedPaymentPages.CreateHostedPaymentRequestLink(ctx, components.CreateHostedPaymentRequestLink{
        InstitutionIdentifiers: components.InstitutionIdentifiers{
            InstitutionCountryCode: "GB",
        },
        UserSettings: &components.UserSettings{
            Language: yapily.Pointer("en"),
            Location: yapily.Pointer("GB"),
        },
        RedirectURL: "https://tpp-application.com",
        PaymentRequestDetails: components.HostedPaymentRequestDetailsLink{
            Reference: yapily.Pointer("Bill payment"),
            Payee: &components.PayeeDetailsResponse{
                Name: yapily.Pointer("Jane Doe"),
                AccountIdentifications: []components.AccountIdentificationResponse{
                    components.AccountIdentificationResponse{
                        Type: components.AccountIdentificationTypeResponseSortCode.ToPointer(),
                        Identification: yapily.Pointer("401016"),
                    },
                    components.AccountIdentificationResponse{
                        Type: components.AccountIdentificationTypeResponseAccountNumber.ToPointer(),
                        Identification: yapily.Pointer("71518920"),
                    },
                },
                Address: &components.AddressResponse{
                    Country: yapily.Pointer("GB"),
                },
                MerchantID: yapily.Pointer("24589303"),
                MerchantCategoryCode: yapily.Pointer("5551"),
            },
            Payer: &components.PayerDetailsResponse{
                Name: yapily.Pointer("John Doe"),
                AccountIdentifications: []components.AccountIdentificationResponse{
                    components.AccountIdentificationResponse{
                        Type: components.AccountIdentificationTypeResponseSortCode.ToPointer(),
                        Identification: yapily.Pointer("401016"),
                    },
                },
                Address: &components.AddressResponse{
                    Country: yapily.Pointer("GB"),
                },
            },
            AmountDetails: &components.AmountDetailsResponse{
                Amount: yapily.Pointer[float64](10.0),
                Currency: yapily.Pointer("GBP"),
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfCreateHostedPaymentRequestLink != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                              | Type                                                                                                   | Required                                                                                               | Description                                                                                            |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                  | [context.Context](https://pkg.go.dev/context#Context)                                                  | :heavy_check_mark:                                                                                     | The context to use for the request.                                                                    |
| `request`                                                                                              | [components.CreateHostedPaymentRequestLink](../../models/components/createhostedpaymentrequestlink.md) | :heavy_check_mark:                                                                                     | The request object to use for the request.                                                             |
| `opts`                                                                                                 | [][operations.Option](../../models/operations/option.md)                                               | :heavy_minus_sign:                                                                                     | The options for this request.                                                                          |

### Response

**[*operations.CreateHostedPaymentRequestLinkResponse](../../models/operations/createhostedpaymentrequestlinkresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401                       | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## GetHostedPaymentRequest

Used to get details of a payment request

### Example Usage: 401 Error Response

<!-- UsageSnippet language="go" operationID="getHostedPaymentRequest" method="get" path="/hosted/payment-requests/{paymentRequestId}" example="401 Error Response" -->
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

    res, err := s.HostedPaymentPages.GetHostedPaymentRequest(ctx, "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfGetHostedPaymentRequest != nil {
        // handle response
    }
}
```
### Example Usage: Get Hosted Payment Request Response

<!-- UsageSnippet language="go" operationID="getHostedPaymentRequest" method="get" path="/hosted/payment-requests/{paymentRequestId}" example="Get Hosted Payment Request Response" -->
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

    res, err := s.HostedPaymentPages.GetHostedPaymentRequest(ctx, "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfGetHostedPaymentRequest != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                         | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `ctx`                                                             | [context.Context](https://pkg.go.dev/context#Context)             | :heavy_check_mark:                                                | The context to use for the request.                               |
| `paymentRequestID`                                                | `string`                                                          | :heavy_check_mark:                                                | Unique Identifier of the payment request                          |
| `subApplication`                                                  | `*string`                                                         | :heavy_minus_sign:                                                | The sub-application ID to which event type is being subscribed to |
| `opts`                                                            | [][operations.Option](../../models/operations/option.md)          | :heavy_minus_sign:                                                | The options for this request.                                     |

### Response

**[*operations.GetHostedPaymentRequestResponse](../../models/operations/gethostedpaymentrequestresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 401, 404                       | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |