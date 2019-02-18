## The Customer object

Store a representation of your personal account information in a customer object. Contains your name, email, shipping address, and billing information. Customers and merchants can retrieve customer information.


### Base path  

www.recordstackoverflow.com/api/v1/

### Customers endpoints

- GET `/customers/{customerId}/`
- PUT `/customers/{customerId}/`

### Sample customer object

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
| username | | The username of the customer account.  | String |
| firstName | | The first name of the customer account. | String |
| lastName | | The last name of the customer account. | String |
| email | | The email address of the customer account. | String |
| shipping_info | | | |
| | shipping_address1 | The street address that you want your order shipped to. | String |
| | shipping_address2 | The street address that you want your order shipped to. | String |
| | shipping_city | The city that you want your order shipped to. | String |
| | shipping_state | The state that you want your order shipped to. | String |
| | shipping_zip | The zip code you your order shipped to. | String |
| billing_info | | | |
| |paypal_email | The PayPal email address used to pay for orders. | String |
| | billing_address1 | The address associated with the PayPal account, if different from shipping address. | String |
| | billing_address2 | The address associated with the PayPal account, if different from shipping address. | String |
| | billing_city | The city associated with the PayPal account, if different from the shipping address. | String |
| | billing_state | The state associated with the PayPal account, if different from the shipping address. | String |
| | billing_zip | The zip code associated with the PayPal account, if different from the shipping address. | String |

****

## Retrieve customer information

Retrieves the information for a specific customer ID. You can update only customer objects associated with the request's access token.

GET `/customer/{customerId}/`

###Parameters

**Path parameters**

| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| {customerId}   | Required       | Refers to the customer ID of the customer that you want to retrieve information for. | String |


### Sample request

```
curl -X GET http://www.recordstackoverflow.com/api/v1/customers/{customerID} -H 'Authorization: Bearer <access-token>'
```

###Sample response
Returns a customer object.

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


****

## Update customer by ID

Retrieves the customer account by the specified ID and updates the object with the information provided in the body parameters.

PUT `/customers/{customerId}/`

###Parameters

**Path parameters**

| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| {customerId}   | Required       | Refers to the customer ID of the customer that you want to retrieve information for. | String |


**Body parameters**

| Parameter |  | Required    | Description | Type |
| :---------|--| :-----------| :-----------| :----|
| username |  | Optional | Username used at Record Stack Overflow login.  | String |
| firstName |  |Optional | Customer first name used for billing purposes | String |
| lastName |  |Optional | Customer last name used for billing purposes | String |
| email |  |Optional | Email address for customer questions regarding inventory, order fulfillment, returns, etc. | String |
| shipping_info | | | |
| | shipping_address1 | Optional | The street address that you want your order shipped to. | String |
| | shipping_address2 | Optional | The street address that you want your order shipped to. | String |
| | shipping_city | Optional | The city that you want your order shipped to. | String |
| | shipping_state | Optional | The state that you want your order shipped to. | String |
| | shipping_zip | Optional | The zip code you your order shipped to. | String |
| billing_info | | | |
| |paypal_email | Optional | The PayPal email address used to pay for orders. | String |
| | billing_address1 | Optional | The address associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_address2 | Optional | The address associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_city | Optional | The city associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_state | Optional | The state associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_zip | Optional | The zip code associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |

###Sample request

```
curl -X PUT http://www.recordstackoverflow.com/api/v1/customers/{customerID} -H 'Authorization: Bearer <access-token>' -H 'Content-Type: application/json' -d username=NewUserName
```

###Sample response
Returns an updated customer object.

```json hl_lines="3"
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
