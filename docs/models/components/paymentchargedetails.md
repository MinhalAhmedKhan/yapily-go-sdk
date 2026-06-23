# PaymentChargeDetails

Details the charges that will apply to the payment.


## Fields

| Field                                                                                    | Type                                                                                     | Required                                                                                 | Description                                                                              |
| ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| `ChargeAmount`                                                                           | [*components.Amount](../../models/components/amount.md)                                  | :heavy_minus_sign:                                                                       | __Mandatory__. Monetary Amount.                                                          |
| `ChargeType`                                                                             | `*string`                                                                                | :heavy_minus_sign:                                                                       | __Mandatory__. Specifies the nature of the transaction charge e.g. (Bank transfer fees). |
| `ChargeTo`                                                                               | `*string`                                                                                | :heavy_minus_sign:                                                                       | __Mandatory__. States which party of the payment bears the charges.                      |