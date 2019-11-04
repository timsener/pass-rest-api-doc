| URI                                                | Method | Returns                             |
| -------------------------------------------------- | ------ | ----------------------------------- |
| [/sales/v1/pashouder](#retrieve-pashouder)         | `GET`  | retrieve pashouder details by token |
| [/sales/v1/pashouder](#update-pashouder)           | `POST` | update pashouder by token           |
| [/sales/v1/registerpashouder](#register-pashouder) | `POST` | register pashouder to account       |

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
        "has_account": true,
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
    
- **Error Response:**

  - **Code:** 404 <br />
    **Message:** Token not related to pashouder


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
    "password_current": "curr3ntp@ss",
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
    **Message:** No changes found<br />

    **Description:** returns same data as Retrieve pashouder operation but with updated data <br />

    **Content:**

    ```javascript
    {
        "id": 1234567890,
        "has_account": true,
        "login_name": "john.doe@gmail.com",
        "voornaam": "John",
        ...
    ```

    see [/sales/v1/pashouder](#retrieve-pashouder) for pashouder entity details

- **Error Response:**

  - **Code:** 404 <br />
    **Message:** Token not related to pashouder

  - **Code:** 406 <br />
    **Message:** Login name already taken

  - **Code:** 406 <br />
    **Message:** Current password is not valid {password_current}

  - **Code:** 406 <br />
    **Message:** Password not valid. A password needs to consist of: (8 characters, 1 uppercase, 1 lowercase, 1 special en 1 numeric character)

## **Register pashouder**

Register account on existing pashouder

- **URL**

  /sales/v1/registerashouder

- **Method:**

  `POST`

- **Headers**

  **Required:**

  `API-Key`

- **URL Params**

  None

- **Data Params**

  All elements in the following body are required. {id} refers to the pashouder id to which the account needs to be registered.

  ```javascript
    {
        "id": 1234567890,
        "login_name": "john.doe@gmail.com",
        "password": "$0m35ecr3T"
    }
  ```

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />

    **Description:** returns same data as Retrieve pashouder operation but with updated data <br />

    **Content:**

    ```javascript
    {
        "id": 1234567890,
        "has_account": true,
        "login_name": "john.doe@gmail.com",
        "voornaam": "John",
        ...
    ```

    see [/sales/v1/pashouder](#retrieve-pashouder) for pashouder entity details

- **Error Response:**

  - **Code:** 406 <br />
    **Message:** {id} attribute missing or empty

  - **Code:** 406 <br />
    **Message:** Pashouder not found for {id}: XXXXXXX

  - **Code:** 406 <br />
    **Message:** {login_name} is empty or missing

  - **Code:** 406 <br />
    **Message:** {login_name} already taken

  - **Code:** 406 <br />
    **Message:** {password} is empty or missing

  - **Code:** 406 <br />
    **Message:** {password} not valid: [message containing invalid properties in nl_NL]
