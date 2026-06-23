# GetBulkPaymentStatusRequest


## Fields

| Field                                                                                       | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `Consent`                                                                                   | `string`                                                                                    | :heavy_check_mark:                                                                          | __Mandatory__. The `consent token` containing the user's authorisation to make the request. |
| `BulkPaymentID`                                                                             | `string`                                                                                    | :heavy_check_mark:                                                                          | __Mandatory__. Bulk payment id returned when bulk payment request was submitted.            |