# ChargeBearerType

__Conditional__. Depending on the bank and payment type for international Euro payments. The field ChargeBearer specifies which party/parties will bear the charges associated with the processing of the payment transaction. Valid values are:

- `DEBT` - All transaction charges are to be borne by the debtor.
- `CRED` - All transaction charges are to be borne by the creditor.
- `SHAR` - In a credit transfer context, means that transaction charges on the sender side are to be borne by the debtor, transaction charges on the receiver side are to be borne by the creditor
- `SLEV` - Charges are to be applied following the rules agreed in the service level and/or scheme.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.ChargeBearerTypeDebt
```


## Values

| Name                   | Value                  |
| ---------------------- | ---------------------- |
| `ChargeBearerTypeDebt` | DEBT                   |
| `ChargeBearerTypeCred` | CRED                   |
| `ChargeBearerTypeShar` | SHAR                   |
| `ChargeBearerTypeSlev` | SLEV                   |