# AccountIdentificationTypeResponse

Used to describe the format of the account.

 See [Account Identification Combinations](/payments/payment-resources/intro-to-payment-execution#account-identifications-combinations) for more information.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.AccountIdentificationTypeResponseSortCode

// Open enum: custom values can be created with a direct type cast
custom := components.AccountIdentificationTypeResponse("custom_value")
```


## Values

| Name                                                | Value                                               |
| --------------------------------------------------- | --------------------------------------------------- |
| `AccountIdentificationTypeResponseSortCode`         | SORT_CODE                                           |
| `AccountIdentificationTypeResponseAccountNumber`    | ACCOUNT_NUMBER                                      |
| `AccountIdentificationTypeResponseIban`             | IBAN                                                |
| `AccountIdentificationTypeResponseBban`             | BBAN                                                |
| `AccountIdentificationTypeResponseBic`              | BIC                                                 |
| `AccountIdentificationTypeResponsePan`              | PAN                                                 |
| `AccountIdentificationTypeResponseMaskedPan`        | MASKED_PAN                                          |
| `AccountIdentificationTypeResponseMsisdn`           | MSISDN                                              |
| `AccountIdentificationTypeResponseBsb`              | BSB                                                 |
| `AccountIdentificationTypeResponseNcc`              | NCC                                                 |
| `AccountIdentificationTypeResponseAba`              | ABA                                                 |
| `AccountIdentificationTypeResponseAbaWire`          | ABA_WIRE                                            |
| `AccountIdentificationTypeResponseAbaAch`           | ABA_ACH                                             |
| `AccountIdentificationTypeResponseEmail`            | EMAIL                                               |
| `AccountIdentificationTypeResponseRollNumber`       | ROLL_NUMBER                                         |
| `AccountIdentificationTypeResponseBlz`              | BLZ                                                 |
| `AccountIdentificationTypeResponseIfs`              | IFS                                                 |
| `AccountIdentificationTypeResponseClabe`            | CLABE                                               |
| `AccountIdentificationTypeResponseCtn`              | CTN                                                 |
| `AccountIdentificationTypeResponseBranchCode`       | BRANCH_CODE                                         |
| `AccountIdentificationTypeResponseVirtualAccountID` | VIRTUAL_ACCOUNT_ID                                  |