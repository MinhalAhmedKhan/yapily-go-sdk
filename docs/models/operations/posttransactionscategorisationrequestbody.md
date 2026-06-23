# PostTransactionsCategorisationRequestBody


## Fields

| Field                                                                         | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `CountryCode`                                                                 | `string`                                                                      | :heavy_check_mark:                                                            | __Mandatory__. Two-letter country code in ISO 3166-1 alpha-2 format (e.g. GB) |
| `CategorisationType`                                                          | `string`                                                                      | :heavy_check_mark:                                                            | __Mandatory__. Allowed values are `consumer` and `business`.                  |
| `Transactions`                                                                | [][operations.Transaction](../../models/operations/transaction.md)            | :heavy_check_mark:                                                            | N/A                                                                           |