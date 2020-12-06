| URI                                           | Method | Returns               |
| --------------------------------------------- | ------ | --------------------- |
| [/data/v1/fulfilment](#add-fulfilment-data)   | `POST` | add fulfilment data   |

## **Add fulfilment data**

Add fulfilment data to be processed.

- **URL**

  /data/v1/fulfilment

- **Method:**

  `POST`

- **Headers**

  **Required:**

  `API-Key`

- **Data params**

  ```javascript
  {
    "hoofdpashouder": {
        "gemeentecode": "0363",
        "adminnummer": "1"
    },
    "pashouder": {
        "gemeentecode": "0363",
        "adminnummer": "1",
        "voorletters": "J",
        "voornaam": "John",
        "tussenvoegsel": "",
        "geboortenaam": "Doe",
        "naamkeuze": "E",
        "partnernaam": "",
        "partnertussenvoegsel": "",
        "geslacht": "M",
        "geboortedatum": "2002-01-01T00:00:00.0000000",
        "datumoverlijden": "2020-12-01T00:00:00.0000000",
        "gegevensgeheim": false
    },
    "verblijfsadres": {
        "straatnaam": "Straatweg",
        "huisnummer": 100,
        "huisletter": "A",
        "huisnummer_toevoeging": "Kamer 12",
        "postcode": "1100AA",
        "plaatsnaam": "Amsterdam"
    },
    "postadres": {
        "straatnaam": "Straatweg",
        "huisnummer": 100,
        "huisletter": "A",
        "huisnummer_toevoeging": "Kamer 12",
        "postcode": "1100AA",
        "plaatsnaam": "Amsterdam"
    },
    "voorzieningen": [
        {
            "code": "MINIMA",
            "omschrijving": "Minima Stadspas",
            "datumvanaf": "2020-09-01T00:00:00.0000000",
            "datumtm": "2021-08-30T23:59:59.0000000"
        }
    ]
  }
  ```

- **Message definition:**

| Name                                | Type        | Optional | Additional information |
| :---------------------------------- | :---------- | :-- | :--------------- |
| _`hoofdpashouder`_                  | object      | Yes |
| &nbsp;&nbsp;`gemeentcode`           | string(4)   |     |
| &nbsp;&nbsp;`adminnummer`           | string(15)  |     |
| _`pashouder`_                       | object      |     |
| &nbsp;&nbsp;`gemeentcode`           | string(4)   |     |
| &nbsp;&nbsp;`adminnummer`           | string(15)  |     |
| &nbsp;&nbsp;`voorletters`           | string(20)  |     |
| &nbsp;&nbsp;`voornaam`              | string(200) | Yes |
| &nbsp;&nbsp;`tussenvoegsel`         | string(50)  | Yes |
| &nbsp;&nbsp;`geboortenaam`          | string(100) |     |
| &nbsp;&nbsp;`naamkeuze`             | string enum |     | { E, P, N, V} resp. (Eigennaam, Partnernaam, Partnernaam na eigennaam, Partnernaam voor eigennaam
| &nbsp;&nbsp;`partnernaam`           | string(100) | Yes |
| &nbsp;&nbsp;`partnertussenvoegsel`  | string(50)  | Yes |
| &nbsp;&nbsp;`geslacht`              | string enum | Yes | { M, F, U } resp. (Male, Female, Unknown)
| &nbsp;&nbsp;`geboortedatum`         | string date | Yes | ie `1974-06-14T00:00:00.000Z` as per ISO 8601
| &nbsp;&nbsp;`datumoverlijden`       | string date |     | ie `1974-06-14T00:00:00.000Z` as per ISO 8601
| &nbsp;&nbsp;`gegevensgeheim`        | boolean     |     |
| _`verblijfsadres`_                  | object      |     |
| &nbsp;&nbsp;`straatnaam`            | string(100) |     |
| &nbsp;&nbsp;`huisnummer`            | integer     |     |
| &nbsp;&nbsp;`huisletter`            | string(1)   | Yes |
| &nbsp;&nbsp;`huisnummer_toevoeging` | string(15)  | Yes |
| &nbsp;&nbsp;`postcode`              | string(6)   |     | ie 1100 AA
| &nbsp;&nbsp;`plaatsnaam`            | string(50)  |     |
| _`postadres`_                       | object      | Yes |
| &nbsp;&nbsp;`straatnaam`            | string(100) |     |
| &nbsp;&nbsp;`huisnummer`            | integer     |     |
| &nbsp;&nbsp;`huisletter`            | string(1)   | Yes |
| &nbsp;&nbsp;`huisnummer_toevoeging` | string(15)  | Yes |
| &nbsp;&nbsp;`postcode`              | string(6)   |     | ie 1100 AA
| &nbsp;&nbsp;`plaatsnaam`            | string(50)  |     |
| _`voorzieningen`_                   | object arr  | Yes |
| &nbsp;&nbsp;`code`                  | string(10)  |     |
| &nbsp;&nbsp;`omschrijving`          | string(200) | Yes |
| &nbsp;&nbsp;`datumvanaf`            | string date |     |
| &nbsp;&nbsp;`datumtm`               | string date |     |

- **Success Response:**

  A typical response consists of a http status code and message.

  - **Code:** 200 <br />
    **Content:**

  ```javascript
  {
    "result": {
        "code": 200,
        "message": "Data received for {adminnummer}: 1"
    }
  }
  ```

- **Error Response:**

  - **Code:** 401<br />
    **Message:** APIKey missing (provide a header "API-Key" with a valid key)

  - **Code:** 401<br />
    **Message:** API key invalid

  - **Code:** 401<br />
    **Message:** API key inactive

  - **Code:** 406<br />
    **Message:** [several data validation related messages]
