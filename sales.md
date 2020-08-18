| URI                                                | Method | Returns                             |
| -------------------------------------------------- | ------ | ----------------------------------- |
| [/sales/v1/pashouder](#retrieve-pashouder)         | `GET`  | retrieve pashouder details by token |
| [/sales/v1/pashouder](#update-pashouder)           | `POST` | update pashouder by token           |
| [/sales/v1/registerpashouder](#register-pashouder) | `POST` | register pashouder to account       |
| [/sales/v1/pas](#retrieve-pas)                     | `GET`  | retrieve pas details by pasnummer   |
| [/sales/v1/togglepas](#toggle-pas)                 | `POST` | toggle pas status (block/unblock)   |

## **Retrieve pashouder**

Returns json data about pashouder.

- **URL**

  /sales/v1/pashouder

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `Authorization` (type: Bearer or AppBearer)

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
        "emailadres": "john.doe@gmail.com",
        "geslacht": "Man",
        "geboortedatum": "1974-06-14T00:00:00.0000000",
        "mailing": true,
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
            },
            {
                "id": 3213,
                "adres_type": "Postadres",
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
                "emailadres": "john.doe@gmail.com",
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

  `Authorization` (type: Bearer or AppBearer)

- **URL Params**

  None

- **Data Params**

  Minimum of one and any combination of any of the root attributes in the JSON body below with the exception of {password} and {password_current} which always need to be combined

  ```javascript
  {
    "login_name": "j.doe@gmail.com",
    "password": "s0m3$3cr3T",
    "password_current": "curr3ntp@ss", // required in combination with {password}
    "voornaam": "John",
    "initialen": "J",
    "tussenvoegsel": "",
    "achternaam": "Doe",
    "telefoon_nummer": "0201234567",
    "mobiel_nummer": "0612345678",
    "emailadres": "j.doe@gmail.com",
    "mailing_strbool": "true",        // string boolean used to avoid unwanted changes in mapping (regular empty boolean results in false)
    "adressen": [
      {
        "adres_type": "Postadres",
        "straat": "Spuiboulevard",
        "huisnummer": 300,
        "huisnummer_letter": "",
        "huisnummer_toevoeging": "",
        "postcode": "3311GJ",
        "plaatsnaam": "Dordrecht"
      }
    ]
  }
  ```

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    OR
  - **Code:** 204 <br />
    **Message:** No changes found<br />

    **Description:** returns same data as Retrieve pashouder operation but with updated data - no data is returned if no changes were found <br />

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

  Elements {pashouder_id} or {pasnummer} combined with {geboortedatum} are required to identify an existing pashouder for account registration. {login_name} and {passowrd} are required to execute the registration.

  ```javascript
    {
        "pashouder_id": "050523913912",
        "pasnummer": 95064162,
        "geboortedatum": "1974-06-14T00:00:00.000Z",
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
    **Message:** Either {pashouder_id} or a combination of {geboortedatum} and {pasnummer} attributes are mandatory and are missing or empty

  - **Code:** 406 <br />
    **Message:** Pashouder not found for {pashouder_id}: XXXXXX and {pasnummer}: XXXXXX

  - **Code:** 406 <br />
    **Message:** {login_name} is empty or missing

  - **Code:** 406 <br />
    **Message:** {login_name} already taken

  - **Code:** 406 <br />
    **Message:** {password} is empty or missing

  - **Code:** 406 <br />
    **Message:** {password} not valid: [message containing invalid properties in nl_NL]

## **Retrieve pas**

Returns json data about pas.

- **URL**

  /sales/v1/pas/{pasnummer}

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `Authorization` (type: Bearer or AppBearer)

- **URL Params**

  **Required**

  `pasnummer=XXXXXX`

  **Optional:**

  `include_balance=[boolean]` (include card balance information >> default: false)

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
    {
        "id": 3618,
        "pasnummer": 43635824,
        "pasnummer_volledig": "6064367007843635824",
        "categorie_code": "C",
        "categorie": "Standaardpas",
        "balance": 250,
        "balance_update_time": "2019-10-28T19:41:08.000Z",
        "actief": true,
        "passoort": {
            "id": 5,
            "naam": "Dordtpas"
        },
        "geldigheid": [
            {
                "geldig_vanaf": "2019-09-30T22:00:00.000Z",
                "geldig_tm": "2020-12-31T22:59:59.000Z"
            }
        ],
        "budgetten": [
            {
                "code": "TESTBUDGET",
                "omschrijving": "Budget tbv testen",
                "budget_assigned": 300.00,
                "budget_balance": 250.00
            }
        ]
    }
    ```

- **Error Response:**

  - **Code:** 404 <br />
    **Message:** Pas not found for pasnummer: XXXXXXXX

## **Toggle pas**

Toggle pas status (block/unblock)

- **URL**

  /sales/v1/togglepas/{pasnummer}

- **Method:**

  `POST`

- **Headers**

  **Required:**

  `Authorization` (type: Bearer or AppBearer)

- **URL Params**

  **Required:**

  `pasnummer`

- **Data Params**

  None

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />

    **Description:** returns same data as Get pas operation but with updated status <br />

    **Content:**

    ```javascript
        {
        "id": 3618,
        "pasnummer": 43635824,
        "pasnummer_volledig": "6064367007843635824",
        "categorie_code": "C",
        ...
    ```

    see [/sales/v1/pas](#retrieve-pas) for pas entity details

- **Error Response:**

  - **Code:** 404 <br />
    **Message:** Pas not found for pasnummer: XXXXXX

  - **Code:** 406 <br />
    **Message:** Pas has been replaced - status cannot be changed

  - **Code:** 406 <br />
    **Message:** Error occurred while trying to change pas status
