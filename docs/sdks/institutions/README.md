# Institutions

## Overview

An `Institution` object represents any Account Serving Payment Servicing Provider (ASPSP) that has been integrated and is accessible through the Yapily APIs (ASPSPs are entities that publish Read/Write APIs to permit, with customer consent, payments initiated by third party providers and/or make their customers financial data available to third party providers via their API endpoints).

Any one of the following would be represented as Institution:

- Traditional banks e.g. Santander
- Neo-banks e.g. Monzo
- Building societies e.g. Cumberland Building Society

### Available Operations

* [GetInstitutions](#getinstitutions) - Get Institutions
* [GetInstitution](#getinstitution) - Get Institution

## GetInstitutions

Used to retrieve all `Institutions` within an application

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getInstitutions" method="get" path="/institutions" example="Error Response" -->
```go
package main

import(
	"context"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
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

    res, err := s.Institutions.GetInstitutions(ctx)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfInstitution != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="getInstitutions" method="get" path="/institutions" example="Example Response" -->
```go
package main

import(
	"context"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
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

    res, err := s.Institutions.GetInstitutions(ctx)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfInstitution != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetInstitutionsResponse](../../models/operations/getinstitutionsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetInstitution

Used to retrieves details of a specific `Institution` within an application

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getInstitution" method="get" path="/institutions/{institutionId}" example="Error Response" -->
```go
package main

import(
	"context"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
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

    res, err := s.Institutions.GetInstitution(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.Institution != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="getInstitution" method="get" path="/institutions/{institutionId}" example="Example Response" -->
```go
package main

import(
	"context"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
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

    res, err := s.Institutions.GetInstitution(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.Institution != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                       | Type                                                            | Required                                                        | Description                                                     |
| --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| `ctx`                                                           | [context.Context](https://pkg.go.dev/context#Context)           | :heavy_check_mark:                                              | The context to use for the request.                             |
| `institutionID`                                                 | `string`                                                        | :heavy_check_mark:                                              | __Mandatory__. The Yapily institution Id for the `Institution`. |
| `opts`                                                          | [][operations.Option](../../models/operations/option.md)        | :heavy_minus_sign:                                              | The options for this request.                                   |

### Response

**[*operations.GetInstitutionResponse](../../models/operations/getinstitutionresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |