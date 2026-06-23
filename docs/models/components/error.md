# Error


## Fields

| Field                                                                 | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `TracingID`                                                           | `string`                                                              | :heavy_check_mark:                                                    | Unique identifier of the request, used by Yapily for support purposes |
| `Code`                                                                | `int`                                                                 | :heavy_check_mark:                                                    | Numeric HTTP status code associated with the error                    |
| `Status`                                                              | `string`                                                              | :heavy_check_mark:                                                    | Textual description of the HTTP status                                |
| `SupportURL`                                                          | `*string`                                                             | :heavy_minus_sign:                                                    | Link to where further information regarding the error can be found    |
| `Source`                                                              | `*string`                                                             | :heavy_minus_sign:                                                    | Source of the error. This may be YAPILY, the INSTITUTION, or the USER |
| `Issues`                                                              | [][components.Issue](../../models/components/issue.md)                | :heavy_check_mark:                                                    | List of issues relating to the error                                  |