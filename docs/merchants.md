## The Merchant object

Store a representation of your company data in a merchant object. Contains your organization name, primary contact name, email, phone number, and mailing address. Customers and merchants can retrieve merchant information. 

### Merchant object example

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
| merchantAccount | | Identifies the account as a merchant account | Boolean | 
| _id         | | Unique system-generated identifier for the record object. | String |
| companyName | | Name of company that accepts customer payments | String |
| primaryContact | | Customer contact for questions regarding inventory, order fulfillment, returns, etc. | String |
| email | | Email address for customer questions regarding inventory, order fulfillment, returns, etc. | String |
| phoneNumber | | Phone number for `primaryContact` or automated system to answer customer calls regarding inventory, order fulfillment, returns, etc. | String | 
| address | | | |
| | shipping_address1 | Street address that record products ship or that accepts returns | String |
| | shipping_address2 | Street address that merchant ships record products from | String |
| | shipping_city | City that merchant ships record products from | String |
| | shipping_state | State that merchant ships record products from | String |
| | shipping_zip | Zip code that merchant ships record products from | String |

****

## Retrieve merchant information

`GET /api/v1/merchant/{merchantId}`

Gets the information for a specific merchant ID.

###Parameters

**Path parameters**


| Parameter | Description | Type | 
| :----------| :-----------| :----| 
| {merchantId}     | Refers to the merchant ID of the merchant that you want to retrieve information for. | String |


###Sample request

```
curl -X GET http://www.recordstackoverflow.com/api/v1/merchants/{merchantId} -H 'Authorization: Bearer <access-token>'
```

### Sample response

Returns merchant information that can be public.

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

Merchant accounts only. Retrieves a merchant by ID and updates the existing merchant object using the provided body parameters. You can only update merchant objects that were created using your registered merchant ID.

`PUT /api/v1/merchant/{merchantId}`


###Parameters

**Path parameters**

| Parameter | Description | Type | 
| :----------| :-----------| :----| 
| {merchantId}     | Refers to the merchant ID of the merchant that you want to retrieve information for. | String |

**Body parameters**

| Parameter | Required    | Description | Type |
| :---------| :-----------| :-----------| :----|
| companyName |  Optional | Name of company that accepts customer payments | String |
| primaryContact | Optional | Customer contact for questions regarding inventory, order fulfillment, returns, etc. | String |
| email | Optional | Email address for customer questions regarding inventory, order fulfillment, returns, etc. | String |
| phoneNumber | Optional | Phone number for `primaryContact` or automated system to answer customer calls regarding inventory, order fulfillment, returns, etc. | String | 
| shipping_address1 | Optional | Street address that record products ship or that accepts returns | String |
| shipping_address2 | Optional |Street address that merchant ships record products from | String |
| shipping_city | Optional | City that merchant ships record products from | String |
| shipping_state | Optional | State that merchant ships record products from | String |
| shipping_zip | Optional | Zip code that merchant ships record products from | String |

###Sample request

```
curl -X PUT \
  http://www.recordstackoverflow.com/api/v1/merchants/{merchantID} \
  -H 'Authorization: Bearer <access-token>' \
  -d 'primaryContact=Updated%20Contact&undefined='
```

###Sample response

```json
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


































