# Webhooks

## Overview

Webhook endpoints

### Available Operations

* [GetWebhookEventsCategories](#getwebhookeventscategories) - Get Webhook Categories
* [RegisterWebhook](#registerwebhook) - Register Webhook Event
* [GetRegisteredWebhooks](#getregisteredwebhooks) - Retrieve All Webhook Events
* [DeleteWebhook](#deletewebhook) - Delete Webhook Event
* [WebhookSecretReset](#webhooksecretreset) - Reset Webhook Secret

## GetWebhookEventsCategories

Retrieve a comprehensive list of event categories that can be registered for webhook notifications in your application. These event categories can be used to subscribe a webhook to specific events, enabling your application to receive real-time notifications when these events occur.

### Example Usage

<!-- UsageSnippet language="go" operationID="getWebhookEventsCategories" method="get" path="/webhook/events/categories" example="SuccessfulResponse" -->
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

    res, err := s.Webhooks.GetWebhookEventsCategories(ctx)
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
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

**[*operations.GetWebhookEventsCategoriesResponse](../../models/operations/getwebhookeventscategoriesresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401                       | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## RegisterWebhook

Register a webhook to one or multiple event categories to receive real-time notifications when specific events occur in your application.

### Example Usage

<!-- UsageSnippet language="go" operationID="registerWebhook" method="post" path="/webhook/events" -->
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

    res, err := s.Webhooks.RegisterWebhook(ctx, nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.WebhookDetailsWithSecret != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                       | Type                                                                                            | Required                                                                                        | Description                                                                                     |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `ctx`                                                                                           | [context.Context](https://pkg.go.dev/context#Context)                                           | :heavy_check_mark:                                                                              | The context to use for the request.                                                             |
| `subApplication`                                                                                | `*string`                                                                                       | :heavy_minus_sign:                                                                              | The sub-application ID to which event type is being subscribed to                               |
| `body`                                                                                          | [*operations.RegisterWebhookRequestBody](../../models/operations/registerwebhookrequestbody.md) | :heavy_minus_sign:                                                                              | N/A                                                                                             |
| `opts`                                                                                          | [][operations.Option](../../models/operations/option.md)                                        | :heavy_minus_sign:                                                                              | The options for this request.                                                                   |

### Response

**[*operations.RegisterWebhookResponse](../../models/operations/registerwebhookresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 406                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## GetRegisteredWebhooks

Retrieve the list of registered webhooks for your application

### Example Usage

<!-- UsageSnippet language="go" operationID="getRegisteredWebhooks" method="get" path="/webhook/events" -->
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

    res, err := s.Webhooks.GetRegisteredWebhooks(ctx, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                         | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `ctx`                                                             | [context.Context](https://pkg.go.dev/context#Context)             | :heavy_check_mark:                                                | The context to use for the request.                               |
| `subApplication`                                                  | `*string`                                                         | :heavy_minus_sign:                                                | The sub-application ID to which event type is being subscribed to |
| `opts`                                                            | [][operations.Option](../../models/operations/option.md)          | :heavy_minus_sign:                                                | The options for this request.                                     |

### Response

**[*operations.GetRegisteredWebhooksResponse](../../models/operations/getregisteredwebhooksresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401                       | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## DeleteWebhook

Delete a webhook event for a specified webhook ID, unregistering it from receiving any further notifications for the subscribed event categories in your application.

### Example Usage

<!-- UsageSnippet language="go" operationID="deleteWebhook" method="delete" path="/webhook/events/{webhook_id}" -->
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

    res, err := s.Webhooks.DeleteWebhook(ctx, "2f4cf1de-535d-40b8-9860-de80b52e1022", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                         | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `ctx`                                                             | [context.Context](https://pkg.go.dev/context#Context)             | :heavy_check_mark:                                                | The context to use for the request.                               |
| `webhookID`                                                       | `string`                                                          | :heavy_check_mark:                                                | Registered webhook ID                                             |
| `subApplication`                                                  | `*string`                                                         | :heavy_minus_sign:                                                | The sub-application ID to which event type is being subscribed to |
| `opts`                                                            | [][operations.Option](../../models/operations/option.md)          | :heavy_minus_sign:                                                | The options for this request.                                     |

### Response

**[*operations.DeleteWebhookResponse](../../models/operations/deletewebhookresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 404                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |

## WebhookSecretReset

Reset webhook secret for a webhook that is already registered to your application

### Example Usage

<!-- UsageSnippet language="go" operationID="webhookSecretReset" method="post" path="/webhook/secrets/{webhook_id}" -->
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

    res, err := s.Webhooks.WebhookSecretReset(ctx, "a8054faf-cea9-4de0-aa1b-a6b1ff1cd2cc", nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.WebhookDetailsWithSecret != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                             | Type                                                                                                  | Required                                                                                              | Description                                                                                           |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                 | [context.Context](https://pkg.go.dev/context#Context)                                                 | :heavy_check_mark:                                                                                    | The context to use for the request.                                                                   |
| `webhookID`                                                                                           | `string`                                                                                              | :heavy_check_mark:                                                                                    | Registered webhook ID                                                                                 |
| `subApplication`                                                                                      | `*string`                                                                                             | :heavy_minus_sign:                                                                                    | The sub-application ID to which event type is being subscribed to                                     |
| `body`                                                                                                | [*operations.WebhookSecretResetRequestBody](../../models/operations/webhooksecretresetrequestbody.md) | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `opts`                                                                                                | [][operations.Option](../../models/operations/option.md)                                              | :heavy_minus_sign:                                                                                    | The options for this request.                                                                         |

### Response

**[*operations.WebhookSecretResetResponse](../../models/operations/webhooksecretresetresponse.md), error**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| apierrors.APIErrorResponseV2   | 400, 401, 404                  | application/json;charset=UTF-8 |
| apierrors.APIErrorResponseV2   | 500                            | application/json;charset=UTF-8 |
| apierrors.APIError             | 4XX, 5XX                       | \*/\*                          |