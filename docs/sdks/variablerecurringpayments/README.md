# VariableRecurringPayments

## Overview

Variable Recurring Payments enables transfer of money between accounts held by the same person or transfer of money for business payments. 

In order to make Sweeping Variable Recurring Payments on behalf of a user, you are required to request an [Consent](#tag/Authorisations) from the user by calling the Sweeping Consent endpoint to authorise the user's account to make the payment. Once a `consent-token` is obtained, you can call the Payments endpoint to execute the Sweeping Variable Recurring Payments transaction. Before executing the payment, you have the option to confirm availability of funds in the user's account by calling the Funds Confirmation endpoint. 

See [VRP Payments](/payments/vrps/additional-information) for more information.

### Available Operations

* [CreateSweepingAuthorisation](#createsweepingauthorisation) - Create Sweeping VRP Authorisation
* [GetSweepingVrpConsentByID](#getsweepingvrpconsentbyid) - Get Sweeping VRP Consent Details
* [GetCommercialVrpConsentByID](#getcommercialvrpconsentbyid) - Get Commercial VRP Consent Details
* [CreateVrpFundsConfirmation](#createvrpfundsconfirmation) - Confirm Funds for VRP Payment
* [CreateVrpPayment](#createvrppayment) - Create VRP Payment
* [GetVrpPaymentDetails](#getvrppaymentdetails) - Get VRP Payment Details

## CreateSweepingAuthorisation

Initiate authorisation for a Sweeping [VRP](/payments/vrps/introduction) consent.

The response will contain an Authorisation URL and the associated Consent ID. The user will have to complete authorisation of the consent at their institution via [Redirect Flows](/getting-started/glossary#redirect-flow), after which you will be able to use the authorised consent to create payments.

Feature:

- `INITIATE_DOMESTIC_VARIABLE_RECURRING_PAYMENT_SWEEPING`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="createSweepingAuthorisation" method="post" path="/variable-recurring-payments/sweeping/consents" example="Error Response" -->
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

    res, err := s.VariableRecurringPayments.CreateSweepingAuthorisation(ctx, components.VrpSweepingAuthorisationRequest{
        InstitutionID: "<id>",
        ControlParameters: components.VrpControlParameters{
            PsuAuthenticationMethods: []string{
                "<value 1>",
            },
            MaxAmountPerPayment: components.Amount{
                Amount: 10.0,
                Currency: "GBP",
            },
            PeriodicLimits: []components.VrpPeriodicLimits{},
        },
        InitiationDetails: components.VrpInitiationDetails{
            Payer: &components.Payer{
                Name: yapily.Pointer("John Doe"),
                AccountIdentifications: []components.AccountIdentification{},
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
        ComplianceData: &components.VrpComplianceData{
            Payer: &components.VrpComplianceDataPayer{
                Type: "INDIVIDUAL",
                Individual: &components.VrpComplianceDataIndividual{
                    Name: "John Doe",
                    BirthDate: types.MustDateFromString("2000-08-12"),
                },
                Business: &components.VrpComplianceDataBusiness{
                    Name: "Company LTD",
                    RegistrationNumber: "COM123NO",
                    RegisteredAddress: components.VrpComplianceDataAddress{
                        AddressLine1: "123 Queens Street",
                        AddressLine2: yapily.Pointer("Unit 13"),
                        TownName: "York",
                        PostCode: "12345",
                        Country: "GB",
                    },
                    TradingAddress: &components.VrpComplianceDataAddress{
                        AddressLine1: "123 Queens Street",
                        AddressLine2: yapily.Pointer("Unit 13"),
                        TownName: "York",
                        PostCode: "12345",
                        Country: "GB",
                    },
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfVrpSweepingAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: UK Domestic Sweeping VRP Authorisation Response

<!-- UsageSnippet language="go" operationID="createSweepingAuthorisation" method="post" path="/variable-recurring-payments/sweeping/consents" example="UK Domestic Sweeping VRP Authorisation Response" -->
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

    res, err := s.VariableRecurringPayments.CreateSweepingAuthorisation(ctx, components.VrpSweepingAuthorisationRequest{
        InstitutionID: "<id>",
        ControlParameters: components.VrpControlParameters{
            PsuAuthenticationMethods: []string{
                "<value 1>",
            },
            MaxAmountPerPayment: components.Amount{
                Amount: 10.0,
                Currency: "GBP",
            },
            PeriodicLimits: []components.VrpPeriodicLimits{},
        },
        InitiationDetails: components.VrpInitiationDetails{
            Payer: &components.Payer{
                Name: yapily.Pointer("John Doe"),
                AccountIdentifications: []components.AccountIdentification{},
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
        ComplianceData: &components.VrpComplianceData{
            Payer: &components.VrpComplianceDataPayer{
                Type: "INDIVIDUAL",
                Individual: &components.VrpComplianceDataIndividual{
                    Name: "John Doe",
                    BirthDate: types.MustDateFromString("2000-08-12"),
                },
                Business: &components.VrpComplianceDataBusiness{
                    Name: "Company LTD",
                    RegistrationNumber: "COM123NO",
                    RegisteredAddress: components.VrpComplianceDataAddress{
                        AddressLine1: "123 Queens Street",
                        AddressLine2: yapily.Pointer("Unit 13"),
                        TownName: "York",
                        PostCode: "12345",
                        Country: "GB",
                    },
                    TradingAddress: &components.VrpComplianceDataAddress{
                        AddressLine1: "123 Queens Street",
                        AddressLine2: yapily.Pointer("Unit 13"),
                        TownName: "York",
                        PostCode: "12345",
                        Country: "GB",
                    },
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfVrpSweepingAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: UK Sweeping VRP Authorisation Request

<!-- UsageSnippet language="go" operationID="createSweepingAuthorisation" method="post" path="/variable-recurring-payments/sweeping/consents" example="UK Sweeping VRP Authorisation Request" -->
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

    res, err := s.VariableRecurringPayments.CreateSweepingAuthorisation(ctx, components.VrpSweepingAuthorisationRequest{
        UserUUID: yapily.Pointer("00000000-0000-0000-0000-000000000000"),
        InstitutionID: "mock-sandbox",
        Callback: yapily.Pointer("https://parameter-viewer.yapily.com/"),
        ControlParameters: components.VrpControlParameters{
            PsuAuthenticationMethods: []string{
                "SCA_NOT_REQUIRED",
            },
            MaxAmountPerPayment: components.Amount{
                Amount: 10.0,
                Currency: "GBP",
            },
            PeriodicLimits: []components.VrpPeriodicLimits{
                components.VrpPeriodicLimits{
                    Frequency: "MONTHLY",
                    TotalMaxAmount: components.Amount{
                        Amount: 50.0,
                        Currency: "GBP",
                    },
                    Alignment: "CONSENT",
                },
            },
        },
        InitiationDetails: components.VrpInitiationDetails{
            Reference: yapily.Pointer("My Sweeping VRP"),
            Payer: &components.Payer{
                Name: yapily.Pointer("Payer"),
                AccountIdentifications: []components.AccountIdentification{
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeAccountNumber,
                        Identification: "87654321",
                    },
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "332211",
                    },
                },
            },
            Payee: &components.Payee{
                Name: "Payee",
                AccountIdentifications: []components.AccountIdentification{
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeAccountNumber,
                        Identification: "12345678",
                    },
                    components.AccountIdentification{
                        Type: components.AccountIdentificationTypeSortCode,
                        Identification: "112233",
                    },
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfVrpSweepingAuthorisationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                | Type                                                                                                     | Required                                                                                                 | Description                                                                                              |
| -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                    | [context.Context](https://pkg.go.dev/context#Context)                                                    | :heavy_check_mark:                                                                                       | The context to use for the request.                                                                      |
| `request`                                                                                                | [components.VrpSweepingAuthorisationRequest](../../models/components/vrpsweepingauthorisationrequest.md) | :heavy_check_mark:                                                                                       | The request object to use for the request.                                                               |
| `opts`                                                                                                   | [][operations.Option](../../models/operations/option.md)                                                 | :heavy_minus_sign:                                                                                       | The options for this request.                                                                            |

### Response

**[*operations.CreateSweepingAuthorisationResponse](../../models/operations/createsweepingauthorisationresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponse     | 401                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## GetSweepingVrpConsentByID

Get Sweeping [VRP](/payments/vrps/introduction) consent details from the Consent ID.

Feature: `CREATE_DOMESTIC_VARIABLE_RECURRING_PAYMENT_SWEEPING`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getSweepingVrpConsentById" method="get" path="/variable-recurring-payments/sweeping/consents/{consentId}" example="Error Response" -->
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

    res, err := s.VariableRecurringPayments.GetSweepingVrpConsentByID(ctx, "951c05b4-2313-446b-8cc6-72bdd9a4868d")
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfVrpSweepingAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: UK Sweeping VRP Consent Details Response

<!-- UsageSnippet language="go" operationID="getSweepingVrpConsentById" method="get" path="/variable-recurring-payments/sweeping/consents/{consentId}" example="UK Sweeping VRP Consent Details Response" -->
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

    res, err := s.VariableRecurringPayments.GetSweepingVrpConsentByID(ctx, "84160353-25ca-4e7c-acb8-00145f08d0af")
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfVrpSweepingAuthorisationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `consentID`                                              | `string`                                                 | :heavy_check_mark:                                       | The Consent ID to retrieve.                              |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetSweepingVrpConsentByIDResponse](../../models/operations/getsweepingvrpconsentbyidresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponse     | 401                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## GetCommercialVrpConsentByID

Get Commercial [VRP](/payments/vrps/introduction) consent details from the Consent ID.

Feature: `CREATE_DOMESTIC_VARIABLE_RECURRING_PAYMENT_COMMERCIAL`

Note that Commercial VRP authorisation/initiation is currently only available through a Hosted VRP flow (specifically, `POST /hosted/vrp-requests`).

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getCommercialVrpConsentById" method="get" path="/variable-recurring-payments/commercial/consents/{consentId}" example="Error Response" -->
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

    res, err := s.VariableRecurringPayments.GetCommercialVrpConsentByID(ctx, "bbbb23ab-093b-41bd-94f2-e3f8aebf713e")
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfVrpCommercialAuthorisationResponse != nil {
        // handle response
    }
}
```
### Example Usage: UK Commercial VRP Consent Details Response

<!-- UsageSnippet language="go" operationID="getCommercialVrpConsentById" method="get" path="/variable-recurring-payments/commercial/consents/{consentId}" example="UK Commercial VRP Consent Details Response" -->
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

    res, err := s.VariableRecurringPayments.GetCommercialVrpConsentByID(ctx, "0f77f3c7-5fe2-4084-a799-de4066c62656")
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfVrpCommercialAuthorisationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `consentID`                                              | `string`                                                 | :heavy_check_mark:                                       | The Consent ID to retrieve.                              |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetCommercialVrpConsentByIDResponse](../../models/operations/getcommercialvrpconsentbyidresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponse     | 401                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## CreateVrpFundsConfirmation

Check whether the requested funds amount is available on the [VRP](/payments/vrps/introduction) consent.

Note that you should not call this before each VRP payment submission because we do it for you.

Required feature: `VARIABLE_RECURRING_PAYMENT_FUNDS_CONFIRMATION`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="createVrpFundsConfirmation" method="post" path="/variable-recurring-payments/funds-confirmation" example="Error Response" -->
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

    res, err := s.VariableRecurringPayments.CreateVrpFundsConfirmation(ctx, "{consentToken}", components.VrpFundsConfirmationRequest{
        PaymentAmount: components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfVrpFundsConfirmationResponse != nil {
        // handle response
    }
}
```
### Example Usage: UK VRP Funds Confirmation Request

<!-- UsageSnippet language="go" operationID="createVrpFundsConfirmation" method="post" path="/variable-recurring-payments/funds-confirmation" example="UK VRP Funds Confirmation Request" -->
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

    res, err := s.VariableRecurringPayments.CreateVrpFundsConfirmation(ctx, "{consentToken}", components.VrpFundsConfirmationRequest{
        PaymentAmount: components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
        Reference: yapily.Pointer("Own Account Commercial"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfVrpFundsConfirmationResponse != nil {
        // handle response
    }
}
```
### Example Usage: UK VRP Funds Confirmation Response

<!-- UsageSnippet language="go" operationID="createVrpFundsConfirmation" method="post" path="/variable-recurring-payments/funds-confirmation" example="UK VRP Funds Confirmation Response" -->
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

    res, err := s.VariableRecurringPayments.CreateVrpFundsConfirmation(ctx, "{consentToken}", components.VrpFundsConfirmationRequest{
        PaymentAmount: components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfVrpFundsConfirmationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      | Example                                                                                          |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                            | [context.Context](https://pkg.go.dev/context#Context)                                            | :heavy_check_mark:                                                                               | The context to use for the request.                                                              |                                                                                                  |
| `consent`                                                                                        | `string`                                                                                         | :heavy_check_mark:                                                                               | The user's VRP [Consent Token](/getting-started/glossary#consent-token)                          | {consentToken}                                                                                   |
| `body`                                                                                           | [components.VrpFundsConfirmationRequest](../../models/components/vrpfundsconfirmationrequest.md) | :heavy_check_mark:                                                                               | N/A                                                                                              |                                                                                                  |
| `opts`                                                                                           | [][operations.Option](../../models/operations/option.md)                                         | :heavy_minus_sign:                                                                               | The options for this request.                                                                    |                                                                                                  |

### Response

**[*operations.CreateVrpFundsConfirmationResponse](../../models/operations/createvrpfundsconfirmationresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponse     | 401                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## CreateVrpPayment

Submit payment on the [VRP](/payments/vrps/introduction) consent.

Required feature: `CREATE_DOMESTIC_VARIABLE_RECURRING_PAYMENT_SWEEPING` or `CREATE_DOMESTIC_VARIABLE_RECURRING_PAYMENT_COMMERCIAL`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="createVrpPayment" method="post" path="/variable-recurring-payments/payments" example="Error Response" -->
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

    res, err := s.VariableRecurringPayments.CreateVrpPayment(ctx, "{consentToken}", components.VrpSubmissionRequest{
        PaymentIdempotencyID: "<id>",
        PsuAuthenticationMethod: "<value>",
        PaymentAmount: components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfVrpSubmissionResponse != nil {
        // handle response
    }
}
```
### Example Usage: UK VRP Payment Request

<!-- UsageSnippet language="go" operationID="createVrpPayment" method="post" path="/variable-recurring-payments/payments" example="UK VRP Payment Request" -->
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

    res, err := s.VariableRecurringPayments.CreateVrpPayment(ctx, "{consentToken}", components.VrpSubmissionRequest{
        PaymentIdempotencyID: "234g87t58tgeuo848wudjew489",
        PsuAuthenticationMethod: "SCA_NOT_REQUIRED",
        PsuInteractionType: yapily.Pointer("PSU_PRESENT"),
        PaymentAmount: components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfVrpSubmissionResponse != nil {
        // handle response
    }
}
```
### Example Usage: UK VRP Payment Response

<!-- UsageSnippet language="go" operationID="createVrpPayment" method="post" path="/variable-recurring-payments/payments" example="UK VRP Payment Response" -->
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

    res, err := s.VariableRecurringPayments.CreateVrpPayment(ctx, "{consentToken}", components.VrpSubmissionRequest{
        PaymentIdempotencyID: "<id>",
        PsuAuthenticationMethod: "<value>",
        PaymentAmount: components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfVrpSubmissionResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                          | Type                                                                               | Required                                                                           | Description                                                                        | Example                                                                            |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `ctx`                                                                              | [context.Context](https://pkg.go.dev/context#Context)                              | :heavy_check_mark:                                                                 | The context to use for the request.                                                |                                                                                    |
| `consent`                                                                          | `string`                                                                           | :heavy_check_mark:                                                                 | The user's VRP [Consent Token](/getting-started/glossary#consent-token)            | {consentToken}                                                                     |
| `body`                                                                             | [components.VrpSubmissionRequest](../../models/components/vrpsubmissionrequest.md) | :heavy_check_mark:                                                                 | N/A                                                                                |                                                                                    |
| `opts`                                                                             | [][operations.Option](../../models/operations/option.md)                           | :heavy_minus_sign:                                                                 | The options for this request.                                                      |                                                                                    |

### Response

**[*operations.CreateVrpPaymentResponse](../../models/operations/createvrppaymentresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponse     | 401                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## GetVrpPaymentDetails

Get [VRP](/payments/vrps/introduction) payment details from the Payment ID.

Features: `CREATE_DOMESTIC_VARIABLE_RECURRING_PAYMENT_SWEEPING` or `CREATE_DOMESTIC_VARIABLE_RECURRING_PAYMENT_COMMERCIAL`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getVrpPaymentDetails" method="get" path="/variable-recurring-payments/payments/{paymentId}/details" example="Error Response" -->
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

    res, err := s.VariableRecurringPayments.GetVrpPaymentDetails(ctx, "<id>", "<value>")
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfVrpSubmissionResponse != nil {
        // handle response
    }
}
```
### Example Usage: UK VRP Payment Details Response

<!-- UsageSnippet language="go" operationID="getVrpPaymentDetails" method="get" path="/variable-recurring-payments/payments/{paymentId}/details" example="UK VRP Payment Details Response" -->
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

    res, err := s.VariableRecurringPayments.GetVrpPaymentDetails(ctx, "<id>", "<value>")
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfVrpSubmissionResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                                                          | Type                                                                                                                                                               | Required                                                                                                                                                           | Description                                                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                                                                              | [context.Context](https://pkg.go.dev/context#Context)                                                                                                              | :heavy_check_mark:                                                                                                                                                 | The context to use for the request.                                                                                                                                |
| `paymentID`                                                                                                                                                        | `string`                                                                                                                                                           | :heavy_check_mark:                                                                                                                                                 | __Mandatory__. The Payment Id of the `Variable Recurring Payments` to retrieve.                                                                                    |
| `consent`                                                                                                                                                          | `string`                                                                                                                                                           | :heavy_check_mark:                                                                                                                                                 | __Mandatory__. The [Consent Token](/getting-started/glossary#consent-token) containing the user's authorisation to make the `Variable Recurring Payments` request. |
| `opts`                                                                                                                                                             | [][operations.Option](../../models/operations/option.md)                                                                                                           | :heavy_minus_sign:                                                                                                                                                 | The options for this request.                                                                                                                                      |

### Response

**[*operations.GetVrpPaymentDetailsResponse](../../models/operations/getvrppaymentdetailsresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponse     | 401                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |