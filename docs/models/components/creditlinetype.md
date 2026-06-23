# CreditLineType

__Mandatory__. The type of credit that has been provided.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.CreditLineTypeAvailable

// Open enum: custom values can be created with a direct type cast
custom := components.CreditLineType("custom_value")
```


## Values

| Name                      | Value                     |
| ------------------------- | ------------------------- |
| `CreditLineTypeAvailable` | AVAILABLE                 |
| `CreditLineTypeCredit`    | CREDIT                    |
| `CreditLineTypeEmergency` | EMERGENCY                 |
| `CreditLineTypePreAgreed` | PRE_AGREED                |
| `CreditLineTypeTemporary` | TEMPORARY                 |
| `CreditLineTypeOther`     | OTHER                     |
| `CreditLineTypeUnknown`   | UNKNOWN                   |