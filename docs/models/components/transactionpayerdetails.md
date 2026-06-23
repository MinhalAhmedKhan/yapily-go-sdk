# TransactionPayerDetails

Details of the benefactor [person or business].


## Fields

| Field                                                                                                          | Type                                                                                                           | Required                                                                                                       | Description                                                                                                    |
| -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `Name`                                                                                                         | `*string`                                                                                                      | :heavy_minus_sign:                                                                                             | The account holder name of the Payer.                                                                          |
| `AccountIdentifications`                                                                                       | [][components.PayerDetailsAccountIdentification](../../models/components/payerdetailsaccountidentification.md) | :heavy_minus_sign:                                                                                             | The account identifications that identify the Payer's bank account.                                            |