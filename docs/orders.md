## The Order object

The order object is a representation of an order created from a record object. Contains information about the order status, original record object, customer, customer shipping information, customer billing information, merchant information, and any additional comments. Orders can be created, retrieved, updated, and cancelled. Request orders by customer ID or by merchant ID.


### Base path  

www.recordstackoverflow.com/api/v1/

### Orders endpoints  

- PUT `/orders/merchants/{merchantId}/records/{recordId}/`
- GET `/orders/customers/{customerId}/`
- GET `/orders/merchants/{merchantId}/`
- PUT `/orders/{orderId}/`
- DELETE `/orders/{orderId}/customers/{customerId}/`

### Sample orders object

```json
{
    "status": "In progress",
    "_id": "<orderID>",
    "record_id": "<recordID>",
    "merchant_id": "<merchantID>",
    "customer_info": [
        {
            "username": "customerName",
            "email": "email@example.com",
            "firstName": "First",
            "lastName": "Name"
        }
    ],
    "shipping_info": [
        {
            "shipping_address1": "123 Shipping Lane",
            "shipping_address2": "",
            "shipping_city": "Raleigh",
            "shipping_state": "NC",
            "shipping_zip": "27615"
        }
    ],
    "billing_info": [
        {
            "paypal_email": "paypal@example.com",
            "billing_address1": "123 Billing Drive",
            "billing_address2": "Ste. #100",
            "billing_city": "Raleigh",
            "billing_state": "NC",
            "billing_zip": "27615"
        }
    ],
    "comments": [
        "This is a comment"
    ],
    "_createdBy": "<customerID>",
    "created_date": "2019-02-12T02:16:49.482Z",
    "__v": 0
}
```

| Attributes |      | Description | Type |
| :----------| :----| :-----------| :----|
| status  | | Describes the stage in order fulfillment. Possible values are "In progress", "Completed", or "Cancelled". | String |
| _id | | The unique system-generated order ID | String |
| product_info | | | |
| | record_id | The ID of the record object that was turned into an order. | String |
| | merchant_id | The merchant ID of the merchant account that created the record object. | String |
| customer_info | | | |
| | username | The registered username of the customer account that created the order. | String |
| | email | The registered email address of the customer account that created the order. | String |
| | firstName | The registered firstName of the customer account that created the order. | String |
| | lastName | The registered lastName of the customer account that created the order. | String |
| shipping_info | | | |
| | shipping_address1 | The street address to ship the order to. | String |
| | shipping_address2 | The street address to ship the order to. | String |
| | shipping_city | The city to ship the order to. | String |
| | shipping_state | The state to ship the order to. | String |
| | shipping_zip | The zip code to ship the order to. | String |
| billing_info | | | |
| |paypal_email | The PayPal email address used to pay for orders. | String |
| | billing_address1 | The address associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_address2 | The address associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_city | The city associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_state | The state associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_zip | The zip code associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| comments | | Additional notes about the order. | Array of Strings |
| _createdBy | | The ID of the customer that created the record object. | 
| created_date | | The date order object was created. The date is system-generated in GMT format YYYY-MM-DDThh:mmTZD | Date |  

***  

## Create an order
**(Customer accounts only)**

Creates a new order object.

PUT `/orders/merchants/{merchantId}/records/{recordId}/`


### Parameters

**Path parameter**

| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| {recordId}    | Required       | Refers to the record ID of the record object that you want to create an order for. | String |

**Body parameters**

| Parameter      |                    |   Required       | Description    | Type |
| :------------- |--------------------|:-----------------| :--------------| :----|
| shipping_info | | | |
| | shipping_address1 | Required | The street address to ship the order to. | String |
| | shipping_address2 | Optional | The street address to ship the order to. | String |
| | shipping_city | Required | The city to ship the order to. | String |
| | shipping_state | Required | The state to ship the order to. | String |
| | shipping_zip | Required | The zip code to ship the order to. | String |
| billing_info | | | |
| |paypal_email | Required | The PayPal email address used to pay for orders. | String |
| | billing_address1 | Optional | The address associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_address2 | Optional | The address associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_city | Optional | The city associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_state | Optional | The state associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_zip | Optional | The zip code associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| comments | | Optional | Additional notes about the order | Array of Strings |
| _createdBy | | System-generated | The unique ID of the customer that created the record object | 
| created_date | | System-generated | The date the order object was created. The date is system-generated in GMT format YYYY-MM-DDThh:mmTZD | Date |  

