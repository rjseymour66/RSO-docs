## The Record object

Store representations of each record item you sell in record objects. Contains information about the record for sale, including the artist, record title, price, and condition. Records can be added, requested, updated, and deleted. Request records by artist name or by a specified merchant. Records are physical goods.

### Base path  

https://<span></span>www.recordstackoverflow.com/api/v1/

### Records endpoints



- POST `/records/`  
- GET `/records/`  
- GET `/records/merchant/{merchantId}/`  
- PUT `/records/{recordId}/`  
- DELETE `/records/{recordId}/merchants/{merchantId}/`  


### Sample record object

```json
{
    "_id": "<recordID>",
    "artist": "Artist Example",
    "title": "Record Title Example",
    "price": "22.00",
    "condition": "vg",
    "comments": [
        "Near perfect condition"
    ],
    "_createdBy": "5c5ceb52b78f5f297244d6eb",
    "created_date": "2019-02-08T02:40:20.381Z",
    "__v": 0
}
```

| Attributes | Description | Type | 
| :----------| :-----------| :----| 
| _id | Unique system-generated identifier of the record object. | String |
| artist | The name of the artist. Enter the artist name exactly as it appears on the physical record packaging. | String |
| title | The title of the record. Enter the record title exactly as it appears on the physical record packaging. | String |
| price | The sale price of the record in USD. | String |
| condition | Describes the playability and overall quality of the physical record and packaging. | Array of Strings |
| comments | Additional notes about the record. | Array of Strings |
| created_date | The date the record object was created. The date is system-generated in GMT format YYYY-MM-DDThh:mmTZD | Date |  

****

## Create a record

Creates a new record object.

POST `/records/`

### Parameters

**Body Parameters**

| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| artist | Required | The name of the artist. Enter the artist name exactly as it appears on the physical record packaging. | String |
| title | Required | The title of the record. Enter the record title exactly as it appears on the physical record packaging. | String |
| price | Required | The sale price of the record in USD. | String |
| condition | Required | Describes the playability and overall quality of the physical record and packaging. | Array of Strings |
| comments | Optional | Additional notes about the record. | Array of Strings |

### Sample request

```shell
curl -X POST \
  https://www.recordstackoverflow.com/api/v1/records \
  -H 'Authorization: Bearer <access-token>' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'artist=Artist%20Name&title=Title%20name&price=25.00&condition=g&comments=Comment%20example&undefined='
```

### Sample response

Returns a record object.

```json
{
    "_id": "<recordID>",
    "artist": "Artist Name",
    "title": "Title name",
    "price": "25.00",
    "condition": "g",
    "comments": [
        "Comment example"
    ],
    "_createdBy": "5c679751bb102c001706bf0a",
    "created_date": "2019-02-16T05:01:33.597Z",
    "__v": 0
}
```
****

## Retrieve all records

GET `/records/`

Retrieves all records. Filter results using the query parameters.

### Parameters

**Query string parameters**

| Parameter | Required    | Description | Type     |
| :---------| :-----------| :-----------| :--------| 
| artist    | Optional | Name of artist to search for. | String |
| limit | Optional | The number of record objects to return. Default is all. | Integer |
| sort | Optional | The order results are returned in. Use "asc" or "1" to sort alphabetically by artist name. Use "desc" or "-1" to sort reverse-alphabetically by artist name. | String |
| offset | Optional | The index to start with. The default is 0. | Integer |


### Sample request

```
curl -X GET \
  https://www.recordstackoverflow.com/api/v1/records \
  -H 'Authorization: Bearer <access-token>' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
```

### Sample response

Returns an Array of record objects. If no record matches the query and no errors occur, returns an empty Array.

