# AccountStatement

Statement information belonging to the account.


## Fields

| Field                                              | Type                                               | Required                                           | Description                                        |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| `ID`                                               | `*string`                                          | :heavy_minus_sign:                                 | Unique identifier for the statement.               |
| `StartDateTime`                                    | [*time.Time](https://pkg.go.dev/time#Time)         | :heavy_minus_sign:                                 | Date and time of when the statement period starts. |
| `EndDateTime`                                      | [*time.Time](https://pkg.go.dev/time#Time)         | :heavy_minus_sign:                                 | Date and time of when the statement period ends.   |
| `CreationDateTime`                                 | [*time.Time](https://pkg.go.dev/time#Time)         | :heavy_minus_sign:                                 | Date and time of when the statement was created.   |