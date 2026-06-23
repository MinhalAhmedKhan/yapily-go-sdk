# RequestBody

Patch details to be applied to user.


## Fields

| Field                                                                  | Type                                                                   | Required                                                               | Description                                                            |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `Op`                                                                   | [components.PatchOperation](../../models/components/patchoperation.md) | :heavy_check_mark:                                                     | The operation to be performed                                          |
| `Path`                                                                 | `string`                                                               | :heavy_check_mark:                                                     | The path to the target location                                        |
| `Value`                                                                | `string`                                                               | :heavy_check_mark:                                                     | The value to be added, replaced or tested                              |