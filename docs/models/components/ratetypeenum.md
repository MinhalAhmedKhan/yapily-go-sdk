# RateTypeEnum

__Mandatory__. The type used to complete the currency exchange.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.RateTypeEnumActual

// Open enum: custom values can be created with a direct type cast
custom := components.RateTypeEnum("custom_value")
```


## Values

| Name                     | Value                    |
| ------------------------ | ------------------------ |
| `RateTypeEnumActual`     | ACTUAL                   |
| `RateTypeEnumAgreed`     | AGREED                   |
| `RateTypeEnumIndicative` | INDICATIVE               |