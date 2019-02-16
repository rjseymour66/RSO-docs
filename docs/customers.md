## The Customer object

Store a representation of your customer data in a customer object. Contains your name, email, shipping address, and billing information. Customers and merchants can retrieve customer information.

### Customer object example

```json
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

| Attributes | | Description | Type |
| :----------|-| :-----------| :----| 
| _id         | | Unique system-generated identifier for the record object. | String |
| username | | Username used at Record Stack Overflow login.  | String |
| firstName | | Customer first name used for billing purposes | String |
| lastName | | Customer last name used for billing purposes | String |
| email | | Email address for customer questions regarding inventory, order fulfillment, returns, etc. | String |
| shipping_info | | | |
| | shipping_address1 | Street address that you want merchants to ship record products to | String |
| | shipping_address2 | Street address that you want merchants to ship record products to | String |
| | shipping_city | City that you want merchants to ship record products to | String |
| | shipping_state | State that you want merchants to ship record products to | String |
| | shipping_zip | Zip code you want merchants to ship record products to | String |
| billing_info | | | |
| |paypal_email | PayPal email address used to pay for orders | String |
| | billing_address1 | Address associated with PayPal account, if different from shipping address | String |
| | billing_address2 | Address associated with PayPal account, if different from shipping address | String |
| | billing_city | City associated with PayPal account, if different from shipping address | String |
| | billing_state | State associated with PayPal account, if different from shipping address | String |
| | billing_zip | Zip code associated with PayPal account, if different from shipping address | String |

****

## Retrieve customer information

Gets the information for a specific customer ID. Customers information is only returned if the you information associated with the provided access token.

`GET /api/v1/customer/{customerId}`

###Parameters

**Path parameters**

| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| {customerId}   | Required       | Refers to the `_id` of the customer you want to retrieve information for | String |


### Sample request

```
curl -X GET http://www.recordstackoverflow.com/api/v1/customers/{customerID} -H 'Authorization: Bearer <access-token>'
```

###Sample response
Returns a customer object 

```json
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
    "hashPassword": "$2b$10$Yi6NImE0YGSRYPw2h/XlT.MV0yCRGkWD4pARnnu70qMe0jIDccnhq",
    "__v": 0
}
```

### Sample error response

```json
{
  "error_message" : "Customer not found. Check customer ID",
  "status_code": 404 
}
```
****

## Update customer by ID

Retrieves the customer account by the specified ID and updates the object with the information provided in the body parameters.

`PUT /api/v1/customers/{customerId}`

###Parameters

**Path parameters**

| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| {customerId}   | Required       | Refers to the `_id` of the customer object you want to update | String |


**Body parameters**

| Parameter |  | Required    | Description | Type |
| :---------|--| :-----------| :-----------| :----|
| username |  | Optional | Username used at Record Stack Overflow login.  | String |
| firstName |  |Optional | Customer first name used for billing purposes | String |
| lastName |  |Optional | Customer last name used for billing purposes | String |
| email |  |Optional | Email address for customer questions regarding inventory, order fulfillment, returns, etc. | String |
| shipping_info | | | |
| | shipping_address1 |Optional | Street address that you want merchants to ship record products to | String |
| | shipping_address2 | Optional |Street address that you want merchants to ship record products to | String |
| | shipping_city | Optional |City that you want merchants to ship record products to | String |
| | shipping_state | Optional |State that you want merchants to ship record products to | String |
| | shipping_zip | Optional |Zip code you want merchants to ship record products to | String |
| billing_info | | | |
| |paypal_email | Optional |PayPal email address used to pay for orders | String |
| | billing_address1 | Optional |Address associated with PayPal account, if different from shipping address | String |
| | billing_address2 | Optional |Address associated with PayPal account, if different from shipping address | String |
| | billing_city | Optional |City associated with PayPal account, if different from shipping address | String |
| | billing_state | Optional |State associated with PayPal account, if different from shipping address | String |
| | billing_zip | Optional | Zip code associated with PayPal account, if different from shipping address | String |

###Sample request

```
curl -X PUT http://www.recordstackoverflow.com/api/v1/customers/{customerID} -H 'Authorization: Bearer <access-token>' -H 'Content-Type: application/json' -d username=NewUserName
```

###Sample response
Returns an updated customer object

```json
{
    "_id": "<customerID>",
    "username": "newUserName",
    "firstName": "First",
    "lastName": "Name",
    "email": "email@example.com",
    "shipping_info": [
        {
            "shipping_address1": "123 Customer Drive",
            "shipping_address2": "",
            "shipping_city": "Raleigh",
            "shipping_state": "NC",
            "shipping_zip": "27615"
        }
    ],
    "billing_info": [
        {
            "paypal_email": " paypal@example.com",
            "billing_address1": " 123 Second Home Drive",
            "billing_address2": "",
            "billing_city": " Raleigh",
            "billing_state": " NC",
            "billing_zip": " 27615"
        }
    ],
    "created_date": "2019-02-06T02:56:26.213Z",
    "__v": 0
}
```

### Sample error response

```json
{
  "error_message" : "Customer not found. Check customer ID",
  "status_code": 404 
}
```

































