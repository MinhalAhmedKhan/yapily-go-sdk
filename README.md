# Yapily API v12.10.2

<!-- Start Summary [summary] -->
## Summary

Yapily API: The Yapily API enables connections between your application and users' banks. For more information check out our [documentation](/introduction).

In particular, make sure to view our [Getting Started](https://docs.yapily.com/getting-started/get-started) steps if this is your first time here.

While testing the API, our list of [sandbox credentials](https://docs.yapily.com/resources/sandbox/sandbox-credentials) maybe useful.
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [yapily](#yapily)
  * [SDK Installation](#sdk-installation)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
  * [Custom HTTP Client](#custom-http-client)
  * [Special Types](#special-types)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

To add the SDK as a dependency to your project:
```bash
go get github.com/MinhalAhmedKhan/yapily-go-sdk
```
<!-- End SDK Installation [installation] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```go
package main

import (
	"context"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
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
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name                      | Type | Scheme     | Environment Variable                    |
| ------------------------- | ---- | ---------- | --------------------------------------- |
| `Username`<br/>`Password` | http | HTTP Basic | `YAPILY_USERNAME`<br/>`YAPILY_PASSWORD` |

You can configure it using the `WithSecurity` option when initializing the SDK client instance. For example:
```go
package main

import (
	"context"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
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
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [ApplicationBeneficiaries](docs/sdks/applicationbeneficiaries/README.md)

* [CreateApplicationBeneficiary](docs/sdks/applicationbeneficiaries/README.md#createapplicationbeneficiary) - Create application beneficiary
* [GetApplicationBeneficiaries](docs/sdks/applicationbeneficiaries/README.md#getapplicationbeneficiaries) - Get all application beneficiaries
* [GetApplicationBeneficiaryByID](docs/sdks/applicationbeneficiaries/README.md#getapplicationbeneficiarybyid) - Get application beneficiary by id
* [DeleteApplicationBeneficiaryByID](docs/sdks/applicationbeneficiaries/README.md#deleteapplicationbeneficiarybyid) - Delete application beneficiary by id

### [ApplicationManagement](docs/sdks/applicationmanagement/README.md)

* [CreateSubApplication](docs/sdks/applicationmanagement/README.md#createsubapplication) - Creates a sub-application for the root application id provided in the authentication token
* [SearchApplications](docs/sdks/applicationmanagement/README.md#searchapplications) - Retrieve sub-applications for the root application provided in the authentication token.
* [GetApplicationByID](docs/sdks/applicationmanagement/README.md#getapplicationbyid) - Get application details
* [UpdateApplication](docs/sdks/applicationmanagement/README.md#updateapplication) - Update an Application
* [DeleteApplication](docs/sdks/applicationmanagement/README.md#deleteapplication) - Delete an application
* [CreateApplicationVRPConfigurationByApplicationID](docs/sdks/applicationmanagement/README.md#createapplicationvrpconfigurationbyapplicationid) - Create application VRP configuration by Application Id
* [UpdateApplicationVRPConfigurationByApplicationID](docs/sdks/applicationmanagement/README.md#updateapplicationvrpconfigurationbyapplicationid) - Update application VRP configuration by Application Id
* [GetApplicationVRPConfigurationByApplicationID](docs/sdks/applicationmanagement/README.md#getapplicationvrpconfigurationbyapplicationid) - Get application VRP configuration by Application Id

### [Authorisations](docs/sdks/authorisations/README.md)

* [ReAuthoriseAccount](docs/sdks/authorisations/README.md#reauthoriseaccount) - Re-authorise Account Consent
* [InitiateAccountRequest](docs/sdks/authorisations/README.md#initiateaccountrequest) - Create Account Authorisation
* [UpdatePreAuthoriseAccountConsent](docs/sdks/authorisations/README.md#updatepreauthoriseaccountconsent) - Update Account Pre-authorisation
* [CreateBulkPaymentAuthorisation](docs/sdks/authorisations/README.md#createbulkpaymentauthorisation) - Create Bulk Payment Authorisation
* [InitiateEmbeddedAccountRequest](docs/sdks/authorisations/README.md#initiateembeddedaccountrequest) - Create Embedded Account Authorisation
* [UpdateEmbeddedAccountRequest](docs/sdks/authorisations/README.md#updateembeddedaccountrequest) - Update Embedded Account Authorisation
* [CreateEmbeddedBulkPaymentAuthorisation](docs/sdks/authorisations/README.md#createembeddedbulkpaymentauthorisation) - Create Embedded Bulk Payment Authorisation
* [UpdateEmbeddedBulkPaymentAuthorisation](docs/sdks/authorisations/README.md#updateembeddedbulkpaymentauthorisation) - Update Embedded Bulk Payment Authorisation
* [CreateEmbeddedPaymentAuthorisation](docs/sdks/authorisations/README.md#createembeddedpaymentauthorisation) - Create Embedded Payment Authorisation
* [UpdateEmbeddedPaymentAuthorisation](docs/sdks/authorisations/README.md#updateembeddedpaymentauthorisation) - Update Embedded Payment Authorisation
* [CreatePaymentAuthorisation](docs/sdks/authorisations/README.md#createpaymentauthorisation) - Create Payment Authorisation
* [UpdatePaymentAuthorisation](docs/sdks/authorisations/README.md#updatepaymentauthorisation) - Update Payment Pre-authorisation
* [CreatePreAuthorisationRequest](docs/sdks/authorisations/README.md#createpreauthorisationrequest) - Create Pre-authorisation
* [CreatePaymentPreAuthorisationRequest](docs/sdks/authorisations/README.md#createpaymentpreauthorisationrequest) - Create Payment Pre-authorisation

### [Consents](docs/sdks/consents/README.md)

* [CreateConsentWithCode](docs/sdks/consents/README.md#createconsentwithcode) - Exchange OAuth2 Code
* [GetConsentBySingleAccessConsent](docs/sdks/consents/README.md#getconsentbysingleaccessconsent) - Exchange One Time Token
* [GetConsents](docs/sdks/consents/README.md#getconsents) - Get Consents
* [Delete](docs/sdks/consents/README.md#delete) - Delete Consent
* [GetConsentByID](docs/sdks/consents/README.md#getconsentbyid) - Get Consent
* [ExtendConsent](docs/sdks/consents/README.md#extendconsent) - Extend Consent

### [Constraints](docs/sdks/constraints/README.md)

* [GetPaymentConstraintsRulesByInstitution](docs/sdks/constraints/README.md#getpaymentconstraintsrulesbyinstitution) - Get Payment Constraints Rules
* [GetAccountConstraintsRulesByInstitution](docs/sdks/constraints/README.md#getaccountconstraintsrulesbyinstitution) - Get Data Constraints Rules

### [DataPlus](docs/sdks/dataplus/README.md)

* [PostAccountsAccountIDTransactionsCategorisation](docs/sdks/dataplus/README.md#postaccountsaccountidtransactionscategorisation) - Transactions and Enrichment
* [~~GetAccountsTransactionsCategorised~~](docs/sdks/dataplus/README.md#getaccountstransactionscategorised) - Get Categorised Transactions (Deprecated) :warning: **Deprecated**
* [PostTransactionsCategorisation](docs/sdks/dataplus/README.md#posttransactionscategorisation) - Enrichment
* [GetTransactionsCategorised](docs/sdks/dataplus/README.md#gettransactionscategorised) - Get Enrichment Results
* [GetCategorisationAccountType](docs/sdks/dataplus/README.md#getcategorisationaccounttype) - Get Enrichment Labels

### [FinancialData](docs/sdks/financialdata/README.md)

* [GetAccounts](docs/sdks/financialdata/README.md#getaccounts) - Get Accounts
* [GetAccount](docs/sdks/financialdata/README.md#getaccount) - Get Account
* [GetAccountBalances](docs/sdks/financialdata/README.md#getaccountbalances) - Get Account Balances
* [GetBeneficiaries](docs/sdks/financialdata/README.md#getbeneficiaries) - Get Account Beneficiaries
* [GetAccountDirectDebits](docs/sdks/financialdata/README.md#getaccountdirectdebits) - Get Account Direct Debits
* [GetAccountPeriodicPayments](docs/sdks/financialdata/README.md#getaccountperiodicpayments) - Get Account Periodic Payments
* [GetAccountScheduledPayments](docs/sdks/financialdata/README.md#getaccountscheduledpayments) - Get Account Scheduled Payments
* [GetStatements](docs/sdks/financialdata/README.md#getstatements) - Get Account Statements
* [GetStatement](docs/sdks/financialdata/README.md#getstatement) - Get Account Statement
* [GetStatementFile](docs/sdks/financialdata/README.md#getstatementfile) - Get Account Statement File
* [GetTransactions](docs/sdks/financialdata/README.md#gettransactions) - Get Account Transactions
* [GetIdentity](docs/sdks/financialdata/README.md#getidentity) - Get Identity
* [GetRealTimeTransactions](docs/sdks/financialdata/README.md#getrealtimetransactions) - Get Real Time Account Transactions

### [HostedConsentPages](docs/sdks/hostedconsentpages/README.md)

* [CreateHostedConsentRequest](docs/sdks/hostedconsentpages/README.md#createhostedconsentrequest) - Create Hosted Consent Request
* [GetHostedConsentRequest](docs/sdks/hostedconsentpages/README.md#gethostedconsentrequest) - Get Hosted Consent Request

### [HostedPaymentPages](docs/sdks/hostedpaymentpages/README.md)

* [CreateHostedPaymentRequest](docs/sdks/hostedpaymentpages/README.md#createhostedpaymentrequest) - Create Hosted payment request
* [CreateHostedPaymentRequestLink](docs/sdks/hostedpaymentpages/README.md#createhostedpaymentrequestlink) - Create Pay By Link
* [GetHostedPaymentRequest](docs/sdks/hostedpaymentpages/README.md#gethostedpaymentrequest) - Get Hosted payment request

### [HostedVRPPages](docs/sdks/hostedvrppages/README.md)

* [PostHostedCommercialVrpRequest](docs/sdks/hostedvrppages/README.md#posthostedcommercialvrprequest) - Create Hosted Commercial VRP request
* [GetHostedCommercialVrpRequest](docs/sdks/hostedvrppages/README.md#gethostedcommercialvrprequest) - Get Hosted Commercial VRP request

### [Institutions](docs/sdks/institutions/README.md)

* [GetInstitutions](docs/sdks/institutions/README.md#getinstitutions) - Get Institutions
* [GetInstitution](docs/sdks/institutions/README.md#getinstitution) - Get Institution

### [Notifications](docs/sdks/notifications/README.md)

* [CreateEventSubscription](docs/sdks/notifications/README.md#createeventsubscription) - Create Event Subscription
* [GetEventSubscriptions](docs/sdks/notifications/README.md#geteventsubscriptions) - Get Event Subscriptions
* [GetEventSubscriptionByID](docs/sdks/notifications/README.md#geteventsubscriptionbyid) - Get Event Subscription
* [DeleteEventSubscriptionByID](docs/sdks/notifications/README.md#deleteeventsubscriptionbyid) - Delete Event Subscription

### [Payments](docs/sdks/payments/README.md)

* [CreateBulkPayment](docs/sdks/payments/README.md#createbulkpayment) - Create Bulk Payment
* [GetBulkPaymentStatus](docs/sdks/payments/README.md#getbulkpaymentstatus) - Get Bulk Payment File Status
* [GetBulkPaymentDetailsByID](docs/sdks/payments/README.md#getbulkpaymentdetailsbyid) - Get Bulk Payment Status Details
* [CreatePayment](docs/sdks/payments/README.md#createpayment) - Create Payment
* [GetPayments](docs/sdks/payments/README.md#getpayments) - Get Payment Details

### [UserBeneficiaries](docs/sdks/userbeneficiaries/README.md)

* [CreateUserBeneficiary](docs/sdks/userbeneficiaries/README.md#createuserbeneficiary) - Create Beneficiary
* [GetUserBeneficiaries](docs/sdks/userbeneficiaries/README.md#getuserbeneficiaries) - Get all users beneficiaries
* [PatchUserBeneficiary](docs/sdks/userbeneficiaries/README.md#patchuserbeneficiary) - Patch User Beneficiary
* [GetUserBeneficiary](docs/sdks/userbeneficiaries/README.md#getuserbeneficiary) - Get beneficiary by id
* [DeleteUserBeneficiary](docs/sdks/userbeneficiaries/README.md#deleteuserbeneficiary) - Delete user beneficiary by id.
* [ApproveBeneficiary](docs/sdks/userbeneficiaries/README.md#approvebeneficiary) - Approve Beneficiary
* [RejectBeneficiary](docs/sdks/userbeneficiaries/README.md#rejectbeneficiary) - Reject Beneficiary

### [Users](docs/sdks/users/README.md)

* [GetUsers](docs/sdks/users/README.md#getusers) - Get Users
* [AddUser](docs/sdks/users/README.md#adduser) - Create User
* [PatchUser](docs/sdks/users/README.md#patchuser) - Update User
* [DeleteUser](docs/sdks/users/README.md#deleteuser) - Delete User
* [GetUser](docs/sdks/users/README.md#getuser) - Get User

### [VariableRecurringPayments](docs/sdks/variablerecurringpayments/README.md)

* [CreateSweepingAuthorisation](docs/sdks/variablerecurringpayments/README.md#createsweepingauthorisation) - Create Sweeping VRP Authorisation
* [GetSweepingVrpConsentByID](docs/sdks/variablerecurringpayments/README.md#getsweepingvrpconsentbyid) - Get Sweeping VRP Consent Details
* [GetCommercialVrpConsentByID](docs/sdks/variablerecurringpayments/README.md#getcommercialvrpconsentbyid) - Get Commercial VRP Consent Details
* [CreateVrpFundsConfirmation](docs/sdks/variablerecurringpayments/README.md#createvrpfundsconfirmation) - Confirm Funds for VRP Payment
* [CreateVrpPayment](docs/sdks/variablerecurringpayments/README.md#createvrppayment) - Create VRP Payment
* [GetVrpPaymentDetails](docs/sdks/variablerecurringpayments/README.md#getvrppaymentdetails) - Get VRP Payment Details

### [Webhooks](docs/sdks/webhooks/README.md)

* [GetWebhookEventsCategories](docs/sdks/webhooks/README.md#getwebhookeventscategories) - Get Webhook Categories
* [RegisterWebhook](docs/sdks/webhooks/README.md#registerwebhook) - Register Webhook Event
* [GetRegisteredWebhooks](docs/sdks/webhooks/README.md#getregisteredwebhooks) - Retrieve All Webhook Events
* [DeleteWebhook](docs/sdks/webhooks/README.md#deletewebhook) - Delete Webhook Event
* [WebhookSecretReset](docs/sdks/webhooks/README.md#webhooksecretreset) - Reset Webhook Secret

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a `retry.Config` object to the call by using the `WithRetries` option:
```go
package main

import (
	"context"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/operations"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/retry"
	"log"
	"models/operations"
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
	}, operations.WithRetries(
		retry.Config{
			Strategy: "backoff",
			Backoff: &retry.BackoffStrategy{
				InitialInterval: 1,
				MaxInterval:     50,
				Exponent:        1.1,
				MaxElapsedTime:  100,
			},
			RetryConnectionErrors: false,
		}))
	if err != nil {
		log.Fatal(err)
	}
	if res.APIResponseOfAccountAuthorisationResponse != nil {
		// handle response
	}
}

```

If you'd like to override the default retry strategy for all operations that support retries, you can use the `WithRetryConfig` option at SDK initialization:
```go
package main

import (
	"context"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/operations"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/retry"
	"log"
)

func main() {
	ctx := context.Background()

	s := yapily.New(
		yapily.WithRetryConfig(
			retry.Config{
				Strategy: "backoff",
				Backoff: &retry.BackoffStrategy{
					InitialInterval: 1,
					MaxInterval:     50,
					Exponent:        1.1,
					MaxElapsedTime:  100,
				},
				RetryConnectionErrors: false,
			}),
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
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

Handling errors in this SDK should largely match your expectations. All operations return a response object or an error, they will never return both.

By Default, an API error will return `apierrors.APIError`. When custom error responses are specified for an operation, the SDK may also return their associated error. You can refer to respective *Errors* tables in SDK docs for more details on possible error types for each operation.

For example, the `GetRealTimeTransactions` function may return the following errors:

| Error Type                 | Status Code | Content Type                   |
| -------------------------- | ----------- | ------------------------------ |
| apierrors.APIResponseError | 401         | application/json;charset=UTF-8 |
| apierrors.APIError         | 4XX, 5XX    | \*/\*                          |

### Example

```go
package main

import (
	"context"
	"errors"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/apierrors"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
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
		Consent:   "{consentToken}",
	})
	if err != nil {

		var e *apierrors.APIResponseError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}

		var e *apierrors.APIError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}
	}
}

```
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Override Server URL Per-Client

The default server can be overridden globally using the `WithServerURL(serverURL string)` option when initializing the SDK client instance. For example:
```go
package main

import (
	"context"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/operations"
	"log"
)

func main() {
	ctx := context.Background()

	s := yapily.New(
		yapily.WithServerURL("https://api.yapily.com"),
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
<!-- End Server Selection [server] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The Go SDK makes API calls that wrap an internal HTTP client. The requirements for the HTTP client are very simple. It must match this interface:

```go
type HTTPClient interface {
	Do(req *http.Request) (*http.Response, error)
}
```

The built-in `net/http` client satisfies this interface and a default client based on the built-in is provided by default. To replace this default with a client of your own, you can implement this interface yourself or provide your own client configured as desired. Here's a simple example, which adds a client with a 30 second timeout.

```go
import (
	"net/http"
	"time"

	"github.com/MinhalAhmedKhan/yapily-go-sdk"
)

var (
	httpClient = &http.Client{Timeout: 30 * time.Second}
	sdkClient  = yapily.New(yapily.WithClient(httpClient))
)
```

This can be a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration.
<!-- End Custom HTTP Client [http-client] -->

<!-- Start Special Types [types] -->
## Special Types

This SDK defines the following custom types to assist with marshalling and unmarshalling data.

### Date

`types.Date` is a wrapper around time.Time that allows for JSON marshaling a date string formatted as "2006-01-02".

#### Usage

```go
d1 := types.NewDate(time.Now()) // returns *types.Date

d2 := types.DateFromTime(time.Now()) // returns types.Date

d3, err := types.NewDateFromString("2019-01-01") // returns *types.Date, error

d4, err := types.DateFromString("2019-01-01") // returns types.Date, error

d5 := types.MustNewDateFromString("2019-01-01") // returns *types.Date and panics on error

d6 := types.MustDateFromString("2019-01-01") // returns types.Date and panics on error
```
<!-- End Special Types [types] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->
