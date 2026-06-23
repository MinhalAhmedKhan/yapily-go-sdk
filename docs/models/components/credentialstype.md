# CredentialsType

The type of credentials required to register the `Institution`

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.CredentialsTypeOauth1

// Open enum: custom values can be created with a direct type cast
custom := components.CredentialsType("custom_value")
```


## Values

| Name                                           | Value                                          |
| ---------------------------------------------- | ---------------------------------------------- |
| `CredentialsTypeOauth1`                        | OAUTH1                                         |
| `CredentialsTypeOauth2`                        | OAUTH2                                         |
| `CredentialsTypeOauth2Nosecret`                | OAUTH2_NOSECRET                                |
| `CredentialsTypeOauth2Signature`               | OAUTH2_SIGNATURE                               |
| `CredentialsTypeOpenBankingUkManual`           | OPEN_BANKING_UK_MANUAL                         |
| `CredentialsTypeOpenBankingUkAuto`             | OPEN_BANKING_UK_AUTO                           |
| `CredentialsTypeOpenBankingIbm`                | OPEN_BANKING_IBM                               |
| `CredentialsTypeOpenBankingAuto`               | OPEN_BANKING_AUTO                              |
| `CredentialsTypeOpenBankingAutoEmail`          | OPEN_BANKING_AUTO_EMAIL                        |
| `CredentialsTypeOpenBankingManual`             | OPEN_BANKING_MANUAL                            |
| `CredentialsTypeOpenBankingWithTppIDAndSecret` | OPEN_BANKING_WITH_TPP_ID_AND_SECRET            |
| `CredentialsTypeAPIKey`                        | API_KEY                                        |
| `CredentialsTypeOpenBankingNoKey`              | OPEN_BANKING_NO_KEY                            |
| `CredentialsTypeOpenBankingNoTransport`        | OPEN_BANKING_NO_TRANSPORT                      |
| `CredentialsTypeTokenIo`                       | TOKEN_IO                                       |