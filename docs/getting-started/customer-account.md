Create a customer account to purchase records, create orders, and cancel orders for your account.  

You must [register](#register-with-curl) your customer information before you can [log in]() and receive your authentication token to make API requests.

## Register with cURL

Send a cURL request in your terminal to register your Record Stack Overflow customer account information.

Use `http://www.recordstackoverflow.com/auth/register/customer` to register.

The following fields are **required** for customer accounts:  
- `username`  
- `firstName`  
- `lastName`  
- `email`  
- `password`  
- `shipping_address1`  
- `shipping_city`  
- `shipping_state`  
- `shipping_zip`  
- `paypal_email`  

The following fields are optional for customer accounts:  
- `shipping_address2`  
- `billing_address1`  
- `billing_address2`  
- `billing_city`  
- `billing_state`  
- `billing_zip`  

!!! note
    If there is no billing information provided, Record Stack Overflow uses your shipping information for billing purposes. Provide your billing information if it is different from your shipping information to prevent errors during purchasing.
    
**Request example**

```curl
curl -X POST \
  http://www.recordstackoverflow.com/auth/login/customer \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'username=customerName&firstName=First&lastName=Name&email=email%40example.com&password=password123&shipping_address1=123%20Shipping%20Lane&shipping_address2=Ste.%20%23100&shipping_city=Raleigh&shipping_state=NC&shipping_zip=27615&paypal_email=paypal%40example.com&billing_address1=123%20Billing%20Drive&billing_city=Boston&billing_state=MA&billing_zip=02101'
```

**Request response**

```
{"_id":"5c5ef0909c73b3004414ac9d","username":"userName","firstName":"First","lastName":"Name","email":"email@example.com","shipping_info":[{"shipping_address1":"123 Shipping Lane","shipping_address2":"Ste. #100","shipping_city":"Raleigh","shipping_state":"NC","shipping_zip":"27615"}],"billing_info":[{"paypal_email":"paypal@example.com","billing_address1":"123 Billing Drive","billing_city":"Boston","billing_state":"MA","billing_zip":"02101"}],"created_date":"2019-02-09T15:24:00.863Z","__v":0}
```

Below is an example of the parsed JSON response:

```json
{
    "_id": "<customerID>",
    "username": "userName",
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
    "created_date": "2019-02-09T15:20:45.155Z",
    "__v": 0
}
```
!!! important
    Save your `<customerID>` in a secure location.
    
***
***

## Log in with cURL

Send a cURL request to receive your JSON web token (JWT) to authenticate your API calls. For more information on JWTs, see [Authentication](authentication.md)

Send your registered email and password to `http://www.recordstackoverflow.com/auth/login/customer` to get your access token.

**Request example**

```shell
curl -X POST \
  http://www.recordstackoverflow.com/auth/login/customer \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'email=email%40example.com&password=password123&undefined='
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
    There are various API testing tools. [Read this article](https://alternativeto.net/software/postman/) to explore alternatives to Postman.

Use Postman to send a `POST` request to register your Record Stack Overflow customer account information.

If you already have a Postman account, click [![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/ab12924f72b9d522cd62) to access the Record Stack Overflow Postman Collection. Select the **Register customer account** request from the **RSO-getting-started** collection to register your account.



**Before you begin:** Download and install [Postman](https://www.getpostman.com/).

1. Start **Postman**.

2. Select **POST** in the drop-down to the left of **Enter request URL**.

3. In **Enter request URL**, enter `www.recordstackoverflow.com/auth/register/customer`.  
  
4. Click **Body**.

5. Select the **x-www-form-urlencoded** radio button.  
  **Step result:** A header with **KEY** `Content-Type` and **VALUE** `application/x-www-form-urlencoded` is added in the **Headers** tab.

6. Enter the following required body parameters in the corresponding columns:

    | Key                  | Value               |
    | :------------------- | :------------------ |
    | `username`           |`[your_username]`    |
    | `firstName`          |  `[your_first_name]`|
    | `lastName`           |`[your_last_name]`   |
    |   `email`            | `[your_email]`      |
    | `password`           | `[your_password]`   |
    |  `shipping_address1` | `[your_shipping_address]` |
    | `shipping_city`      | `[your_shipping_city]` |
    | `shipping_state`     |  `[your_shipping_state]` |
    |  `shipping_zip`      | `[your_shipping_zip]` |
    |  `paypal_email`      |  `[your_shipping_email]` |

    The following key fields are optional for customer accounts:  
    - `shipping_address2`  
    - `billing_address1`  
    - `billing_address2`  
    - `billing_city`  
    - `billing_state`  
    - `billing_zip`   

    !!! note
        If there is no billing information provided, Record Stack Overflow uses your shipping information for billing purposes. Provide your billing information if it is different from your shipping information to prevent errors during purchasing.
    
7. Click **Send** to the right of the request URL.


You receive a JSON object with your credentials.  
    
```json
{
    "_id": "<userID>",
    "username": "userName",
    "firstName": "First",
    "lastName": "Name",
    "email": "email@example.com",
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
            "paypal_email": " paypal@example.com",
            "billing_address1": "123 Billing Drive",
            "billing_address2": "",
            "billing_city": " Boston",
            "billing_state": " MA",
            "billing_zip": " 02101"
        }
    ],
    "created_date": "2019-02-09T12:39:06.482Z",
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

If you already have a Postman account, click [![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/ab12924f72b9d522cd62) to access the Record Stack Overflow Postman Collection. Select the **Login customer account** request from the **RSO-getting-started** collection to log in to your account. 

**Before you begin:** Complete [Register with Postman](#register-with-postman).

1. Start **Postman**.

2. Select **POST** in the drop-down to the left of **Enter request URL**.
 
3. In **Enter request URL**, enter `www.recordstackoverflow.com/auth/login/customer`.  

4. Click **Body** to access the request body.

5. Select the **x-www-form-urlencoded** radio button.  
  **Step result:** A header with **KEY** `Content-Type` **VALUE** `application/x-www-form-urlencoded` is added in the **Headers** tab.

6. Enter the following body parameters in the corresponding columns:

    | Key | Value |
    | :------------- | :------------- |
    | `email`      | `[your_registered_email]`       |
    | `password` | `[your_registered_password]` |

  
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