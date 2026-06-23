# CreditLine

__Mandatory__. Details whether the account has access to a credit line from an `Institution`.


## Fields

| Field                                                                   | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `Type`                                                                  | [*components.CreditLineType](../../models/components/creditlinetype.md) | :heavy_minus_sign:                                                      | __Mandatory__. The type of credit that has been provided.               |
| `CreditLineAmount`                                                      | [*components.Amount](../../models/components/amount.md)                 | :heavy_minus_sign:                                                      | __Mandatory__. Monetary Amount.                                         |