### Sample request

```
curl -X POST \
  http://www.recordstackoverflow.com/api/v1/orders/merchants/5c679751bb102c001706bf0a/records/5c679811bb102c001706bf0b \
  -H 'Authorization: Bearer <access-token>' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'shipping_address1=123%20Shipping%20Lane&shipping_address2=&shipping_city=Raleigh&shipping_state=NC&shipping_zip=27615&paypal_email=paypal%40example.com&billing_address1=123%20Billing%20Drive&billing_address2=Ste.%20%23100&billing_city=Raleigh&billing_state=NC&billing_zip=27615&comments=This%20is%20a%20comment'
```


### Sample response

Returns an order object if request was successful.

```json
{
    "status": "In progress",
    "_id": "<orderID>",
    "record_id": "<recordID>",
    "merchant_id": "<merchantID>",
    "customer_info": [
        {
            "username": "customerName",
            "email": "email@example.com",
            "firstName": "First",
            "lastName": "Name"
        }
    ],
    "shipping_info": [
        {
            "shipping_address1": "123 Shipping Lane",
            "shipping_address2": "",
            "shipping_city": "Raleigh",
            "shipping_state": "NC",
            "shipping_zip": "27615"
        }
    ],
    "billing_info": [
        {
            "paypal_email": "paypal@example.com",
            "billing_address1": "123 Billing Drive",
            "billing_address2": "Ste. #100",
            "billing_city": "Raleigh",
            "billing_state": "NC",
            "billing_zip": "27615"
        }
    ],
    "comments": [
        "This is a comment"
    ],
    "_createdBy": "<customerID>",
    "created_date": "2019-02-12T02:16:49.482Z",
    "__v": 0
}
```
****


## Retrieve all orders for a customer

Retrieves all order information for a specific customer ID. Customers can only request order information associated with their customer ID.

GET `/orders/customers/{customerId}/`

###Parameters

**Path parameters**

| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| {customerId}   | Required       | Refers to the customer ID that you want to retrieve all orders for. | String |

**Query string parameters**


| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| limit | Optional | The number of record objects to return. Default is all. | Integer |
| sort | Optional | The order results are returned in. Use "asc" or "1" to sort alphabetically by artist name. Use "desc" or "-1" to sort reverse-alphabetically by artist name. | String |
| offset | Optional | The index to start with. The default is 0. | Integer |

###Sample request

```
curl -X GET \
  http://www.recordstackoverflow.com/api/v1/orders/customers/5c6777d1d6a7470017de33c3 \
  -H 'Authorization: Bearer <access-token>' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'shipping_address1=123%20Shipping%20Lane&shipping_address2=&shipping_city=Raleigh&shipping_state=NC&shipping_zip=27615&paypal_email=paypal%40example.com&billing_address1=123%20Billing%20Drive&billing_address2=Ste.%20%23100&billing_city=Raleigh&billing_state=NC&billing_zip=27615&comments=This%20is%20a%20comment'
```

###Sample response
Returns a list of order objects.

