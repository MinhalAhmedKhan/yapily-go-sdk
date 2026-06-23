# APIErrorResponse

Used to return errors from the bank from each request

- `400` - Returned by any `POST` endpoint when the body does not conform to the contract
- `401` - Returned by any endpoint when an invalid `authToken` is used for authentication
- `403` - Returned by any [Financial Data](/api-reference/...) and any [Payments](/api-reference/...) endpoint when the `Consent` is no longer authorised to access financial data or to make a payment
- `404` - Returned by any endpoint where there are path parameters and the path parameters supplied are unable to find the desired resource
- `409` - Returned by any `POST` endpoint when creating a resource that conflicts with any other existing resource e.g. [Create User](/api-reference/...)
- `424` - Returned by any [Financial Data](/api-reference/...) and any [Payments](/api-reference/...) endpoint when the feature to be accessed is not supported by the `Institution`.
- `500` - Returned by any endpoint when Yapily is down. If you encounter any false positives, please [notify us](mailto:support@yapily.com)


## Fields

| Field                                                               | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `Error`                                                             | [*components.ErrorDetails](../../models/components/errordetails.md) | :heavy_minus_sign:                                                  | N/A                                                                 |