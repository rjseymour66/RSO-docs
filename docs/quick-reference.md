## Base path  

www.recordstackoverflow.com/api/v1/

## Records

| HTTP Method      | URL                        | Description         |
| :------------- | :--------------------------| : ------------------|
| POST           | [/records/](records.md)    | Create a new record |
| GET            | [/records/](records.md)    | Retrieve all records |
| GET | [/records/merchant/{merchantId}/](records.md)  | Retrieve all records by merchant   |
| PUT | [/records/{recordId}/](records.md)    | Update a record  |
| DELETE | [/records/{recordId}/merchants/{merchantId}/](records.md) | Delete a record   |


<!-- [`/records/`](records.md)  
Create a new record  

[`/records/`](records.md)   
Retrieve all records  

[`/records/merchant/{merchantId}/`](records.md)  
Retrieve all records by merchant  

[`/records/{recordId}/`](records.md)  
Update a record  

[`/records/{recordId}/merchants/{merchantId}/`](records.md)  
Delete a record   -->



## Orders

| HTTP Method      | URL                        | Description         |
| :------------- | :--------------------------| : ------------------|
| POST           | [/orders/merchants/{merchantId}/records/{recordId}/](orders.md)    | Create and order  |
| GET            | [/orders/customers/{customerId}/](orders.md)     | Retrieve all orders for a customer   |
| GET | [/orders/merchants/{merchantId}/](orders.md)  | Retrieve all orders for a merchant     |
| PUT | [/orders/{orderId}/](orders.md)     | Update an order by ID   |
| DELETE | [/orders/{orderId}/customers/{customerId}/](orders.md) | Delete an order   |

<!-- [`/orders/merchants/{merchantId}/records/{recordId}/`](orders.md)  
Create and order  

[`/orders/customers/{customerId}/`](orders.md)  
Retrieve all orders for a customer  

[`/orders/merchants/{merchantId}/`](orders.md)  
Retrieve all orders for a merchant  

[`/orders/{orderId}/`](orders.md)  
Update an order by ID  

[`/orders/{orderId}/customers/{customerId}/`](orders.md)  
Delete an order   -->

## Merchants

| HTTP Method      | URL                        | Description         |
| :------------- | :--------------------------| : --------------------|
| GET | [/merchants/{merchantId}/](merchants.md) | Retrieve merchant information |
| PUT | [/merchants/{merchantId}/](merchants.md) | Update a merchant by ID  |

<!-- [`/merchants/{merchantId}/`](merchants.md)  
Retrieve merchant information  

[`/merchants/{merchantId}/`](merchants.md)  
Update a merchant by ID   -->


## Customers

| HTTP Method      | URL                        | Description         |
| :------------- | :--------------------------| : --------------------|
| GET | [/customers/{customerId}/](customers.md)  | Retrieve customer information  |
| PUT | [/customers/{customerId}/](customers.md) | Update a customer by ID    |

<!-- [`/customers/{customerId}/`](customers.md)  
Retrieve customer information  

[`/customers/{customerId}/`](customers.md)  
Update a customer by ID   -->