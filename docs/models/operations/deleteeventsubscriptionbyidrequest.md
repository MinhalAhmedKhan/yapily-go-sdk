# DeleteEventSubscriptionByIDRequest


## Fields

| Field                                                                        | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `EventTypeID`                                                                | `string`                                                                     | :heavy_check_mark:                                                           | Unique identifier of the event type (for which notifications will be sent).  |
| `SubApplication`                                                             | `*string`                                                                    | :heavy_minus_sign:                                                           | The sub-application ID for which event type will be deleted                  |