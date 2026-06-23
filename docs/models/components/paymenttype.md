# PaymentType

__Mandatory__. Used to specify which of the [payment types](/payments/payment-resources/intro-to-payment-execution#payment-types) to execute.

See [European Payments](/payments/payment-resources/european-payments) to verify whether the `type` should be `DOMESTIC` or `INTERNATIONAL`.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.PaymentTypeDomesticPayment
```


## Values

| Name                                          | Value                                         |
| --------------------------------------------- | --------------------------------------------- |
| `PaymentTypeDomesticPayment`                  | DOMESTIC_PAYMENT                              |
| `PaymentTypeDomesticInstantPayment`           | DOMESTIC_INSTANT_PAYMENT                      |
| `PaymentTypeDomesticVariableRecurringPayment` | DOMESTIC_VARIABLE_RECURRING_PAYMENT           |
| `PaymentTypeDomesticScheduledPayment`         | DOMESTIC_SCHEDULED_PAYMENT                    |
| `PaymentTypeDomesticPeriodicPayment`          | DOMESTIC_PERIODIC_PAYMENT                     |
| `PaymentTypeInternationalPayment`             | INTERNATIONAL_PAYMENT                         |
| `PaymentTypeInternationalScheduledPayment`    | INTERNATIONAL_SCHEDULED_PAYMENT               |
| `PaymentTypeInternationalPeriodicPayment`     | INTERNATIONAL_PERIODIC_PAYMENT                |
| `PaymentTypeBulkPayment`                      | BULK_PAYMENT                                  |