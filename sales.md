| URI                                        | Method | Returns                             |
| ------------------------------------------ | ------ | ----------------------------------- |
| [/sales/v1/pashouder](#retrieve-pashouder) | `GET`  | retrieve pashouder details by token |
| [/sales/v1/pashouder](#update-pashouder)   | `POST` | update pashouder by token           |

## **Retrieve pashouder**

Returns json data about pashouder.

- **URL**

  /sales/v1/pashouder

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `Authorization` (type: bearer)

- **URL Params**

  **Optional:**

  `addsubs=[boolean]` (include subpashouder >> default: false)

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
    {
        "id": 1234567890,
        "login_name": "john.doe@gmail.com",
        "voornaam": "John",
        "initialen": "J",
        "tussenvoegsel": "",
        "achternaam": "Doe",
        "volledige_naam": "J. Doe",
        "telefoon_nummer": "020-1234567",
        "mobiel_nummer": "06-12345678",
        "email_adres": "john.doe@gmail.com",
        "geslacht": "Man",
        "geboortedatum": "1974-06-14T00:00:00.0000000",
        "foto_cdn_url": "https://cdn.intermediad.nl/content/xKLDKyuN6L8OY",
        "adressen": [
            {
                "id": 3213,
                "adres_type": "Woonadres",
                "straat": "Leidsestraat",
                "huisnummer": "20",
                "postcode": "1100AB",
                "plaats": {
                    "id": 3921,
                    "naam": "Amsterdam",
                    "gemeente": "Amsterdam"
                }
            }
        ],
        "hoofd_pashouder": {
            "voornaam": "John",
            "initialen": "J",
            "tussenvoegsel": "",
            "achternaam": "Doe",
            "volledige_naam": "J. Doe"
        },
        "passen": [
            {
                "id": 1234567890,
                "pasnummer": 690301232131,
                "pasnummer_volledig": "64030690301232131",
                "actief": true,
                "originele_pas": {
                    "id": 1234567890,
                    "pasnummer": 690301862131,
                    "pasnummer_volledig": "64030690301862131",
                    "geldigheid": [
                        {
                            "geldig_vanaf": "2019-01-01T00:00:00.0000000",
                            "geldig_tm": "2019-12-31T00:00:00.0000000"
                        }
                    ]
                },
                "geldigheid": [
                    {
                        "geldig_vanaf": "2019-01-01T00:00:00.0000000",
                        "geldig_tm": "2019-12-31T00:00:00.0000000"
                    }
                ]
            }
        ],
        "sub_pashouders": [
            {
                "id": 1234567890,
                "voornaam": "John",
                "initialen": "J",
                "tussenvoegsel": "",
                "achternaam": "Doe",
                "volledige_naam": "J. Doe",
                "telefoon_nummer": "020-1234567",
                "mobiel_nummer": "06-12345678",
                "email_adres": "john.doe@gmail.com",
                "geslacht": "Man",
                "geboortedatum": "1974-06-14T00:00:00.0000000",
                "foto_cdn_url": "https://cdn.intermediad.nl/content/xKLDKyuN6L8OY",
                "passen": [
                    {
                        "id": 1234567890,
                        "pasnummer": 690301232131,
                        "pasnummer_volledig": "64030690301232131",
                        "actief": true,
                        "originele_pas": {
                            "id": 1234567890,
                            "pasnummer": 690301862131,
                            "pasnummer_volledig": "64030690301862131",
                            "geldigheid": [
                                {
                                    "geldig_vanaf": "2019-01-01T00:00:00.0000000",
                                    "geldig_tm": "2019-12-31T00:00:00.0000000"
                                }
                            ]
                        },
                        "geldigheid": [
                            {
                                "geldig_vanaf": "2019-01-01T00:00:00.0000000",
                                "geldig_tm": "2019-12-31T00:00:00.0000000"
                            }
                        ]
                    }
                ]
            }
        ]
    }
    ```

## **Update pashouder**

Updates pashouder and return json data about pashouder

- **URL**

  /sales/v1/pashouder

- **Method:**

  `POST`

- **Headers**

  **Required:**

  `Authorization` (type: bearer)

- **URL Params**

  None

- **Data Params**

  Minimum of one and any combination of any of the attributes in the JSON body below.

  ```javascript
  {
    "login_name": "j.doe@gmail.com",
    "password": "s0m3$3cr3T",
    "voornaam": "John",
    "initialen": "J",
    "tussenvoegsel": "",
    "achternaam": "Doe",
    "telefoon_nummer": "0201234567",
    "mobiel_nummer": "0612345678",
    "email_adres": "j.doe@gmail.com"
  }
  ```

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    OR
  - **Code:** 204 <br />
    **Message:** geen wijzigingen gevonden<br />
    **Description:** returns same data as Retrieve pashouder operation but with updated data <br />

    **Content:**

    ```javascript
    {
        "id": 1234567890,
        "login_name": "john.doe@gmail.com",
        "voornaam": "John",
        ...
    ```

    see [/sales/v1/pashouder](#retrieve-pashouder) for pashouder entity details

- **Error Response:**

  - **Code:** 404 <br />
    **Message:** Token niet gerelateerd aan pashouder

  - **Code:** 422 <br />
    **Message:** Login naam niet uniek

  - **Code:** 422 <br />
    **Message:** Wachtwoord voldoet niet aan eisen - (8 karakters, 1 hoofdletter, 1 kleine letter, 1 speciaal karakter en 1 numeriek karakter)

  - **Code:** 422 <br />
    **Message:** Login naam niet uniek
