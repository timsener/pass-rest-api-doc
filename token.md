| URI                                        | Method   | Returns                                                         |
| ------------------------------------------ | -------- | --------------------------------------------------------------- |
| [/token/v1/login](#login)                  | `POST`   | login using Basic authentication and return an AccessToken      |
| [/token/v1/login](#logout)                 | `DELETE` | logout using Bearer authentication and expiring the AccessToken |
| [/token/v1/refresh](#refresh)              | `POST`   | refresh the given AccessToken expiry date                       |
| [/token/v1/passwordtoken](#passwordtoken)  | `GET`    | retrieve a password token by login_name                         |
| [/token/v1/changepassword](#passwordtoken) | `POST`   | change password for pashouder related to provided PasswordToken |

## **Login**

Authenticates pashouder by basic authentication header and returns json data about an AccessToken.

- **URL**

  /token/v1/login

- **Method:**

  `POST`

- **Headers**

  **Required:**

  `Authorization` (type: basic)

  The basic Authorizaton header value should consist of the type 'Basic' followed by a space, followed by a base64 encoded representation of the pashouder login_name:password concatenation.

  For a pashouder with login_name `username` and password `secret` this would result in the concatenated value `username:secret` which in turn needs to be encoded using base64 (ie dXNlcm5hbWU6c2VjcmV0). The resulting string can be used in the Authorization header: `Authorization: Basic dXNlcm5hbWU6c2VjcmV0`

- **URL Params**

  None

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
    {
        "token_type": "AccessToken",
        "token": "FTUHDoBug9iyiUSiRoujRWZPs74",
        "expiry_date": "2019-09-25T13:40:45.904Z"
    }
    ```

- **Error Response:**

  - **Code:** 400 <br />
    **Message:** Authorization header missing <br />

  - **Code:** 400 <br />
    **Message:** Authorization header invalid (ie Authorization: Basic {token}) <br />

  - **Code:** 401 <br />
    **Message:** User not found <br />

  - **Code:** 401 <br />
    **Message:** User not active <br />

  - **Code:** 401 <br />
    **Message:** Password is missing <br />

  - **Code:** 401 <br />
    **Message:** Authentication failed <br />

## **Logout**

Logout the user by expiring the token given in the Authorization bearer.

- **URL**

  /token/v1/login

- **Method:**

  `DELETE`

- **Headers**

  **Required:**

  `Authorization` (type: bearer)

- **URL Params**

  None

- **Success Response:**

  - **Code:** 204 <br />
    **Message:** User logged out - tokens expired <br />

- **Error Response:**

  - **Code:** 404 <br />
    **Message:** Token niet gerelateerd aan pashouder

  - **Code:** 422 <br />
    **Message:** Login naam niet uniek

  - **Code:** 422 <br />
    **Message:** Wachtwoord voldoet niet aan eisen - (8 karakters, 1 hoofdletter, 1 kleine letter, 1 speciaal karakter en 1 numeriek karakter)

  - **Code:** 422 <br />
    **Message:** Login naam niet uniek

## **Refresh**

Refresh expiry date of the token given in the Authorization bearer.

- **URL**

  /token/v1/refresh

- **Method:**

  `DELETE`

- **Headers**

  **Required:**

  `Authorization` (type: bearer)

- **URL Params**

  None

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
    {
        "token_type": "AccessToken",
        "token": "FTUHDoBug9iyiUSiRoujRWZPs74",
        "expiry_date": "2019-09-25T13:40:45.904Z"
    }
    ```

## **Passwordtoken**

Request a PasswordToken required for a password reset

- **URL**

  /token/v1/passwordtoken

- **Method:**

  `POST`

- **Headers**

  **Required:**

  `API-Key`

- **URL Params**

  **Required:**

  `login_name=[string]`

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
    {
        "token_type": "PasswordToken",
        "token": "FTUHDoBug9iyiUSiRoujRWZPs74",
        "expiry_date": "2019-09-25T13:40:45.904Z"
    }
    ```

- **Error Response:**

  - **Code:** 400 <br />
    **Message:** Mandatory [login_name] query parameter empty

  - **Code:** 401 <br />
    **Message:** User not found

  - **Code:** 401 <br />
    **Message:** User is inactive

## **Passwordtoken**

Change a pashouder password using a PasswordToken

- **URL**

  /token/v1/changepassword

- **Method:**

  `POST`

- **Headers**

  **Required:**

  `Authorization` (type: bearer | using a PasswordToken)

- **URL Params**

  **Required:**

  `login_name=[string]`

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
    {
        "token_type": "PasswordToken",
        "token": "FTUHDoBug9iyiUSiRoujRWZPs74",
        "expiry_date": "2019-09-25T13:40:45.904Z"
    }
    ```

- **Error Response:**

  - **Code:** 400 <br />
    **Message:** Mandatory [login_name] query parameter empty

  - **Code:** 401 <br />
    **Message:** User not found

  - **Code:** 401 <br />
    **Message:** User is inactive
