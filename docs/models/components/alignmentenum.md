# AlignmentEnum

__Mandatory__. Period alignment for which the payment limits are enforced. Allowed values are [CONSENT, CALENDAR]. If CONSENT, then period starts on consent creation date. If CALENDAR, then period lines up with the frequency e.g. WEEKLY period will begin at start of the week in question.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.AlignmentEnumConsent

// Open enum: custom values can be created with a direct type cast
custom := components.AlignmentEnum("custom_value")
```


## Values

| Name                    | Value                   |
| ----------------------- | ----------------------- |
| `AlignmentEnumConsent`  | CONSENT                 |
| `AlignmentEnumCalendar` | CALENDAR                |