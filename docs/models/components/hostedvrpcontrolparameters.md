# HostedVrpControlParameters

__Mandatory__. The parameters for the VRP mandate.


## Fields

| Field                                                                    | Type                                                                     | Required                                                                 | Description                                                              |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| `MaxAmountPerPayment`                                                    | [components.Amount](../../models/components/amount.md)                   | :heavy_check_mark:                                                       | __Mandatory__. The maximum amount that will be allowed per VRP payment.  |
| `PeriodicLimit`                                                          | [components.PeriodicLimit](../../models/components/periodiclimit.md)     | :heavy_check_mark:                                                       | N/A                                                                      |
| `ValidFrom`                                                              | [*time.Time](https://pkg.go.dev/time#Time)                               | :heavy_minus_sign:                                                       | __Optional__. The start date when the consent becomes valid.             |
| `ValidTo`                                                                | [*time.Time](https://pkg.go.dev/time#Time)                               | :heavy_minus_sign:                                                       | __Optional__. The end date when the consent expires and becomes invalid. |