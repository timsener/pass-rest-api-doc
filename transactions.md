| URI                                                                | Method | Returns                                              |
| ------------------------------------------------------------------ | ------ | ---------------------------------------------------- |
| [/transactions/v1/aanbiedingen](#retrieve-aanbieding-transactions) | `GET`  | retrieve transactions for aanbiedingen for pashouder |
| [/transactions/v1/budget](#retrieve-budget-transactions)           | `GET`  | retrieve transactions for budgetten for pashouder    |

## **Retrieve aanbieding transactions**

Returns json data about aanbieding transactions.

- **URL**

  /transacties/v1/aanbiedingen

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `Authorization` (type: Bearer or AppBearer)

- **URL Params**

  **Optional:**

  `sub_transactions=[boolean]` (include transactions for subpashouders >> default: false)

  `date_from=[date]` filter transactions by transaction date from, ie. '2020-01-01'

  `date_until=[date]` filter transactions by transaction date until, ie. '2020-12-31'

  `pasnummer=[string]` filter transactions by pas

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
    {
        "number_of_items": 20,
        "total_items:" 36,
        "transacties": [
            {
                "id": 4119,
                "transactiedatum": "2019-10-28T00:00:00.000Z",
                "verleende_korting": 5.5,
                "pashouder": {
                    "id": 3561,
                    "hoofd_pashouder_id": 3559
                },
                "leeftijd_pashouder": 35,
                "pas": {
                    "id": 3620,
                    "pasnummer": 70498534,
                    "pasnummer_volledig": "6064367007870498534",
                    "originele_pas": {
                        "id": 3620,
                        "pasnummer": 70498534,
                        "pasnummer_volledig": "6064367007870498534"
                    }
                },
                "aanbieding": {
                    "id": 339,
                    "aanbiedingnummer": 1002,
                    "publicatienummer": 8,
                    "kortingzin": "1x 25% korting op op een portie poffertjes naar keuze",
                    "omschrijving": "Poffertjes lekker",
                    "communicatienaam": "Visser's Poffertjes",
                    "pijler": "Horeca",
                    "aanbieder": {
                        "id": 100043
                    },
                    "afbeeldingen": [
                        {
                            "id": 1086,
                            "cdn_url": "https://images.intermediadpas.nl/dordrecht/acc/67_web-small20191029140510.jpg",
                            "medium": "Web",
                            "size": "Small"
                        },
                        {
                            "id": 1084,
                            "cdn_url": "https://images.intermediadpas.nl/dordrecht/acc/67_web-large20191029140509.jpg",
                            "medium": "Web",
                            "size": "Large"
                        }
                    ]
                }
            }
        ]
    }
    ```

## **Retrieve budget transactions**

Returns json data about budget transactions.

- **URL**

  /transacties/v1/budget

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `Authorization` (type: bearer)

- **URL Params**

  **Optional:**

  `sub_transactions=[boolean]` (include transactions for subpashouders >> default: false)

  `date_from=[date]` filter transactions by transaction date from, ie. '2020-01-01'

  `date_until=[date]` filter transactions by transaction date until, ie. '2020-12-31'

  `budgetcode=[string]` filter transactions by budgetcode

  `pasnummer=[string]` filter transactions by pas

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
    {
        "number_of_items": 20,
        "total_items:" 42,
        "transacties": [
            {
                "id": 137,
                "transactiedatum": "2017-10-05T12:58:20.0000000",
                "bedrag": 20.0,
                "pashouder": {
                    "id": 1232,
                    "hoofd_pashouder_id": 53243
                },
                "pas": {
                    "id": 14316,
                    "pasnummer": 6903031370805,
                    "pasnummer_volledig": "36064366903031370803",
                    "originele_pas": {
                        "id": 14316,
                        "pasnummer": 6903031370805,
                        "pasnummer_volledig": "36064366903031370803"
                    }
                },
                "budget": {
                    "id": 44,
                    "code": "GPAS05_19",
                    "naam": "Schoolactiviteiten",
                    "aanbieder": {
                        "id": 200109,
                        "naam": "Fietsenwinkel - Bigline B.V."
                    }
                }
            }
        ]
    }
    ```
