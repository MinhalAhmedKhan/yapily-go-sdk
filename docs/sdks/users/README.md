# Users

## Overview

The Users endpoints are used to manage each user (otherwise known as the PSU) in Yapily. Each user belongs to an Application and as a consequence, so do each `Consent` created for a particular `User`.

### Available Operations

* [GetUsers](#getusers) - Get Users
* [AddUser](#adduser) - Create User
* [PatchUser](#patchuser) - Update User
* [DeleteUser](#deleteuser) - Delete User
* [GetUser](#getuser) - Get User

## GetUsers

Retrieves all users created in your application for a specified applicationUserId using the filter[applicationUserId] query parameter. If filter[applicationUserId] is not provided, the response will include up to 50,000 users.

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getUsers" method="get" path="/users" example="Error Response" -->
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

    res, err := s.Users.GetUsers(ctx, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.ApplicationUsers != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="getUsers" method="get" path="/users" example="Example Response" -->
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

    res, err := s.Users.GetUsers(ctx, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.ApplicationUsers != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                             | Type                                                                                  | Required                                                                              | Description                                                                           |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `ctx`                                                                                 | [context.Context](https://pkg.go.dev/context#Context)                                 | :heavy_check_mark:                                                                    | The context to use for the request.                                                   |
| `filterApplicationUserID`                                                             | []`string`                                                                            | :heavy_minus_sign:                                                                    | __Optional__. Filter records based on the list of `applicationUserId` users provided. |
| `opts`                                                                                | [][operations.Option](../../models/operations/option.md)                              | :heavy_minus_sign:                                                                    | The options for this request.                                                         |

### Response

**[*operations.GetUsersResponse](../../models/operations/getusersresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## AddUser

Create a new user in your application

### Example Usage: Create User Example Request

<!-- UsageSnippet language="go" operationID="addUser" method="post" path="/users" example="Create User Example Request" -->
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

    res, err := s.Users.AddUser(ctx, components.NewApplicationUser{
        ApplicationUserID: yapily.Pointer("string"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.ApplicationUser != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="addUser" method="post" path="/users" example="Error Response" -->
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

    res, err := s.Users.AddUser(ctx, components.NewApplicationUser{
        ApplicationUserID: yapily.Pointer("user-234562290"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.ApplicationUser != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="addUser" method="post" path="/users" example="Example Response" -->
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

    res, err := s.Users.AddUser(ctx, components.NewApplicationUser{
        ApplicationUserID: yapily.Pointer("user-234562290"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.ApplicationUser != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                      | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `ctx`                                                                          | [context.Context](https://pkg.go.dev/context#Context)                          | :heavy_check_mark:                                                             | The context to use for the request.                                            |
| `request`                                                                      | [components.NewApplicationUser](../../models/components/newapplicationuser.md) | :heavy_check_mark:                                                             | The request object to use for the request.                                     |
| `opts`                                                                         | [][operations.Option](../../models/operations/option.md)                       | :heavy_minus_sign:                                                             | The options for this request.                                                  |

### Response

**[*operations.AddUserResponse](../../models/operations/adduserresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## PatchUser

Update the users information

### Example Usage

<!-- UsageSnippet language="go" operationID="patchUser" method="patch" path="/users/{userUuid}" -->
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

    res, err := s.Users.PatchUser(ctx, "9d48623f-b953-4935-9aa1-597ab1b377ff", []components.ApplicationUserPatchRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res.ApplicationUser != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                          | Type                                                                                               | Required                                                                                           | Description                                                                                        |
| -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                              | [context.Context](https://pkg.go.dev/context#Context)                                              | :heavy_check_mark:                                                                                 | The context to use for the request.                                                                |
| `userUUID`                                                                                         | `string`                                                                                           | :heavy_check_mark:                                                                                 | __Mandatory__. The Yapily generated UUID for the user.                                             |
| `body`                                                                                             | [][components.ApplicationUserPatchRequest](../../models/components/applicationuserpatchrequest.md) | :heavy_check_mark:                                                                                 | N/A                                                                                                |
| `opts`                                                                                             | [][operations.Option](../../models/operations/option.md)                                           | :heavy_minus_sign:                                                                                 | The options for this request.                                                                      |

### Response

**[*operations.PatchUserResponse](../../models/operations/patchuserresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## DeleteUser

Delete a user from your application along with any sub-resources (including consent resources on institution APIs if they exist)

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="deleteUser" method="delete" path="/users/{userUuid}" example="Error Response" -->
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

    res, err := s.Users.DeleteUser(ctx, "8791f5cf-aa73-409f-a8ee-516069b2e7e6")
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfUserDeleteResponse != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="deleteUser" method="delete" path="/users/{userUuid}" example="Example Response" -->
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

    res, err := s.Users.DeleteUser(ctx, "d2de79a2-682e-4194-8a4b-901df2fa9451")
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfUserDeleteResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `userUUID`                                               | `string`                                                 | :heavy_check_mark:                                       | __Mandatory__. The Yapily generated UUID for the user.   |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.DeleteUserResponse](../../models/operations/deleteuserresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetUser

Get a specific user using the user UUID

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="getUser" method="get" path="/users/{userUuid}" example="Error Response" -->
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

    res, err := s.Users.GetUser(ctx, "e43476cb-fcaf-4bca-9c6c-97a76317b46f")
    if err != nil {
        log.Fatal(err)
    }
    if res.ApplicationUser != nil {
        // handle response
    }
}
```
### Example Usage: Example Response

<!-- UsageSnippet language="go" operationID="getUser" method="get" path="/users/{userUuid}" example="Example Response" -->
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

    res, err := s.Users.GetUser(ctx, "23d6a551-c558-4ea6-af9d-e8b1650326ce")
    if err != nil {
        log.Fatal(err)
    }
    if res.ApplicationUser != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `userUUID`                                               | `string`                                                 | :heavy_check_mark:                                       | __Mandatory__. The Yapily generated UUID for the user.   |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetUserResponse](../../models/operations/getuserresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |