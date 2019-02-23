Create a merchant account to sell records, purchase records, update record information, delete records, create orders, and cancel orders.

You must register your merchant account information before you can log in and receive your authentication token to make API requests.

## Register with cURL

Send a cURL request in your terminal to register your Record Stack Overflow merchant account information.

Use `https://www.recordstackoverflow.com/auth/register/customer` to register.

The following fields are **required** for merchant accounts:  
- `companyName`  
- `primaryContact`  
- `email`  
- `phoneNumber`  
- `password`  
- `shipping_address1`  
- `shipping_city`  
- `shipping_state`  
- `shipping_zip`  

!!! note
    `shipping_address2` is optional for merchant accounts.

    
**Request example**

```curl
curl -X POST \
  https://www.recordstackoverflow.com/auth/register/merchant \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'companyName=Company%20Name&primaryContact=Primary%20Contact&email=company%40email.com&phoneNumber=555-555-5555&password=password123&shipping_address1=321%20Shipping%20Lane&shipping_address2=&shipping_city=Raleigh&shipping_state=NC&shipping_zip=27615'
```

**Request response**

```
{"merchantAccount":true,"_id":"5c5efbeae1c7320044507e11","companyName":"Company Name","primaryContact":"Primary Contact","email":"company@email.com","phoneNumber":"555-555-5555","address":[{"shipping_address1":"321 Shipping Lane","shipping_address2":"","shipping_city":"Raleigh","shipping_state":"NC","shipping_zip":"27615"}],"created_date":"2019-02-09T16:12:26.504Z","__v":0}
```

Below is an example of the parsed JSON response:

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
!!! important
    Save your `_id` in a secure location.
    
***
***

## Log in with cURL

Send a cURL request to receive your JSON web token (JWT) to authenticate your API calls. For more information on JWTs, see [Authentication](authentication.md)

Send your registered email and password to `https://www.recordstackoverflow.com/auth/login/merchant` to get your access token.

**Request example**

```shell
curl -X POST \
  https://www.recordstackoverflow.com/auth/login/merchant \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'email=company%40email.com&password=password123&undefined='
```

**Request response**

```
{"secret token":"<access-token>"}
```

!!! important
    Save your `<access-token>` in a secure location.
    
***
***

## Register with Postman

[Postman](https://www.getpostman.com/) is an API development tool that provides a GUI (graphical user interface) to test and interact with APIs.

!!! note
    [Read this article](https://alternativeto.net/software/postman/) to explore alternatives to Postman.

Use Postman to send a `POST` request to register your Record Stack Overflow merchant account information.

If you already have a Postman account, click [![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/ab12924f72b9d522cd62) to access the Record Stack Overflow Postman Collection. Select **Register merchant account** from the **RSO-getting-started** collection to register your account.



**Before you begin:** Download and install [Postman](https://www.getpostman.com/).

1. Start **Postman**.

2. Select **POST** in the drop-down to the left of **Enter request URL**.

3. In **Enter request URL**, enter `www.recordstackoverflow.com/auth/register/merchant`.  
  
4. Click **Body**.

5. Select the **x-www-form-urlencoded** radio button.  
  **Step result:** A header with **KEY** `Content-Type` and **VALUE** `application/x-www-form-urlencoded` is added in the **Headers** tab.

6. Enter the following required body parameters in the corresponding columns:

    | Key                  | Value               |
    | :------------------- | :------------------ |
    | `companyName`           |`[your_companyName]`    |
    | `primaryContact`          |  `[your_merchant_primaryContact]`|
    | `email`           |`[your_merchant_email]`   |
    |   `phoneNumber`            | `[your_merchant_phoneNumber]`      |
    | `password`           | `[your_password]`   |
    |  `shipping_address1` | `[your_merchant_shipping_address]` |
    | `shipping_city`      | `[your_merchant_shipping_city]` |
    | `shipping_state`     |  `[your_merchant_shipping_state]` |
    |  `shipping_zip`      | `[your_merchant_shipping_zip]` |
    |  `paypal_email`      |  `[your_merchant_shipping_email]` |

    

    !!! note
        `shipping_address2` is optional for merchant accounts
    
7. Click **Send** to the right of the request URL.


You receive a JSON object with your credentials.  
    
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

!!! important
    Save your `_id` in a secure location.

***
***
    
## Log in with Postman

Use Postman to send a `POST` request to log in to your registered account to receive your JSON web token (JWT) to authenticate your API calls. For more information on JWTs, see [Authentication](authentication.md).

Send a `POST` request to login and receive your JSON web token (JWT).

If you already have a Postman account, click [![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/ab12924f72b9d522cd62) to access the Record Stack Overflow Postman Collection. Select **Login merchant account** from the **RSO-getting-started** collection to log in to your account. 

**Before you begin:** Complete [Register with Postman](#register-with-postman).

1. Start **Postman**.

2. Select **POST** in the drop-down to the left of **Enter request URL**.
 
3. In **Enter request URL**, enter `www.recordstackoverflow.com/auth/login/merchant`.  

4. Click **Body** to access the request body.

5. Select the **x-www-form-urlencoded** radio button.  
  **Step result:** A header with **KEY** `Content-Type` **VALUE** `application/x-www-form-urlencoded` is added in the **Headers** tab.

6. Enter the following body parameters in the corresponding columns:

    | Key | Value |
    | :------------- | :------------- |
    | `email`      | `[your_registered_merchant_email]`       |
    | `password` | `[your_registered_merchant_password]` |

  
7. Click **Send**.

    **Result**  
    You receive your JWT in a JSON response:  
    ```
    {
        "secret token": "<access-token>" 
    }
    ```

!!! important
    Save your `<access-token>` in a secure location.
