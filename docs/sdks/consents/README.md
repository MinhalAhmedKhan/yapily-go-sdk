# Consents

## Overview

The Consents endpoints are used to manage each `Consent` created by Yapily in response to an authorisation created for a user.

The `Consent` object contains data that identifies a user's consent for a specific `Institution` within a Yapily application. Other than the id of the consent, the `institution-id` for the corresponding `Institution` and the user identifiers (`user-uuid` and `application-user-id`), it contains various details that indicates how the `Consent` can be used.

### Available Operations

* [CreateConsentWithCode](#createconsentwithcode) - Exchange OAuth2 Code
* [GetConsentBySingleAccessConsent](#getconsentbysingleaccessconsent) - Exchange One Time Token
* [GetConsents](#getconsents) - Get Consents
* [Delete](#delete) - Delete Consent
* [GetConsentByID](#getconsentbyid) - Get Consent
* [ExtendConsent](#extendconsent) - Extend Consent

## CreateConsentWithCode

Used to obtain a Yapily Consent object containing the `consentToken` once the user has authenticated and you have an OAuth2 authorisation code `auth-code` and state `auth-state`.

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="createConsentWithCode" method="post" path="/consent-auth-code" example="Error Response" -->
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

    res, err := s.Consents.CreateConsentWithCode(ctx, components.ConsentAuthCodeRequest{
        AuthCode: "6b965fbb-ff09-4afa-b897-90c34797cb8f",
        AuthState: "1270cb2ffc4842b78953afa2228e0a87",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.Consent != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="createConsentWithCode" method="post" path="/consent-auth-code" example="Example Response" -->
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

    res, err := s.Consents.CreateConsentWithCode(ctx, components.ConsentAuthCodeRequest{
        AuthCode: "6b965fbb-ff09-4afa-b897-90c34797cb8f",
        AuthState: "1270cb2ffc4842b78953afa2228e0a87",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.Consent != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                              | Type                                                                                   | Required                                                                               | Description                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `ctx`                                                                                  | [context.Context](https://pkg.go.dev/context#Context)                                  | :heavy_check_mark:                                                                     | The context to use for the request.                                                    |
| `request`                                                                              | [components.ConsentAuthCodeRequest](../../models/components/consentauthcoderequest.md) | :heavy_check_mark:                                                                     | The request object to use for the request.                                             |
| `opts`                                                                                 | [][operations.Option](../../models/operations/option.md)                               | :heavy_minus_sign:                                                                     | The options for this request.                                                          |

### Response

**[*operations.CreateConsentWithCodeResponse](../../models/operations/createconsentwithcoderesponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetConsentBySingleAccessConsent

Exchange a One-time-token for the consent token

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getConsentBySingleAccessConsent" method="post" path="/consent-one-time-token" example="Error Response" -->
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

    res, err := s.Consents.GetConsentBySingleAccessConsent(ctx, components.OneTimeTokenRequest{
        OneTimeToken: "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJJTlNUSVRVVElPTiI6ImJidmEtc2FuZGJveCIsIlVVSUQiOiJmMzNmNGU4ZC1jMDQ0LTQ2YTktOTlkMC0wYmRlMzIyYTJjOTIifQ.4Qv3NJI6av2nKi1U3aNmm71cIwJ3TvRsIlYDafQUVv_Khy_e-8oEpV_BoP4V1CII12oT-Yq4cPveHILz8BOwjg",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.Consent != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="getConsentBySingleAccessConsent" method="post" path="/consent-one-time-token" example="Example Response" -->
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

    res, err := s.Consents.GetConsentBySingleAccessConsent(ctx, components.OneTimeTokenRequest{
        OneTimeToken: "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJJTlNUSVRVVElPTiI6ImJidmEtc2FuZGJveCIsIlVVSUQiOiJmMzNmNGU4ZC1jMDQ0LTQ2YTktOTlkMC0wYmRlMzIyYTJjOTIifQ.4Qv3NJI6av2nKi1U3aNmm71cIwJ3TvRsIlYDafQUVv_Khy_e-8oEpV_BoP4V1CII12oT-Yq4cPveHILz8BOwjg",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.Consent != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                        | Type                                                                             | Required                                                                         | Description                                                                      |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `ctx`                                                                            | [context.Context](https://pkg.go.dev/context#Context)                            | :heavy_check_mark:                                                               | The context to use for the request.                                              |
| `request`                                                                        | [components.OneTimeTokenRequest](../../models/components/onetimetokenrequest.md) | :heavy_check_mark:                                                               | The request object to use for the request.                                       |
| `opts`                                                                           | [][operations.Option](../../models/operations/option.md)                         | :heavy_minus_sign:                                                               | The options for this request.                                                    |

### Response

**[*operations.GetConsentBySingleAccessConsentResponse](../../models/operations/getconsentbysingleaccessconsentresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetConsents

Used to retrieve all the consents created for each user within an application. At least one of the following filters needs to be applied: filter[applicationUserId], filter[userUuid]=, limit=. 

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getConsents" method="get" path="/consents" example="Error Response" -->
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

    res, err := s.Consents.GetConsents(ctx, operations.GetConsentsRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfConsent != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="getConsents" method="get" path="/consents" example="Example Response" -->
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

    res, err := s.Consents.GetConsents(ctx, operations.GetConsentsRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfConsent != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                      | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `ctx`                                                                          | [context.Context](https://pkg.go.dev/context#Context)                          | :heavy_check_mark:                                                             | The context to use for the request.                                            |
| `request`                                                                      | [operations.GetConsentsRequest](../../models/operations/getconsentsrequest.md) | :heavy_check_mark:                                                             | The request object to use for the request.                                     |
| `opts`                                                                         | [][operations.Option](../../models/operations/option.md)                       | :heavy_minus_sign:                                                             | The options for this request.                                                  |

### Response

**[*operations.GetConsentsResponse](../../models/operations/getconsentsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## Delete

Delete a consent using the consent Id

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="delete" method="delete" path="/consents/{consentId}" example="Error Response" -->
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

    res, err := s.Consents.Delete(ctx, "9e8a8b5f-b871-4680-b1c7-84f42b624ff2", yapily.Pointer(true))
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfConsentDeleteResponse != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="delete" method="delete" path="/consents/{consentId}" example="Example Response" -->
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

    res, err := s.Consents.Delete(ctx, "11d5c4b0-31a3-4d6c-8242-5294165bc42f", yapily.Pointer(true))
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfConsentDeleteResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                 | Type                                                      | Required                                                  | Description                                               |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `ctx`                                                     | [context.Context](https://pkg.go.dev/context#Context)     | :heavy_check_mark:                                        | The context to use for the request.                       |
| `consentID`                                               | `string`                                                  | :heavy_check_mark:                                        | __Mandatory__. The consent Id of the `Consent` to update. |
| `forceDelete`                                             | `*bool`                                                   | :heavy_minus_sign:                                        | __Optional__. Whether to force the deletion.              |
| `opts`                                                    | [][operations.Option](../../models/operations/option.md)  | :heavy_minus_sign:                                        | The options for this request.                             |

### Response

**[*operations.DeleteResponse](../../models/operations/deleteresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetConsentByID

Get consent using the consent Id

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getConsentById" method="get" path="/consents/{consentId}" example="Error Response" -->
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

    res, err := s.Consents.GetConsentByID(ctx, "be40ca71-966a-4e02-9182-0da96c30bc4d")
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfConsent != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="getConsentById" method="get" path="/consents/{consentId}" example="Example Response" -->
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

    res, err := s.Consents.GetConsentByID(ctx, "9bc22dce-5451-48ce-8ef2-b4ff91249b6a")
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfConsent != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                 | Type                                                      | Required                                                  | Description                                               |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `ctx`                                                     | [context.Context](https://pkg.go.dev/context#Context)     | :heavy_check_mark:                                        | The context to use for the request.                       |
| `consentID`                                               | `string`                                                  | :heavy_check_mark:                                        | __Mandatory__. The consent Id of the `Consent` to update. |
| `opts`                                                    | [][operations.Option](../../models/operations/option.md)  | :heavy_minus_sign:                                        | The options for this request.                             |

### Response

**[*operations.GetConsentByIDResponse](../../models/operations/getconsentbyidresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## ExtendConsent

Used to indicate to Yapily that reconfirmation has occurred for a given Consent, and to update lastUpdatedAt and reconfirmBy for that Consent. Returns the Consent.

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="extendConsent" method="post" path="/consents/{consentId}/extend" example="Error Response" -->
```go
package main

import(
	"context"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/types"
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

    res, err := s.Consents.ExtendConsent(ctx, "dacb03aa-5e1f-46ab-8ed8-4fd7e2e4e862", components.ExtendConsentRequest{
        LastConfirmedAt: types.MustTimeFromString("2022-08-16T10:59:53.288Z"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfConsent != nil {
        // handle response
    }
}
```
### Example Usage: Example Request

<!-- UsageSnippet language="go" operationID="extendConsent" method="post" path="/consents/{consentId}/extend" example="Example Request" -->
```go
package main

import(
	"context"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/types"
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

    res, err := s.Consents.ExtendConsent(ctx, "59b9f6fd-1713-40b3-9724-19f232709d9d", components.ExtendConsentRequest{
        LastConfirmedAt: types.MustTimeFromString("2021-07-08T10:59:53.288Z"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfConsent != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="extendConsent" method="post" path="/consents/{consentId}/extend" example="Example Response" -->
```go
package main

import(
	"context"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
	yapily "github.com/MinhalAhmedKhan/yapily-go-sdk"
	"github.com/MinhalAhmedKhan/yapily-go-sdk/types"
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

    res, err := s.Consents.ExtendConsent(ctx, "b6df2e8c-0d0e-49b8-9a3b-83bf74855f0f", components.ExtendConsentRequest{
        LastConfirmedAt: types.MustTimeFromString("2022-08-16T10:59:53.288Z"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfConsent != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                          | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `ctx`                                                                              | [context.Context](https://pkg.go.dev/context#Context)                              | :heavy_check_mark:                                                                 | The context to use for the request.                                                |
| `consentID`                                                                        | `string`                                                                           | :heavy_check_mark:                                                                 | __Mandatory__. The consent Id of the `Consent` to update.                          |
| `body`                                                                             | [components.ExtendConsentRequest](../../models/components/extendconsentrequest.md) | :heavy_check_mark:                                                                 | N/A                                                                                |
| `opts`                                                                             | [][operations.Option](../../models/operations/option.md)                           | :heavy_minus_sign:                                                                 | The options for this request.                                                      |

### Response

**[*operations.ExtendConsentResponse](../../models/operations/extendconsentresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponse     | 400                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |