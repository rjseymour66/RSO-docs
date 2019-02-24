## The Merchant object

Store a representation of your company information in a merchant object. Contains your organization name, primary contact name, email, phone number, and mailing address. Customers and merchants can retrieve merchant information. 


### Base path  


https://www.recordstackoverflow.com/api/v1/

### Merchants endpoints

- GET `/merchants/{merchantId}/`  
- PUT `/merchants/{merchantId}/`  

### Sample merchant object

```json
{
    "merchantAccount": true,
    "_id": "<merchantID>",
    "companyName": "Company Name",
    "primaryContact": "Primary Contact",
    "email": "company@email.com",
    "phoneNumber": "555-555-5555",
    "address": [
        {
            "shipping_address1": "321 Shipping Lane",
            "shipping_address2": "",
            "shipping_city": "Raleigh",
            "shipping_state": "NC",
            "shipping_zip": "27615"
        }
    ],
    "created_date": "2019-02-09T16:09:37.897Z",
    "__v": 0
}
```

| Attributes | | Description | Type |
| :----------|-| :-----------| :----| 
| merchantAccount | | Identifies the account as a merchant account. | Boolean | 
| _id         | | Unique system-generated identifier of the record object. | String |
| companyName | | The name of the company that accepts customer payments. | String |
| primaryContact | | The customer contact for questions regarding inventory, order fulfillment, returns, etc. | String |
| email | | The email address for customer questions regarding inventory, order fulfillment, returns, etc. | String |
| phoneNumber | | The phone number for `primaryContact` or the automated system to answer customer calls regarding inventory, order fulfillment, returns, etc. | String | 
| address | | | |
| | shipping_address1 | The street address that the merchant ships orders from and accepts returns from. | String |
| | shipping_address2 | The street address that the merchant ships orders from and accepts returns from. | String |
| | shipping_city | The city that the merchant ships orders from. | String |
| | shipping_state | The state that the merchant ships orders from. | String |
| | shipping_zip | The zip code that the merchant ships orders from. | String |

****

## Retrieve merchant information

GET `/merchant/{merchantId}/`

Retrieves the information for a specific merchant ID.

###Parameters

**Path parameters**


| Parameter | Description | Type | 
| :----------| :-----------| :----| 
| {merchantId}     | Refers to the merchant ID of the merchant that you want to retrieve information for. | String |


###Sample request

```
curl -X GET https://www.recordstackoverflow.com/api/v1/merchants/{merchantId} -H 'Authorization: Bearer <access-token>'
```

### Sample response

Returns the specified merchant information.

```json
{
    "companyName": "Company Name",
    "primaryContact": "Primary Contact",
    "email": "email@example.com",
    "phoneNumber": "555-555-4321",
    "address": [
        {
            "shipping_address1": "321 Shipping Lane",
            "shipping_address2": "",
            "shipping_city": "Raleigh",
            "shipping_state": "NC",
            "shipping_zip": "27615"
        }
    ]
}
```

****

## Update merchant by ID
**(Merchant accounts only)**

Retrieves a merchant by ID and updates the existing merchant object with the information provided in the body parameters. You can update only merchant objects associated with the request's access token.

PUT `/merchant/{merchantId}/`


###Parameters

**Path parameters**

| Parameter | Description | Type | 
| :----------| :-----------| :----| 
| {merchantId}     | Refers to the merchant ID of the merchant that you want to retrieve information for. | String |

**Body parameters**

| Parameter | Required    | Description | Type |
| :---------| :-----------| :-----------| :----|
| companyName |  Optional | The name of the company that accepts customer payments. | String |
| primaryContact | Optional | The customer contact for questions regarding inventory, order fulfillment, returns, etc. | String |
| email | Optional | The email address for customer questions regarding inventory, order fulfillment, returns, etc. | String |
| phoneNumber | Optional | The phone number for customer calls regarding inventory, order fulfillment, returns, etc. | String | 
| shipping_address1 | Optional | The street address that the merchant ships orders from and accepts returns from. | String |
| shipping_address2 | Optional | The street address that the merchant ships orders from and accepts returns from. | String |
| shipping_city | Optional | The city that the merchant ships orders from. | String |
| shipping_state | Optional | The state that the merchant ships orders from. | String |
| shipping_zip | Optional | The zip code that the merchant ships orders from. | String |

###Sample request

```
curl -X PUT \
  https://www.recordstackoverflow.com/api/v1/merchants/{merchantID} \
  -H 'Authorization: Bearer <access-token>' \
  -d 'primaryContact=Updated%20Contact'
```

###Sample response

```json hl_lines="5"
{
    "merchantAccount": true,
    "_id": "<merchantID>",
    "companyName": "Company Name",
    "primaryContact": "Updated Contact",
    "email": "company@email.com",
    "phoneNumber": "555-555-5555",
    "address": [
        {
            "shipping_address1": "432 Shipping Lane",
            "shipping_address2": "",
            "shipping_city": "Raleigh",
            "shipping_state": "NC",
            "shipping_zip": "27615"
        }
    ],
    "created_date": "2019-02-09T16:09:37.897Z",
    "__v": 0
}
```
