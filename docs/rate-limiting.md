# Rate limiting

Each authenticated user account can make a maximum of 100 server calls every 15 minutes. Authenticated requests are associated with the JSON web token (JWT) assigned to the account.

The Record Stack Overflow API provides API calls free-of-charge to registered users. There is no charge if you exceed the rate limit threshold.

If you exceed the rate limit, you receive the following 429 error response:

```json
{
  "error_message": "Too many request, please try again later",
  "response_code": 429
}
```