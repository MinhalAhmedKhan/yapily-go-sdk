# AddressTypeEnum

__Optional__. The type of address

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.AddressTypeEnumBusiness

// Open enum: custom values can be created with a direct type cast
custom := components.AddressTypeEnum("custom_value")
```


## Values

| Name                            | Value                           |
| ------------------------------- | ------------------------------- |
| `AddressTypeEnumBusiness`       | BUSINESS                        |
| `AddressTypeEnumCorrespondence` | CORRESPONDENCE                  |
| `AddressTypeEnumDeliveryTo`     | DELIVERY_TO                     |
| `AddressTypeEnumMailTo`         | MAIL_TO                         |
| `AddressTypeEnumPoBox`          | PO_BOX                          |
| `AddressTypeEnumPostal`         | POSTAL                          |
| `AddressTypeEnumResidential`    | RESIDENTIAL                     |
| `AddressTypeEnumStatement`      | STATEMENT                       |
| `AddressTypeEnumUnknown`        | UNKNOWN                         |