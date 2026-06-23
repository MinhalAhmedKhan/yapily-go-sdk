# Notification

Subscription details for how and where to receive notifications.


## Fields

| Field                                                                       | Type                                                                        | Required                                                                    | Description                                                                 | Example                                                                     |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `Type`                                                                      | `string`                                                                    | :heavy_check_mark:                                                          | How the notification will be delivered. This is currently only via WEBHOOK. | WEBHOOK                                                                     |
| `URL`                                                                       | `string`                                                                    | :heavy_check_mark:                                                          | URL to which the notification will be sent.                                 | https://httpbin.com/new_endpoint                                            |