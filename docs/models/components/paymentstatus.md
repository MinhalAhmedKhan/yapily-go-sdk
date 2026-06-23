# PaymentStatus

The status of the Payment. 

For more information, see [Payment Status](/guides/payments/payment-status/)

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.PaymentStatusPending

// Open enum: custom values can be created with a direct type cast
custom := components.PaymentStatus("custom_value")
```


## Values

| Name                                        | Value                                       |
| ------------------------------------------- | ------------------------------------------- |
| `PaymentStatusPending`                      | PENDING                                     |
| `PaymentStatusFailed`                       | FAILED                                      |
| `PaymentStatusDeclined`                     | DECLINED                                    |
| `PaymentStatusCompleted`                    | COMPLETED                                   |
| `PaymentStatusCompletedSettlementInProcess` | COMPLETED_SETTLEMENT_IN_PROCESS             |
| `PaymentStatusExpired`                      | EXPIRED                                     |
| `PaymentStatusUnknown`                      | UNKNOWN                                     |
| `PaymentStatusActive`                       | ACTIVE                                      |
| `PaymentStatusInactive`                     | INACTIVE                                    |