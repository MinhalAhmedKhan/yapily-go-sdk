# PaymentContextType

__Optional__. The payment context code. This defaults to `OTHER` if not specified.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.PaymentContextTypeBill
```


## Values

| Name                                     | Value                                    |
| ---------------------------------------- | ---------------------------------------- |
| `PaymentContextTypeBill`                 | BILL                                     |
| `PaymentContextTypeGoods`                | GOODS                                    |
| `PaymentContextTypeServices`             | SERVICES                                 |
| `PaymentContextTypeOther`                | OTHER                                    |
| `PaymentContextTypePersonToPerson`       | PERSON_TO_PERSON                         |
| `PaymentContextTypeBillInAdvance`        | BILL_IN_ADVANCE                          |
| `PaymentContextTypeBillInArrears`        | BILL_IN_ARREARS                          |
| `PaymentContextTypeEcommerceMerchant`    | ECOMMERCE_MERCHANT                       |
| `PaymentContextTypeFaceToFacePos`        | FACE_TO_FACE_POS                         |
| `PaymentContextTypeTransferToSelf`       | TRANSFER_TO_SELF                         |
| `PaymentContextTypeTransferToThirdParty` | TRANSFER_TO_THIRD_PARTY                  |
| `PaymentContextTypePispPayee`            | PISP_PAYEE                               |