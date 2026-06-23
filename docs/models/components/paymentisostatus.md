# PaymentIsoStatus

The payment status code, as denoted by a 3-letter ISO 20022 code.


## Fields

| Field                                                                                       | Type                                                                                        | Required                                                                                    | Description                                                                                 | Example                                                                                     |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `Code`                                                                                      | [*components.PaymentIsoStatusCodeEnum](../../models/components/paymentisostatuscodeenum.md) | :heavy_minus_sign:                                                                          | The ISO 20022 `PaymentStatusCode`.                                                          | ACCC                                                                                        |
| `Name`                                                                                      | `*string`                                                                                   | :heavy_minus_sign:                                                                          | The full name of the ISO 20022 `PaymentStatusCode`.                                         | AcceptedCreditSettlementCompleted                                                           |