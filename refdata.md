| URI                                                                | Method | Returns                                              |
| ------------------------------------------------------------------ | ------ | ---------------------------------------------------- |
| [/refdata/v1/paymentmethods](#retrieve-payment-methods)            | `GET`  | retrieve payment methods and related issuers         |

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
                    "id": "ideal_ABC22",
                    "name": "iDEAL",
                    "image": "https://www.mollie.com/external/icons/ideal-issuers/FVLBNL22.svg"
                }
            ]
        }
    ]
}
```