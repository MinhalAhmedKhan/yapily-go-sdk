# AccountInfo

__Conditional__. Used to create a request for the balance of the account specified. Once the user authorises the request, only the balance can be obtained by executing [GET Account Balances](./#get-account-balances).

 This can be specified in conjunction with `accountIdentifiersForTransaction` to generate a `Consent` that can both access the accounts balance and transactions.


## Fields

| Field                                                                                | Type                                                                                 | Required                                                                             | Description                                                                          | Example                                                                              |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `AccountID`                                                                          | `*string`                                                                            | :heavy_minus_sign:                                                                   | __Conditional__. Unique identifier of the account.                                   | 500000000000000000000001                                                             |
| `AccountIdentification`                                                              | [components.AccountIdentification](../../models/components/accountidentification.md) | :heavy_check_mark:                                                                   | N/A                                                                                  |                                                                                      |