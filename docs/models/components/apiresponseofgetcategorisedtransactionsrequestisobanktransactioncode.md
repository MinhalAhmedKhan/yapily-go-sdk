# APIResponseOfGetCategorisedTransactionsRequestIsoBankTransactionCode

__Conditional.__ The ISO 20022 codes specifying the type of the transaction (eg. domain of 'Payments', family of 'Issued Credit Transfers', and sub-family of 'Domestic Credit Transfer')

This may be present when using [Transactions and Categorisation endpoint](/api-reference/post-accounts-accountId-transactions-categorisation)


## Fields

| Field                                                                 | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `DomainCode`                                                          | [*components.DomainCode](../../models/components/domaincode.md)       | :heavy_minus_sign:                                                    | The domain of the transaction                                         |
| `FamilyCode`                                                          | [*components.FamilyCode](../../models/components/familycode.md)       | :heavy_minus_sign:                                                    | The family of the transaction                                         |
| `SubFamilyCode`                                                       | [*components.SubFamilyCode](../../models/components/subfamilycode.md) | :heavy_minus_sign:                                                    | The sub-family of the transaction                                     |