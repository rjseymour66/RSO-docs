Record Stack Overflow uses secure JSON Web Tokens (JWT) to authenticate server requests. You cannot complete a successful request to the Record Stack Overflow API without a JWT access token included in the request header.

You must [create a customer account](customer-account.md) or [create a merchant account](merchant-account.md) to receive a JWT. Each request must include an `Authorization` header and the access token using the following format:  

`-H 'Authorization: Bearer <access-token>'`

!!! important
    Enter exactly 1 space between `Bearer` and `<access-token>` or your request will fail.

    
Record Stack Overflow's JWTs do not expire, and there is no tiered access. See [Rate Limiting](../rate-limiting.md) for additional information.

After you register your customer or merchant account, a customer or merchant object is returned containing a unique  unique system-generated `_id`.

```json hl_lines="2"
{
    "_id": "<customerID>",
    "username": "customerName",
    "firstName": "First",
    "lastName": "Name",
    "email": "email@example.com",
    "shipping_info": [
        {
            "shipping_address1": "123 Shipping Lane",
            "shipping_address2": "Ste. #100",
            "shipping_city": "Raleigh",
            "shipping_state": "NC",
            "shipping_zip": "27615"
        }
    ],
    "billing_info": [
        {
            "paypal_email": "paypal@example.com",
            "billing_address1": "123 Billing Drive",
            "billing_city": "Boston",
            "billing_state": "MA",
            "billing_zip": "02101"
        }
    ],
    "created_date": "2019-02-11T23:25:09.979Z",
    "__v": 0
}
```
Use `_id` to access your account and update information when necessary. You cannot change your access token or your system-generated `_id`.

!!! important
    Save your JWT access token and `_id` in a secure location for use during configuration.