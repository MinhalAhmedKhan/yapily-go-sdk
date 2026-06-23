# Authorisations

## Overview

Before calling [Financial Data](#yapily-api-financial-data) or [Payments](#yapily-api-payments) endpoints, a consent from an end-user must be obtained.

Consents are valid for up to 90 days for Financial Data endpoints and have a single-use for Payment endpoints i.e. a new consent must be obtained for each payment.

NOTE: A user consent is also referred to as an 'Authorisation'.

### Available Operations

* [ReAuthoriseAccount](#reauthoriseaccount) - Re-authorise Account Consent
* [InitiateAccountRequest](#initiateaccountrequest) - Create Account Authorisation
* [UpdatePreAuthoriseAccountConsent](#updatepreauthoriseaccountconsent) - Update Account Pre-authorisation
* [CreateBulkPaymentAuthorisation](#createbulkpaymentauthorisation) - Create Bulk Payment Authorisation
* [InitiateEmbeddedAccountRequest](#initiateembeddedaccountrequest) - Create Embedded Account Authorisation
* [UpdateEmbeddedAccountRequest](#updateembeddedaccountrequest) - Update Embedded Account Authorisation
* [CreateEmbeddedBulkPaymentAuthorisation](#createembeddedbulkpaymentauthorisation) - Create Embedded Bulk Payment Authorisation
* [UpdateEmbeddedBulkPaymentAuthorisation](#updateembeddedbulkpaymentauthorisation) - Update Embedded Bulk Payment Authorisation
* [CreateEmbeddedPaymentAuthorisation](#createembeddedpaymentauthorisation) - Create Embedded Payment Authorisation
* [UpdateEmbeddedPaymentAuthorisation](#updateembeddedpaymentauthorisation) - Update Embedded Payment Authorisation
* [CreatePaymentAuthorisation](#createpaymentauthorisation) - Create Payment Authorisation
* [UpdatePaymentAuthorisation](#updatepaymentauthorisation) - Update Payment Pre-authorisation
* [CreatePreAuthorisationRequest](#createpreauthorisationrequest) - Create Pre-authorisation
* [CreatePaymentPreAuthorisationRequest](#createpaymentpreauthorisationrequest) - Create Payment Pre-authorisation

## ReAuthoriseAccount

Used to prompt the account holder for continued access to their financial data. This endpoint should be used when a `Consent` that was previously `AUTHORIZED` can no longer be used to retrieve data.

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="reAuthoriseAccount" method="patch" path="/account-auth-requests" example="Error Response" -->
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

    res, err := s.Authorisations.ReAuthoriseAccount(ctx, operations.ReAuthoriseAccountRequest{
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfAccountAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: OBIE Example Response

<!-- UsageSnippet language="go" operationID="reAuthoriseAccount" method="patch" path="/account-auth-requests" example="OBIE Example Response" -->
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

    res, err := s.Authorisations.ReAuthoriseAccount(ctx, operations.ReAuthoriseAccountRequest{
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfAccountAuthorisationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                    | Type                                                                                         | Required                                                                                     | Description                                                                                  |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `ctx`                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                        | :heavy_check_mark:                                                                           | The context to use for the request.                                                          |
| `request`                                                                                    | [operations.ReAuthoriseAccountRequest](../../models/operations/reauthoriseaccountrequest.md) | :heavy_check_mark:                                                                           | The request object to use for the request.                                                   |
| `opts`                                                                                       | [][operations.Option](../../models/operations/option.md)                                     | :heavy_minus_sign:                                                                           | The options for this request.                                                                |

### Response

**[*operations.ReAuthoriseAccountResponse](../../models/operations/reauthoriseaccountresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## InitiateAccountRequest

Used to initiate the authorisation process and direct users to the login screen of their financial institution in order to give consent to access account data.

Feature: `INITIATE_ACCOUNT_REQUEST`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="initiateAccountRequest" method="post" path="/account-auth-requests" example="Error Response" -->
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

    res, err := s.Authorisations.InitiateAccountRequest(ctx, operations.InitiateAccountRequestRequest{
        Body: components.AccountAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            AccountRequest: &components.AccountRequest{
                TransactionFrom: types.MustNewTimeFromString("2020-01-01T00:00:00Z"),
                TransactionTo: types.MustNewTimeFromString("2021-01-01T00:00:00Z"),
                ExpiresAt: types.MustNewTimeFromString("2025-01-01T00:00:00Z"),
                AccountIdentifiers: &components.AccountInfo{
                    AccountID: yapily.Pointer("500000000000000000000001"),
                    AccountIdentification: components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                AccountIdentifiersForTransaction: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
                AccountIdentifiersForBalance: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfAccountAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: OBIE Example Request

<!-- UsageSnippet language="go" operationID="initiateAccountRequest" method="post" path="/account-auth-requests" example="OBIE Example Request" -->
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

    res, err := s.Authorisations.InitiateAccountRequest(ctx, operations.InitiateAccountRequestRequest{
        Body: components.AccountAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("string"),
            InstitutionID: "modelo-sandbox",
            Callback: yapily.Pointer("https://display-parameters.com/"),
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfAccountAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: OBIE Example Response

<!-- UsageSnippet language="go" operationID="initiateAccountRequest" method="post" path="/account-auth-requests" example="OBIE Example Response" -->
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

    res, err := s.Authorisations.InitiateAccountRequest(ctx, operations.InitiateAccountRequestRequest{
        Body: components.AccountAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            AccountRequest: &components.AccountRequest{
                TransactionFrom: types.MustNewTimeFromString("2020-01-01T00:00:00Z"),
                TransactionTo: types.MustNewTimeFromString("2021-01-01T00:00:00Z"),
                ExpiresAt: types.MustNewTimeFromString("2025-01-01T00:00:00Z"),
                AccountIdentifiers: &components.AccountInfo{
                    AccountID: yapily.Pointer("500000000000000000000001"),
                    AccountIdentification: components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                AccountIdentifiersForTransaction: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
                AccountIdentifiersForBalance: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfAccountAuthorisationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                            | Type                                                                                                 | Required                                                                                             | Description                                                                                          |
| ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                | [context.Context](https://pkg.go.dev/context#Context)                                                | :heavy_check_mark:                                                                                   | The context to use for the request.                                                                  |
| `request`                                                                                            | [operations.InitiateAccountRequestRequest](../../models/operations/initiateaccountrequestrequest.md) | :heavy_check_mark:                                                                                   | The request object to use for the request.                                                           |
| `opts`                                                                                               | [][operations.Option](../../models/operations/option.md)                                             | :heavy_minus_sign:                                                                                   | The options for this request.                                                                        |

### Response

**[*operations.InitiateAccountRequestResponse](../../models/operations/initiateaccountrequestresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## UpdatePreAuthoriseAccountConsent

Used to continue the authorisation process and for any `Institution` that contains the `INITIATE_PRE_AUTHORISATION` feature and direct user to the login screen of their financial institution in order to give consent to access account data.

Features:

- `INITIATE_ACCOUNT_REQUEST`
- `INITIATE_PRE_AUTHORISATION`

### Example Usage: Berlin Group Example Request

<!-- UsageSnippet language="go" operationID="updatePreAuthoriseAccountConsent" method="put" path="/account-auth-requests" example="Berlin Group Example Request" -->
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

    res, err := s.Authorisations.UpdatePreAuthoriseAccountConsent(ctx, operations.UpdatePreAuthoriseAccountConsentRequest{
        Consent: "{consentToken}",
        Body: components.AccountAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("string"),
            InstitutionID: "n26",
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfAccountAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="updatePreAuthoriseAccountConsent" method="put" path="/account-auth-requests" example="Error Response" -->
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

    res, err := s.Authorisations.UpdatePreAuthoriseAccountConsent(ctx, operations.UpdatePreAuthoriseAccountConsentRequest{
        Consent: "{consentToken}",
        Body: components.AccountAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            AccountRequest: &components.AccountRequest{
                TransactionFrom: types.MustNewTimeFromString("2020-01-01T00:00:00Z"),
                TransactionTo: types.MustNewTimeFromString("2021-01-01T00:00:00Z"),
                ExpiresAt: types.MustNewTimeFromString("2025-01-01T00:00:00Z"),
                AccountIdentifiers: &components.AccountInfo{
                    AccountID: yapily.Pointer("500000000000000000000001"),
                    AccountIdentification: components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                AccountIdentifiersForTransaction: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
                AccountIdentifiersForBalance: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfAccountAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: OBIE Example Response

<!-- UsageSnippet language="go" operationID="updatePreAuthoriseAccountConsent" method="put" path="/account-auth-requests" example="OBIE Example Response" -->
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

    res, err := s.Authorisations.UpdatePreAuthoriseAccountConsent(ctx, operations.UpdatePreAuthoriseAccountConsentRequest{
        Consent: "{consentToken}",
        Body: components.AccountAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            AccountRequest: &components.AccountRequest{
                TransactionFrom: types.MustNewTimeFromString("2020-01-01T00:00:00Z"),
                TransactionTo: types.MustNewTimeFromString("2021-01-01T00:00:00Z"),
                ExpiresAt: types.MustNewTimeFromString("2025-01-01T00:00:00Z"),
                AccountIdentifiers: &components.AccountInfo{
                    AccountID: yapily.Pointer("500000000000000000000001"),
                    AccountIdentification: components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                AccountIdentifiersForTransaction: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
                AccountIdentifiersForBalance: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfAccountAuthorisationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                | Type                                                                                                                     | Required                                                                                                                 | Description                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                                    | [context.Context](https://pkg.go.dev/context#Context)                                                                    | :heavy_check_mark:                                                                                                       | The context to use for the request.                                                                                      |
| `request`                                                                                                                | [operations.UpdatePreAuthoriseAccountConsentRequest](../../models/operations/updatepreauthoriseaccountconsentrequest.md) | :heavy_check_mark:                                                                                                       | The request object to use for the request.                                                                               |
| `opts`                                                                                                                   | [][operations.Option](../../models/operations/option.md)                                                                 | :heavy_minus_sign:                                                                                                       | The options for this request.                                                                                            |

### Response

**[*operations.UpdatePreAuthoriseAccountConsentResponse](../../models/operations/updatepreauthoriseaccountconsentresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## CreateBulkPaymentAuthorisation

Used to initiate the authorisation process and direct users to the login screen of their financial Institution in order to give their consent for a bulk payment.

Feature: `INITIATE_BULK_PAYMENT`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="createBulkPaymentAuthorisation" method="post" path="/bulk-payment-auth-requests" example="Error Response" -->
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

    res, err := s.Authorisations.CreateBulkPaymentAuthorisation(ctx, components.BulkPaymentAuthorisationRequest{
        UserUUID: yapily.Pointer("e006a012-c306-4355-a6a1-99bf69ae5171"),
        ApplicationUserID: yapily.Pointer("user-234562290"),
        InstitutionID: "yapily-mock",
        Callback: yapily.Pointer("https://display-parameters.com"),
        OneTimeToken: yapily.Pointer(false),
        PaymentRequest: &components.BulkPaymentRequest{
            Payments: []components.PaymentRequest{},
        },
    }, nil, nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: UK Bulk Payment Example Request

<!-- UsageSnippet language="go" operationID="createBulkPaymentAuthorisation" method="post" path="/bulk-payment-auth-requests" example="UK Bulk Payment Example Request" -->
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

    res, err := s.Authorisations.CreateBulkPaymentAuthorisation(ctx, components.BulkPaymentAuthorisationRequest{
        ApplicationUserID: yapily.Pointer("string"),
        InstitutionID: "modelo-sandbox",
        Callback: yapily.Pointer("https://display-parameters.com/"),
        PaymentRequest: &components.BulkPaymentRequest{
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
                    ContextType: components.PaymentContextTypeBillInArrears.ToPointer(),
                    PurposeCode: yapily.Pointer("COMT"),
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
                        AccountType: yapily.Pointer("BUSINESS_SAVING"),
                    },
                    Amount: components.Amount{
                        Amount: 5.0,
                        Currency: "GBP",
                    },
                },
            },
        },
    }, nil, nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: UK Bulk Payment Example Response

<!-- UsageSnippet language="go" operationID="createBulkPaymentAuthorisation" method="post" path="/bulk-payment-auth-requests" example="UK Bulk Payment Example Response" -->
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

    res, err := s.Authorisations.CreateBulkPaymentAuthorisation(ctx, components.BulkPaymentAuthorisationRequest{
        UserUUID: yapily.Pointer("e006a012-c306-4355-a6a1-99bf69ae5171"),
        ApplicationUserID: yapily.Pointer("user-234562290"),
        InstitutionID: "yapily-mock",
        Callback: yapily.Pointer("https://display-parameters.com"),
        OneTimeToken: yapily.Pointer(false),
        PaymentRequest: &components.BulkPaymentRequest{
            Payments: []components.PaymentRequest{},
        },
    }, nil, nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentAuthorisationRequestResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                                                                                                      | Type                                                                                                                                                                                                           | Required                                                                                                                                                                                                       | Description                                                                                                                                                                                                    |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                                                                                                          | [context.Context](https://pkg.go.dev/context#Context)                                                                                                                                                          | :heavy_check_mark:                                                                                                                                                                                             | The context to use for the request.                                                                                                                                                                            |
| `body`                                                                                                                                                                                                         | [components.BulkPaymentAuthorisationRequest](../../models/components/bulkpaymentauthorisationrequest.md)                                                                                                       | :heavy_check_mark:                                                                                                                                                                                             | N/A                                                                                                                                                                                                            |
| `psuID`                                                                                                                                                                                                        | `*string`                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                             | __Conditional__. Represents the user's login ID for the `Institution` to a personal account. <br/><br/>See [PSU identifiers](/open-banking-flow/user-authorisation/psu-identifiers) to see if this header is required. |
| `psuCorporateID`                                                                                                                                                                                               | `*string`                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                             | __Conditional__. Represents the user's login ID for the `Institution` to a business account. <br/><br/>See [PSU identifiers](/open-banking-flow/user-authorisation/psu-identifiers) to see if this header is required. |
| `psuIPAddress`                                                                                                                                                                                                 | `*string`                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                             | __Conditional__. The IP address of the PSU. <br/><br/>See [PSU identifiers](/open-banking-flow/user-authorisation/psu-identifiers) to see if this header is required.                                          |
| `opts`                                                                                                                                                                                                         | [][operations.Option](../../models/operations/option.md)                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                             | The options for this request.                                                                                                                                                                                  |

### Response

**[*operations.CreateBulkPaymentAuthorisationResponse](../../models/operations/createbulkpaymentauthorisationresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## InitiateEmbeddedAccountRequest

Used to initiate the embedded authorisation process for an `Institution` that contains the `INITIATE_EMBEDDED_ACCOUNT_REQUEST` feature in order to obtain the the user's authorisation to access their account information.

Feature: `INITIATE_EMBEDDED_ACCOUNT_REQUEST`

### Example Usage: Berlin Group (Multiple SCA Methods) Example Response

<!-- UsageSnippet language="go" operationID="initiateEmbeddedAccountRequest" method="post" path="/embedded-account-auth-requests" example="Berlin Group (Multiple SCA Methods) Example Response" -->
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

    res, err := s.Authorisations.InitiateEmbeddedAccountRequest(ctx, operations.InitiateEmbeddedAccountRequestRequest{
        Body: components.EmbeddedAccountAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            UserCredentials: &components.UserCredentials{
                ID: "6154057725",
                CorporateID: yapily.Pointer("6345898763"),
                Password: "PISPWD12",
            },
            SelectedScaMethod: &components.ScaMethod{
                ID: "944",
                Type: components.TypePushOtp.ToPointer(),
                Description: yapily.Pointer("SecureSIGN"),
            },
            ScaCode: yapily.Pointer("325614"),
            AccountRequest: &components.AccountRequest{
                TransactionFrom: types.MustNewTimeFromString("2020-01-01T00:00:00Z"),
                TransactionTo: types.MustNewTimeFromString("2021-01-01T00:00:00Z"),
                ExpiresAt: types.MustNewTimeFromString("2025-01-01T00:00:00Z"),
                AccountIdentifiers: &components.AccountInfo{
                    AccountID: yapily.Pointer("500000000000000000000001"),
                    AccountIdentification: components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                AccountIdentifiersForTransaction: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
                AccountIdentifiersForBalance: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfEmbeddedAccountAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Berlin Group (Single SCA Method) Example Response

<!-- UsageSnippet language="go" operationID="initiateEmbeddedAccountRequest" method="post" path="/embedded-account-auth-requests" example="Berlin Group (Single SCA Method) Example Response" -->
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

    res, err := s.Authorisations.InitiateEmbeddedAccountRequest(ctx, operations.InitiateEmbeddedAccountRequestRequest{
        Body: components.EmbeddedAccountAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            UserCredentials: &components.UserCredentials{
                ID: "6154057725",
                CorporateID: yapily.Pointer("6345898763"),
                Password: "PISPWD12",
            },
            SelectedScaMethod: &components.ScaMethod{
                ID: "944",
                Type: components.TypePushOtp.ToPointer(),
                Description: yapily.Pointer("SecureSIGN"),
            },
            ScaCode: yapily.Pointer("325614"),
            AccountRequest: &components.AccountRequest{
                TransactionFrom: types.MustNewTimeFromString("2020-01-01T00:00:00Z"),
                TransactionTo: types.MustNewTimeFromString("2021-01-01T00:00:00Z"),
                ExpiresAt: types.MustNewTimeFromString("2025-01-01T00:00:00Z"),
                AccountIdentifiers: &components.AccountInfo{
                    AccountID: yapily.Pointer("500000000000000000000001"),
                    AccountIdentification: components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                AccountIdentifiersForTransaction: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
                AccountIdentifiersForBalance: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfEmbeddedAccountAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Berlin Group Example Request

<!-- UsageSnippet language="go" operationID="initiateEmbeddedAccountRequest" method="post" path="/embedded-account-auth-requests" example="Berlin Group Example Request" -->
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

    res, err := s.Authorisations.InitiateEmbeddedAccountRequest(ctx, operations.InitiateEmbeddedAccountRequestRequest{
        Body: components.EmbeddedAccountAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("string"),
            InstitutionID: "fiducia-sandbox",
            UserCredentials: &components.UserCredentials{
                ID: "6154057725",
                Password: "PISPWD12",
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfEmbeddedAccountAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="initiateEmbeddedAccountRequest" method="post" path="/embedded-account-auth-requests" example="Error Response" -->
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

    res, err := s.Authorisations.InitiateEmbeddedAccountRequest(ctx, operations.InitiateEmbeddedAccountRequestRequest{
        Body: components.EmbeddedAccountAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            UserCredentials: &components.UserCredentials{
                ID: "6154057725",
                CorporateID: yapily.Pointer("6345898763"),
                Password: "PISPWD12",
            },
            SelectedScaMethod: &components.ScaMethod{
                ID: "944",
                Type: components.TypePushOtp.ToPointer(),
                Description: yapily.Pointer("SecureSIGN"),
            },
            ScaCode: yapily.Pointer("325614"),
            AccountRequest: &components.AccountRequest{
                TransactionFrom: types.MustNewTimeFromString("2020-01-01T00:00:00Z"),
                TransactionTo: types.MustNewTimeFromString("2021-01-01T00:00:00Z"),
                ExpiresAt: types.MustNewTimeFromString("2025-01-01T00:00:00Z"),
                AccountIdentifiers: &components.AccountInfo{
                    AccountID: yapily.Pointer("500000000000000000000001"),
                    AccountIdentification: components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                AccountIdentifiersForTransaction: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
                AccountIdentifiersForBalance: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfEmbeddedAccountAuthorisationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                            | Type                                                                                                                 | Required                                                                                                             | Description                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                | [context.Context](https://pkg.go.dev/context#Context)                                                                | :heavy_check_mark:                                                                                                   | The context to use for the request.                                                                                  |
| `request`                                                                                                            | [operations.InitiateEmbeddedAccountRequestRequest](../../models/operations/initiateembeddedaccountrequestrequest.md) | :heavy_check_mark:                                                                                                   | The request object to use for the request.                                                                           |
| `opts`                                                                                                               | [][operations.Option](../../models/operations/option.md)                                                             | :heavy_minus_sign:                                                                                                   | The options for this request.                                                                                        |

### Response

**[*operations.InitiateEmbeddedAccountRequestResponse](../../models/operations/initiateembeddedaccountrequestresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## UpdateEmbeddedAccountRequest

Used to pass the SCA Code received from the `Institution` (and the SCA method selected by the user where multiple SCA methods are supported by the `Institution`) in order to complete the embedded authorisation to access the user's financial data.

Feature: `INITIATE_EMBEDDED_ACCOUNT_REQUEST`

### Example Usage: Berlin Group (SCA Code) Example Request

<!-- UsageSnippet language="go" operationID="updateEmbeddedAccountRequest" method="put" path="/embedded-account-auth-requests/{consentId}" example="Berlin Group (SCA Code) Example Request" -->
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

    res, err := s.Authorisations.UpdateEmbeddedAccountRequest(ctx, operations.UpdateEmbeddedAccountRequestRequest{
        ConsentID: "<id>",
        Body: components.EmbeddedAccountAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("string"),
            InstitutionID: "fiducia-sandbox",
            ScaCode: yapily.Pointer("6154057725"),
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfEmbeddedAccountAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Berlin Group (SCA Code) Example Response

<!-- UsageSnippet language="go" operationID="updateEmbeddedAccountRequest" method="put" path="/embedded-account-auth-requests/{consentId}" example="Berlin Group (SCA Code) Example Response" -->
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

    res, err := s.Authorisations.UpdateEmbeddedAccountRequest(ctx, operations.UpdateEmbeddedAccountRequestRequest{
        ConsentID: "<id>",
        Body: components.EmbeddedAccountAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            UserCredentials: &components.UserCredentials{
                ID: "6154057725",
                CorporateID: yapily.Pointer("6345898763"),
                Password: "PISPWD12",
            },
            SelectedScaMethod: &components.ScaMethod{
                ID: "944",
                Type: components.TypePushOtp.ToPointer(),
                Description: yapily.Pointer("SecureSIGN"),
            },
            ScaCode: yapily.Pointer("325614"),
            AccountRequest: &components.AccountRequest{
                TransactionFrom: types.MustNewTimeFromString("2020-01-01T00:00:00Z"),
                TransactionTo: types.MustNewTimeFromString("2021-01-01T00:00:00Z"),
                ExpiresAt: types.MustNewTimeFromString("2025-01-01T00:00:00Z"),
                AccountIdentifiers: &components.AccountInfo{
                    AccountID: yapily.Pointer("500000000000000000000001"),
                    AccountIdentification: components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                AccountIdentifiersForTransaction: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
                AccountIdentifiersForBalance: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfEmbeddedAccountAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Berlin Group (Selected SCA Method) Example Request

<!-- UsageSnippet language="go" operationID="updateEmbeddedAccountRequest" method="put" path="/embedded-account-auth-requests/{consentId}" example="Berlin Group (Selected SCA Method) Example Request" -->
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

    res, err := s.Authorisations.UpdateEmbeddedAccountRequest(ctx, operations.UpdateEmbeddedAccountRequestRequest{
        ConsentID: "<id>",
        Body: components.EmbeddedAccountAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("string"),
            InstitutionID: "fiducia-sandbox",
            SelectedScaMethod: &components.ScaMethod{
                ID: "944",
                Type: components.TypePushOtp.ToPointer(),
                Description: yapily.Pointer("SecureSIGN"),
                Information: yapily.Pointer("Bitte bestätigen Sie den Vorgang in Ihrer SecureGo plus App"),
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfEmbeddedAccountAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Berlin Group (Selected SCA Method) Example Response

<!-- UsageSnippet language="go" operationID="updateEmbeddedAccountRequest" method="put" path="/embedded-account-auth-requests/{consentId}" example="Berlin Group (Selected SCA Method) Example Response" -->
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

    res, err := s.Authorisations.UpdateEmbeddedAccountRequest(ctx, operations.UpdateEmbeddedAccountRequestRequest{
        ConsentID: "<id>",
        Body: components.EmbeddedAccountAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            UserCredentials: &components.UserCredentials{
                ID: "6154057725",
                CorporateID: yapily.Pointer("6345898763"),
                Password: "PISPWD12",
            },
            SelectedScaMethod: &components.ScaMethod{
                ID: "944",
                Type: components.TypePushOtp.ToPointer(),
                Description: yapily.Pointer("SecureSIGN"),
            },
            ScaCode: yapily.Pointer("325614"),
            AccountRequest: &components.AccountRequest{
                TransactionFrom: types.MustNewTimeFromString("2020-01-01T00:00:00Z"),
                TransactionTo: types.MustNewTimeFromString("2021-01-01T00:00:00Z"),
                ExpiresAt: types.MustNewTimeFromString("2025-01-01T00:00:00Z"),
                AccountIdentifiers: &components.AccountInfo{
                    AccountID: yapily.Pointer("500000000000000000000001"),
                    AccountIdentification: components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                AccountIdentifiersForTransaction: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
                AccountIdentifiersForBalance: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfEmbeddedAccountAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="updateEmbeddedAccountRequest" method="put" path="/embedded-account-auth-requests/{consentId}" example="Error Response" -->
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

    res, err := s.Authorisations.UpdateEmbeddedAccountRequest(ctx, operations.UpdateEmbeddedAccountRequestRequest{
        ConsentID: "<id>",
        Body: components.EmbeddedAccountAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            UserCredentials: &components.UserCredentials{
                ID: "6154057725",
                CorporateID: yapily.Pointer("6345898763"),
                Password: "PISPWD12",
            },
            SelectedScaMethod: &components.ScaMethod{
                ID: "944",
                Type: components.TypePushOtp.ToPointer(),
                Description: yapily.Pointer("SecureSIGN"),
            },
            ScaCode: yapily.Pointer("325614"),
            AccountRequest: &components.AccountRequest{
                TransactionFrom: types.MustNewTimeFromString("2020-01-01T00:00:00Z"),
                TransactionTo: types.MustNewTimeFromString("2021-01-01T00:00:00Z"),
                ExpiresAt: types.MustNewTimeFromString("2025-01-01T00:00:00Z"),
                AccountIdentifiers: &components.AccountInfo{
                    AccountID: yapily.Pointer("500000000000000000000001"),
                    AccountIdentification: components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "401016",
                    },
                },
                AccountIdentifiersForTransaction: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
                AccountIdentifiersForBalance: []components.AccountInfo{
                    components.AccountInfo{
                        AccountID: yapily.Pointer("500000000000000000000001"),
                        AccountIdentification: components.AccountIdentification{
                            Type: components.AccountIdentificationTypeSortCode,
                            Identification: "401016",
                        },
                    },
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfEmbeddedAccountAuthorisationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                        | Type                                                                                                             | Required                                                                                                         | Description                                                                                                      |
| ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                            | [context.Context](https://pkg.go.dev/context#Context)                                                            | :heavy_check_mark:                                                                                               | The context to use for the request.                                                                              |
| `request`                                                                                                        | [operations.UpdateEmbeddedAccountRequestRequest](../../models/operations/updateembeddedaccountrequestrequest.md) | :heavy_check_mark:                                                                                               | The request object to use for the request.                                                                       |
| `opts`                                                                                                           | [][operations.Option](../../models/operations/option.md)                                                         | :heavy_minus_sign:                                                                                               | The options for this request.                                                                                    |

### Response

**[*operations.UpdateEmbeddedAccountRequestResponse](../../models/operations/updateembeddedaccountrequestresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## CreateEmbeddedBulkPaymentAuthorisation

Used to initiate the embedded authorisation process for an `Institution` that contains the `INITIATE_EMBEDDED_BULK_PAYMENT` feature in order to obtain the the user's authorisation for a bulk payment. See [Bulk Payments](/payments/bulk-payments/additional-information) for more information. Feature: `INITIATE_EMBEDDED_BULK_PAYMENT`

### Example Usage: Berlin Group EUR Embedded Bulk Payment Example Request

<!-- UsageSnippet language="go" operationID="createEmbeddedBulkPaymentAuthorisation" method="post" path="/embedded-bulk-payment-auth-requests" example="Berlin Group EUR Embedded Bulk Payment Example Request" -->
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

    res, err := s.Authorisations.CreateEmbeddedBulkPaymentAuthorisation(ctx, components.BulkPaymentEmbeddedAuthorisationRequest{
        ApplicationUserID: yapily.Pointer("string"),
        InstitutionID: "fiducia-sandbox",
        PaymentRequest: &components.BulkPaymentRequest{
            Payments: []components.PaymentRequest{
                components.PaymentRequest{
                    PaymentIdempotencyID: "e4f913909a3d11eabb370242ac130002",
                    Payer: &components.Payer{
                        Name: yapily.Pointer("John Doe"),
                        AccountIdentifications: []components.AccountIdentification{
                            components.AccountIdentification{
                                Type: components.AccountIdentificationTypeIban,
                                Identification: "DE39499999600000005111",
                            },
                        },
                    },
                    Reference: yapily.Pointer("REFERENCE"),
                    Type: components.PaymentTypeDomesticPayment,
                    Payee: components.Payee{
                        Name: "Jane Doe",
                        AccountIdentifications: []components.AccountIdentification{
                            components.AccountIdentification{
                                Type: components.AccountIdentificationTypeIban,
                                Identification: "DE12345678901234567890",
                            },
                        },
                        Address: &components.Address{
                            Country: yapily.Pointer("DE"),
                        },
                    },
                    Amount: components.Amount{
                        Amount: 1.0,
                        Currency: "EUR",
                    },
                },
                components.PaymentRequest{
                    PaymentIdempotencyID: "e4f913909a3d11eabb370242ac130002",
                    Payer: &components.Payer{
                        Name: yapily.Pointer("Jane Doe"),
                        AccountIdentifications: []components.AccountIdentification{
                            components.AccountIdentification{
                                Type: components.AccountIdentificationTypeIban,
                                Identification: "DE39499999600000005111",
                            },
                        },
                    },
                    Reference: yapily.Pointer("REFERENCE"),
                    Type: components.PaymentTypeDomesticPayment,
                    Payee: components.Payee{
                        Name: "John Doe",
                        AccountIdentifications: []components.AccountIdentification{
                            components.AccountIdentification{
                                Type: components.AccountIdentificationTypeIban,
                                Identification: "DE12345678900000000000",
                            },
                        },
                        Address: &components.Address{
                            Country: yapily.Pointer("DE"),
                        },
                    },
                    Amount: components.Amount{
                        Amount: 1.0,
                        Currency: "EUR",
                    },
                },
            },
            ExecutionDateTime: types.MustNewTimeFromString("2021-10-29T00:00:00Z"),
        },
        UserCredentials: &components.UserCredentials{
            ID: "VRK1234567890PLUS",
            Password: "password",
        },
    }, nil, nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentEmbeddedAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: Berlin Group EUR Embedded Bulk Payment Example Response

<!-- UsageSnippet language="go" operationID="createEmbeddedBulkPaymentAuthorisation" method="post" path="/embedded-bulk-payment-auth-requests" example="Berlin Group EUR Embedded Bulk Payment Example Response" -->
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

    res, err := s.Authorisations.CreateEmbeddedBulkPaymentAuthorisation(ctx, components.BulkPaymentEmbeddedAuthorisationRequest{
        UserUUID: yapily.Pointer("e006a012-c306-4355-a6a1-99bf69ae5171"),
        ApplicationUserID: yapily.Pointer("user-234562290"),
        InstitutionID: "yapily-mock",
        Callback: yapily.Pointer("https://display-parameters.com"),
        OneTimeToken: yapily.Pointer(false),
        PaymentRequest: &components.BulkPaymentRequest{
            Payments: []components.PaymentRequest{},
        },
        UserCredentials: &components.UserCredentials{
            ID: "6154057725",
            CorporateID: yapily.Pointer("6345898763"),
            Password: "PISPWD12",
        },
        SelectedScaMethod: &components.ScaMethod{
            ID: "944",
            Type: components.TypePushOtp.ToPointer(),
            Description: yapily.Pointer("SecureSIGN"),
        },
        ScaCode: yapily.Pointer("325614"),
    }, nil, nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentEmbeddedAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="createEmbeddedBulkPaymentAuthorisation" method="post" path="/embedded-bulk-payment-auth-requests" example="Error Response" -->
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

    res, err := s.Authorisations.CreateEmbeddedBulkPaymentAuthorisation(ctx, components.BulkPaymentEmbeddedAuthorisationRequest{
        UserUUID: yapily.Pointer("e006a012-c306-4355-a6a1-99bf69ae5171"),
        ApplicationUserID: yapily.Pointer("user-234562290"),
        InstitutionID: "yapily-mock",
        Callback: yapily.Pointer("https://display-parameters.com"),
        OneTimeToken: yapily.Pointer(false),
        PaymentRequest: &components.BulkPaymentRequest{
            Payments: []components.PaymentRequest{},
        },
        UserCredentials: &components.UserCredentials{
            ID: "6154057725",
            CorporateID: yapily.Pointer("6345898763"),
            Password: "PISPWD12",
        },
        SelectedScaMethod: &components.ScaMethod{
            ID: "944",
            Type: components.TypePushOtp.ToPointer(),
            Description: yapily.Pointer("SecureSIGN"),
        },
        ScaCode: yapily.Pointer("325614"),
    }, nil, nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentEmbeddedAuthorisationRequestResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                                                                                                      | Type                                                                                                                                                                                                           | Required                                                                                                                                                                                                       | Description                                                                                                                                                                                                    |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                                                                                                          | [context.Context](https://pkg.go.dev/context#Context)                                                                                                                                                          | :heavy_check_mark:                                                                                                                                                                                             | The context to use for the request.                                                                                                                                                                            |
| `body`                                                                                                                                                                                                         | [components.BulkPaymentEmbeddedAuthorisationRequest](../../models/components/bulkpaymentembeddedauthorisationrequest.md)                                                                                       | :heavy_check_mark:                                                                                                                                                                                             | N/A                                                                                                                                                                                                            |
| `psuID`                                                                                                                                                                                                        | `*string`                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                             | __Conditional__. Represents the user's login ID for the `Institution` to a personal account. <br/><br/>See [PSU identifiers](/open-banking-flow/user-authorisation/psu-identifiers) to see if this header is required. |
| `psuCorporateID`                                                                                                                                                                                               | `*string`                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                             | __Conditional__. Represents the user's login ID for the `Institution` to a business account. <br/><br/>See [PSU identifiers](/open-banking-flow/user-authorisation/psu-identifiers) to see if this header is required. |
| `psuIPAddress`                                                                                                                                                                                                 | `*string`                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                             | __Conditional__. The IP address of the PSU. <br/><br/>See [PSU identifiers](/open-banking-flow/user-authorisation/psu-identifiers) to see if this header is required.                                          |
| `opts`                                                                                                                                                                                                         | [][operations.Option](../../models/operations/option.md)                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                             | The options for this request.                                                                                                                                                                                  |

### Response

**[*operations.CreateEmbeddedBulkPaymentAuthorisationResponse](../../models/operations/createembeddedbulkpaymentauthorisationresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## UpdateEmbeddedBulkPaymentAuthorisation

Used to pass the SCA Code received from the `Institution` (and the SCA method selected by the user where multiple SCA methods are supported by the `Institution`) in order to complete the embedded authorisation to initiate a bulk payment. See [Bulk Payments](/payments/bulk-payments/additional-information) for more information. Feature: `INITIATE_EMBEDDED_BULK_PAYMENT`

### Example Usage: Berlin Group EUR Embedded Bulk Payment (SCA Code) Example Request

<!-- UsageSnippet language="go" operationID="updateEmbeddedBulkPaymentAuthorisation" method="put" path="/embedded-bulk-payment-auth-requests/{consentId}" example="Berlin Group EUR Embedded Bulk Payment (SCA Code) Example Request" -->
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

    res, err := s.Authorisations.UpdateEmbeddedBulkPaymentAuthorisation(ctx, operations.UpdateEmbeddedBulkPaymentAuthorisationRequest{
        ConsentID: "<id>",
        Body: components.BulkPaymentEmbeddedAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("string"),
            InstitutionID: "fiducia-sandbox",
            PaymentRequest: &components.BulkPaymentRequest{
                Payments: []components.PaymentRequest{
                    components.PaymentRequest{
                        PaymentIdempotencyID: "e4f913909a3d11eabb370242ac130002",
                        Payer: &components.Payer{
                            Name: yapily.Pointer("John Doe"),
                            AccountIdentifications: []components.AccountIdentification{
                                components.AccountIdentification{
                                    Type: components.AccountIdentificationTypeIban,
                                    Identification: "DE39499999600000005111",
                                },
                            },
                        },
                        Reference: yapily.Pointer("REFERENCE"),
                        Type: components.PaymentTypeDomesticPayment,
                        Payee: components.Payee{
                            Name: "Jane Doe",
                            AccountIdentifications: []components.AccountIdentification{
                                components.AccountIdentification{
                                    Type: components.AccountIdentificationTypeIban,
                                    Identification: "DE12345678901234567890",
                                },
                            },
                            Address: &components.Address{
                                Country: yapily.Pointer("DE"),
                            },
                        },
                        Amount: components.Amount{
                            Amount: 1.0,
                            Currency: "EUR",
                        },
                    },
                    components.PaymentRequest{
                        PaymentIdempotencyID: "e4f913909a3d11eabb370242ac130002",
                        Payer: &components.Payer{
                            Name: yapily.Pointer("Jane Doe"),
                            AccountIdentifications: []components.AccountIdentification{
                                components.AccountIdentification{
                                    Type: components.AccountIdentificationTypeIban,
                                    Identification: "DE39499999600000005111",
                                },
                            },
                        },
                        Reference: yapily.Pointer("REFERENCE"),
                        Type: components.PaymentTypeDomesticPayment,
                        Payee: components.Payee{
                            Name: "John Doe",
                            AccountIdentifications: []components.AccountIdentification{
                                components.AccountIdentification{
                                    Type: components.AccountIdentificationTypeIban,
                                    Identification: "DE12345678900000000000",
                                },
                            },
                            Address: &components.Address{
                                Country: yapily.Pointer("DE"),
                            },
                        },
                        Amount: components.Amount{
                            Amount: 1.0,
                            Currency: "EUR",
                        },
                    },
                },
                ExecutionDateTime: types.MustNewTimeFromString("2021-10-29T00:00:00Z"),
            },
            ScaCode: yapily.Pointer("123456"),
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentEmbeddedAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: Berlin Group EUR Embedded Bulk Payment (SCA Code) Example Response

<!-- UsageSnippet language="go" operationID="updateEmbeddedBulkPaymentAuthorisation" method="put" path="/embedded-bulk-payment-auth-requests/{consentId}" example="Berlin Group EUR Embedded Bulk Payment (SCA Code) Example Response" -->
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

    res, err := s.Authorisations.UpdateEmbeddedBulkPaymentAuthorisation(ctx, operations.UpdateEmbeddedBulkPaymentAuthorisationRequest{
        ConsentID: "<id>",
        Body: components.BulkPaymentEmbeddedAuthorisationRequest{
            UserUUID: yapily.Pointer("e006a012-c306-4355-a6a1-99bf69ae5171"),
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            PaymentRequest: &components.BulkPaymentRequest{
                Payments: []components.PaymentRequest{},
            },
            UserCredentials: &components.UserCredentials{
                ID: "6154057725",
                CorporateID: yapily.Pointer("6345898763"),
                Password: "PISPWD12",
            },
            SelectedScaMethod: &components.ScaMethod{
                ID: "944",
                Type: components.TypePushOtp.ToPointer(),
                Description: yapily.Pointer("SecureSIGN"),
            },
            ScaCode: yapily.Pointer("325614"),
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentEmbeddedAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="updateEmbeddedBulkPaymentAuthorisation" method="put" path="/embedded-bulk-payment-auth-requests/{consentId}" example="Error Response" -->
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

    res, err := s.Authorisations.UpdateEmbeddedBulkPaymentAuthorisation(ctx, operations.UpdateEmbeddedBulkPaymentAuthorisationRequest{
        ConsentID: "<id>",
        Body: components.BulkPaymentEmbeddedAuthorisationRequest{
            UserUUID: yapily.Pointer("e006a012-c306-4355-a6a1-99bf69ae5171"),
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            PaymentRequest: &components.BulkPaymentRequest{
                Payments: []components.PaymentRequest{},
            },
            UserCredentials: &components.UserCredentials{
                ID: "6154057725",
                CorporateID: yapily.Pointer("6345898763"),
                Password: "PISPWD12",
            },
            SelectedScaMethod: &components.ScaMethod{
                ID: "944",
                Type: components.TypePushOtp.ToPointer(),
                Description: yapily.Pointer("SecureSIGN"),
            },
            ScaCode: yapily.Pointer("325614"),
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentEmbeddedAuthorisationRequestResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                            | Type                                                                                                                                 | Required                                                                                                                             | Description                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                                                | [context.Context](https://pkg.go.dev/context#Context)                                                                                | :heavy_check_mark:                                                                                                                   | The context to use for the request.                                                                                                  |
| `request`                                                                                                                            | [operations.UpdateEmbeddedBulkPaymentAuthorisationRequest](../../models/operations/updateembeddedbulkpaymentauthorisationrequest.md) | :heavy_check_mark:                                                                                                                   | The request object to use for the request.                                                                                           |
| `opts`                                                                                                                               | [][operations.Option](../../models/operations/option.md)                                                                             | :heavy_minus_sign:                                                                                                                   | The options for this request.                                                                                                        |

### Response

**[*operations.UpdateEmbeddedBulkPaymentAuthorisationResponse](../../models/operations/updateembeddedbulkpaymentauthorisationresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## CreateEmbeddedPaymentAuthorisation

Used to initiate the embedded authorisation process for an `Institution` that contains the `INITIATE_EMBEDDED_DOMESTIC_SINGLE_PAYMENT` feature in order to obtain the the user's authorisation for a payment. Feature: `INITIATE_EMBEDDED_DOMESTIC_SINGLE_PAYMENT`

### Example Usage: Berlin Group EUR Single Domestic Payment Example Request

<!-- UsageSnippet language="go" operationID="createEmbeddedPaymentAuthorisation" method="post" path="/embedded-payment-auth-requests" example="Berlin Group EUR Single Domestic Payment Example Request" -->
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

    res, err := s.Authorisations.CreateEmbeddedPaymentAuthorisation(ctx, operations.CreateEmbeddedPaymentAuthorisationRequest{
        Body: components.PaymentEmbeddedAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("string"),
            InstitutionID: "postbank-sandbox",
            PaymentRequest: components.PaymentRequest{
                PaymentIdempotencyID: "e4f913909a3d11eabb370242ac130002",
                Payer: &components.Payer{
                    Name: yapily.Pointer("John Doe"),
                    AccountIdentifications: []components.AccountIdentification{
                        components.AccountIdentification{
                            Type: components.AccountIdentificationTypeIban,
                            Identification: "DE12345678901234567890",
                        },
                    },
                },
                Reference: yapily.Pointer("REFERENCE"),
                Type: components.PaymentTypeDomesticPayment,
                Payee: components.Payee{
                    Name: "Jane Doe",
                    AccountIdentifications: []components.AccountIdentification{
                        components.AccountIdentification{
                            Type: components.AccountIdentificationTypeIban,
                            Identification: "DE09876543210987654321",
                        },
                    },
                    Address: &components.Address{
                        Country: yapily.Pointer("DE"),
                    },
                },
                Amount: components.Amount{
                    Amount: 1.0,
                    Currency: "EUR",
                },
            },
            UserCredentials: &components.UserCredentials{
                ID: "6154057725",
                Password: "PISPWD12",
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentEmbeddedAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: Berlin Group EUR Single Domestic Payment Example Response

<!-- UsageSnippet language="go" operationID="createEmbeddedPaymentAuthorisation" method="post" path="/embedded-payment-auth-requests" example="Berlin Group EUR Single Domestic Payment Example Response" -->
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

    res, err := s.Authorisations.CreateEmbeddedPaymentAuthorisation(ctx, operations.CreateEmbeddedPaymentAuthorisationRequest{
        Body: components.PaymentEmbeddedAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            PaymentRequest: components.PaymentRequest{
                PaymentIdempotencyID: "04ab4536gaerfc0e1f93c4f4",
                Payer: &components.Payer{
                    Name: yapily.Pointer("John Doe"),
                    AccountIdentifications: []components.AccountIdentification{},
                    Address: &components.Address{
                        Country: yapily.Pointer("GB"),
                    },
                },
                Reference: yapily.Pointer("Bill payment"),
                Type: components.PaymentTypeInternationalScheduledPayment,
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
            UserCredentials: &components.UserCredentials{
                ID: "6154057725",
                CorporateID: yapily.Pointer("6345898763"),
                Password: "PISPWD12",
            },
            SelectedScaMethod: &components.ScaMethod{
                ID: "944",
                Type: components.TypePushOtp.ToPointer(),
                Description: yapily.Pointer("SecureSIGN"),
            },
            ScaCode: yapily.Pointer("325614"),
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentEmbeddedAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="createEmbeddedPaymentAuthorisation" method="post" path="/embedded-payment-auth-requests" example="Error Response" -->
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

    res, err := s.Authorisations.CreateEmbeddedPaymentAuthorisation(ctx, operations.CreateEmbeddedPaymentAuthorisationRequest{
        Body: components.PaymentEmbeddedAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            PaymentRequest: components.PaymentRequest{
                PaymentIdempotencyID: "04ab4536gaerfc0e1f93c4f4",
                Payer: &components.Payer{
                    Name: yapily.Pointer("John Doe"),
                    AccountIdentifications: []components.AccountIdentification{},
                    Address: &components.Address{
                        Country: yapily.Pointer("GB"),
                    },
                },
                Reference: yapily.Pointer("Bill payment"),
                Type: components.PaymentTypeInternationalScheduledPayment,
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
            UserCredentials: &components.UserCredentials{
                ID: "6154057725",
                CorporateID: yapily.Pointer("6345898763"),
                Password: "PISPWD12",
            },
            SelectedScaMethod: &components.ScaMethod{
                ID: "944",
                Type: components.TypePushOtp.ToPointer(),
                Description: yapily.Pointer("SecureSIGN"),
            },
            ScaCode: yapily.Pointer("325614"),
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentEmbeddedAuthorisationRequestResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                    | Type                                                                                                                         | Required                                                                                                                     | Description                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                                                        | :heavy_check_mark:                                                                                                           | The context to use for the request.                                                                                          |
| `request`                                                                                                                    | [operations.CreateEmbeddedPaymentAuthorisationRequest](../../models/operations/createembeddedpaymentauthorisationrequest.md) | :heavy_check_mark:                                                                                                           | The request object to use for the request.                                                                                   |
| `opts`                                                                                                                       | [][operations.Option](../../models/operations/option.md)                                                                     | :heavy_minus_sign:                                                                                                           | The options for this request.                                                                                                |

### Response

**[*operations.CreateEmbeddedPaymentAuthorisationResponse](../../models/operations/createembeddedpaymentauthorisationresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## UpdateEmbeddedPaymentAuthorisation

Used to pass the SCA Code received from the `Institution` (and the SCA method selected by the user where multiple SCA methods are supported by the `Institution`) in order to complete the embedded authorisation to initiate a payment. Feature: `INITIATE_EMBEDDED_DOMESTIC_SINGLE_PAYMENT`

### Example Usage: Berlin Group EUR Single Domestic Payment (SCA Code) Example Request

<!-- UsageSnippet language="go" operationID="updateEmbeddedPaymentAuthorisation" method="put" path="/embedded-payment-auth-requests/{consentId}" example="Berlin Group EUR Single Domestic Payment (SCA Code) Example Request" -->
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

    res, err := s.Authorisations.UpdateEmbeddedPaymentAuthorisation(ctx, operations.UpdateEmbeddedPaymentAuthorisationRequest{
        ConsentID: "<id>",
        Body: components.PaymentEmbeddedAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("string"),
            InstitutionID: "postbank-sandbox",
            PaymentRequest: components.PaymentRequest{
                PaymentIdempotencyID: "e4f913909a3d11eabb370242ac130002",
                Payer: &components.Payer{
                    Name: yapily.Pointer("John Doe"),
                    AccountIdentifications: []components.AccountIdentification{
                        components.AccountIdentification{
                            Type: components.AccountIdentificationTypeIban,
                            Identification: "DE12345678901234567890",
                        },
                    },
                },
                Reference: yapily.Pointer("REFERENCE"),
                Type: components.PaymentTypeDomesticPayment,
                Payee: components.Payee{
                    Name: "Jane Doe",
                    AccountIdentifications: []components.AccountIdentification{
                        components.AccountIdentification{
                            Type: components.AccountIdentificationTypeIban,
                            Identification: "DE09876543210987654321",
                        },
                    },
                    Address: &components.Address{
                        Country: yapily.Pointer("DE"),
                    },
                },
                Amount: components.Amount{
                    Amount: 1.0,
                    Currency: "EUR",
                },
            },
            ScaCode: yapily.Pointer("325614"),
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentEmbeddedAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: Berlin Group EUR Single Domestic Payment (SCA Code) Example Response

<!-- UsageSnippet language="go" operationID="updateEmbeddedPaymentAuthorisation" method="put" path="/embedded-payment-auth-requests/{consentId}" example="Berlin Group EUR Single Domestic Payment (SCA Code) Example Response" -->
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

    res, err := s.Authorisations.UpdateEmbeddedPaymentAuthorisation(ctx, operations.UpdateEmbeddedPaymentAuthorisationRequest{
        ConsentID: "<id>",
        Body: components.PaymentEmbeddedAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            PaymentRequest: components.PaymentRequest{
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
                PeriodicPayment: &components.PeriodicPaymentRequest{
                    Frequency: components.FrequencyRequest{
                        Type: components.FrequencyEnumExtendedAnnual,
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
            UserCredentials: &components.UserCredentials{
                ID: "6154057725",
                CorporateID: yapily.Pointer("6345898763"),
                Password: "PISPWD12",
            },
            SelectedScaMethod: &components.ScaMethod{
                ID: "944",
                Type: components.TypePushOtp.ToPointer(),
                Description: yapily.Pointer("SecureSIGN"),
            },
            ScaCode: yapily.Pointer("325614"),
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentEmbeddedAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: Berlin Group EUR Single Domestic Payment (Selected SCA Method) Example Request

<!-- UsageSnippet language="go" operationID="updateEmbeddedPaymentAuthorisation" method="put" path="/embedded-payment-auth-requests/{consentId}" example="Berlin Group EUR Single Domestic Payment (Selected SCA Method) Example Request" -->
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

    res, err := s.Authorisations.UpdateEmbeddedPaymentAuthorisation(ctx, operations.UpdateEmbeddedPaymentAuthorisationRequest{
        ConsentID: "<id>",
        Body: components.PaymentEmbeddedAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("string"),
            InstitutionID: "postbank-sandbox",
            PaymentRequest: components.PaymentRequest{
                PaymentIdempotencyID: "e4f913909a3d11eabb370242ac130002",
                Payer: &components.Payer{
                    Name: yapily.Pointer("John Doe"),
                    AccountIdentifications: []components.AccountIdentification{
                        components.AccountIdentification{
                            Type: components.AccountIdentificationTypeIban,
                            Identification: "DE12345678901234567890",
                        },
                    },
                },
                Reference: yapily.Pointer("REFERENCE"),
                Type: components.PaymentTypeDomesticPayment,
                Payee: components.Payee{
                    Name: "Jane Doe",
                    AccountIdentifications: []components.AccountIdentification{
                        components.AccountIdentification{
                            Type: components.AccountIdentificationTypeIban,
                            Identification: "DE09876543210987654321",
                        },
                    },
                    Address: &components.Address{
                        Country: yapily.Pointer("DE"),
                    },
                },
                Amount: components.Amount{
                    Amount: 1.0,
                    Currency: "EUR",
                },
            },
            SelectedScaMethod: &components.ScaMethod{
                ID: "591655",
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentEmbeddedAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: Berlin Group EUR Single Domestic Payment (Selected SCA Method) Example Response

<!-- UsageSnippet language="go" operationID="updateEmbeddedPaymentAuthorisation" method="put" path="/embedded-payment-auth-requests/{consentId}" example="Berlin Group EUR Single Domestic Payment (Selected SCA Method) Example Response" -->
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

    res, err := s.Authorisations.UpdateEmbeddedPaymentAuthorisation(ctx, operations.UpdateEmbeddedPaymentAuthorisationRequest{
        ConsentID: "<id>",
        Body: components.PaymentEmbeddedAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            PaymentRequest: components.PaymentRequest{
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
                PeriodicPayment: &components.PeriodicPaymentRequest{
                    Frequency: components.FrequencyRequest{
                        Type: components.FrequencyEnumExtendedAnnual,
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
            UserCredentials: &components.UserCredentials{
                ID: "6154057725",
                CorporateID: yapily.Pointer("6345898763"),
                Password: "PISPWD12",
            },
            SelectedScaMethod: &components.ScaMethod{
                ID: "944",
                Type: components.TypePushOtp.ToPointer(),
                Description: yapily.Pointer("SecureSIGN"),
            },
            ScaCode: yapily.Pointer("325614"),
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentEmbeddedAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="updateEmbeddedPaymentAuthorisation" method="put" path="/embedded-payment-auth-requests/{consentId}" example="Error Response" -->
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

    res, err := s.Authorisations.UpdateEmbeddedPaymentAuthorisation(ctx, operations.UpdateEmbeddedPaymentAuthorisationRequest{
        ConsentID: "<id>",
        Body: components.PaymentEmbeddedAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            PaymentRequest: components.PaymentRequest{
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
                PeriodicPayment: &components.PeriodicPaymentRequest{
                    Frequency: components.FrequencyRequest{
                        Type: components.FrequencyEnumExtendedAnnual,
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
            UserCredentials: &components.UserCredentials{
                ID: "6154057725",
                CorporateID: yapily.Pointer("6345898763"),
                Password: "PISPWD12",
            },
            SelectedScaMethod: &components.ScaMethod{
                ID: "944",
                Type: components.TypePushOtp.ToPointer(),
                Description: yapily.Pointer("SecureSIGN"),
            },
            ScaCode: yapily.Pointer("325614"),
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentEmbeddedAuthorisationRequestResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                    | Type                                                                                                                         | Required                                                                                                                     | Description                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                                                        | :heavy_check_mark:                                                                                                           | The context to use for the request.                                                                                          |
| `request`                                                                                                                    | [operations.UpdateEmbeddedPaymentAuthorisationRequest](../../models/operations/updateembeddedpaymentauthorisationrequest.md) | :heavy_check_mark:                                                                                                           | The request object to use for the request.                                                                                   |
| `opts`                                                                                                                       | [][operations.Option](../../models/operations/option.md)                                                                     | :heavy_minus_sign:                                                                                                           | The options for this request.                                                                                                |

### Response

**[*operations.UpdateEmbeddedPaymentAuthorisationResponse](../../models/operations/updateembeddedpaymentauthorisationresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## CreatePaymentAuthorisation

Used to initiate the authorisation process and direct users to the login screen of their financial Institution in order to give their consent for a payment. This endpoint is used to initiate all the different payment listed below. Based on the type of payment you wish to make, you may be required to provide specific properties in [PaymentRequest](/api-reference/createPaymentAuthorisation). First make sure that the payment feature you wish to execute is supported by the bank by checking the features array in [GET Institution](/api-reference/getInstitution).

Features:

- `INITIATE_DOMESTIC_PERIODIC_PAYMENT`
- `INITIATE_DOMESTIC_SCHEDULED_PAYMENT`
- `INITIATE_DOMESTIC_SINGLE_INSTANT_PAYMENT`
- `INITIATE_DOMESTIC_SINGLE_PAYMENT`
- `INITIATE_INTERNATIONAL_PERIODIC_PAYMENT`
- `INITIATE_INTERNATIONAL_SCHEDULED_PAYMENT`
- `INITIATE_INTERNATIONAL_SINGLE_PAYMENT`

### Example Usage: EUR Single Domestic Example Request

<!-- UsageSnippet language="go" operationID="createPaymentAuthorisation" method="post" path="/payment-auth-requests" example="EUR Single Domestic Example Request" -->
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

    res, err := s.Authorisations.CreatePaymentAuthorisation(ctx, operations.CreatePaymentAuthorisationRequest{
        Body: components.PaymentAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("string"),
            InstitutionID: "bpm-sandbox",
            Callback: yapily.Pointer("https://display-parameters.com/"),
            PaymentRequest: components.PaymentRequest{
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
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: EUR Single Domestic Example Response

<!-- UsageSnippet language="go" operationID="createPaymentAuthorisation" method="post" path="/payment-auth-requests" example="EUR Single Domestic Example Response" -->
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

    res, err := s.Authorisations.CreatePaymentAuthorisation(ctx, operations.CreatePaymentAuthorisationRequest{
        Body: components.PaymentAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            PaymentRequest: components.PaymentRequest{
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
                        Type: components.FrequencyEnumExtendedCalendarDay,
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
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="createPaymentAuthorisation" method="post" path="/payment-auth-requests" example="Error Response" -->
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

    res, err := s.Authorisations.CreatePaymentAuthorisation(ctx, operations.CreatePaymentAuthorisationRequest{
        Body: components.PaymentAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            PaymentRequest: components.PaymentRequest{
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
                        Type: components.FrequencyEnumExtendedCalendarDay,
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
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: GBP Single Domestic Example Request

<!-- UsageSnippet language="go" operationID="createPaymentAuthorisation" method="post" path="/payment-auth-requests" example="GBP Single Domestic Example Request" -->
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

    res, err := s.Authorisations.CreatePaymentAuthorisation(ctx, operations.CreatePaymentAuthorisationRequest{
        Body: components.PaymentAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("string"),
            InstitutionID: "modelo-sandbox",
            Callback: yapily.Pointer("https://display-parameters.com/"),
            PaymentRequest: components.PaymentRequest{
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
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: GBP Single Domestic Example Response

<!-- UsageSnippet language="go" operationID="createPaymentAuthorisation" method="post" path="/payment-auth-requests" example="GBP Single Domestic Example Response" -->
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

    res, err := s.Authorisations.CreatePaymentAuthorisation(ctx, operations.CreatePaymentAuthorisationRequest{
        Body: components.PaymentAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            PaymentRequest: components.PaymentRequest{
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
                        Type: components.FrequencyEnumExtendedCalendarDay,
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
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentAuthorisationRequestResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                    | Type                                                                                                         | Required                                                                                                     | Description                                                                                                  |
| ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                                        | :heavy_check_mark:                                                                                           | The context to use for the request.                                                                          |
| `request`                                                                                                    | [operations.CreatePaymentAuthorisationRequest](../../models/operations/createpaymentauthorisationrequest.md) | :heavy_check_mark:                                                                                           | The request object to use for the request.                                                                   |
| `opts`                                                                                                       | [][operations.Option](../../models/operations/option.md)                                                     | :heavy_minus_sign:                                                                                           | The options for this request.                                                                                |

### Response

**[*operations.CreatePaymentAuthorisationResponse](../../models/operations/createpaymentauthorisationresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## UpdatePaymentAuthorisation

Used to continue the authorisation process and for any `Institution` that contains the `INITIATE_PRE_AUTHORISATION` feature and direct user to the login screen of their financial institution in order to give consent to initiate a payment. Feature: `INITIATE_PRE_AUTHORISATION`

### Example Usage: Berlin Group EUR Single Domestic Payment Example Request

<!-- UsageSnippet language="go" operationID="updatePaymentAuthorisation" method="put" path="/payment-auth-requests" example="Berlin Group EUR Single Domestic Payment Example Request" -->
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

    res, err := s.Authorisations.UpdatePaymentAuthorisation(ctx, operations.UpdatePaymentAuthorisationRequest{
        Consent: "{consentToken}",
        Body: components.PaymentAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("string"),
            InstitutionID: "n26",
            PaymentRequest: components.PaymentRequest{
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
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: Berlin Group EUR Single Domestic Payment Example Response

<!-- UsageSnippet language="go" operationID="updatePaymentAuthorisation" method="put" path="/payment-auth-requests" example="Berlin Group EUR Single Domestic Payment Example Response" -->
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

    res, err := s.Authorisations.UpdatePaymentAuthorisation(ctx, operations.UpdatePaymentAuthorisationRequest{
        Consent: "{consentToken}",
        Body: components.PaymentAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            PaymentRequest: components.PaymentRequest{
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
                PeriodicPayment: &components.PeriodicPaymentRequest{
                    Frequency: components.FrequencyRequest{
                        Type: components.FrequencyEnumExtendedAnnual,
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
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentAuthorisationRequestResponse != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="updatePaymentAuthorisation" method="put" path="/payment-auth-requests" example="Error Response" -->
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

    res, err := s.Authorisations.UpdatePaymentAuthorisation(ctx, operations.UpdatePaymentAuthorisationRequest{
        Consent: "{consentToken}",
        Body: components.PaymentAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            PaymentRequest: components.PaymentRequest{
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
                PeriodicPayment: &components.PeriodicPaymentRequest{
                    Frequency: components.FrequencyRequest{
                        Type: components.FrequencyEnumExtendedAnnual,
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
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPaymentAuthorisationRequestResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                    | Type                                                                                                         | Required                                                                                                     | Description                                                                                                  |
| ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                                        | :heavy_check_mark:                                                                                           | The context to use for the request.                                                                          |
| `request`                                                                                                    | [operations.UpdatePaymentAuthorisationRequest](../../models/operations/updatepaymentauthorisationrequest.md) | :heavy_check_mark:                                                                                           | The request object to use for the request.                                                                   |
| `opts`                                                                                                       | [][operations.Option](../../models/operations/option.md)                                                     | :heavy_minus_sign:                                                                                           | The options for this request.                                                                                |

### Response

**[*operations.UpdatePaymentAuthorisationResponse](../../models/operations/updatepaymentauthorisationresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## CreatePreAuthorisationRequest

Used to initiate the pre-authorisation process for any `Institution` that contains the `INITIATE_PRE_AUTHORISATION` feature to authenticate the user. 

Feature: `INITIATE_PRE_AUTHORISATION`

### Example Usage: Berlin Group (AIS) Example Request

<!-- UsageSnippet language="go" operationID="createPreAuthorisationRequest" method="post" path="/pre-auth-requests" example="Berlin Group (AIS) Example Request" -->
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

    res, err := s.Authorisations.CreatePreAuthorisationRequest(ctx, operations.CreatePreAuthorisationRequestRequest{
        Body: components.PreAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("string"),
            InstitutionID: "n26",
            Callback: yapily.Pointer("https://display-parameters.com/"),
            Scope: "AIS",
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPreAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Berlin Group (PIS) Example Request

<!-- UsageSnippet language="go" operationID="createPreAuthorisationRequest" method="post" path="/pre-auth-requests" example="Berlin Group (PIS) Example Request" -->
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

    res, err := s.Authorisations.CreatePreAuthorisationRequest(ctx, operations.CreatePreAuthorisationRequestRequest{
        Body: components.PreAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("string"),
            InstitutionID: "n26",
            Callback: yapily.Pointer("https://display-parameters.com/"),
            Scope: "PIS",
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPreAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Berlin Group Example (AIS) Response

<!-- UsageSnippet language="go" operationID="createPreAuthorisationRequest" method="post" path="/pre-auth-requests" example="Berlin Group Example (AIS) Response" -->
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

    res, err := s.Authorisations.CreatePreAuthorisationRequest(ctx, operations.CreatePreAuthorisationRequestRequest{
        Body: components.PreAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            Scope: "AIS",
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPreAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Berlin Group Example (PIS) Response

<!-- UsageSnippet language="go" operationID="createPreAuthorisationRequest" method="post" path="/pre-auth-requests" example="Berlin Group Example (PIS) Response" -->
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

    res, err := s.Authorisations.CreatePreAuthorisationRequest(ctx, operations.CreatePreAuthorisationRequestRequest{
        Body: components.PreAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            Scope: "AIS",
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPreAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="createPreAuthorisationRequest" method="post" path="/pre-auth-requests" example="Error Response" -->
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

    res, err := s.Authorisations.CreatePreAuthorisationRequest(ctx, operations.CreatePreAuthorisationRequestRequest{
        Body: components.PreAuthorisationRequest{
            ApplicationUserID: yapily.Pointer("user-234562290"),
            InstitutionID: "yapily-mock",
            Callback: yapily.Pointer("https://display-parameters.com"),
            OneTimeToken: yapily.Pointer(false),
            Scope: "AIS",
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPreAuthorisationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                          | Type                                                                                                               | Required                                                                                                           | Description                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                              | [context.Context](https://pkg.go.dev/context#Context)                                                              | :heavy_check_mark:                                                                                                 | The context to use for the request.                                                                                |
| `request`                                                                                                          | [operations.CreatePreAuthorisationRequestRequest](../../models/operations/createpreauthorisationrequestrequest.md) | :heavy_check_mark:                                                                                                 | The request object to use for the request.                                                                         |
| `opts`                                                                                                             | [][operations.Option](../../models/operations/option.md)                                                           | :heavy_minus_sign:                                                                                                 | The options for this request.                                                                                      |

### Response

**[*operations.CreatePreAuthorisationRequestResponse](../../models/operations/createpreauthorisationrequestresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## CreatePaymentPreAuthorisationRequest

Used to initiate the pre-authorisation process for payments for CBI Globe institutions that contain the `INITIATE_ONETIME_PRE_AUTHORISATION_PAYMENTS` feature to authenticate the user. 

Feature: `INITIATE_ONETIME_PRE_AUTHORISATION_PAYMENTS`

### Example Usage: Berlin Group Example (PIS) Response

<!-- UsageSnippet language="go" operationID="createPaymentPreAuthorisationRequest" method="post" path="/payment-pre-auth-requests" example="Berlin Group Example (PIS) Response" -->
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

    res, err := s.Authorisations.CreatePaymentPreAuthorisationRequest(ctx, components.PaymentPreAuthorisationRequest{
        ApplicationUserID: yapily.Pointer("user-234562290"),
        InstitutionID: "yapily-mock",
        Callback: yapily.Pointer("https://display-parameters.com"),
        OneTimeToken: yapily.Pointer(false),
        Scope: "AIS",
        Payee: components.PayeeDetails{
            Name: "Jane Doe",
            AccountIdentifications: []components.AccountIdentification{
                components.AccountIdentification{
                    Type: components.AccountIdentificationTypeIban,
                    Identification: "IBUK123456789",
                },
            },
            Country: "GB",
            Address: &components.Address{
                Country: yapily.Pointer("GB"),
            },
        },
        Payer: components.PayerDetails{
            AccountIdentifications: []components.AccountIdentification{},
        },
        Amount: components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
        Reference: "Bill payment",
    }, nil, nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPreAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: CBI Globe (PIS) example request

<!-- UsageSnippet language="go" operationID="createPaymentPreAuthorisationRequest" method="post" path="/payment-pre-auth-requests" example="CBI Globe (PIS) example request" -->
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

    res, err := s.Authorisations.CreatePaymentPreAuthorisationRequest(ctx, components.PaymentPreAuthorisationRequest{
        ApplicationUserID: yapily.Pointer("string"),
        InstitutionID: "n26",
        Callback: yapily.Pointer("https://display-parameters.com/"),
        Scope: "PIS",
        Payee: components.PayeeDetails{
            Name: "Jane Doe",
            AccountIdentifications: []components.AccountIdentification{
                components.AccountIdentification{
                    Type: components.AccountIdentificationTypeIban,
                    Identification: "BE12345678901234",
                },
            },
            Country: "BE",
        },
        Payer: components.PayerDetails{
            AccountIdentifications: []components.AccountIdentification{
                components.AccountIdentification{
                    Type: components.AccountIdentificationTypeIban,
                    Identification: "DE12345678901234567890",
                },
            },
        },
        Amount: components.Amount{
            Amount: 1.0,
            Currency: "EUR",
        },
        Reference: "Bill Payment",
    }, nil, nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPreAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="createPaymentPreAuthorisationRequest" method="post" path="/payment-pre-auth-requests" example="Error Response" -->
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

    res, err := s.Authorisations.CreatePaymentPreAuthorisationRequest(ctx, components.PaymentPreAuthorisationRequest{
        ApplicationUserID: yapily.Pointer("user-234562290"),
        InstitutionID: "yapily-mock",
        Callback: yapily.Pointer("https://display-parameters.com"),
        OneTimeToken: yapily.Pointer(false),
        Scope: "AIS",
        Payee: components.PayeeDetails{
            Name: "Jane Doe",
            AccountIdentifications: []components.AccountIdentification{
                components.AccountIdentification{
                    Type: components.AccountIdentificationTypeIban,
                    Identification: "IBUK123456789",
                },
            },
            Country: "GB",
            Address: &components.Address{
                Country: yapily.Pointer("GB"),
            },
        },
        Payer: components.PayerDetails{
            AccountIdentifications: []components.AccountIdentification{},
        },
        Amount: components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
        Reference: "Bill payment",
    }, nil, nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfPreAuthorisationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                                                     | Type                                                                                                                                                          | Required                                                                                                                                                      | Description                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                                                         | [context.Context](https://pkg.go.dev/context#Context)                                                                                                         | :heavy_check_mark:                                                                                                                                            | The context to use for the request.                                                                                                                           |
| `body`                                                                                                                                                        | [components.PaymentPreAuthorisationRequest](../../models/components/paymentpreauthorisationrequest.md)                                                        | :heavy_check_mark:                                                                                                                                            | N/A                                                                                                                                                           |
| `raw`                                                                                                                                                         | `*bool`                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                            | __Optional__. Used to obtain the raw request and response to and from the `Institution`.                                                                      |
| `psuIPAddress`                                                                                                                                                | `*string`                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                            | __Conditional__. The IP address of the PSU. <br/><br/>See [PSU identifiers](/open-banking-flow/user-authorisation/psu-identifiers) to see if this header is required. |
| `subApplication`                                                                                                                                              | `*string`                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                            | The sub-application ID to which event type is being subscribed to                                                                                             |
| `opts`                                                                                                                                                        | [][operations.Option](../../models/operations/option.md)                                                                                                      | :heavy_minus_sign:                                                                                                                                            | The options for this request.                                                                                                                                 |

### Response

**[*operations.CreatePaymentPreAuthorisationRequestResponse](../../models/operations/createpaymentpreauthorisationrequestresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |