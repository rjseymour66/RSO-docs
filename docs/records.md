## The Record object

Store representations of each record item you sell in `Record` objects. Contains information about the record for sale, including the artist, record title, price, and condition. Records can be added, requested, updated, and deleted. Request records by artist name or records added by a specified merchant. Records are physical goods.

**Records endpoints**

- POST `/records/`  
- GET `/records/`  
- GET `/records/merchant/{merchantId}/`  
- PUT `/records/{recordId}/`  
- DELETE `/records/{recordId}/merchants/{merchantId}/`  


**Record object example**

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
| _id | Unique system-generated identifier for the record object. | String |
| artist | Name of the artist. Enter the artist name exactly as it appears on the physical record packaging. | String |
| title | Title of the record. Enter the record title exactly as it appears on the physical record packaging. | String |
| price | Price to sell record in USD. | String |
| condition | Measures the playability and overall quality of the physical record and packaging. | Array of Strings |
| comments | Additional notes about the record. | Array of Strings |
| created_date | Date record object was created. The date is system-generated in GMT format YYYY-MM-DDThh:mmTZD | Date |  

****

## Create a record

Creates a new record object.

**POST `api/v1/records/`**

### Parameters

**Body Parameters**

| Parameter      | Required       | Description | Type |
| :------------- | :------------- | :-----------| :----|
| artist | Required | Name of the artist. Enter the artist name exactly as it appears on the physical record packaging. | String |
| title | Required | Title of the record. Enter the record title exactly as it appears on the physical record packaging. | String |
| price | Required | Price to sell record in USD. | String |
| condition | Required | Measures the playability and overall quality of the physical record and packaging. | Array of Strings |
| comments | Optional | Additional notes about the record. | Array of Strings |

### Sample request

```shell
curl -X POST \
  http://www.recordstackoverflow.com/api/v1/records \
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

`GET /api/v1/records`

Gets all records using the specified parameters.

### Parameters

**Query string parameters**

| Parameter | Required    | Description | Type     |
| :---------| :-----------| :-----------| :--------| 
| artist    | Optional | Name of artist to return in search | String |
| limit | Optional | Number of record objects to return | Integer |
| sort | Optional | Sorts results alphabetically by artist name. "asc" or "1" sort alphabetically. "desc" or "-1" sort reverse-alphabetically. | String |
| offset | Optional | The index to start with. The default is 0. | integer |


### Sample request

```
curl -X GET \
  http://www.recordstackoverflow.com/api/v1/records \
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

`GET /api/v1/records/merchant/{merchantId}`

Gets all records for sale for a specific merchant ID.

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

### Sample request

```
curl -X GET \
  http://www.recordstackoverflow.com/api/v1/records/merchants/{merchantId} \
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
(Merchant accounts only)

`PUT /api/v1/records/{recordId}`

Retrieves a record by ID and updates the existing record object using the provided body parameters. You can only update record objects that were created using your registered merchant ID.

### Path Parameters

**Path parameters**

| URL Parameter  | Description    |
| :------------- | :------------- |
| {recordId}     | Refers to the record ID of the record object you want to edit. |



**Body Parameters**

Parameter | Description | Type | Required | Notes |
----------|-------------|------|----------|-------|
| artist | Optional | Name of the artist. Enter the artist name exactly as it appears on the physical record packaging. | String |
| title | Optional | Title of the record. Enter the artist name exactly as it appears on the physical record packaging. | String |
| price | Optional | Price to sell record in USD. | String |
| condition | Optional | Measures the playability and overall quality of the physical record and record packaging. | Array of Strings |
| comments | Optional | Additional notes about the record. | Array of Strings |

### Sample request

```
curl -X PUT \
  http://www.recordstackoverflow.com/api/v1/records/{recordId} \
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
Merchant accounts only.

`DELETE /api/v1/records/{recordId}/merchants/{merchantId}`

Deletes a record by ID using the provided path parameter. You can only delete record objects that were created using your registered merchant ID.

### Parameters

**Path parameters**

| URL Parameter  | Description    |
| :------------- | :------------- |
| {recordId}     | Refers to the record ID of the record object you want to edit. |
| {merchantId}   | Refers to the merchant ID of the merchant that created the record you want to delete. |

### Sample request

```
curl -X DELETE \
  http://www.recordstackoverflow.com/api/v1/records/{recordId}/merchants/{merchantId} \
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







