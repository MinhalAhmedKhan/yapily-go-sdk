# AuthorisationStatus

Current status of the embedded authorisation request in code form.

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.AuthorisationStatusAwaitingAuthorization

// Open enum: custom values can be created with a direct type cast
custom := components.AuthorisationStatus("custom_value")
```


## Values

| Name                                                   | Value                                                  |
| ------------------------------------------------------ | ------------------------------------------------------ |
| `AuthorisationStatusAwaitingAuthorization`             | AWAITING_AUTHORIZATION                                 |
| `AuthorisationStatusAwaitingFurtherAuthorization`      | AWAITING_FURTHER_AUTHORIZATION                         |
| `AuthorisationStatusAwaitingReAuthorization`           | AWAITING_RE_AUTHORIZATION                              |
| `AuthorisationStatusAuthorized`                        | AUTHORIZED                                             |
| `AuthorisationStatusConsumed`                          | CONSUMED                                               |
| `AuthorisationStatusRejected`                          | REJECTED                                               |
| `AuthorisationStatusRevoked`                           | REVOKED                                                |
| `AuthorisationStatusFailed`                            | FAILED                                                 |
| `AuthorisationStatusExpired`                           | EXPIRED                                                |
| `AuthorisationStatusUnknown`                           | UNKNOWN                                                |
| `AuthorisationStatusInvalid`                           | INVALID                                                |
| `AuthorisationStatusAwaitingDecoupledPreAuthorization` | AWAITING_DECOUPLED_PRE_AUTHORIZATION                   |
| `AuthorisationStatusAwaitingPreAuthorization`          | AWAITING_PRE_AUTHORIZATION                             |
| `AuthorisationStatusPreAuthorized`                     | PRE_AUTHORIZED                                         |
| `AuthorisationStatusAwaitingDecoupledAuthorization`    | AWAITING_DECOUPLED_AUTHORIZATION                       |
| `AuthorisationStatusAwaitingScaMethod`                 | AWAITING_SCA_METHOD                                    |
| `AuthorisationStatusAwaitingScaCode`                   | AWAITING_SCA_CODE                                      |