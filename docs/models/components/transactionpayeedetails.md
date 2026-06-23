# TransactionPayeeDetails

Details of the beneficiary [person or business].


## Fields

| Field                                                                                                          | Type                                                                                                           | Required                                                                                                       | Description                                                                                                    |
| -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `Name`                                                                                                         | `*string`                                                                                                      | :heavy_minus_sign:                                                                                             | The account holder name of the Payee.                                                                          |
| `AccountIdentifications`                                                                                       | [][components.PayeeDetailsAccountIdentification](../../models/components/payeedetailsaccountidentification.md) | :heavy_minus_sign:                                                                                             | The account identifications that identify the Payee's bank account.                                            |