# PaymentContextTypeResponse

The payment context code.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.PaymentContextTypeResponseBill

// Open enum: custom values can be created with a direct type cast
custom := components.PaymentContextTypeResponse("custom_value")
```


## Values

| Name                                       | Value                                      |
| ------------------------------------------ | ------------------------------------------ |
| `PaymentContextTypeResponseBill`           | BILL                                       |
| `PaymentContextTypeResponseGoods`          | GOODS                                      |
| `PaymentContextTypeResponseServices`       | SERVICES                                   |
| `PaymentContextTypeResponseOther`          | OTHER                                      |
| `PaymentContextTypeResponsePersonToPerson` | PERSON_TO_PERSON                           |