```json
[
    {
        "_id": "<recordID>",
        "artist": "1 Record",
        "title": "1 Title",
        "price": "11.00",
        "condition": "g",
        "comments": [
            "This is the first comment!"
        ],
        "_createdBy": "<merchantID>",
        "created_date": "2019-02-16T04:56:49.564Z",
        "__v": 0
    },
    {
        "_id": "<recordID>",
        "artist": "2 Record",
        "title": "2 Title",
        "price": "25.00",
        "condition": "g",
        "comments": [
            "This is the second comment!"
        ],
        "_createdBy": "<merchantID>",
        "created_date": "2019-02-16T05:04:48.563Z",
        "__v": 0
    },
    {
        "_id": "<recordID>",
        "artist": "3 Record",
        "title": "3 Title",
        "price": "25.00",
        "condition": "g",
        "comments": [
            "This is the third comment!"
        ],
        "_createdBy": "<merchantID>",
        "created_date": "2019-02-16T05:07:26.503Z",
        "__v": 0
    }
]
```

****

## Retrieve all records by merchant

GET `/records/merchant/{merchantId}/`

Retrieves all records for sale for a specific merchant ID.

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
| offset | Optional | The index to start with. The default is 0. | integer |

### Sample request

```
curl -X GET \
  https://www.recordstackoverflow.com/api/v1/records/merchants/{merchantId} \
  -H 'Authorization: Bearer <access-token>' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
```

### Sample response

Returns an Array of record objects created by the specified merchant ID. If no record matches the query and no errors occur, returns an empty Array.


```json
[
    {
        "_id": "<recordID>",
        "artist": "1 Record",
        "title": "1 Title",
        "price": "11.00",
        "condition": "g",
        "comments": [
            "This is the first comment!"
        ],
        "_createdBy": "<merchantID>",
        "created_date": "2019-02-16T04:56:49.564Z",
        "__v": 0
    },
    {
        "_id": "<recordID>",
        "artist": "2 Record",
        "title": "2 Title",
        "price": "25.00",
        "condition": "g",
        "comments": [
            "This is the second comment!"
        ],
        "_createdBy": "<merchantID>",
        "created_date": "2019-02-16T05:04:48.563Z",
        "__v": 0
    }
]
```

****

## Update a record
**(Merchant accounts only)**

`PUT /api/v1/records/{recordId}`

Retrieves a record by ID and updates the existing record object using the body parameters. Update only record objects that were created using your registered merchant ID.

### Parameters

**Path parameters**

| URL Parameter  | Description    |
| :------------- | :------------- |
| {recordId}     | Refers to the record ID of the record object you want to edit. |



**Body Parameters**

Parameter | Description | Type | Required | Notes |
----------|-------------|------|----------|-------|
| artist | Optional | The name of the artist. Enter the artist name exactly as it appears on the record packaging. | String |
| title | Optional | The title of the record. Enter the record title exactly as it appears on the record packaging. | String |
| price | Optional | The sale price of the record in USD. | String |
| condition | Optional | Describes the playability and overall quality of the physical record and record packaging. | String |
| comments | Optional | Additional notes about the record. | Array of Strings |

### Sample request

```
curl -X PUT \
  https://www.recordstackoverflow.com/api/v1/records/{recordId} \
  -H 'Authorization: Bearer <access-token>' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'comments=Price%20drop&price=9.00'
```

### Sample response 

Returns the updated record object:

```json hl_lines="5 8"
{
    "_id": "<recordID>",
    "artist": "1 Record",
    "title": "1 Title",
    "price": "9.00",
    "condition": "g",
    "comments": [
        "Price drop"
    ],
    "_createdBy": "<merchantID>",
    "created_date": "2019-02-16T04:56:49.564Z",
    "__v": 0
}
```

****

## Delete a record
**(Merchant accounts only)**

DELETE `/records/{recordId}/merchants/{merchantId}/`

Deletes a record by ID. Delete only record objects that were created using your registered merchant ID.

### Parameters

**Path parameters**

| URL Parameter  | Description    |
| :------------- | :------------- |
| {recordId}     | Refers to the record ID of the record object you want to edit. |
| {merchantId}   | Refers to the merchant ID of the merchant that created the record you want to delete. |

### Sample request

```
curl -X DELETE \
  https://www.recordstackoverflow.com/api/v1/records/{recordId}/merchants/{merchantId} \
  -H 'Authorization: Bearer <access-token>' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
```


### Sample response

```json
{
    "success_message": "Record deleted",
    "response_code": 200
}
```