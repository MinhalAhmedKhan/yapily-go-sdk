# BeneficiaryStatus

Status of the beneficiary check.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.BeneficiaryStatusPending

// Open enum: custom values can be created with a direct type cast
custom := components.BeneficiaryStatus("custom_value")
```


## Values

| Name                        | Value                       |
| --------------------------- | --------------------------- |
| `BeneficiaryStatusPending`  | PENDING                     |
| `BeneficiaryStatusVerified` | VERIFIED                    |
| `BeneficiaryStatusRejected` | REJECTED                    |