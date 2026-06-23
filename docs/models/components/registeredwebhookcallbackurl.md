# RegisteredWebhookCallbackURL

Callback URLs where events will be sent


## Fields

| Field                                                                                     | Type                                                                                      | Required                                                                                  | Description                                                                               |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `Main`                                                                                    | [*components.RegisteredWebhookMain](../../models/components/registeredwebhookmain.md)     | :heavy_minus_sign:                                                                        | Primary URL where events will be sent                                                     |
| `Backup`                                                                                  | [*components.RegisteredWebhookBackup](../../models/components/registeredwebhookbackup.md) | :heavy_minus_sign:                                                                        | Secondary URL where events will be sent whenever the primary URL is not responding        |