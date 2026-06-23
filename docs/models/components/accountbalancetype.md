# AccountBalanceType

Specifies the type of the stated account balance.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.AccountBalanceTypeClosingAvailable

// Open enum: custom values can be created with a direct type cast
custom := components.AccountBalanceType("custom_value")
```


## Values

| Name                                       | Value                                      |
| ------------------------------------------ | ------------------------------------------ |
| `AccountBalanceTypeClosingAvailable`       | CLOSING_AVAILABLE                          |
| `AccountBalanceTypeClosingBooked`          | CLOSING_BOOKED                             |
| `AccountBalanceTypeClosingCleared`         | CLOSING_CLEARED                            |
| `AccountBalanceTypeExpected`               | EXPECTED                                   |
| `AccountBalanceTypeForwardAvailable`       | FORWARD_AVAILABLE                          |
| `AccountBalanceTypeInformation`            | INFORMATION                                |
| `AccountBalanceTypeInterimAvailable`       | INTERIM_AVAILABLE                          |
| `AccountBalanceTypeInterimBooked`          | INTERIM_BOOKED                             |
| `AccountBalanceTypeInterimCleared`         | INTERIM_CLEARED                            |
| `AccountBalanceTypeOpeningAvailable`       | OPENING_AVAILABLE                          |
| `AccountBalanceTypeOpeningBooked`          | OPENING_BOOKED                             |
| `AccountBalanceTypeOpeningCleared`         | OPENING_CLEARED                            |
| `AccountBalanceTypePreviouslyClosedBooked` | PREVIOUSLY_CLOSED_BOOKED                   |
| `AccountBalanceTypeAuthorised`             | AUTHORISED                                 |
| `AccountBalanceTypeOther`                  | OTHER                                      |
| `AccountBalanceTypeUnknown`                | UNKNOWN                                    |