```json
[
    {
        "status": "In progress",
        "_id": "<orderID>",
        "record_id": "<recordID>",
        "merchant_id": "<merchantID>",
        "customer_info": [
            {
                "username": "customerName",
                "email": "email@example.com",
                "firstName": "First",
                "lastName": "Name"
            }
        ],
        "shipping_info": [
            {
                "shipping_address1": "123 Shipping Lane",
                "shipping_address2": "",
                "shipping_city": "Raleigh",
                "shipping_state": "NC",
                "shipping_zip": "27615"
            }
        ],
        "billing_info": [
            {
                "paypal_email": "paypal@example.com",
                "billing_address1": "123 Billing Drive",
                "billing_address2": "Ste. #100",
                "billing_city": "Raleigh",
                "billing_state": "NC",
                "billing_zip": "27615"
            }
        ],
        "comments": [
            "This is a comment"
        ],
        "_createdBy": "<customerID>",
        "created_date": "2019-02-17T00:06:32.391Z",
        "__v": 0
    },
    {
        "status": "In progress",
        "_id": "<orderID>",
        "record_id": "<recordID>",
        "merchant_id": "<merchantID>",
        "customer_info": [
            {
                "username": "customerName",
                "email": "email@example.com",
                "firstName": "First",
                "lastName": "Name"
            }
        ],
        "shipping_info": [
            {
                "shipping_address1": "123 Shipping Lane",
                "shipping_address2": "",
                "shipping_city": "Raleigh",
                "shipping_state": "NC",
                "shipping_zip": "27615"
            }
        ],
        "billing_info": [
            {
                "paypal_email": "paypal@example.com",
                "billing_address1": "123 Billing Drive",
                "billing_address2": "Ste. #100",
                "billing_city": "Raleigh",
                "billing_state": "NC",
                "billing_zip": "27615"
            }
        ],
        "comments": [
            "This is a comment"
        ],
        "_createdBy": "<customerID>",
        "created_date": "2019-02-17T00:08:36.722Z",
        "__v": 0
    }
]
```

****

## Retrieve all orders for a merchant

Retrieves all customer orders using the specified customer id. Merchants can only request order information associated with their merchant ID.

GET `/orders/merchants/{merchantId}/`


###Parameters

**Path parameters**

| URL Parameter  | Description    |
| :------------- | :------------- |
| {merchantId}     | Refers to the merchant ID of the merchant that created the records you want to retrieve. |

**Query string parameters**


| Parameter | Required | Description | Type |
| :---------| :-----------| :----| :--------|
| limit | Optional | The number of record objects to return. Default is all. | Integer |
| sort | Optional | The order results are returned in. Use "asc" or "1" to sort alphabetically by artist name. Use "desc" or "-1" to sort reverse-alphabetically by artist name. | String |
| offset | Optional | The index to start with. The default is 0. | Integer |

###Sample request

```
curl -X GET \
  http://www.recordstackoverflow.com/api/v1/orders/merchants/5c679751bb102c001706bf0a \
  -H 'Authorization: Bearer <access-token>' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
```

###Sample response
Returns a list of order objects for the specified merchant.

```json
[
    {
        "status": "In progress",
        "_id": "<orderID>",
        "record_id": "<recordID>",
        "merchant_id": "<merchantID>",
        "customer_info": [
            {
                "username": "customerName",
                "email": "email@example.com",
                "firstName": "First",
                "lastName": "Name"
            }
        ],
        "shipping_info": [
            {
                "shipping_address1": "123 Shipping Lane",
                "shipping_address2": "",
                "shipping_city": "Raleigh",
                "shipping_state": "NC",
                "shipping_zip": "27615"
            }
        ],
        "billing_info": [
            {
                "paypal_email": "paypal@example.com",
                "billing_address1": "123 Billing Drive",
                "billing_address2": "Ste. #100",
                "billing_city": "Raleigh",
                "billing_state": "NC",
                "billing_zip": "27615"
            }
        ],
        "comments": [
            "This is a comment"
        ],
        "_createdBy": "<customerID>",
        "created_date": "2019-02-17T00:06:32.391Z",
        "__v": 0
    },
    {
        "status": "In progress",
        "_id": "<orderID>",
        "record_id": "<recordID>",
        "merchant_id": "<merchantID>",
        "customer_info": [
            {
                "username": "customerName",
                "email": "email@example.com",
                "firstName": "First",
                "lastName": "Name"
            }
        ],
        "shipping_info": [
            {
                "shipping_address1": "123 Shipping Lane",
                "shipping_address2": "",
                "shipping_city": "Raleigh",
                "shipping_state": "NC",
                "shipping_zip": "27615"
            }
        ],
        "billing_info": [
            {
                "paypal_email": "paypal@example.com",
                "billing_address1": "123 Billing Drive",
                "billing_address2": "Ste. #100",
                "billing_city": "Raleigh",
                "billing_state": "NC",
                "billing_zip": "27615"
            }
        ],
        "comments": [
            "This is a comment"
        ],
        "_createdBy": "<customerID>",
        "created_date": "2019-02-17T00:08:36.722Z",
        "__v": 0
    }
]
```

