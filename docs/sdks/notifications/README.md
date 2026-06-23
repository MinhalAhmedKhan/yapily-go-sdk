# Notifications

## Overview

The Notifications endpoints provide an interactive way for user to receive notifications according to different event-types. This feature is currently in private beta. Please reach out if you require access. 



### Available Operations

* [CreateEventSubscription](#createeventsubscription) - Create Event Subscription
* [GetEventSubscriptions](#geteventsubscriptions) - Get Event Subscriptions
* [GetEventSubscriptionByID](#geteventsubscriptionbyid) - Get Event Subscription
* [DeleteEventSubscriptionByID](#deleteeventsubscriptionbyid) - Delete Event Subscription

## CreateEventSubscription

Used to subscribe to notifications relating to a specified event type.

### Example Usage

<!-- UsageSnippet language="go" operationID="createEventSubscription" method="post" path="/notifications/event-subscriptions" -->
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

    res, err := s.Notifications.CreateEventSubscription(ctx, components.EventSubscriptionRequest{
        EventTypeID: "payment.status.completed",
        Notification: components.Notification{
            Type: "WEBHOOK",
            URL: "https://httpbin.com/new_endpoint",
        },
    }, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfEventSubscriptionResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                  | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `ctx`                                                                                      | [context.Context](https://pkg.go.dev/context#Context)                                      | :heavy_check_mark:                                                                         | The context to use for the request.                                                        |
| `body`                                                                                     | [components.EventSubscriptionRequest](../../models/components/eventsubscriptionrequest.md) | :heavy_check_mark:                                                                         | N/A                                                                                        |
| `subApplication`                                                                           | `*string`                                                                                  | :heavy_minus_sign:                                                                         | The sub-application ID to which event type is being subscribed to                          |
| `opts`                                                                                     | [][operations.Option](../../models/operations/option.md)                                   | :heavy_minus_sign:                                                                         | The options for this request.                                                              |

### Response

**[*operations.CreateEventSubscriptionResponse](../../models/operations/createeventsubscriptionresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetEventSubscriptions

Get all event subscriptions that your application is subscribed to

### Example Usage

<!-- UsageSnippet language="go" operationID="getEventSubscriptions" method="get" path="/notifications/event-subscriptions" -->
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

    res, err := s.Notifications.GetEventSubscriptions(ctx, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIListResponseOfEventSubscriptionResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `ctx`                                                                     | [context.Context](https://pkg.go.dev/context#Context)                     | :heavy_check_mark:                                                        | The context to use for the request.                                       |
| `subApplication`                                                          | `*string`                                                                 | :heavy_minus_sign:                                                        | The sub-application ID for which all event subscriptions will be returned |
| `opts`                                                                    | [][operations.Option](../../models/operations/option.md)                  | :heavy_minus_sign:                                                        | The options for this request.                                             |

### Response

**[*operations.GetEventSubscriptionsResponse](../../models/operations/geteventsubscriptionsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## GetEventSubscriptionByID

Used to get details of your subscription to a specified event type.

### Example Usage

<!-- UsageSnippet language="go" operationID="getEventSubscriptionById" method="get" path="/notifications/event-subscriptions/{eventTypeId}" -->
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

    res, err := s.Notifications.GetEventSubscriptionByID(ctx, "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfEventSubscriptionResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                    | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `ctx`                                                                        | [context.Context](https://pkg.go.dev/context#Context)                        | :heavy_check_mark:                                                           | The context to use for the request.                                          |
| `eventTypeID`                                                                | `string`                                                                     | :heavy_check_mark:                                                           | Unique identifier of the event type (for which notifications will be sent).  |
| `subApplication`                                                             | `*string`                                                                    | :heavy_minus_sign:                                                           | The sub-application ID to which event type is being subscribed to            |
| `opts`                                                                       | [][operations.Option](../../models/operations/option.md)                     | :heavy_minus_sign:                                                           | The options for this request.                                                |

### Response

**[*operations.GetEventSubscriptionByIDResponse](../../models/operations/geteventsubscriptionbyidresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |

## DeleteEventSubscriptionByID

Used to unsubscribe to notifications relating to a specified event type.

### Example Usage

<!-- UsageSnippet language="go" operationID="deleteEventSubscriptionById" method="delete" path="/notifications/event-subscriptions/{eventTypeId}" -->
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

    res, err := s.Notifications.DeleteEventSubscriptionByID(ctx, "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.APIResponseOfEventSubscriptionDeleteResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                    | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `ctx`                                                                        | [context.Context](https://pkg.go.dev/context#Context)                        | :heavy_check_mark:                                                           | The context to use for the request.                                          |
| `eventTypeID`                                                                | `string`                                                                     | :heavy_check_mark:                                                           | Unique identifier of the event type (for which notifications will be sent).  |
| `subApplication`                                                             | `*string`                                                                    | :heavy_minus_sign:                                                           | The sub-application ID for which event type will be deleted                  |
| `opts`                                                                       | [][operations.Option](../../models/operations/option.md)                     | :heavy_minus_sign:                                                           | The options for this request.                                                |

### Response

**[*operations.DeleteEventSubscriptionByIDResponse](../../models/operations/deleteeventsubscriptionbyidresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.APIError | 4XX, 5XX           | \*/\*              |