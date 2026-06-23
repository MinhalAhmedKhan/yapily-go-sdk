<!-- Start SDK Example Usage [usage] -->
```go
package main

import (
	"context"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/operations"
	"log"
)

func main() {
	ctx := context.Background()

	s := yapily.New(
		yapily.WithSecurity(components.Security{
			Username: yapily.Pointer(""),
			Password: yapily.Pointer(""),
		}),
	)

	res, err := s.Authorisations.ReAuthoriseAccount(ctx, operations.ReAuthoriseAccountRequest{
		Consent: "{consentToken}",
	})
	if err != nil {
		log.Fatal(err)
	}
	if res.APIResponseOfAccountAuthorisationResponse != nil {
		// handle response
	}
}

```
<!-- End SDK Example Usage [usage] -->