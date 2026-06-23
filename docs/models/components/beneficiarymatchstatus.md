# BeneficiaryMatchStatus

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.BeneficiaryMatchStatusFullMatch

// Open enum: custom values can be created with a direct type cast
custom := components.BeneficiaryMatchStatus("custom_value")
```


## Values

| Name                                                 | Value                                                |
| ---------------------------------------------------- | ---------------------------------------------------- |
| `BeneficiaryMatchStatusFullMatch`                    | FULL_MATCH                                           |
| `BeneficiaryMatchStatusCloseMatch`                   | CLOSE_MATCH                                          |
| `BeneficiaryMatchStatusNoMatch`                      | NO_MATCH                                             |
| `BeneficiaryMatchStatusExempted`                     | EXEMPTED                                             |
| `BeneficiaryMatchStatusVerificationCheckNotPossible` | VERIFICATION_CHECK_NOT_POSSIBLE                      |