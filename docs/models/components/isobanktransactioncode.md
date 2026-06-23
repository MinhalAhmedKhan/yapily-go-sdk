# IsoBankTransactionCode

Defines the underlying transaction type (e.g. Card or Debit Transactions, Loans or Mortages). 

 Conforms to `ISO` standards - ISO 20022.


## Fields

| Field                                                                   | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `DomainCode`                                                            | [*components.IsoCodeDetails](../../models/components/isocodedetails.md) | :heavy_minus_sign:                                                      | __Mandatory__. Details the identification of the ISO code.              |
| `FamilyCode`                                                            | [*components.IsoCodeDetails](../../models/components/isocodedetails.md) | :heavy_minus_sign:                                                      | __Mandatory__. Details the identification of the ISO code.              |
| `SubFamilyCode`                                                         | [*components.IsoCodeDetails](../../models/components/isocodedetails.md) | :heavy_minus_sign:                                                      | __Mandatory__. Details the identification of the ISO code.              |