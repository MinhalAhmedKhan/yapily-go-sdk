# PaymentTypeResponse

Specifies which of the [payment types](/payments/payment-resources/intro-to-payment-execution#payment-types) to execute.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.PaymentTypeResponseDomesticPayment

// Open enum: custom values can be created with a direct type cast
custom := components.PaymentTypeResponse("custom_value")
```


## Values

| Name                                                  | Value                                                 |
| ----------------------------------------------------- | ----------------------------------------------------- |
| `PaymentTypeResponseDomesticPayment`                  | DOMESTIC_PAYMENT                                      |
| `PaymentTypeResponseDomesticInstantPayment`           | DOMESTIC_INSTANT_PAYMENT                              |
| `PaymentTypeResponseDomesticVariableRecurringPayment` | DOMESTIC_VARIABLE_RECURRING_PAYMENT                   |
| `PaymentTypeResponseDomesticScheduledPayment`         | DOMESTIC_SCHEDULED_PAYMENT                            |
| `PaymentTypeResponseDomesticPeriodicPayment`          | DOMESTIC_PERIODIC_PAYMENT                             |
| `PaymentTypeResponseInternationalPayment`             | INTERNATIONAL_PAYMENT                                 |
| `PaymentTypeResponseInternationalScheduledPayment`    | INTERNATIONAL_SCHEDULED_PAYMENT                       |
| `PaymentTypeResponseInternationalPeriodicPayment`     | INTERNATIONAL_PERIODIC_PAYMENT                        |