# FinancialData

## Overview

In order to access a user's Financial Data, you are required to request an [Authorisation](#tag/Authorisations) from the user to share the account information the bank has. Once a `consent-token` is obtained, you can call the necessary Financial Data endpoint(s) to retrieve the user's data.

### Available Operations

* [GetAccounts](#getaccounts) - Get Accounts
* [GetAccount](#getaccount) - Get Account
* [GetAccountBalances](#getaccountbalances) - Get Account Balances
* [GetBeneficiaries](#getbeneficiaries) - Get Account Beneficiaries
* [GetAccountDirectDebits](#getaccountdirectdebits) - Get Account Direct Debits
* [GetAccountPeriodicPayments](#getaccountperiodicpayments) - Get Account Periodic Payments
* [GetAccountScheduledPayments](#getaccountscheduledpayments) - Get Account Scheduled Payments
* [GetStatements](#getstatements) - Get Account Statements
* [GetStatement](#getstatement) - Get Account Statement
* [GetStatementFile](#getstatementfile) - Get Account Statement File
* [GetTransactions](#gettransactions) - Get Account Transactions
* [GetIdentity](#getidentity) - Get Identity
* [GetRealTimeTransactions](#getrealtimetransactions) - Get Real Time Account Transactions

## GetAccounts

Returns all accounts and balances for the end user associated with the presented consent token.

Feature: `ACCOUNTS`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getAccounts" method="get" path="/accounts" example="Error Response" -->
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

    res, err := s.FinancialData.GetAccounts(ctx, operations.GetAccountsRequest{
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.AccountAPIListResponse != nil {
        // handle response
    }
}
```
### Example Usage: OBIE Example Response

<!-- UsageSnippet language="go" operationID="getAccounts" method="get" path="/accounts" example="OBIE Example Response" -->
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

    res, err := s.FinancialData.GetAccounts(ctx, operations.GetAccountsRequest{
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.AccountAPIListResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                      | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `ctx`                                                                          | [context.Context](https://pkg.go.dev/context#Context)                          | :heavy_check_mark:                                                             | The context to use for the request.                                            |
| `request`                                                                      | [operations.GetAccountsRequest](../../models/operations/getaccountsrequest.md) | :heavy_check_mark:                                                             | The request object to use for the request.                                     |
| `opts`                                                                         | [][operations.Option](../../models/operations/option.md)                       | :heavy_minus_sign:                                                             | The options for this request.                                                  |

### Response

**[*operations.GetAccountsResponse](../../models/operations/getaccountsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetAccount

Returns the account and balance information for a user's specified account.

Feature: `ACCOUNT`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getAccount" method="get" path="/accounts/{accountId}" example="Error Response" -->
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

    res, err := s.FinancialData.GetAccount(ctx, operations.GetAccountRequest{
        AccountID: "<id>",
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfAccount != nil {
        // handle response
    }
}
```
### Example Usage: OBIE Example Response

<!-- UsageSnippet language="go" operationID="getAccount" method="get" path="/accounts/{accountId}" example="OBIE Example Response" -->
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

    res, err := s.FinancialData.GetAccount(ctx, operations.GetAccountRequest{
        AccountID: "<id>",
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfAccount != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                    | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `ctx`                                                                        | [context.Context](https://pkg.go.dev/context#Context)                        | :heavy_check_mark:                                                           | The context to use for the request.                                          |
| `request`                                                                    | [operations.GetAccountRequest](../../models/operations/getaccountrequest.md) | :heavy_check_mark:                                                           | The request object to use for the request.                                   |
| `opts`                                                                       | [][operations.Option](../../models/operations/option.md)                     | :heavy_minus_sign:                                                           | The options for this request.                                                |

### Response

**[*operations.GetAccountResponse](../../models/operations/getaccountresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetAccountBalances

Returns the balance for the end user associated with the presented consent token.

Feature: `ACCOUNT_BALANCES`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getAccountBalances" method="get" path="/accounts/{accountId}/balances" example="Error Response" -->
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

    res, err := s.FinancialData.GetAccountBalances(ctx, operations.GetAccountBalancesRequest{
        AccountID: "<id>",
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfBalances != nil {
        // handle response
    }
}
```
### Example Usage: Example response

<!-- UsageSnippet language="go" operationID="getAccountBalances" method="get" path="/accounts/{accountId}/balances" example="Example response" -->
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

    res, err := s.FinancialData.GetAccountBalances(ctx, operations.GetAccountBalancesRequest{
        AccountID: "<id>",
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfBalances != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                    | Type                                                                                         | Required                                                                                     | Description                                                                                  |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `ctx`                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                        | :heavy_check_mark:                                                                           | The context to use for the request.                                                          |
| `request`                                                                                    | [operations.GetAccountBalancesRequest](../../models/operations/getaccountbalancesrequest.md) | :heavy_check_mark:                                                                           | The request object to use for the request.                                                   |
| `opts`                                                                                       | [][operations.Option](../../models/operations/option.md)                                     | :heavy_minus_sign:                                                                           | The options for this request.                                                                |

### Response

**[*operations.GetAccountBalancesResponse](../../models/operations/getaccountbalancesresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetBeneficiaries

Returns all the beneficiaries of a user's account.

Feature: `ACCOUNT_BENEFICIARIES`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getBeneficiaries" method="get" path="/accounts/{accountId}/beneficiaries" example="Error Response" -->
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

    res, err := s.FinancialData.GetBeneficiaries(ctx, "<id>", "{consentToken}", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfBeneficiary != nil {
        // handle response
    }
}
```
### Example Usage: OBIE Example Response

<!-- UsageSnippet language="go" operationID="getBeneficiaries" method="get" path="/accounts/{accountId}/beneficiaries" example="OBIE Example Response" -->
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

    res, err := s.FinancialData.GetBeneficiaries(ctx, "<id>", "{consentToken}", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfBeneficiary != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 | Example                                                                                     |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `ctx`                                                                                       | [context.Context](https://pkg.go.dev/context#Context)                                       | :heavy_check_mark:                                                                          | The context to use for the request.                                                         |                                                                                             |
| `accountID`                                                                                 | `string`                                                                                    | :heavy_check_mark:                                                                          | __Mandatory__. The account Id of the user's bank account.                                   |                                                                                             |
| `consent`                                                                                   | `string`                                                                                    | :heavy_check_mark:                                                                          | __Mandatory__. The `consent-token` containing the user's authorisation to make the request. | {consentToken}                                                                              |
| `subApplication`                                                                            | `*string`                                                                                   | :heavy_minus_sign:                                                                          | The sub-application ID to which event type is being subscribed to                           |                                                                                             |
| `opts`                                                                                      | [][operations.Option](../../models/operations/option.md)                                    | :heavy_minus_sign:                                                                          | The options for this request.                                                               |                                                                                             |

### Response

**[*operations.GetBeneficiariesResponse](../../models/operations/getbeneficiariesresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetAccountDirectDebits

Returns the list of direct debits for an account.

Feature: `ACCOUNT_DIRECT_DEBITS`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getAccountDirectDebits" method="get" path="/accounts/{accountId}/direct-debits" example="Error Response" -->
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

    res, err := s.FinancialData.GetAccountDirectDebits(ctx, "<id>", "{consentToken}", nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfDirectDebitResponse != nil {
        // handle response
    }
}
```
### Example Usage: OBIE Example Response

<!-- UsageSnippet language="go" operationID="getAccountDirectDebits" method="get" path="/accounts/{accountId}/direct-debits" example="OBIE Example Response" -->
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

    res, err := s.FinancialData.GetAccountDirectDebits(ctx, "<id>", "{consentToken}", nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfDirectDebitResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         | Example                                                                                             |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                               | [context.Context](https://pkg.go.dev/context#Context)                                               | :heavy_check_mark:                                                                                  | The context to use for the request.                                                                 |                                                                                                     |
| `accountID`                                                                                         | `string`                                                                                            | :heavy_check_mark:                                                                                  | __Mandatory__. The account Id of the user's bank account.                                           |                                                                                                     |
| `consent`                                                                                           | `string`                                                                                            | :heavy_check_mark:                                                                                  | __Mandatory__. The `consent-token` containing the user's authorisation to make the request.         | {consentToken}                                                                                      |
| `subApplication`                                                                                    | `*string`                                                                                           | :heavy_minus_sign:                                                                                  | The sub-application ID to which event type is being subscribed to                                   |                                                                                                     |
| `limit`                                                                                             | `*int`                                                                                              | :heavy_minus_sign:                                                                                  | __Optional__. The maximum number of transaction records to be returned. Must be between 1 and 1000. |                                                                                                     |
| `opts`                                                                                              | [][operations.Option](../../models/operations/option.md)                                            | :heavy_minus_sign:                                                                                  | The options for this request.                                                                       |                                                                                                     |

### Response

**[*operations.GetAccountDirectDebitsResponse](../../models/operations/getaccountdirectdebitsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetAccountPeriodicPayments

Returns the list of periodic payments (standing orders in the UK) for an account.

Feature: `ACCOUNT_PERIODIC_PAYMENTS`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getAccountPeriodicPayments" method="get" path="/accounts/{accountId}/periodic-payments" example="Error Response" -->
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

    res, err := s.FinancialData.GetAccountPeriodicPayments(ctx, "<id>", "{consentToken}", nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfPaymentResponse != nil {
        // handle response
    }
}
```
### Example Usage: OBIE Example Response

<!-- UsageSnippet language="go" operationID="getAccountPeriodicPayments" method="get" path="/accounts/{accountId}/periodic-payments" example="OBIE Example Response" -->
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

    res, err := s.FinancialData.GetAccountPeriodicPayments(ctx, "<id>", "{consentToken}", nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfPaymentResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         | Example                                                                                             |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                               | [context.Context](https://pkg.go.dev/context#Context)                                               | :heavy_check_mark:                                                                                  | The context to use for the request.                                                                 |                                                                                                     |
| `accountID`                                                                                         | `string`                                                                                            | :heavy_check_mark:                                                                                  | __Mandatory__. The account Id of the user's bank account.                                           |                                                                                                     |
| `consent`                                                                                           | `string`                                                                                            | :heavy_check_mark:                                                                                  | __Mandatory__. The `consent-token` containing the user's authorisation to make the request.         | {consentToken}                                                                                      |
| `subApplication`                                                                                    | `*string`                                                                                           | :heavy_minus_sign:                                                                                  | The sub-application ID to which event type is being subscribed to                                   |                                                                                                     |
| `limit`                                                                                             | `*int`                                                                                              | :heavy_minus_sign:                                                                                  | __Optional__. The maximum number of transaction records to be returned. Must be between 1 and 1000. |                                                                                                     |
| `opts`                                                                                              | [][operations.Option](../../models/operations/option.md)                                            | :heavy_minus_sign:                                                                                  | The options for this request.                                                                       |                                                                                                     |

### Response

**[*operations.GetAccountPeriodicPaymentsResponse](../../models/operations/getaccountperiodicpaymentsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetAccountScheduledPayments

Returns the list of scheduled payments for an account.

Feature: `ACCOUNT_SCHEDULED_PAYMENTS`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getAccountScheduledPayments" method="get" path="/accounts/{accountId}/scheduled-payments" example="Error Response" -->
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

    res, err := s.FinancialData.GetAccountScheduledPayments(ctx, "<id>", "{consentToken}", nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfPaymentResponse != nil {
        // handle response
    }
}
```
### Example Usage: OBIE Example Response

<!-- UsageSnippet language="go" operationID="getAccountScheduledPayments" method="get" path="/accounts/{accountId}/scheduled-payments" example="OBIE Example Response" -->
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

    res, err := s.FinancialData.GetAccountScheduledPayments(ctx, "<id>", "{consentToken}", nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfPaymentResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         | Example                                                                                             |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                               | [context.Context](https://pkg.go.dev/context#Context)                                               | :heavy_check_mark:                                                                                  | The context to use for the request.                                                                 |                                                                                                     |
| `accountID`                                                                                         | `string`                                                                                            | :heavy_check_mark:                                                                                  | __Mandatory__. The account Id of the user's bank account.                                           |                                                                                                     |
| `consent`                                                                                           | `string`                                                                                            | :heavy_check_mark:                                                                                  | __Mandatory__. The `consent-token` containing the user's authorisation to make the request.         | {consentToken}                                                                                      |
| `subApplication`                                                                                    | `*string`                                                                                           | :heavy_minus_sign:                                                                                  | The sub-application ID to which event type is being subscribed to                                   |                                                                                                     |
| `limit`                                                                                             | `*int`                                                                                              | :heavy_minus_sign:                                                                                  | __Optional__. The maximum number of transaction records to be returned. Must be between 1 and 1000. |                                                                                                     |
| `opts`                                                                                              | [][operations.Option](../../models/operations/option.md)                                            | :heavy_minus_sign:                                                                                  | The options for this request.                                                                       |                                                                                                     |

### Response

**[*operations.GetAccountScheduledPaymentsResponse](../../models/operations/getaccountscheduledpaymentsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetStatements

Returns the list of statements for an account.

Feature: `ACCOUNT_STATEMENTS`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getStatements" method="get" path="/accounts/{accountId}/statements" example="Error Response" -->
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

    res, err := s.FinancialData.GetStatements(ctx, operations.GetStatementsRequest{
        Consent: "{consentToken}",
        AccountID: "<id>",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfAccountStatement != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="getStatements" method="get" path="/accounts/{accountId}/statements" example="Example Response" -->
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

    res, err := s.FinancialData.GetStatements(ctx, operations.GetStatementsRequest{
        Consent: "{consentToken}",
        AccountID: "<id>",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfAccountStatement != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                          | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `ctx`                                                                              | [context.Context](https://pkg.go.dev/context#Context)                              | :heavy_check_mark:                                                                 | The context to use for the request.                                                |
| `request`                                                                          | [operations.GetStatementsRequest](../../models/operations/getstatementsrequest.md) | :heavy_check_mark:                                                                 | The request object to use for the request.                                         |
| `opts`                                                                             | [][operations.Option](../../models/operations/option.md)                           | :heavy_minus_sign:                                                                 | The options for this request.                                                      |

### Response

**[*operations.GetStatementsResponse](../../models/operations/getstatementsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetStatement

Returns a statement for an account.

Feature: `ACCOUNT_STATEMENT`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getStatement" method="get" path="/accounts/{accountId}/statements/{statementId}" example="Error Response" -->
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

    res, err := s.FinancialData.GetStatement(ctx, "<value>", "<id>", "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfAccountStatement != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="getStatement" method="get" path="/accounts/{accountId}/statements/{statementId}" example="Example Response" -->
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

    res, err := s.FinancialData.GetStatement(ctx, "<value>", "<id>", "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfAccountStatement != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `ctx`                                                                                       | [context.Context](https://pkg.go.dev/context#Context)                                       | :heavy_check_mark:                                                                          | The context to use for the request.                                                         |
| `consent`                                                                                   | `string`                                                                                    | :heavy_check_mark:                                                                          | __Mandatory__. The `consent-token` containing the user's authorisation to make the request. |
| `accountID`                                                                                 | `string`                                                                                    | :heavy_check_mark:                                                                          | __Mandatory__. The account Id of the user's bank account.                                   |
| `statementID`                                                                               | `string`                                                                                    | :heavy_check_mark:                                                                          | __Mandatory__. The statement Id of the statement file.                                      |
| `subApplication`                                                                            | `*string`                                                                                   | :heavy_minus_sign:                                                                          | The sub-application ID to which event type is being subscribed to                           |
| `opts`                                                                                      | [][operations.Option](../../models/operations/option.md)                                    | :heavy_minus_sign:                                                                          | The options for this request.                                                               |

### Response

**[*operations.GetStatementResponse](../../models/operations/getstatementresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetStatementFile

Returns a PDF file of a statement for an account.

Feature: `ACCOUNT_STATEMENT_FILE`

### Example Usage

<!-- UsageSnippet language="go" operationID="getStatementFile" method="get" path="/accounts/{accountId}/statements/{statementId}/file" example="Error Response" -->
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

    res, err := s.FinancialData.GetStatementFile(ctx, "{consentToken}", "<id>", "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.ResponseStream != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 | Example                                                                                     |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `ctx`                                                                                       | [context.Context](https://pkg.go.dev/context#Context)                                       | :heavy_check_mark:                                                                          | The context to use for the request.                                                         |                                                                                             |
| `consent`                                                                                   | `string`                                                                                    | :heavy_check_mark:                                                                          | __Mandatory__. The `consent-token` containing the user's authorisation to make the request. | {consentToken}                                                                              |
| `accountID`                                                                                 | `string`                                                                                    | :heavy_check_mark:                                                                          | __Mandatory__. The account Id of the user's bank account.                                   |                                                                                             |
| `statementID`                                                                               | `string`                                                                                    | :heavy_check_mark:                                                                          | __Mandatory__. The statement Id of the statement file.                                      |                                                                                             |
| `subApplication`                                                                            | `*string`                                                                                   | :heavy_minus_sign:                                                                          | The sub-application ID to which event type is being subscribed to                           |                                                                                             |
| `opts`                                                                                      | [][operations.Option](../../models/operations/option.md)                                    | :heavy_minus_sign:                                                                          | The options for this request.                                                               |                                                                                             |

### Response

**[*operations.GetStatementFileResponse](../../models/operations/getstatementfileresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetTransactions

Returns the account transactions for an account.

Feature: `ACCOUNT_TRANSACTIONS`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getTransactions" method="get" path="/accounts/{accountId}/transactions" example="Error Response" -->
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

    res, err := s.FinancialData.GetTransactions(ctx, operations.GetTransactionsRequest{
        AccountID: "<id>",
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfTransaction != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="getTransactions" method="get" path="/accounts/{accountId}/transactions" example="Example Response" -->
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

    res, err := s.FinancialData.GetTransactions(ctx, operations.GetTransactionsRequest{
        AccountID: "<id>",
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfTransaction != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                              | Type                                                                                   | Required                                                                               | Description                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `ctx`                                                                                  | [context.Context](https://pkg.go.dev/context#Context)                                  | :heavy_check_mark:                                                                     | The context to use for the request.                                                    |
| `request`                                                                              | [operations.GetTransactionsRequest](../../models/operations/gettransactionsrequest.md) | :heavy_check_mark:                                                                     | The request object to use for the request.                                             |
| `opts`                                                                                 | [][operations.Option](../../models/operations/option.md)                               | :heavy_minus_sign:                                                                     | The options for this request.                                                          |

### Response

**[*operations.GetTransactionsResponse](../../models/operations/gettransactionsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetIdentity

Returns the identity information for an account.

Feature: `IDENTITY`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getIdentity" method="get" path="/identity" example="Error Response" -->
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

    res, err := s.FinancialData.GetIdentity(ctx, "{consentToken}", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfIdentity != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="getIdentity" method="get" path="/identity" example="Example Response" -->
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

    res, err := s.FinancialData.GetIdentity(ctx, "{consentToken}", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfIdentity != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 | Example                                                                                     |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `ctx`                                                                                       | [context.Context](https://pkg.go.dev/context#Context)                                       | :heavy_check_mark:                                                                          | The context to use for the request.                                                         |                                                                                             |
| `consent`                                                                                   | `string`                                                                                    | :heavy_check_mark:                                                                          | __Mandatory__. The `consent-token` containing the user's authorisation to make the request. | {consentToken}                                                                              |
| `subApplication`                                                                            | `*string`                                                                                   | :heavy_minus_sign:                                                                          | The sub-application ID to which event type is being subscribed to                           |                                                                                             |
| `opts`                                                                                      | [][operations.Option](../../models/operations/option.md)                                    | :heavy_minus_sign:                                                                          | The options for this request.                                                               |                                                                                             |

### Response

**[*operations.GetIdentityResponse](../../models/operations/getidentityresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetRealTimeTransactions

Used to get the account transactions for an account in real time with cursor pagination

Feature: `ACCOUNT_TRANSACTIONS`

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getRealTimeTransactions" method="get" path="/accounts/{accountId}/real-time/transactions" example="Error Response" -->
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

    res, err := s.FinancialData.GetRealTimeTransactions(ctx, operations.GetRealTimeTransactionsRequest{
        AccountID: "<id>",
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfRealTimeTransaction != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="getRealTimeTransactions" method="get" path="/accounts/{accountId}/real-time/transactions" example="Example Response" -->
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

    res, err := s.FinancialData.GetRealTimeTransactions(ctx, operations.GetRealTimeTransactionsRequest{
        AccountID: "<id>",
        Consent: "{consentToken}",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfRealTimeTransaction != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                              | Type                                                                                                   | Required                                                                                               | Description                                                                                            |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                  | [context.Context](https://pkg.go.dev/context#Context)                                                  | :heavy_check_mark:                                                                                     | The context to use for the request.                                                                    |
| `request`                                                                                              | [operations.GetRealTimeTransactionsRequest](../../models/operations/getrealtimetransactionsrequest.md) | :heavy_check_mark:                                                                                     | The request object to use for the request.                                                             |
| `opts`                                                                                                 | [][operations.Option](../../models/operations/option.md)                                               | :heavy_minus_sign:                                                                                     | The options for this request.                                                                          |

### Response

**[*operations.GetRealTimeTransactionsResponse](../../models/operations/getrealtimetransactionsresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIResponseError     | 401                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |