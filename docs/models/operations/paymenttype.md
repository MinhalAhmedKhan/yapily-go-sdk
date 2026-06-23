# PaymentType

Type of payment to retrieve payment constraints for

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/operations"
)

value := operations.PaymentTypeDomesticPayment
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