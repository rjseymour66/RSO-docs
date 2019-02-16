## The Order object

Orders objects are representations of the orders created from records objects. Contains information about the order status, original record object, customer, customer shipping information, customer billing information, merchant information, and any additional comments. Orders can be created, retrieved, updated, and cancelled. Request orders by customer ID or merchant ID.

**Orders endpoints**

**Orders object example**

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
| status  | | Describes where the order is in the delivery process. Possible values are "In progress", "Delivered", or "Cancelled". | String |
| _id | | System-generated unique order ID | String |
| product_info | | | |
| | record_id | Record ID for the record object that was turned into an order | String |
| customer_info | | | |
| | username | Registered username of the account that created the order | String |
| | email | Registered email address of the account that created the order | String |
| | firstName | Registered firstName of the account that created the order | String |
| | lastName | Registered lastName of the account that created the order | String |
| shipping_info | | | |
| | shipping_address1 | Registered shipping address of the account that created the order | String |
| | shipping_address2 | Registered shipping address of the account that created the order | String |
| | shipping_city | Registered shipping city of the account that created the order | String |
| | shipping_state | Registered shipping state of the account that created the order | String |
| | shipping_zip | Registered shipping zip code of the account that created the order | String |
| billing_info | | | |
| |paypal_email | Registered PayPal email address of the account that created the order | String |
| | billing_address1 | Registered billing address of the account that created the order | String |
| | billing_address2 | Registered billing address of the account that created the order | String |
| | billing_city | Registered billing city of the account that created the order | String |
| | billing_state | Registered billing state of the account that created the order | String |
| | billing_zip | Registered billing zip code of the account that created the order | String |
| merchant_info | | | |
| | merchant_id | Merchant ID of the merchant account that created the record object | String |
| | companyName | Registered company name of the account that created the record object | String |
| | primaryContact | Registered primary contact of the account that created the record object | String |
| | phoneNumber | Registered phone number of the account that created the record object | String |
| comments | | Additional notes about the order | Array of Strings |
| _createdBy | | System-generated ID of the customer that created the record object | 
| created_date | | Date order object was created. The date is system-generated in GMT format YYYY-MM-DDThh:mmTZD | Date |  

***  

## Create an order

Creates a new order object. Customer accounts only.

`POST api/v1/orders/records/{recordId}/`

### Parameters

**Path parameter**

| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| {recordId}    | Required       | Record ID of the record object you want to create an order for | String |

**Body parameters**

| Parameter      |                    |   Required       | Description    | Type |
| :------------- |--------------------|:-----------------| :--------------| :----|
| shipping_info | | | |
| | shipping_address1 | Required | Registered shipping address of the account that created the order | String |
| | shipping_address2 | Required | Registered shipping address of the account that created the order | String |
| | shipping_city | Required | Registered shipping city of the account that created the order | String |
| | shipping_state | Required | Registered shipping state of the account that created the order | String |
| | shipping_zip | Required | Registered shipping zip code of the account that created the order | String |
| billing_info | | | |
| |paypal_email | Required | Registered PayPal email address of the account that created the order | String |
| | billing_address1 | Required | Registered billing address of the account that created the order | String |
| | billing_address2 | Required | Registered billing address of the account that created the order | String |
| | billing_city | Required | Registered billing city of the account that created the order | String |
| | billing_state | Required | Registered billing state of the account that created the order | String |
| | billing_zip | Required | Registered billing zip code of the account that created the order | String |
| merchant_info | | | |
| | merchant_id | Required | Merchant ID of the merchant account that created the record object | String |
| | companyName | Required | Registered company name of the account that created the record object | String |
| | primaryContact | Required | Registered primary contact of the account that created the record object | String |
| | phoneNumber | Required | Registered phone number of the account that created the record object | String |
| comments | | Optional | Additional notes about the order | Array of Strings |
| _createdBy | | System-generated | ID of the customer that created the record object | 
| created_date | | System-generated | Date order object was created. The date is system-generated in GMT format YYYY-MM-DDThh:mmTZD | Date |  

### Sample request

```
curl -X POST http://www.recordstackoverflow.com/api/v1/orders/records/{recordId} -H 'Authorization: Bearer <access-token>' -H 'Content-Type: application/x-www-form-urlencoded' -H 'Postman-Token: 0bfe6afe-0890-4b55-9b58-6c3de42b9be7' -H 'cache-control: no-cache' -d 'merchant_id=5c57980f47a2107aab422247&merchant_id=&companyName=Company%20Test&primaryContact=John%20Doe&phoneNumber=555-555-5555&shipping_address1=123%20Shipping%20Lane&shipping_address2=&shipping_city=Raleigh&shipping_state=NC&shipping_zip=27615&paypal_email=paypal%40example.com&billing_address1=123%20Billing%20Drive&billing_address2=Ste.%20%23100&billing_city=Raleigh&billing_state=NC&billing_zip=27615&comments=This%20is%20a%20comment&undefined='
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

## Retrieve one order

Gets order information for the specified order ID. 

`GET /api/v1/orders/{orderID}`

### Parameters

**Path parameters**

| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| {orderID}   | Required       | Order ID of the order you want to retrieve information for | String |

### Sample request

```
curl -X GET http://www.recordstackoverflow.com/api/v1/orders/{orderID} -H 'Authorization: Bearer <access-token>' -H 'Content-Type: application/json'
```

### Sample response

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

### Sample error response

```json
{
    "error_message": "Order not found",
    "response_code": 404
}
```
  
****

## Retrieve all orders by customer

Gets all order information for a specific customer ID. Customers can only request order information associated with their customer ID.

`GET /api/v1/orders/customer/{customerId}/`

###Parameters

**Path parameters**

| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| {customerId}   | Required       | Customer ID of the customer you want to retrieve all orders for | String |

**Query string parameters**


| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| limit | Optional | Number of order objects to return | Integer |
| sort | Optional | Sorts results by the date the order was created. Enter "asc" or "1" for an ascending sort. Enter "desc" and "-1" for a descending sort. | String |
| offset | Optional | The index to start with. The default is 0. | integer |

###Sample request

```
curl -X GET
  'http://lwww.recordstackoverflow.com/api/v1/orders/customers/{customerID}?limit=5&sort=asc' \
  -H 'Authorization: Bearer <access-token>' -H 'Content-Type: application/json'
