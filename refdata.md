| URI                                                                | Method | Returns                                              |
| ------------------------------------------------------------------ | ------ | ---------------------------------------------------- |
| [/refdata/v1/paymentmethods](#retrieve-payment-methods)            | `GET`  | retrieve payment methods and related issuers         |
| [/refdata/v1/passwordrules](#retrieve-password-rules)               | `GET` | retrieve the currently valid password rules          |

## **Retrieve payment methods**

Returns json data about payment methods

- **URL**

  /refdata/v1/paymentmethods

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `API-Key` 

- **URL Params**

  None

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
    {
    "number_of_items": 1,
    "methods": [
        {
            "id": "ideal",
            "description": "iDEAL",
            "image": "https://www.mollie.com/external/icons/payment-methods/ideal.svg",
            "issuers": [
                {
                    "id": "ideal_ABNANL2A",
                    "name": "iDEAL",
                    "image": "https://www.mollie.com/external/icons/ideal-issuers/ABNANL2A.svg"
                },
                {
                    "id": "ideal_INGBNL2A",
                    "name": "iDEAL",
                    "image": "https://www.mollie.com/external/icons/ideal-issuers/INGBNL2A.svg"
                },
                {
                    "id": "ideal_RABONL2U",
                    "name": "iDEAL",
                    "image": "https://www.mollie.com/external/icons/ideal-issuers/RABONL2U.svg"
                },
                {
                    "id": "ideal_ASNBNL21",
                    "name": "iDEAL",
                    "image": "https://www.mollie.com/external/icons/ideal-issuers/ASNBNL21.svg"
                },
                {
                    "id": "ideal_BUNQNL2A",
                    "name": "iDEAL",
                    "image": "https://www.mollie.com/external/icons/ideal-issuers/BUNQNL2A.svg"
                },
                {
                    "id": "ideal_HANDNL2A",
                    "name": "iDEAL",
                    "image": "https://www.mollie.com/external/icons/ideal-issuers/HANDNL2A.svg"
                },
                {
                    "id": "ideal_KNABNL2H",
                    "name": "iDEAL",
                    "image": "https://www.mollie.com/external/icons/ideal-issuers/KNABNL2H.svg"
                },
                {
                    "id": "ideal_RBRBNL21",
                    "name": "iDEAL",
                    "image": "https://www.mollie.com/external/icons/ideal-issuers/RBRBNL21.svg"
                },
                {
                    "id": "ideal_REVOLT21",
                    "name": "iDEAL",
                    "image": "https://www.mollie.com/external/icons/ideal-issuers/REVOLT21.svg"
                },
                {
                    "id": "ideal_SNSBNL2A",
                    "name": "iDEAL",
                    "image": "https://www.mollie.com/external/icons/ideal-issuers/SNSBNL2A.svg"
                },
                {
                    "id": "ideal_TRIONL2U",
                    "name": "iDEAL",
                    "image": "https://www.mollie.com/external/icons/ideal-issuers/TRIONL2U.svg"
                },
                {
                    "id": "ideal_FVLBNL22",
                    "name": "iDEAL",
                    "image": "https://www.mollie.com/external/icons/ideal-issuers/FVLBNL22.svg"
                }
            ]
        }
    ]
}
```

## **Retrieve password rules**

Returns json data about the currently valid password rules

- **URL**

  /refdata/v1/passwordrules

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `API-Key` 

- **URL Params**

  None

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
{
        "minimum_chars": 8,
        "require_upper_case": true,
        "require_lower_case": true,
        "require_numeric": true,
        "require_special": true,
        "disallow_username": true
}
```

- **Error Response:**

  - **Code:** 406 <br />
    **Message:** No card organization found
	
  - **Code:** 406 <br />
    **Message:** No API config found
	
  - **Code:** 406 <br />
    **Message:** No password rules found
	
	