****

## Update an order by ID
**(Merchant accounts only)**

Retrieves an order by id and updates the orders object using the body parameters. Update only order objects that were created using your registered merchant ID.

PUT `/orders/{orderId}/`

### Parameters

**Path parameters**


| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| {orderId}     | Refers to the order ID that you want to retrieve. |

**Body parameters**

| Parameter      |                    |   Required       | Description    | Type |
| :------------- |--------------------|:-----------------| :--------------| :----|
| shipping_info | | | |
| | shipping_address1 | Optional | The street address to ship the order to. | String |
| | shipping_address2 | Optional | The street address to ship the order to. | String |
| | shipping_city | Optional | The city to ship the order to. | String |
| | shipping_state | Optional | The state to ship the order to. | String |
| | shipping_zip | Optional | The zip code to ship the order to. | String |
| billing_info | | | |
| |paypal_email | Optional | The PayPal email address used to pay for orders. | String |
| | billing_address1 | Optional | The address associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_address2 | Optional | The address associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_city | Optional | The city associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_state | Optional | The state associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |
| | billing_zip | Optional | The zip code associated with the PayPal account. Not required if the billing address is the same as the shipping address. | String |

### Sample request

```
curl -X PUT \
  http://www.recordstackoverflow.com/api/v1/orders/5c68a588fc924b00178bf143 \
  -H 'Authorization: Bearer <access-token>' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'billing_info%5B0%5D%5Bbilling_address1%5D=789%20New%20Billing%20Ave&billing_info%5B0%5D%5Bbilling_address2%5D=Ste.%20%23950&billing_info%5B0%5D%5Bbilling_city%5D=Boston&billing_info%5B0%5D%5Bbilling_state%5D=MA&billing_info%5B0%5D%5Bbilling_zip%5D=02101&comments=Updated%20billing%20address'
```

### Sample response

```json hl_lines="25 26 27 28 29 33"
{
    "status": "In progress",
    "_id": "<orderID>",
    "record_id": "<recordID>",
    "merchant_id": "<merchantID>",
    "customer_info": [
        {
            "username": "customerName",
            "email": "email@example.com",
            "firstName": "First",
            "lastName": "Name"
        }
    ],
    "shipping_info": [
        {
            "shipping_address1": "123 Shipping Lane",
            "shipping_address2": "",
            "shipping_city": "Raleigh",
            "shipping_state": "NC",
            "shipping_zip": "27615"
        }
    ],
    "billing_info": [
        {
            "billing_address1": "789 New Billing Ave",
            "billing_address2": "Ste. #950",
            "billing_city": "Boston",
            "billing_state": "MA",
            "billing_zip": "02101"
        }
    ],
    "comments": [
        "Updated billing address"
    ],
    "_createdBy": "5c6777d1d6a7470017de33c3",
    "created_date": "2019-02-17T00:06:32.391Z",
    "__v": 0
}
```
****

## Delete an order
**(Customer accounts only)**

Deletes an order by ID. Delete only order objects that were created using your registered customer ID.


!!! important
    Delete orders only when the order `status` is `In progress`.

DELETE `/orders/{orderId}/customers/{customerId}/`

### Parameters

**Path parameters**


| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| {orderId}     | Refers to the order ID that you want to delete. |

### Sample request

```
curl -X DELETE \
  http://www.recordstackoverflow.com/api/v1/orders/5c68a588fc924b00178bf143/customers/5c6777d1d6a7470017de33c3 \
  -H 'Authorization: Bearer <access-token>' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
```

### Sample response 

```json
{
  "success_message": "Order cancelled",
  "response_code": 200  
}
```