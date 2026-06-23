# UserBeneficiaries

## Overview

User Beneficiaries Endpoints

### Available Operations

* [CreateUserBeneficiary](#createuserbeneficiary) - Create Beneficiary
* [GetUserBeneficiaries](#getuserbeneficiaries) - Get all users beneficiaries
* [PatchUserBeneficiary](#patchuserbeneficiary) - Patch User Beneficiary
* [GetUserBeneficiary](#getuserbeneficiary) - Get beneficiary by id
* [DeleteUserBeneficiary](#deleteuserbeneficiary) - Delete user beneficiary by id.
* [ApproveBeneficiary](#approvebeneficiary) - Approve Beneficiary
* [RejectBeneficiary](#rejectbeneficiary) - Reject Beneficiary

## CreateUserBeneficiary

Creation of beneficiaries for a given application User.

### Example Usage

<!-- UsageSnippet language="go" operationID="createUserBeneficiary" method="post" path="/users/{userId}/beneficiaries" example="Example-1" -->
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

    res, err := s.UserBeneficiaries.CreateUserBeneficiary(ctx, "e7b7636d-a041-4013-8a1b-34dc85b7d341", operations.CreateUserBeneficiaryRequestBody{
        Name: "John Doe",
        AccountIdentifier: components.AccountIdentifier{
            Type: components.AccountIdentifierTypeIban,
            Identification: "DE12345123451234512345123",
        },
    }, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.UserBeneficiaryResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                  | Type                                                                                                       | Required                                                                                                   | Description                                                                                                | Example                                                                                                    |
| ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                      | [context.Context](https://pkg.go.dev/context#Context)                                                      | :heavy_check_mark:                                                                                         | The context to use for the request.                                                                        |                                                                                                            |
| `userID`                                                                                                   | `string`                                                                                                   | :heavy_check_mark:                                                                                         | N/A                                                                                                        | e7b7636d-a041-4013-8a1b-34dc85b7d341                                                                       |
| `body`                                                                                                     | [operations.CreateUserBeneficiaryRequestBody](../../models/operations/createuserbeneficiaryrequestbody.md) | :heavy_check_mark:                                                                                         | The beneficiary to be created.                                                                             |                                                                                                            |
| `subApplication`                                                                                           | `*string`                                                                                                  | :heavy_minus_sign:                                                                                         | The sub-application ID to which event type is being subscribed to                                          |                                                                                                            |
| `opts`                                                                                                     | [][operations.Option](../../models/operations/option.md)                                                   | :heavy_minus_sign:                                                                                         | The options for this request.                                                                              |                                                                                                            |

### Response

**[*operations.CreateUserBeneficiaryResponse](../../models/operations/createuserbeneficiaryresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 404, 409, 429        | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## GetUserBeneficiaries

Get all users beneficiaries from an userId.

### Example Usage

<!-- UsageSnippet language="go" operationID="getUserBeneficiaries" method="get" path="/users/{userId}/beneficiaries" -->
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

    res, err := s.UserBeneficiaries.GetUserBeneficiaries(ctx, "e7b7636d-a041-4013-8a1b-34dc85b7d341")
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
| `userID`                                                 | `string`                                                 | :heavy_check_mark:                                       | N/A                                                      | e7b7636d-a041-4013-8a1b-34dc85b7d341                     |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |                                                          |

### Response

**[*operations.GetUserBeneficiariesResponse](../../models/operations/getuserbeneficiariesresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 404                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## PatchUserBeneficiary

Patch the beneficiary details for a given application user and beneficiary

### Example Usage: Example-1

<!-- UsageSnippet language="go" operationID="patchUserBeneficiary" method="patch" path="/users/{userId}/beneficiaries/{beneficiaryId}" example="Example-1" -->
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

    res, err := s.UserBeneficiaries.PatchUserBeneficiary(ctx, "e7b7636d-a041-4013-8a1b-34dc85b7d341", "e7b7636d-a041-4013-8a1b-34dc85b7d341", []operations.RequestBody{}, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.UserBeneficiaryResponse != nil {
        // handle response
    }
}
```
### Example Usage: update-name

<!-- UsageSnippet language="go" operationID="patchUserBeneficiary" method="patch" path="/users/{userId}/beneficiaries/{beneficiaryId}" example="update-name" -->
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

    res, err := s.UserBeneficiaries.PatchUserBeneficiary(ctx, "e7b7636d-a041-4013-8a1b-34dc85b7d341", "e7b7636d-a041-4013-8a1b-34dc85b7d341", []operations.RequestBody{
        operations.RequestBody{
            Op: components.PatchOperationReplace,
            Path: "/name",
            Value: "John Doe",
        },
    }, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.UserBeneficiaryResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                          | Type                                                               | Required                                                           | Description                                                        | Example                                                            |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| `ctx`                                                              | [context.Context](https://pkg.go.dev/context#Context)              | :heavy_check_mark:                                                 | The context to use for the request.                                |                                                                    |
| `beneficiaryID`                                                    | `string`                                                           | :heavy_check_mark:                                                 | N/A                                                                | e7b7636d-a041-4013-8a1b-34dc85b7d341                               |
| `userID`                                                           | `string`                                                           | :heavy_check_mark:                                                 | N/A                                                                | e7b7636d-a041-4013-8a1b-34dc85b7d341                               |
| `body`                                                             | [][operations.RequestBody](../../models/operations/requestbody.md) | :heavy_check_mark:                                                 | The JSON Patch instructions to patch the beneficiary               |                                                                    |
| `subApplication`                                                   | `*string`                                                          | :heavy_minus_sign:                                                 | The sub-application ID to which event type is being subscribed to  |                                                                    |
| `opts`                                                             | [][operations.Option](../../models/operations/option.md)           | :heavy_minus_sign:                                                 | The options for this request.                                      |                                                                    |

### Response

**[*operations.PatchUserBeneficiaryResponse](../../models/operations/patchuserbeneficiaryresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 404, 409, 429        | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## GetUserBeneficiary

Get user beneficiary by id.

### Example Usage

<!-- UsageSnippet language="go" operationID="getUserBeneficiary" method="get" path="/users/{userId}/beneficiaries/{beneficiaryId}" -->
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

    res, err := s.UserBeneficiaries.GetUserBeneficiary(ctx, "e7b7636d-a041-4013-8a1b-34dc85b7d341", "e7b7636d-a041-4013-8a1b-34dc85b7d341", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.UserBeneficiaryResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                         | Type                                                              | Required                                                          | Description                                                       | Example                                                           |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `ctx`                                                             | [context.Context](https://pkg.go.dev/context#Context)             | :heavy_check_mark:                                                | The context to use for the request.                               |                                                                   |
| `beneficiaryID`                                                   | `string`                                                          | :heavy_check_mark:                                                | N/A                                                               | e7b7636d-a041-4013-8a1b-34dc85b7d341                              |
| `userID`                                                          | `string`                                                          | :heavy_check_mark:                                                | N/A                                                               | e7b7636d-a041-4013-8a1b-34dc85b7d341                              |
| `subApplication`                                                  | `*string`                                                         | :heavy_minus_sign:                                                | The sub-application ID to which event type is being subscribed to |                                                                   |
| `opts`                                                            | [][operations.Option](../../models/operations/option.md)          | :heavy_minus_sign:                                                | The options for this request.                                     |                                                                   |

### Response

**[*operations.GetUserBeneficiaryResponse](../../models/operations/getuserbeneficiaryresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 429                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## DeleteUserBeneficiary

Delete user beneficiary by id.

### Example Usage

<!-- UsageSnippet language="go" operationID="deleteUserBeneficiary" method="delete" path="/users/{userId}/beneficiaries/{beneficiaryId}" -->
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

    res, err := s.UserBeneficiaries.DeleteUserBeneficiary(ctx, "e7b7636d-a041-4013-8a1b-34dc85b7d341", "e7b7636d-a041-4013-8a1b-34dc85b7d341", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                         | Type                                                              | Required                                                          | Description                                                       | Example                                                           |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `ctx`                                                             | [context.Context](https://pkg.go.dev/context#Context)             | :heavy_check_mark:                                                | The context to use for the request.                               |                                                                   |
| `beneficiaryID`                                                   | `string`                                                          | :heavy_check_mark:                                                | N/A                                                               | e7b7636d-a041-4013-8a1b-34dc85b7d341                              |
| `userID`                                                          | `string`                                                          | :heavy_check_mark:                                                | N/A                                                               | e7b7636d-a041-4013-8a1b-34dc85b7d341                              |
| `subApplication`                                                  | `*string`                                                         | :heavy_minus_sign:                                                | The sub-application ID to which event type is being subscribed to |                                                                   |
| `opts`                                                            | [][operations.Option](../../models/operations/option.md)          | :heavy_minus_sign:                                                | The options for this request.                                     |                                                                   |

### Response

**[*operations.DeleteUserBeneficiaryResponse](../../models/operations/deleteuserbeneficiaryresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 429                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## ApproveBeneficiary

End-user has approved the beneficiary details

### Example Usage

<!-- UsageSnippet language="go" operationID="approveBeneficiary" method="post" path="/users/{userId}/beneficiaries/{beneficiaryId}/approve" example="Example-1" -->
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

    res, err := s.UserBeneficiaries.ApproveBeneficiary(ctx, "e7b7636d-a041-4013-8a1b-34dc85b7d341", "e7b7636d-a041-4013-8a1b-34dc85b7d341", components.UserBeneficiaryValidationRequest{
        Name: "John Doe",
        Match: &components.UserBeneficiaryMatch{
            CloseMatchName: yapily.Pointer("John Doe"),
        },
        AccountIdentifier: components.AccountIdentifier{
            Type: components.AccountIdentifierTypeIban,
            Identification: "DE12345123451234512345123",
        },
    }, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.UserBeneficiaryResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                  | Type                                                                                                       | Required                                                                                                   | Description                                                                                                | Example                                                                                                    |
| ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                      | [context.Context](https://pkg.go.dev/context#Context)                                                      | :heavy_check_mark:                                                                                         | The context to use for the request.                                                                        |                                                                                                            |
| `beneficiaryID`                                                                                            | `string`                                                                                                   | :heavy_check_mark:                                                                                         | N/A                                                                                                        | e7b7636d-a041-4013-8a1b-34dc85b7d341                                                                       |
| `userID`                                                                                                   | `string`                                                                                                   | :heavy_check_mark:                                                                                         | N/A                                                                                                        | e7b7636d-a041-4013-8a1b-34dc85b7d341                                                                       |
| `body`                                                                                                     | [components.UserBeneficiaryValidationRequest](../../models/components/userbeneficiaryvalidationrequest.md) | :heavy_check_mark:                                                                                         | N/A                                                                                                        |                                                                                                            |
| `subApplication`                                                                                           | `*string`                                                                                                  | :heavy_minus_sign:                                                                                         | The sub-application ID to which event type is being subscribed to                                          |                                                                                                            |
| `opts`                                                                                                     | [][operations.Option](../../models/operations/option.md)                                                   | :heavy_minus_sign:                                                                                         | The options for this request.                                                                              |                                                                                                            |

### Response

**[*operations.ApproveBeneficiaryResponse](../../models/operations/approvebeneficiaryresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 404, 429             | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## RejectBeneficiary

End-user has rejected the beneficiary details

### Example Usage

<!-- UsageSnippet language="go" operationID="rejectBeneficiary" method="post" path="/users/{userId}/beneficiaries/{beneficiaryId}/reject" example="Example-1" -->
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

    res, err := s.UserBeneficiaries.RejectBeneficiary(ctx, "e7b7636d-a041-4013-8a1b-34dc85b7d341", "e7b7636d-a041-4013-8a1b-34dc85b7d341", components.UserBeneficiaryValidationRequest{
        Name: "John Doe",
        Match: &components.UserBeneficiaryMatch{
            CloseMatchName: yapily.Pointer("John Doe"),
        },
        AccountIdentifier: components.AccountIdentifier{
            Type: components.AccountIdentifierTypeIban,
            Identification: "DE12345123451234512345123",
        },
    }, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.UserBeneficiaryResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                  | Type                                                                                                       | Required                                                                                                   | Description                                                                                                | Example                                                                                                    |
| ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                      | [context.Context](https://pkg.go.dev/context#Context)                                                      | :heavy_check_mark:                                                                                         | The context to use for the request.                                                                        |                                                                                                            |
| `beneficiaryID`                                                                                            | `string`                                                                                                   | :heavy_check_mark:                                                                                         | N/A                                                                                                        | e7b7636d-a041-4013-8a1b-34dc85b7d341                                                                       |
| `userID`                                                                                                   | `string`                                                                                                   | :heavy_check_mark:                                                                                         | N/A                                                                                                        | e7b7636d-a041-4013-8a1b-34dc85b7d341                                                                       |
| `body`                                                                                                     | [components.UserBeneficiaryValidationRequest](../../models/components/userbeneficiaryvalidationrequest.md) | :heavy_check_mark:                                                                                         | N/A                                                                                                        |                                                                                                            |
| `subApplication`                                                                                           | `*string`                                                                                                  | :heavy_minus_sign:                                                                                         | The sub-application ID to which event type is being subscribed to                                          |                                                                                                            |
| `opts`                                                                                                     | [][operations.Option](../../models/operations/option.md)                                                   | :heavy_minus_sign:                                                                                         | The options for this request.                                                                              |                                                                                                            |

### Response

**[*operations.RejectBeneficiaryResponse](../../models/operations/rejectbeneficiaryresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 404                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |