# FrequencyEnumExtended

__Mandatory__. See [payment frequency](/guides/payments/payment-execution/periodic-payments/#payment-frequency) for more information

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.FrequencyEnumExtendedDaily

// Open enum: custom values can be created with a direct type cast
custom := components.FrequencyEnumExtended("custom_value")
```


## Values

| Name                                   | Value                                  |
| -------------------------------------- | -------------------------------------- |
| `FrequencyEnumExtendedDaily`           | DAILY                                  |
| `FrequencyEnumExtendedEveryWorkingDay` | EVERY_WORKING_DAY                      |
| `FrequencyEnumExtendedCalendarDay`     | CALENDAR_DAY                           |
| `FrequencyEnumExtendedWeekly`          | WEEKLY                                 |
| `FrequencyEnumExtendedEveryTwoWeeks`   | EVERY_TWO_WEEKS                        |
| `FrequencyEnumExtendedMonthly`         | MONTHLY                                |
| `FrequencyEnumExtendedEveryTwoMonths`  | EVERY_TWO_MONTHS                       |
| `FrequencyEnumExtendedQuarterly`       | QUARTERLY                              |
| `FrequencyEnumExtendedSemiannual`      | SEMIANNUAL                             |
| `FrequencyEnumExtendedAnnual`          | ANNUAL                                 |