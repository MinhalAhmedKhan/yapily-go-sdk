# InstitutionIdentifiers

Specifies the institution requirements for making the payment. Skips the bank selection screen in payment flow if the `institutionId` and `institutionCountryCode` are provided.


## Fields

| Field                                                                                | Type                                                                                 | Required                                                                             | Description                                                                          | Example                                                                              |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `InstitutionID`                                                                      | `*string`                                                                            | :heavy_minus_sign:                                                                   | Yapily identifier which identifies the `Institution` the payment request is sent to. |                                                                                      |
| `InstitutionCountryCode`                                                             | `string`                                                                             | :heavy_check_mark:                                                                   | 2 letter ISO Country code of the `Institution` the payment request is sent to.       | GB                                                                                   |