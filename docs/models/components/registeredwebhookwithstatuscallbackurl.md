# RegisteredWebhookWithStatusCallbackURL

Callback URLs where events will be sent


## Fields

| Field                                                                                                         | Type                                                                                                          | Required                                                                                                      | Description                                                                                                   |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `Main`                                                                                                        | [*components.RegisteredWebhookWithStatusMain](../../models/components/registeredwebhookwithstatusmain.md)     | :heavy_minus_sign:                                                                                            | Primary URL where events will be sent                                                                         |
| `Backup`                                                                                                      | [*components.RegisteredWebhookWithStatusBackup](../../models/components/registeredwebhookwithstatusbackup.md) | :heavy_minus_sign:                                                                                            | Secondary URL where events will be sent whenever the primary URL is not responding                            |