# ApplicationBeneficiaries

## Overview

Application Beneficiaries Endpoints

### Available Operations

* [CreateApplicationBeneficiary](#createapplicationbeneficiary) - Create application beneficiary
* [GetApplicationBeneficiaries](#getapplicationbeneficiaries) - Get all application beneficiaries
* [GetApplicationBeneficiaryByID](#getapplicationbeneficiarybyid) - Get application beneficiary by id
* [DeleteApplicationBeneficiaryByID](#deleteapplicationbeneficiarybyid) - Delete application beneficiary by id

## CreateApplicationBeneficiary

Creation of beneficiaries for a given application.

### Example Usage

<!-- UsageSnippet language="go" operationID="createApplicationBeneficiary" method="post" path="/applications/{applicationId}/beneficiaries" example="Example-1" -->
```go
package main

import(
	"context"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
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

    res, err := s.ApplicationBeneficiaries.CreateApplicationBeneficiary(ctx, "6d97cf35-1000-4787-af16-7100912db9e4", operations.CreateApplicationBeneficiaryRequestBody{
        Name: "John Doe",
        AccountIdentifier: components.AccountIdentifier{
            Type: components.AccountIdentifierTypeIban,
            Identification: "DE12345123451234512345123",
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.ApplicationBeneficiaryResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                | Type                                                                                                                     | Required                                                                                                                 | Description                                                                                                              | Example                                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                                    | [context.Context](https://pkg.go.dev/context#Context)                                                                    | :heavy_check_mark:                                                                                                       | The context to use for the request.                                                                                      |                                                                                                                          |
| `applicationID`                                                                                                          | `string`                                                                                                                 | :heavy_check_mark:                                                                                                       | Yapily application Id                                                                                                    | 6d97cf35-1000-4787-af16-7100912db9e4                                                                                     |
| `body`                                                                                                                   | [operations.CreateApplicationBeneficiaryRequestBody](../../models/operations/createapplicationbeneficiaryrequestbody.md) | :heavy_check_mark:                                                                                                       | The beneficiary to be created.                                                                                           |                                                                                                                          |
| `opts`                                                                                                                   | [][operations.Option](../../models/operations/option.md)                                                                 | :heavy_minus_sign:                                                                                                       | The options for this request.                                                                                            |                                                                                                                          |

### Response

**[*operations.CreateApplicationBeneficiaryResponse](../../models/operations/createapplicationbeneficiaryresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 404, 409, 429        | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## GetApplicationBeneficiaries

Get all application beneficiaries from an application.

### Example Usage

<!-- UsageSnippet language="go" operationID="getApplicationBeneficiaries" method="get" path="/applications/{applicationId}/beneficiaries" -->
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

    res, err := s.ApplicationBeneficiaries.GetApplicationBeneficiaries(ctx, "6d97cf35-1000-4787-af16-7100912db9e4")
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              | Example                                                  |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |                                                          |
| `applicationID`                                          | `string`                                                 | :heavy_check_mark:                                       | Yapily application Id                                    | 6d97cf35-1000-4787-af16-7100912db9e4                     |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |                                                          |

### Response

**[*operations.GetApplicationBeneficiariesResponse](../../models/operations/getapplicationbeneficiariesresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 401                            | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## GetApplicationBeneficiaryByID

Get user beneficiary by id.

### Example Usage

<!-- UsageSnippet language="go" operationID="getApplicationBeneficiaryById" method="get" path="/applications/{applicationId}/beneficiaries/{beneficiaryId}" -->
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

    res, err := s.ApplicationBeneficiaries.GetApplicationBeneficiaryByID(ctx, "6d97cf35-1000-4787-af16-7100912db9e4", "e7b7636d-a041-4013-8a1b-34dc85b7d341")
    if err != nil {
        log.Fatal(err)
    }
    if res.ApplicationBeneficiaryResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              | Example                                                  |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |                                                          |
| `applicationID`                                          | `string`                                                 | :heavy_check_mark:                                       | Yapily application Id                                    | 6d97cf35-1000-4787-af16-7100912db9e4                     |
| `beneficiaryID`                                          | `string`                                                 | :heavy_check_mark:                                       | N/A                                                      | e7b7636d-a041-4013-8a1b-34dc85b7d341                     |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |                                                          |

### Response

**[*operations.GetApplicationBeneficiaryByIDResponse](../../models/operations/getapplicationbeneficiarybyidresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 404                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## DeleteApplicationBeneficiaryByID

Delete application beneficiary.

### Example Usage

<!-- UsageSnippet language="go" operationID="deleteApplicationBeneficiaryById" method="delete" path="/applications/{applicationId}/beneficiaries/{beneficiaryId}" -->
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

    res, err := s.ApplicationBeneficiaries.DeleteApplicationBeneficiaryByID(ctx, "6d97cf35-1000-4787-af16-7100912db9e4", "e7b7636d-a041-4013-8a1b-34dc85b7d341")
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              | Example                                                  |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |                                                          |
| `applicationID`                                          | `string`                                                 | :heavy_check_mark:                                       | Yapily application Id                                    | 6d97cf35-1000-4787-af16-7100912db9e4                     |
| `beneficiaryID`                                          | `string`                                                 | :heavy_check_mark:                                       | N/A                                                      | e7b7636d-a041-4013-8a1b-34dc85b7d341                     |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |                                                          |

### Response

**[*operations.DeleteApplicationBeneficiaryByIDResponse](../../models/operations/deleteapplicationbeneficiarybyidresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 404                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |