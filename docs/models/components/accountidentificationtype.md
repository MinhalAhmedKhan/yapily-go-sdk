# AccountIdentificationType

__Mandatory__. Used to describe the format of the account.

 See [Account Identification Combinations](/payments/payment-resources/intro-to-payment-execution#account-identifications-combinations) for more information on when to specify each type.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.AccountIdentificationTypeSortCode

// Open enum: custom values can be created with a direct type cast
custom := components.AccountIdentificationType("custom_value")
```


## Values

| Name                                        | Value                                       |
| ------------------------------------------- | ------------------------------------------- |
| `AccountIdentificationTypeSortCode`         | SORT_CODE                                   |
| `AccountIdentificationTypeAccountNumber`    | ACCOUNT_NUMBER                              |
| `AccountIdentificationTypeIban`             | IBAN                                        |
| `AccountIdentificationTypeBban`             | BBAN                                        |
| `AccountIdentificationTypeBic`              | BIC                                         |
| `AccountIdentificationTypePan`              | PAN                                         |
| `AccountIdentificationTypeMaskedPan`        | MASKED_PAN                                  |
| `AccountIdentificationTypeMsisdn`           | MSISDN                                      |
| `AccountIdentificationTypeBsb`              | BSB                                         |
| `AccountIdentificationTypeNcc`              | NCC                                         |
| `AccountIdentificationTypeAba`              | ABA                                         |
| `AccountIdentificationTypeAbaWire`          | ABA_WIRE                                    |
| `AccountIdentificationTypeAbaAch`           | ABA_ACH                                     |
| `AccountIdentificationTypeEmail`            | EMAIL                                       |
| `AccountIdentificationTypeRollNumber`       | ROLL_NUMBER                                 |
| `AccountIdentificationTypeBlz`              | BLZ                                         |
| `AccountIdentificationTypeIfs`              | IFS                                         |
| `AccountIdentificationTypeClabe`            | CLABE                                       |
| `AccountIdentificationTypeCtn`              | CTN                                         |
| `AccountIdentificationTypeBranchCode`       | BRANCH_CODE                                 |
| `AccountIdentificationTypeVirtualAccountID` | VIRTUAL_ACCOUNT_ID                          |