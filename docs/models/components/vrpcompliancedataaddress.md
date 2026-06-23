# VrpComplianceDataAddress

This is the registered company or trading address of your end user.


## Fields

| Field                                        | Type                                         | Required                                     | Description                                  | Example                                      |
| -------------------------------------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| `AddressLine1`                               | `string`                                     | :heavy_check_mark:                           | __Mandatory__. AddressLine1 of the business. | 123 Queens Street                            |
| `AddressLine2`                               | `*string`                                    | :heavy_minus_sign:                           | __Optional__. AddressLine2 of the business.  | Unit 13                                      |
| `TownName`                                   | `string`                                     | :heavy_check_mark:                           | __Mandatory__. Town name of the business.    | York                                         |
| `PostCode`                                   | `string`                                     | :heavy_check_mark:                           | __Mandatory__. Post code of the business.    | 12345                                        |
| `Country`                                    | `string`                                     | :heavy_check_mark:                           | __Mandatory__. Country of the business.      | GB                                           |