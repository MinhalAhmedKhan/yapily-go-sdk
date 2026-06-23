# ApplicationManagement

## Overview

Application Management endpoints help with creating and managing client sub-applications.

### Available Operations

* [CreateSubApplication](#createsubapplication) - Creates a sub-application for the root application id provided in the authentication token
* [SearchApplications](#searchapplications) - Retrieve sub-applications for the root application provided in the authentication token.
* [GetApplicationByID](#getapplicationbyid) - Get application details
* [UpdateApplication](#updateapplication) - Update an Application
* [DeleteApplication](#deleteapplication) - Delete an application
* [CreateApplicationVRPConfigurationByApplicationID](#createapplicationvrpconfigurationbyapplicationid) - Create application VRP configuration by Application Id
* [UpdateApplicationVRPConfigurationByApplicationID](#updateapplicationvrpconfigurationbyapplicationid) - Update application VRP configuration by Application Id
* [GetApplicationVRPConfigurationByApplicationID](#getapplicationvrpconfigurationbyapplicationid) - Get application VRP configuration by Application Id

## CreateSubApplication

Creates a sub-application under the given root application id provided in the authentication token. The sub-application can use the root's credentials to call the API

### Example Usage: Create Sub-application Request

<!-- UsageSnippet language="go" operationID="createSubApplication" method="post" path="/applications" example="Create Sub-application Request" -->
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

    res, err := s.ApplicationManagement.CreateSubApplication(ctx, components.ApplicationRequest{
        Name: "Merchant Uno",
        MerchantCategoryCode: "7995",
        PpcUserGroup: "WHOLESALE_FI_FI",
        CallbackUrls: []string{
            "https://www.callback-service.com",
        },
        IsContractPresent: true,
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfApplicationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Create Sub-application Response

<!-- UsageSnippet language="go" operationID="createSubApplication" method="post" path="/applications" example="Create Sub-application Response" -->
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

    res, err := s.ApplicationManagement.CreateSubApplication(ctx, components.ApplicationRequest{
        Name: "<value>",
        MerchantCategoryCode: "0742",
        PpcUserGroup: "WHOLESALE_FI_FI",
        IsContractPresent: false,
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfApplicationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="createSubApplication" method="post" path="/applications" example="Error Response" -->
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

    res, err := s.ApplicationManagement.CreateSubApplication(ctx, components.ApplicationRequest{
        Name: "<value>",
        MerchantCategoryCode: "0742",
        PpcUserGroup: "WHOLESALE_FI_FI",
        IsContractPresent: false,
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfApplicationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                      | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `ctx`                                                                          | [context.Context](https://pkg.go.dev/context#Context)                          | :heavy_check_mark:                                                             | The context to use for the request.                                            |
| `request`                                                                      | [components.ApplicationRequest](../../models/components/applicationrequest.md) | :heavy_check_mark:                                                             | The request object to use for the request.                                     |
| `opts`                                                                         | [][operations.Option](../../models/operations/option.md)                       | :heavy_minus_sign:                                                             | The options for this request.                                                  |

### Response

**[*operations.CreateSubApplicationResponse](../../models/operations/createsubapplicationresponse.md), error**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| apierrors.ValidationErrorResponse | 400                               | application/json;charset=UTF-8    |
| apierrors.APIErrorResponse        | 401, 403, 404                     | application/json;charset=UTF-8    |
| apierrors.APIErrorResponse        | 500                               | application/json;charset=UTF-8    |
| apierrors.APIError                | 4XX, 5XX                          | \*/\*                             |

## SearchApplications

Retrieves sub-applications for the root application provided in the authentication token. If a sub-application is provided in the authentication token, it will return an empty list.

### Example Usage

<!-- UsageSnippet language="go" operationID="searchApplications" method="get" path="/applications" example="Get Applications Response" -->
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

    res, err := s.ApplicationManagement.SearchApplications(ctx, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListOfApplicationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                               | [context.Context](https://pkg.go.dev/context#Context)                                               | :heavy_check_mark:                                                                                  | The context to use for the request.                                                                 |
| `publicFilterValues`                                                                                | [*components.SearchApplicationsParameters](../../models/components/searchapplicationsparameters.md) | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `opts`                                                                                              | [][operations.Option](../../models/operations/option.md)                                            | :heavy_minus_sign:                                                                                  | The options for this request.                                                                       |

### Response

**[*operations.SearchApplicationsResponse](../../models/operations/searchapplicationsresponse.md), error**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| apierrors.ValidationErrorResponse | 400                               | application/json                  |
| apierrors.APIErrorResponse        | 401, 403                          | application/json;charset=UTF-8    |
| apierrors.APIErrorResponse        | 500                               | application/json;charset=UTF-8    |
| apierrors.APIError                | 4XX, 5XX                          | \*/\*                             |

## GetApplicationByID

Retrieves an application by the id provided in the path

### Example Usage

<!-- UsageSnippet language="go" operationID="getApplicationById" method="get" path="/applications/{applicationId}" example="Get Application By Id Response" -->
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

    res, err := s.ApplicationManagement.GetApplicationByID(ctx, "28cf29b9-0609-4635-8c44-7f84b97ceeb3")
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfApplicationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `applicationID`                                          | `string`                                                 | :heavy_check_mark:                                       | The id of the application being fetched                  |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetApplicationByIDResponse](../../models/operations/getapplicationbyidresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponse     | 401, 403, 404                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponse     | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## UpdateApplication

Updates the application properties for the application with the given ID in the path

### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="updateApplication" method="put" path="/applications/{applicationId}" example="Error Response" -->
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

    res, err := s.ApplicationManagement.UpdateApplication(ctx, "27c32aab-48fb-4938-9085-83f3deb512d4", components.ApplicationRequest{
        Name: "<value>",
        MerchantCategoryCode: "0742",
        PpcUserGroup: "WHOLESALE_FI_FI",
        IsContractPresent: true,
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfApplicationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Update Application Request

<!-- UsageSnippet language="go" operationID="updateApplication" method="put" path="/applications/{applicationId}" example="Update Application Request" -->
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

    res, err := s.ApplicationManagement.UpdateApplication(ctx, "c177a64c-ef46-48b4-80d1-6b89b661e873", components.ApplicationRequest{
        Name: "Merchant Uno",
        MerchantCategoryCode: "7995",
        PpcUserGroup: "WHOLESALE_FI_FI",
        CallbackUrls: []string{
            "https://www.callback-service.com",
        },
        IsContractPresent: true,
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfApplicationResponse != nil {
        // handle response
    }
}
```
### Example Usage: Update Application Response

<!-- UsageSnippet language="go" operationID="updateApplication" method="put" path="/applications/{applicationId}" example="Update Application Response" -->
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

    res, err := s.ApplicationManagement.UpdateApplication(ctx, "1ed75fcf-4af3-491c-9d31-4c7dfc3303c0", components.ApplicationRequest{
        Name: "<value>",
        MerchantCategoryCode: "0742",
        PpcUserGroup: "WHOLESALE_FI_FI",
        IsContractPresent: true,
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfApplicationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                      | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `ctx`                                                                          | [context.Context](https://pkg.go.dev/context#Context)                          | :heavy_check_mark:                                                             | The context to use for the request.                                            |
| `applicationID`                                                                | `string`                                                                       | :heavy_check_mark:                                                             | The id of the application being updated                                        |
| `body`                                                                         | [components.ApplicationRequest](../../models/components/applicationrequest.md) | :heavy_check_mark:                                                             | The application to update                                                      |
| `opts`                                                                         | [][operations.Option](../../models/operations/option.md)                       | :heavy_minus_sign:                                                             | The options for this request.                                                  |

### Response

**[*operations.UpdateApplicationResponse](../../models/operations/updateapplicationresponse.md), error**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| apierrors.ValidationErrorResponse | 400                               | application/json;charset=UTF-8    |
| apierrors.APIErrorResponse        | 401, 403                          | application/json;charset=UTF-8    |
| apierrors.APIErrorResponse        | 500                               | application/json;charset=UTF-8    |
| apierrors.APIError                | 4XX, 5XX                          | \*/\*                             |

## DeleteApplication

Deletes the application with the given ID in the path

### Example Usage

<!-- UsageSnippet language="go" operationID="deleteApplication" method="delete" path="/applications/{applicationId}" -->
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

    res, err := s.ApplicationManagement.DeleteApplication(ctx, "595e04a2-d658-4ec4-8cdf-53a39a215528")
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `applicationID`                                          | `string`                                                 | :heavy_check_mark:                                       | The id of the application being deleted                  |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.DeleteApplicationResponse](../../models/operations/deleteapplicationresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponse     | 401, 403, 404                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponse     | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## CreateApplicationVRPConfigurationByApplicationID

Create application vrp configuration

### Example Usage: 401 Error Response

<!-- UsageSnippet language="go" operationID="createApplicationVRPConfigurationByApplicationId" method="post" path="/applications/{applicationId}/vrp" example="401 Error Response" -->
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

    res, err := s.ApplicationManagement.CreateApplicationVRPConfigurationByApplicationID(ctx, "1b885c2d-af5d-4ccf-8614-cdaddc154f68", components.VrpConfiguration{
        MaximumIndividualAmount: &components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
        MaximumCumulativeAmount: &components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
        PeriodicLimits: []components.VrpPeriodicLimit{
            components.VrpPeriodicLimit{
                MaximumAmount: components.Amount{
                    Amount: 10.0,
                    Currency: "GBP",
                },
                Frequency: components.FrequencyEnumMonthly,
                Alignment: components.AlignmentEnumCalendar,
            },
        },
        RecurringPaymentCategory: yapily.Pointer("ONGOING"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="createApplicationVRPConfigurationByApplicationId" method="post" path="/applications/{applicationId}/vrp" example="Error Response" -->
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

    res, err := s.ApplicationManagement.CreateApplicationVRPConfigurationByApplicationID(ctx, "815b5698-f55a-45f9-960b-a984384c091a", components.VrpConfiguration{
        MaximumIndividualAmount: &components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
        MaximumCumulativeAmount: &components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
        PeriodicLimits: []components.VrpPeriodicLimit{
            components.VrpPeriodicLimit{
                MaximumAmount: components.Amount{
                    Amount: 10.0,
                    Currency: "GBP",
                },
                Frequency: components.FrequencyEnumMonthly,
                Alignment: components.AlignmentEnumCalendar,
            },
        },
        RecurringPaymentCategory: yapily.Pointer("ONGOING"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                  | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `ctx`                                                                      | [context.Context](https://pkg.go.dev/context#Context)                      | :heavy_check_mark:                                                         | The context to use for the request.                                        |
| `applicationID`                                                            | `string`                                                                   | :heavy_check_mark:                                                         | The id of the application that vrp configuration being created for         |
| `body`                                                                     | [components.VrpConfiguration](../../models/components/vrpconfiguration.md) | :heavy_check_mark:                                                         | The vrp configuration to create                                            |
| `opts`                                                                     | [][operations.Option](../../models/operations/option.md)                   | :heavy_minus_sign:                                                         | The options for this request.                                              |

### Response

**[*operations.CreateApplicationVRPConfigurationByApplicationIDResponse](../../models/operations/createapplicationvrpconfigurationbyapplicationidresponse.md), error**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| apierrors.ValidationErrorResponse | 400                               | application/json;charset=UTF-8    |
| apierrors.APIErrorResponse        | 401, 403, 404                     | application/json;charset=UTF-8    |
| apierrors.APIErrorResponse        | 500                               | application/json;charset=UTF-8    |
| apierrors.APIError                | 4XX, 5XX                          | \*/\*                             |

## UpdateApplicationVRPConfigurationByApplicationID

Update application vrp configuration

### Example Usage: 401 Error Response

<!-- UsageSnippet language="go" operationID="updateApplicationVRPConfigurationByApplicationId" method="put" path="/applications/{applicationId}/vrp" example="401 Error Response" -->
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

    res, err := s.ApplicationManagement.UpdateApplicationVRPConfigurationByApplicationID(ctx, "6a5ac201-20eb-4d05-9dbe-8979a501a0fe", components.VrpConfiguration{
        MaximumIndividualAmount: &components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
        MaximumCumulativeAmount: &components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
        PeriodicLimits: []components.VrpPeriodicLimit{
            components.VrpPeriodicLimit{
                MaximumAmount: components.Amount{
                    Amount: 10.0,
                    Currency: "GBP",
                },
                Frequency: components.FrequencyEnumMonthly,
                Alignment: components.AlignmentEnumConsent,
            },
        },
        RecurringPaymentCategory: yapily.Pointer("ONGOING"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```
### Example Usage: Error Response

<!-- UsageSnippet language="go" operationID="updateApplicationVRPConfigurationByApplicationId" method="put" path="/applications/{applicationId}/vrp" example="Error Response" -->
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

    res, err := s.ApplicationManagement.UpdateApplicationVRPConfigurationByApplicationID(ctx, "b3e88ec6-8fa9-42fb-9707-6f4f7cb1ac17", components.VrpConfiguration{
        MaximumIndividualAmount: &components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
        MaximumCumulativeAmount: &components.Amount{
            Amount: 10.0,
            Currency: "GBP",
        },
        PeriodicLimits: []components.VrpPeriodicLimit{
            components.VrpPeriodicLimit{
                MaximumAmount: components.Amount{
                    Amount: 10.0,
                    Currency: "GBP",
                },
                Frequency: components.FrequencyEnumMonthly,
                Alignment: components.AlignmentEnumConsent,
            },
        },
        RecurringPaymentCategory: yapily.Pointer("ONGOING"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                  | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `ctx`                                                                      | [context.Context](https://pkg.go.dev/context#Context)                      | :heavy_check_mark:                                                         | The context to use for the request.                                        |
| `applicationID`                                                            | `string`                                                                   | :heavy_check_mark:                                                         | The id of the application that vrp configuration being created for         |
| `body`                                                                     | [components.VrpConfiguration](../../models/components/vrpconfiguration.md) | :heavy_check_mark:                                                         | The vrp configuration to create                                            |
| `opts`                                                                     | [][operations.Option](../../models/operations/option.md)                   | :heavy_minus_sign:                                                         | The options for this request.                                              |

### Response

**[*operations.UpdateApplicationVRPConfigurationByApplicationIDResponse](../../models/operations/updateapplicationvrpconfigurationbyapplicationidresponse.md), error**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| apierrors.ValidationErrorResponse | 400                               | application/json;charset=UTF-8    |
| apierrors.APIErrorResponse        | 401, 403, 404                     | application/json;charset=UTF-8    |
| apierrors.APIErrorResponse        | 500                               | application/json;charset=UTF-8    |
| apierrors.APIError                | 4XX, 5XX                          | \*/\*                             |

## GetApplicationVRPConfigurationByApplicationID

Get application vrp configuration

### Example Usage

<!-- UsageSnippet language="go" operationID="getApplicationVRPConfigurationByApplicationId" method="get" path="/applications/{applicationId}/vrp" -->
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

    res, err := s.ApplicationManagement.GetApplicationVRPConfigurationByApplicationID(ctx, "472a2680-7503-4dc2-9a4f-6c1a4cf40dec")
    if err != nil {
        log.Fatal(err)
    }
    if res.VrpConfiguration != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                          | Type                                                               | Required                                                           | Description                                                        |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| `ctx`                                                              | [context.Context](https://pkg.go.dev/context#Context)              | :heavy_check_mark:                                                 | The context to use for the request.                                |
| `applicationID`                                                    | `string`                                                           | :heavy_check_mark:                                                 | The id of the application that vrp configuration being created for |
| `opts`                                                             | [][operations.Option](../../models/operations/option.md)           | :heavy_minus_sign:                                                 | The options for this request.                                      |

### Response

**[*operations.GetApplicationVRPConfigurationByApplicationIDResponse](../../models/operations/getapplicationvrpconfigurationbyapplicationidresponse.md), error**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| apierrors.ValidationErrorResponse | 400                               | application/json;charset=UTF-8    |
| apierrors.APIErrorResponse        | 401, 403, 404                     | application/json;charset=UTF-8    |
| apierrors.APIErrorResponse        | 500                               | application/json;charset=UTF-8    |
| apierrors.APIError                | 4XX, 5XX                          | \*/\*                             |