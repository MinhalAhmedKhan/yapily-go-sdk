# VrpFundsAvailable


## Fields

| Field                                                               | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `FundsAvailable`                                                    | `bool`                                                              | :heavy_check_mark:                                                  | __Mandatory__. The flag indicating whether the funds are available. |
| `FundsAvailableAt`                                                  | [time.Time](https://pkg.go.dev/time#Time)                           | :heavy_check_mark:                                                  | __Mandatory__. The datetime when the funds were checked.            |