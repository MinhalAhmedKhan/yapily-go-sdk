# DeleteStatusEnum

Indicates the outcome of the delete request.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.DeleteStatusEnumSuccess

// Open enum: custom values can be created with a direct type cast
custom := components.DeleteStatusEnum("custom_value")
```


## Values

| Name                      | Value                     |
| ------------------------- | ------------------------- |
| `DeleteStatusEnumSuccess` | SUCCESS                   |
| `DeleteStatusEnumFailed`  | FAILED                    |