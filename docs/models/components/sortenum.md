# SortEnum

The attribute on which resources / records returned should be sorted. Valid options for the sort parameter.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.SortEnumDate

// Open enum: custom values can be created with a direct type cast
custom := components.SortEnum("custom_value")
```


## Values

| Name                | Value               |
| ------------------- | ------------------- |
| `SortEnumDate`      | date                |
| `SortEnumMinusDate` | -date               |