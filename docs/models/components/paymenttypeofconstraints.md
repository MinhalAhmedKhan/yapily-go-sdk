# PaymentTypeOfConstraints

Payment type associated with constraints.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.PaymentTypeOfConstraintsDomesticPayment

// Open enum: custom values can be created with a direct type cast
custom := components.PaymentTypeOfConstraints("custom_value")
```


## Values

| Name                                                       | Value                                                      |
| ---------------------------------------------------------- | ---------------------------------------------------------- |
| `PaymentTypeOfConstraintsDomesticPayment`                  | DOMESTIC_PAYMENT                                           |
| `PaymentTypeOfConstraintsDomesticInstantPayment`           | DOMESTIC_INSTANT_PAYMENT                                   |
| `PaymentTypeOfConstraintsDomesticVariableRecurringPayment` | DOMESTIC_VARIABLE_RECURRING_PAYMENT                        |
| `PaymentTypeOfConstraintsDomesticScheduledPayment`         | DOMESTIC_SCHEDULED_PAYMENT                                 |
| `PaymentTypeOfConstraintsDomesticPeriodicPayment`          | DOMESTIC_PERIODIC_PAYMENT                                  |
| `PaymentTypeOfConstraintsInternationalPayment`             | INTERNATIONAL_PAYMENT                                      |
| `PaymentTypeOfConstraintsInternationalScheduledPayment`    | INTERNATIONAL_SCHEDULED_PAYMENT                            |
| `PaymentTypeOfConstraintsInternationalPeriodicPayment`     | INTERNATIONAL_PERIODIC_PAYMENT                             |