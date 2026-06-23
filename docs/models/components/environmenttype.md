# EnvironmentType

The environment type. 

See [Institution Configuration](/introductionpages/key-concepts/institutions/#configuration) for more information

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.EnvironmentTypeSandbox

// Open enum: custom values can be created with a direct type cast
custom := components.EnvironmentType("custom_value")
```


## Values

| Name                     | Value                    |
| ------------------------ | ------------------------ |
| `EnvironmentTypeSandbox` | SANDBOX                  |
| `EnvironmentTypeMock`    | MOCK                     |
| `EnvironmentTypeLive`    | LIVE                     |