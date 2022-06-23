| URI                                                                | Method | Returns                                              |
| ------------------------------------------------------------------ | ------ | ---------------------------------------------------- |
| [/refdata/v1/paymentmethods](#retrieve-payment-methods)            | `GET`  | retrieve payment methods and related issuers         |
| [/refdata/v1/verkooppunten](#retrieve-verkooppunten)               | `GET`  | retrieve verkooppunten and related gemeente          |
| [/refdata/v1/pastarieven](#retrieve-pastarieven)                   | `GET`  | retrieve pastarieven bij verkooppunt                 |

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
    }```

## **Retrieve verkooppunten**

Retourneert json data m.b.t. online sales verkooppunten en hun gemeenten.
Daarnaast bevat het informatie betreffende de mogelijk van losse verkoop van passen aan gezinsleden en de aanwezigheid van een actieve BRP connectie.

- **URL**

  /refdata/v1/verkooppunten

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
        "number_of_items": 3,
        "verkooppunten": [
            {
                "verkooppunt_number": 91,
                "verkooppunt_name": "Internet Lokatie01",
                "gemeente_code": "0599",
                "gemeente_name": "Rotterdam",
                "has_brp": true,
                "has_single_sale": false,
                "sort_order": 1
            },
            {
                "verkooppunt_number": 92,
                "verkooppunt_name": "Internet Lokatie02",
                "gemeente_code": "0502",
                "gemeente_name": "Capelle aan den IJssel",
                "has_brp": true,
                "has_single_sale": false,
                "sort_order": 2
            },
            {
                "verkooppunt_number": 93,
                "verkooppunt_name": "Internet Lokatie03",
                "gemeente_code": "0606",
                "gemeente_name": "Schiedam",
                "has_brp": false,
                "has_single_sale": false,
                "sort_order": 3
            }
        ]
    }

## **Retrieve pastarieven**

Retourneert json data m.b.t.de voor een verkooppunt geldende tarieven binnen een pasjaar.

- **URL**

  /refdata/v1/pastarieven

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `API-Key` 

- **URL Params**

  **Required:**

  verkooppunt_nummer <br />
  pasjaar

  **Optional:**
  
  categorie_code

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
    {
        "verkooppunt_nummer": 91,
        "verkooppunt_naam": "Internet Lokatie01",
        "number_of_items": 3,
        "categorieen": [
                    {
                "categorie_code": "A",
                "categorie_naam": "Volwassenen met een minimuminkomen",
                "is_reductietarief": true,
                "is_standaardtarief": false,
                "kindcategorie_code": "E",
                "meerdere_passen": false,
                "alle_leeftijden": false,
                "leeftijd_van": 18,
                "number_of_items": 2,
                "tarieven": [
                    {
                        "pascategorie": "Origineel",
                        "verkoopprijs": 5
                    },
                    {
                        "pascategorie": "Duplicaat",
                        "verkoopprijs": 2.5
                    }
                ]
            },
            {
                "categorie_code": "B",
                "categorie_naam": "65-plussers boven de inkomensgrens",
                "is_reductietarief": false,
                "is_standaardtarief": false,
                "kindcategorie_code": "K",
                "meerdere_passen": false,
                "alle_leeftijden": false,
                "leeftijd_van": 65,
                "number_of_items": 2,
                "tarieven": [
                    {
                        "pascategorie": "Origineel",
                        "verkoopprijs": 20
                    },
                    {
                        "pascategorie": "Duplicaat",
                        "verkoopprijs": 2.5
                    }
                ]
            },
            {
                "categorie_code": "C",
                "categorie_naam": "Volwassenen boven de inkomensgrens",
                "is_reductietarief": false,
                "is_standaardtarief": true,
                "kindcategorie_code": "K",
                "meerdere_passen": true,
                "alle_leeftijden": true,
                "number_of_items": 2,
                "tarieven": [
                    {
                        "pascategorie": "Origineel",
                        "verkoopprijs": 60
                    },
                    {
                        "pascategorie": "Duplicaat",
                        "verkoopprijs": 2.5
                    }
                ]
            },
            {
                "categorie_code": "E",
                "categorie_naam": "Kinderen 3 t/m 17 jr wier ouders een A-pas kopen",
                "is_reductietarief": true,
                "is_standaardtarief": false,
                "meerdere_passen": false,
                "alle_leeftijden": false,
                "leeftijd_tm": 17,
                "number_of_items": 2,
                "tarieven": [
                    {
                        "pascategorie": "Origineel",
                        "verkoopprijs": 0
                    },
                    {
                        "pascategorie": "Duplicaat",
                        "verkoopprijs": 2.5
                    }
                ]
            }
        ]
    }
```
