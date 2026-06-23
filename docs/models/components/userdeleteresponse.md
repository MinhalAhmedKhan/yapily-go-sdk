# UserDeleteResponse

Deletion of the user. Includes the user profile and all associate consents.


## Fields

| Field                                                                                  | Type                                                                                   | Required                                                                               | Description                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `ID`                                                                                   | `*string`                                                                              | :heavy_minus_sign:                                                                     | Unique identifier of the user.                                                         |
| `DeleteStatus`                                                                         | [*components.DeleteStatusEnum](../../models/components/deletestatusenum.md)            | :heavy_minus_sign:                                                                     | Indicates the outcome of the delete request.                                           |
| `CreationDate`                                                                         | [*time.Time](https://pkg.go.dev/time#Time)                                             | :heavy_minus_sign:                                                                     | Date and time that the user was created.                                               |
| `UserConsents`                                                                         | [][components.ConsentDeleteResponse](../../models/components/consentdeleteresponse.md) | :heavy_minus_sign:                                                                     | N/A                                                                                    |