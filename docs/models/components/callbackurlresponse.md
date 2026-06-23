# CallbackURLResponse

Callback URLs where events will be sent


## Fields

| Field                                                                              | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `Main`                                                                             | [*components.MainResponse](../../models/components/mainresponse.md)                | :heavy_minus_sign:                                                                 | Primary URL where events will be sent                                              |
| `Backup`                                                                           | [*components.BackupResponse](../../models/components/backupresponse.md)            | :heavy_minus_sign:                                                                 | Secondary URL where events will be sent whenever the primary URL is not responding |