# FeatureEnum

Used to describe what functions are supported by the associated `Institution`.        

For more information on each feature, see the following links:        

- [Financial Data Features](/data/financial-data-resources/financial-data-features)
- [Payments Features](/payments/payment-resources/payment-features)

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.FeatureEnumInitiatePreAuthorisation

// Open enum: custom values can be created with a direct type cast
custom := components.FeatureEnum("custom_value")
```


## Values

| Name                                                            | Value                                                           |
| --------------------------------------------------------------- | --------------------------------------------------------------- |
| `FeatureEnumInitiatePreAuthorisation`                           | INITIATE_PRE_AUTHORISATION                                      |
| `FeatureEnumInitiatePreAuthorisationAccounts`                   | INITIATE_PRE_AUTHORISATION_ACCOUNTS                             |
| `FeatureEnumInitiatePreAuthorisationPayments`                   | INITIATE_PRE_AUTHORISATION_PAYMENTS                             |
| `FeatureEnumInitiateAccountRequest`                             | INITIATE_ACCOUNT_REQUEST                                        |
| `FeatureEnumInitiateEmbeddedAccountRequest`                     | INITIATE_EMBEDDED_ACCOUNT_REQUEST                               |
| `FeatureEnumAccountRequestDetails`                              | ACCOUNT_REQUEST_DETAILS                                         |
| `FeatureEnumAccounts`                                           | ACCOUNTS                                                        |
| `FeatureEnumAccount`                                            | ACCOUNT                                                         |
| `FeatureEnumAccountTransactions`                                | ACCOUNT_TRANSACTIONS                                            |
| `FeatureEnumAccountStatements`                                  | ACCOUNT_STATEMENTS                                              |
| `FeatureEnumAccountStatement`                                   | ACCOUNT_STATEMENT                                               |
| `FeatureEnumAccountStatementFile`                               | ACCOUNT_STATEMENT_FILE                                          |
| `FeatureEnumAccountScheduledPayments`                           | ACCOUNT_SCHEDULED_PAYMENTS                                      |
| `FeatureEnumAccountDirectDebits`                                | ACCOUNT_DIRECT_DEBITS                                           |
| `FeatureEnumAccountPeriodicPayments`                            | ACCOUNT_PERIODIC_PAYMENTS                                       |
| `FeatureEnumAccountTransactionsWithMerchant`                    | ACCOUNT_TRANSACTIONS_WITH_MERCHANT                              |
| `FeatureEnumIdentity`                                           | IDENTITY                                                        |
| `FeatureEnumAccountsWithoutBalance`                             | ACCOUNTS_WITHOUT_BALANCE                                        |
| `FeatureEnumAccountWithoutBalance`                              | ACCOUNT_WITHOUT_BALANCE                                         |
| `FeatureEnumAccountBalances`                                    | ACCOUNT_BALANCES                                                |
| `FeatureEnumInitiateSinglePaymentSortcode`                      | INITIATE_SINGLE_PAYMENT_SORTCODE                                |
| `FeatureEnumExistingPaymentInitiationDetails`                   | EXISTING_PAYMENT_INITIATION_DETAILS                             |
| `FeatureEnumCreateSinglePaymentSortcode`                        | CREATE_SINGLE_PAYMENT_SORTCODE                                  |
| `FeatureEnumExistingPaymentsDetails`                            | EXISTING_PAYMENTS_DETAILS                                       |
| `FeatureEnumInitiateDomesticSinglePayment`                      | INITIATE_DOMESTIC_SINGLE_PAYMENT                                |
| `FeatureEnumInitiateEmbeddedDomesticSinglePayment`              | INITIATE_EMBEDDED_DOMESTIC_SINGLE_PAYMENT                       |
| `FeatureEnumCreateDomesticSinglePayment`                        | CREATE_DOMESTIC_SINGLE_PAYMENT                                  |
| `FeatureEnumInitiateEmbeddedBulkPayment`                        | INITIATE_EMBEDDED_BULK_PAYMENT                                  |
| `FeatureEnumInitiateDomesticSingleInstantPayment`               | INITIATE_DOMESTIC_SINGLE_INSTANT_PAYMENT                        |
| `FeatureEnumCreateDomesticSingleInstantPayment`                 | CREATE_DOMESTIC_SINGLE_INSTANT_PAYMENT                          |
| `FeatureEnumInitiateDomesticVariableRecurringPayment`           | INITIATE_DOMESTIC_VARIABLE_RECURRING_PAYMENT                    |
| `FeatureEnumCreateDomesticVariableRecurringPayment`             | CREATE_DOMESTIC_VARIABLE_RECURRING_PAYMENT                      |
| `FeatureEnumInitiateDomesticVariableRecurringPaymentSweeping`   | INITIATE_DOMESTIC_VARIABLE_RECURRING_PAYMENT_SWEEPING           |
| `FeatureEnumCreateDomesticVariableRecurringPaymentSweeping`     | CREATE_DOMESTIC_VARIABLE_RECURRING_PAYMENT_SWEEPING             |
| `FeatureEnumInitiateDomesticVariableRecurringPaymentCommercial` | INITIATE_DOMESTIC_VARIABLE_RECURRING_PAYMENT_COMMERCIAL         |
| `FeatureEnumCreateDomesticVariableRecurringPaymentCommercial`   | CREATE_DOMESTIC_VARIABLE_RECURRING_PAYMENT_COMMERCIAL           |
| `FeatureEnumInitiateDomesticScheduledPayment`                   | INITIATE_DOMESTIC_SCHEDULED_PAYMENT                             |
| `FeatureEnumCreateDomesticScheduledPayment`                     | CREATE_DOMESTIC_SCHEDULED_PAYMENT                               |
| `FeatureEnumInitiateDomesticPeriodicPayment`                    | INITIATE_DOMESTIC_PERIODIC_PAYMENT                              |
| `FeatureEnumCreateDomesticPeriodicPayment`                      | CREATE_DOMESTIC_PERIODIC_PAYMENT                                |
| `FeatureEnumPeriodicPaymentFrequencyExtended`                   | PERIODIC_PAYMENT_FREQUENCY_EXTENDED                             |
| `FeatureEnumInitiateInternationalScheduledPayment`              | INITIATE_INTERNATIONAL_SCHEDULED_PAYMENT                        |
| `FeatureEnumCreateInternationalScheduledPayment`                | CREATE_INTERNATIONAL_SCHEDULED_PAYMENT                          |
| `FeatureEnumInitiateInternationalPeriodicPayment`               | INITIATE_INTERNATIONAL_PERIODIC_PAYMENT                         |
| `FeatureEnumCreateInternationalPeriodicPayment`                 | CREATE_INTERNATIONAL_PERIODIC_PAYMENT                           |
| `FeatureEnumInitiateInternationalSinglePayment`                 | INITIATE_INTERNATIONAL_SINGLE_PAYMENT                           |
| `FeatureEnumCreateInternationalSinglePayment`                   | CREATE_INTERNATIONAL_SINGLE_PAYMENT                             |
| `FeatureEnumInitiateBulkPayment`                                | INITIATE_BULK_PAYMENT                                           |
| `FeatureEnumCreateBulkPayment`                                  | CREATE_BULK_PAYMENT                                             |
| `FeatureEnumExistingBulkPaymentDetails`                         | EXISTING_BULK_PAYMENT_DETAILS                                   |
| `FeatureEnumTransfer`                                           | TRANSFER                                                        |
| `FeatureEnumOpenDataPersonalCurrentAccounts`                    | OPEN_DATA_PERSONAL_CURRENT_ACCOUNTS                             |
| `FeatureEnumOpenDataAtms`                                       | OPEN_DATA_ATMS                                                  |
| `FeatureEnumReadDomesticSingleRefund`                           | READ_DOMESTIC_SINGLE_REFUND                                     |
| `FeatureEnumReadDomesticScheduledRefund`                        | READ_DOMESTIC_SCHEDULED_REFUND                                  |
| `FeatureEnumReadDomesticPeriodicPaymentRefund`                  | READ_DOMESTIC_PERIODIC_PAYMENT_REFUND                           |
| `FeatureEnumReadInternationalSingleRefund`                      | READ_INTERNATIONAL_SINGLE_REFUND                                |
| `FeatureEnumReadInternationalScheduledRefund`                   | READ_INTERNATIONAL_SCHEDULED_REFUND                             |
| `FeatureEnumAccountBeneficiaries`                               | ACCOUNT_BENEFICIARIES                                           |
| `FeatureEnumInitiateOnetimePreAuthorisationPayments`            | INITIATE_ONETIME_PRE_AUTHORISATION_PAYMENTS                     |
| `FeatureEnumInitiateOnetimePreAuthorisationAccounts`            | INITIATE_ONETIME_PRE_AUTHORISATION_ACCOUNTS                     |
| `FeatureEnumInitiateOnetimePreAuthorisation`                    | INITIATE_ONETIME_PRE_AUTHORISATION                              |
| `FeatureEnumVariableRecurringPaymentFundsConfirmation`          | VARIABLE_RECURRING_PAYMENT_FUNDS_CONFIRMATION                   |