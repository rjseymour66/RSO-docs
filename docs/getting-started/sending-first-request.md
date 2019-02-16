This tutorial uses Postman, an API testing tool, to complete the API call. If you do not have a Postman account, download and install [Postman](https://www.getpostman.com/). For information on how to use Postman, explore the Postman [Getting Started tutorial](https://learning.getpostman.com/getting-started/).

If you are already familiar with Postman, click [![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/ab12924f72b9d522cd62) to access the Record Stack Overflow Postman request collection. Select **Sending first request demo** from **RSO-getting-started**, then add your information to the template and click **Send**.

!!! note
    There are various API testing tools. [Read this article](https://alternativeto.net/software/postman/) to explore alternatives to Postman.

**Before you begin:** [Create a customer account](customer-account.md) or [create a merchant account](merchant-account.md).

Send a `GET` request to retrieve 5 records currently available in the Record Stack Overflow inventory and sort the returned information by artist name.

1. Start **Postman**.

2. Select **GET** in the drop-down to the left of **Enter request URL**.

3. In **Enter request URL**, enter `www.recordstackoverflow.com/api/v1/records`.

4. Click **Params**.

5. Enter the following key/value pairs as query parameters: 
    
    | Key            | Value |
    | :------------- | :---- |
    | `sort`           | `desc`  |
    | `limit`          | `5`     |


6. Click **Headers**.
 
7. Enter the following key/value pairs as request headers:

    | Key            | Value                 |
    | :------------- | :-------------------- |
    | `Content-Type`   | `application/x-www-form-urlencoded`  |
    | `Authorization`  | `Bearer <access-token>` |

    !!! important
        In the **Value** column in the **Authorization** row, enter exactly 1 space between `Bearer` and `<access-token>` or your request will fail.

8. Click **Send**.

**Result:**

Five JSON record objects are returned in descending alphabetical order by artist name.

!!! note
    By default, record objects are sorted alphabetically by `artist` when more than 1 record object is returned.