```

###Sample response
Returns a list of order objects.

****

## Retrieve all orders for a merchant

Retrieves all customer orders using the specified customer id. Merchants can only request order information associated with their merchant ID.

`GET /api/v1/orders/customers/{merchantID}/`

###Parameters

**Path parameters**

| URL Parameter  | Description    |
| :------------- | :------------- |
| {merchantId}     | Refers to the merchant ID of the merchant that created the records you want to retrieve. |

**Query string parameters**


| Parameter | Required | Description | Type |
| :---------| :-----------| :----| :--------|
| limit | Optional | Number of record objects to return | Integer |
| sort | Optional | Sorts results alphabetically by artist name. "asc" and "1" sort alphabetically. "desc" and "-1" sort reverse-alphabetically. | String |
| offset | Optional | The index to start with. The default is 0. | integer |

###Sample request

```
curl -X GET 'http://www.recordstackoverflow.com/api/v1/orders/customers/<merchantId>?limit=3&offset=10' 
  -H 'Authorization: Bearer <access-token>' -H 'Content-Type: application/json'
```

###Sample response
Returns a list of order objects for the specified merchant.

****

## Get order by id

Retrieves an order by id.

`GET /api/v1/orders/{orderId}/`

### Parameters

**Query string parameters**


| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| {orderId}     | Refers to the order ID that you want to retrieve. |


### Sample request

```
curl -X GET http://www.recordstackoverflow.com/api/v1/orders/{orderId} -H 'Authorization: Bearer <access-token>' -H 'Content-Type: application/json' \
```

### Returns 

Returns a list of record objects

****

## Update an order by id

Merchant accounts only. Retrieves an order by id and updates the orders object using the body parameters.

`GET /api/v1/orders/{orderId}/`

### Parameters

**Query string parameters**


| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| {orderId}     | Refers to the order ID that you want to retrieve. |

**Body parameters**

| Parameter      |                    |   Required       | Description    | Type |
| :------------- |--------------------|:-----------------| :--------------| :----|
| shipping_info | | | |
| | shipping_address1 | Optional | Registered shipping address of the account that created the order | String |
| | shipping_address2 | Optional | Registered shipping address of the account that created the order | String |
| | shipping_city | Optional | Registered shipping city of the account that created the order | String |
| | shipping_state | Optional | Registered shipping state of the account that created the order | String |
| | shipping_zip | Optional | Registered shipping zip code of the account that created the order | String |
| billing_info | | | |
| |paypal_email | Optional | Registered PayPal email address of the account that created the order | String |
| | billing_address1 | Optional | Registered billing address of the account that created the order | String |
| | billing_address2 | Optional | Registered billing address of the account that created the order | String |
| | billing_city | Optional | Registered billing city of the account that created the order | String |
| | billing_state | Optional | Registered billing state of the account that created the order | String |
| | billing_zip | Optional | Registered billing zip code of the account that created the order | String |
| comments | | Optional | Additional notes about the order | Array of Strings |

### Sample request

```
curl -X PUT http://www.recordstackoverflow.com/api/v1/orders/{orderId} -H 'Authorization: Bearer <access-token>' -H 'Content-Type: application/json' -d 'price=15&comments=Price%20drop%20with%20coupon'
```

### Sample response

```json
{
    "status": "In progress",
    "_id": "5c622fab2d312f70807cbc6f",
    "record_id": "5c620710c258e86bbcab95e9",
    "merchant_id": "5c620580c258e86bbcab95e6",
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
        "Price drop with coupon"
    ],
    "_createdBy": "5c62045537ca8a6ba560ee80",
    "created_date": "2019-02-12T02:30:03.964Z",
    "__v": 0
}
```
****

## Delete an order

Customer accounts only. Deletes an order by ID. You can only delete order objects that were created using your registered customer ID.
!!! important
    Delete orders only when the order `status` is `In progress`.

`DELETE /api/v1/orders/{orderId}/customer/{customerId}`

### Parameters

**Query string parameters**


| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| {orderId}     | Refers to the order ID that you want to delete. |

## Sample request

```
curl -X DELETE 'http://www.recordstackoverflow.com/api/v1/orders/{orderId}/customers/{customerId}' -H 'Authorization: Bearer <access-token>' -H 'Content-Type: application/json'
```

**Returns**

```json
{
  "Success": "Order deleted"
}
```