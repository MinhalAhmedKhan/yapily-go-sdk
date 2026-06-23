# Payments

## Overview

In order to make a Payment on behalf of a user, you are required to request an [Authorisation](#tag/Authorisations) from the user to authorise the user's account to make the payment from. Once a `consent-token` is obtained, you can call the necessary Payments endpoint(s) to execute a payment.

### Available Operations

* [CreateBulkPayment](#createbulkpayment) - Create Bulk Payment
* [GetBulkPaymentStatus](#getbulkpaymentstatus) - Get Bulk Payment File Status
* [GetBulkPaymentDetailsByID](#getbulkpaymentdetailsbyid) - Get Bulk Payment Status Details
* [CreatePayment](#createpayment) - Create Payment
* [GetPayments](#getpayments) - Get Payment Details

## CreateBulkPayment

Creates a bulk payment after obtaining the user's authorisation. 

Feature: `CREATE_BULK_PAYMENT`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="createBulkPayment" method="post" path="/bulk-payments" example="Error Response" -->
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

    res, err := s.Payments.CreateBulkPayment(ctx, operations.CreateBulkPaymentRequest{
        Consent: "{consentToken}",
        Body: components.SubmitBulkPaymentRequest{
            IdempotencyID: yapily.Pointer("1cc3e60d-5500-42be-aaeb-3c5e2f5ed048"),
            Payments: []components.PaymentRequest{
                components.PaymentRequest{
                    PaymentIdempotencyID: "04ab4536gaerfc0e1f93c4f4",
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
                    Reference: yapily.Pointer("Bill payment"),
                    Type: components.PaymentTypeInternationalPeriodicPayment,
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
                    PeriodicPayment: &components.PeriodicPaymentRequest{
                        Frequency: components.FrequencyRequest{
                            Type: components.FrequencyEnumExtendedWeekly,
                            IntervalWeek: yapily.Pointer[int](1),
                            IntervalMonth: yapily.Pointer[int](1),
                            ExecutionDay: yapily.Pointer[int](1),
                        },
                        NumberOfPayments: yapily.Pointer[int](5),
                        NextPaymentDateTime: types.MustNewTimeFromString("2018-01-10T00:00:00Z"),
                        NextPaymentAmount: &components.Amount{
                            Amount: 10.0,
                            Currency: "GBP",
                        },
                        FinalPaymentDateTime: types.MustNewTimeFromString("2030-01-10T00:00:00Z"),
                        FinalPaymentAmount: &components.Amount{
                            Amount: 10.0,
                            Currency: "GBP",
                        },
                    },
                    Amount: components.Amount{
                        Amount: 10.0,
                        Currency: "GBP",
                    },
                    PaymentDateTime: types.MustNewTimeFromString("2021-07-21T17:32:28Z"),
                    ReadRefundAccount: yapily.Pointer(false),
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfCreateBulkPaymentRequest != nil {
        // handle response
    }
}
```
### Example Usage: UK Bulk Payment Example Request

<!-- UsageSnippet language="go" operationID="createBulkPayment" method="post" path="/bulk-payments" example="UK Bulk Payment Example Request" -->
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

    res, err := s.Payments.CreateBulkPayment(ctx, operations.CreateBulkPaymentRequest{
        Consent: "{consentToken}",
        Body: components.SubmitBulkPaymentRequest{
            IdempotencyID: yapily.Pointer("1cc3e60d-5500-42be-aaeb-3c5e2f5ed048"),
            Payments: []components.PaymentRequest{
                components.PaymentRequest{
                    PaymentIdempotencyID: "d78fy48uh8f9odhde68dfi38di9",
                    Reference: yapily.Pointer("payment1"),
                    ContextType: components.PaymentContextTypeBillInArrears.ToPointer(),
                    PurposeCode: yapily.Pointer("COMT"),
                    Type: components.PaymentTypeDomesticPayment,
                    Payee: components.Payee{
                        Name: "Jane Doe",
                        AccountIdentifications: []components.AccountIdentification{
                            components.AccountIdentification{
                                Type: components.AccountIdentificationTypeAccountNumber,
                                Identification: "12345678",
                            },
                            components.AccountIdentification{
                                Type: components.AccountIdentificationTypeSortCode,
                                Identification: "123456",
                            },
                        },
                        AccountType: yapily.Pointer("BUSINESS_SAVING"),
                    },
                    Amount: components.Amount{
                        Amount: 2.0,
                        Currency: "GBP",
                    },
                },
                components.PaymentRequest{
                    PaymentIdempotencyID: "4279gdy8t63dg73gd8gx87738dg",
                    Reference: yapily.Pointer("payment2"),
                    Type: components.PaymentTypeDomesticPayment,
                    Payee: components.Payee{
                        Name: "John Doe",
                        AccountIdentifications: []components.AccountIdentification{
                            components.AccountIdentification{
                                Type: components.AccountIdentificationTypeAccountNumber,
                                Identification: "87654321",
                            },
                            components.AccountIdentification{
                                Type: components.AccountIdentificationTypeSortCode,
                                Identification: "654321",
                            },
                        },
                    },
                    Amount: components.Amount{
                        Amount: 5.0,
                        Currency: "GBP",
                    },
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfCreateBulkPaymentRequest != nil {
        // handle response
    }
}
```
### Example Usage: UK Bulk Payment Example Response

<!-- UsageSnippet language="go" operationID="createBulkPayment" method="post" path="/bulk-payments" example="UK Bulk Payment Example Response" -->
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

    res, err := s.Payments.CreateBulkPayment(ctx, operations.CreateBulkPaymentRequest{
        Consent: "{consentToken}",
        Body: components.SubmitBulkPaymentRequest{
            IdempotencyID: yapily.Pointer("1cc3e60d-5500-42be-aaeb-3c5e2f5ed048"),
            Payments: []components.PaymentRequest{
                components.PaymentRequest{
                    PaymentIdempotencyID: "04ab4536gaerfc0e1f93c4f4",
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
                    Reference: yapily.Pointer("Bill payment"),
                    Type: components.PaymentTypeInternationalPeriodicPayment,
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
                    PeriodicPayment: &components.PeriodicPaymentRequest{
                        Frequency: components.FrequencyRequest{
                            Type: components.FrequencyEnumExtendedWeekly,
                            IntervalWeek: yapily.Pointer[int](1),
                            IntervalMonth: yapily.Pointer[int](1),
                            ExecutionDay: yapily.Pointer[int](1),
                        },
                        NumberOfPayments: yapily.Pointer[int](5),
                        NextPaymentDateTime: types.MustNewTimeFromString("2018-01-10T00:00:00Z"),
                        NextPaymentAmount: &components.Amount{
                            Amount: 10.0,
                            Currency: "GBP",
                        },
                        FinalPaymentDateTime: types.MustNewTimeFromString("2030-01-10T00:00:00Z"),
                        FinalPaymentAmount: &components.Amount{
                            Amount: 10.0,
                            Currency: "GBP",
                        },
                    },
                    Amount: components.Amount{
                        Amount: 10.0,
                        Currency: "GBP",
                    },
                    PaymentDateTime: types.MustNewTimeFromString("2021-07-21T17:32:28Z"),
                    ReadRefundAccount: yapily.Pointer(false),
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfCreateBulkPaymentRequest != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                  | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `ctx`                                                                                      | [context.Context](https://pkg.go.dev/context#Context)                                      | :heavy_check_mark:                                                                         | The context to use for the request.                                                        |
| `request`                                                                                  | [operations.CreateBulkPaymentRequest](../../models/operations/createbulkpaymentrequest.md) | :heavy_check_mark:                                                                         | The request object to use for the request.                                                 |
| `opts`                                                                                     | [][operations.Option](../../models/operations/option.md)                                   | :heavy_minus_sign:                                                                         | The options for this request.                                                              |

### Response

**[*operations.CreateBulkPaymentResponse](../../models/operations/createbulkpaymentresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetBulkPaymentStatus

Returns the bulk file status of the bulk payment for given bulkPaymentId

### Example Usage

<!-- UsageSnippet language="go" operationID="getBulkPaymentStatus" method="get" path="/bulk-payments/{bulkPaymentId}" example="Successful 200 OK" -->
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

    res, err := s.Payments.GetBulkPaymentStatus(ctx, "<value>", "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `ctx`                                                                                       | [context.Context](https://pkg.go.dev/context#Context)                                       | :heavy_check_mark:                                                                          | The context to use for the request.                                                         |
| `consent`                                                                                   | `string`                                                                                    | :heavy_check_mark:                                                                          | __Mandatory__. The `consent token` containing the user's authorisation to make the request. |
| `bulkPaymentID`                                                                             | `string`                                                                                    | :heavy_check_mark:                                                                          | __Mandatory__. Bulk payment id returned when bulk payment request was submitted.            |
| `opts`                                                                                      | [][operations.Option](../../models/operations/option.md)                                    | :heavy_minus_sign:                                                                          | The options for this request.                                                               |

### Response

**[*operations.GetBulkPaymentStatusResponse](../../models/operations/getbulkpaymentstatusresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 404                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## GetBulkPaymentDetailsByID

Retrieve details of each payment submitted for a given bulkPaymentId. 

Feature: `EXISTING_BULK_PAYMENT_DETAILS`

### Example Usage

<!-- UsageSnippet language="go" operationID="getBulkPaymentDetailsById" method="get" path="/bulk-payments/{bulkPaymentId}/details" example="Successful 200 OK" -->
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

    res, err := s.Payments.GetBulkPaymentDetailsByID(ctx, "<value>", "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.BulkPaymentDetailsResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `ctx`                                                                                       | [context.Context](https://pkg.go.dev/context#Context)                                       | :heavy_check_mark:                                                                          | The context to use for the request.                                                         |
| `consent`                                                                                   | `string`                                                                                    | :heavy_check_mark:                                                                          | __Mandatory__. The `consent token` containing the user's authorisation to make the request. |
| `bulkPaymentID`                                                                             | `string`                                                                                    | :heavy_check_mark:                                                                          | __Mandatory__. Bulk payment id returned when bulk payment request was submitted             |
| `opts`                                                                                      | [][operations.Option](../../models/operations/option.md)                                    | :heavy_minus_sign:                                                                          | The options for this request.                                                               |

### Response

**[*operations.GetBulkPaymentDetailsByIDResponse](../../models/operations/getbulkpaymentdetailsbyidresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 404                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## CreatePayment

Creates a payment after obtaining the user's authorisation. 

Features:

- `CREATE_DOMESTIC_PERIODIC_PAYMENT`
- `CREATE_DOMESTIC_SCHEDULED_PAYMENT`
- `CREATE_DOMESTIC_SINGLE_INSTANT_PAYMENT`
- `CREATE_DOMESTIC_SINGLE_PAYMENT`
- `CREATE_INTERNATIONAL_PERIODIC_PAYMENT`
- `CREATE_INTERNATIONAL_SCHEDULED_PAYMENT`
- `CREATE_INTERNATIONAL_SINGLE_PAYMENT`

### Example Usage: EUR Domestic Single Payment Example Request

<!-- UsageSnippet language="go" operationID="createPayment" method="post" path="/payments" example="EUR Domestic Single Payment Example Request" -->
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

    res, err := s.Payments.CreatePayment(ctx, operations.CreatePaymentRequest{
        Consent: "{consentToken}",
        Body: components.PaymentRequest{
            PaymentIdempotencyID: "234g87t58tgeuo848wudjew489",
            Payer: &components.Payer{
                Name: yapily.Pointer("John Doe"),
                AccountIdentifications: []components.AccountIdentification{
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeIban,
                        Identification: "DE12345678901234567890",
                    },
                },
            },
            Reference: yapily.Pointer("Bill Payment"),
            Type: components.PaymentTypeDomesticPayment,
            Payee: components.Payee{
                Name: "Jane Doe",
                AccountIdentifications: []components.AccountIdentification{
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeIban,
                        Identification: "BE12345678901234",
                    },
                },
                Address: &components.Address{
                    Country: yapily.Pointer("BE"),
                },
            },
            Amount: components.Amount{
                Amount: 1.0,
                Currency: "EUR",
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentResponse != nil {
        // handle response
    }
}
```
### Example Usage: EUR Domestic Single Payment Example Response

<!-- UsageSnippet language="go" operationID="createPayment" method="post" path="/payments" example="EUR Domestic Single Payment Example Response" -->
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

    res, err := s.Payments.CreatePayment(ctx, operations.CreatePaymentRequest{
        Consent: "{consentToken}",
        Body: components.PaymentRequest{
            PaymentIdempotencyID: "04ab4536gaerfc0e1f93c4f4",
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
            Reference: yapily.Pointer("Bill payment"),
            Type: components.PaymentTypeBulkPayment,
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
            PeriodicPayment: &components.PeriodicPaymentRequest{
                Frequency: components.FrequencyRequest{
                    Type: components.FrequencyEnumExtendedMonthly,
                    IntervalWeek: yapily.Pointer[int](1),
                    IntervalMonth: yapily.Pointer[int](1),
                    ExecutionDay: yapily.Pointer[int](1),
                },
                NumberOfPayments: yapily.Pointer[int](5),
                NextPaymentDateTime: types.MustNewTimeFromString("2018-01-10T00:00:00Z"),
                NextPaymentAmount: &components.Amount{
                    Amount: 10.0,
                    Currency: "GBP",
                },
                FinalPaymentDateTime: types.MustNewTimeFromString("2030-01-10T00:00:00Z"),
                FinalPaymentAmount: &components.Amount{
                    Amount: 10.0,
                    Currency: "GBP",
                },
            },
            Amount: components.Amount{
                Amount: 10.0,
                Currency: "GBP",
            },
            PaymentDateTime: types.MustNewTimeFromString("2021-07-21T17:32:28Z"),
            ReadRefundAccount: yapily.Pointer(false),
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentResponse != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="createPayment" method="post" path="/payments" example="Error Response" -->
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

    res, err := s.Payments.CreatePayment(ctx, operations.CreatePaymentRequest{
        Consent: "{consentToken}",
        Body: components.PaymentRequest{
            PaymentIdempotencyID: "04ab4536gaerfc0e1f93c4f4",
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
            Reference: yapily.Pointer("Bill payment"),
            Type: components.PaymentTypeBulkPayment,
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
            PeriodicPayment: &components.PeriodicPaymentRequest{
                Frequency: components.FrequencyRequest{
                    Type: components.FrequencyEnumExtendedMonthly,
                    IntervalWeek: yapily.Pointer[int](1),
                    IntervalMonth: yapily.Pointer[int](1),
                    ExecutionDay: yapily.Pointer[int](1),
                },
                NumberOfPayments: yapily.Pointer[int](5),
                NextPaymentDateTime: types.MustNewTimeFromString("2018-01-10T00:00:00Z"),
                NextPaymentAmount: &components.Amount{
                    Amount: 10.0,
                    Currency: "GBP",
                },
                FinalPaymentDateTime: types.MustNewTimeFromString("2030-01-10T00:00:00Z"),
                FinalPaymentAmount: &components.Amount{
                    Amount: 10.0,
                    Currency: "GBP",
                },
            },
            Amount: components.Amount{
                Amount: 10.0,
                Currency: "GBP",
            },
            PaymentDateTime: types.MustNewTimeFromString("2021-07-21T17:32:28Z"),
            ReadRefundAccount: yapily.Pointer(false),
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentResponse != nil {
        // handle response
    }
}
```
### Example Usage: GBP Domestic Single Payment Example Request

<!-- UsageSnippet language="go" operationID="createPayment" method="post" path="/payments" example="GBP Domestic Single Payment Example Request" -->
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

    res, err := s.Payments.CreatePayment(ctx, operations.CreatePaymentRequest{
        Consent: "{consentToken}",
        Body: components.PaymentRequest{
            PaymentIdempotencyID: "4289457hd38djoa783jw9qag3",
            Reference: yapily.Pointer("Bill Payment"),
            ContextType: components.PaymentContextTypeBillInArrears.ToPointer(),
            PurposeCode: yapily.Pointer("COMT"),
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
                AccountType: yapily.Pointer("BUSINESS_SAVING"),
                Address: &components.Address{
                    Country: yapily.Pointer("GB"),
                },
            },
            Amount: components.Amount{
                Amount: 1.0,
                Currency: "GBP",
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentResponse != nil {
        // handle response
    }
}
```
### Example Usage: GBP Domestic Single Payment Example Response

<!-- UsageSnippet language="go" operationID="createPayment" method="post" path="/payments" example="GBP Domestic Single Payment Example Response" -->
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

    res, err := s.Payments.CreatePayment(ctx, operations.CreatePaymentRequest{
        Consent: "{consentToken}",
        Body: components.PaymentRequest{
            PaymentIdempotencyID: "04ab4536gaerfc0e1f93c4f4",
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
            Reference: yapily.Pointer("Bill payment"),
            Type: components.PaymentTypeBulkPayment,
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
            PeriodicPayment: &components.PeriodicPaymentRequest{
                Frequency: components.FrequencyRequest{
                    Type: components.FrequencyEnumExtendedMonthly,
                    IntervalWeek: yapily.Pointer[int](1),
                    IntervalMonth: yapily.Pointer[int](1),
                    ExecutionDay: yapily.Pointer[int](1),
                },
                NumberOfPayments: yapily.Pointer[int](5),
                NextPaymentDateTime: types.MustNewTimeFromString("2018-01-10T00:00:00Z"),
                NextPaymentAmount: &components.Amount{
                    Amount: 10.0,
                    Currency: "GBP",
                },
                FinalPaymentDateTime: types.MustNewTimeFromString("2030-01-10T00:00:00Z"),
                FinalPaymentAmount: &components.Amount{
                    Amount: 10.0,
                    Currency: "GBP",
                },
            },
            Amount: components.Amount{
                Amount: 10.0,
                Currency: "GBP",
            },
            PaymentDateTime: types.MustNewTimeFromString("2021-07-21T17:32:28Z"),
            ReadRefundAccount: yapily.Pointer(false),
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                          | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `ctx`                                                                              | [context.Context](https://pkg.go.dev/context#Context)                              | :heavy_check_mark:                                                                 | The context to use for the request.                                                |
| `request`                                                                          | [operations.CreatePaymentRequest](../../models/operations/createpaymentrequest.md) | :heavy_check_mark:                                                                 | The request object to use for the request.                                         |
| `opts`                                                                             | [][operations.Option](../../models/operations/option.md)                           | :heavy_minus_sign:                                                                 | The options for this request.                                                      |

### Response

**[*operations.CreatePaymentResponse](../../models/operations/createpaymentresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetPayments

Returns the details of a payment. 

Most commonly used to check for payment status updates. 

Feature: `EXISTING_PAYMENTS_DETAILS`

### Example Usage: EUR Single Domestic Payment Example Response

<!-- UsageSnippet language="go" operationID="getPayments" method="get" path="/payments/{paymentId}/details" example="EUR Single Domestic Payment Example Response" -->
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

    res, err := s.Payments.GetPayments(ctx, operations.GetPaymentsRequest{
        PaymentID: "<id>",
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentResponses != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getPayments" method="get" path="/payments/{paymentId}/details" example="Error Response" -->
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

    res, err := s.Payments.GetPayments(ctx, operations.GetPaymentsRequest{
        PaymentID: "<id>",
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentResponses != nil {
        // handle response
    }
}
```
### Example Usage: GBP Single Domestic Payment Example Response

<!-- UsageSnippet language="go" operationID="getPayments" method="get" path="/payments/{paymentId}/details" example="GBP Single Domestic Payment Example Response" -->
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

    res, err := s.Payments.GetPayments(ctx, operations.GetPaymentsRequest{
        PaymentID: "<id>",
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentResponses != nil {
        // handle response
    }
}
```
### Example Usage: UK Bulk Payment Example Response

<!-- UsageSnippet language="go" operationID="getPayments" method="get" path="/payments/{paymentId}/details" example="UK Bulk Payment Example Response" -->
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

    res, err := s.Payments.GetPayments(ctx, operations.GetPaymentsRequest{
        PaymentID: "<id>",
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentResponses != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                      | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `ctx`                                                                          | [context.Context](https://pkg.go.dev/context#Context)                          | :heavy_check_mark:                                                             | The context to use for the request.                                            |
| `request`                                                                      | [operations.GetPaymentsRequest](../../models/operations/getpaymentsrequest.md) | :heavy_check_mark:                                                             | The request object to use for the request.                                     |
| `opts`                                                                         | [][operations.Option](../../models/operations/option.md)                       | :heavy_minus_sign:                                                             | The options for this request.                                                  |

### Response

**[*operations.GetPaymentsResponse](../../models/operations/getpaymentsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |