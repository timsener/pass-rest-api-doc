| URI                                                 | Method | Returns                            |
| --------------------------------------------------- | ------ | ---------------------------------- |
| [/aanbod/v1/aanbiedingen](#retrieve-aanbiedingen)   | `GET`  | retrieve a list of aanbiedingen    |
| [/aanbod/v1/aanbiedingen/:id](#retrieve-aanbieding) | `GET`  | retrieve a single aanbieding by id |

## **Retrieve aanbiedingen**

Returns json data about aanbiedingen.

- **URL**

  /aanbod/v1/aanbiedingen

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `API-Key`

- **URL Params**

  **Optional:**

  `limit=[integer]` <br /> `offset=[integer]` <br /> `aanbieding_nummer=[integer]` <br /> `valid_on_or_after=[date i.e. 2020-12-01]` <br />

- **Success Response:**

  - **Code:** 200 <br />
    **Content:**

    ```javascript
    {
        "number_of_items": 1,
        "aanbiedingen": [
            {
                "id": 1234567890,
                "aanbiedingnummer": 100025,
                "publicatienummer": 1321094,
                "aanbieding_type": "sequal"
                ...
    ```

    see [/aanbod/v1/aanbiedingen/:aanbiedingnummer](#retrieve-aanbieding) for aanbieding entity details

## **Retrieve aanbieding**

Returns json data about an aanbieding.

- **URL**

  /aanbod/v1/aanbiedingen/:aanbiedingnummer

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `API-Key`

- **URL Params**

  None

- **Success Response:**

  - **Code:** 200 <br />
    **Content:**

    ```json
    {
      "id": 1234567890,
      "aanbiedingnummer": 100025,
      "publicatienummer": 1321094,
      "aanbieding_type": "sequal",
      "inwisselbaarheid": "Eenmalig",
      "communicatie_naam": "Dagje uit",
      "actie_soort": "Kortingsactie",
      "actie_jaar": 2019,
      "pijler": "Cultuur",
      "titel": "Volksbuurtmuseum",
      "beschrijving": "Maak er kennis met twee eeuwen dagelijks leven van gewone mensen in Nederland.",
      "beschrijving_html": "Maak er kennis met twee eeuwen dagelijks leven van gewone mensen in Nederland.",
      "publicatie_datum": "2019-06-14T00:00:00.0000000",
      "start_datum": "2019-07-01T00:00:00.0000000",
      "eind_datum": "2020-06-30T00:00:00.0000000",
      "kortingszin": "Onbeperkt gratis toegang museum",
      "meer_info_url": "https://www.volksbuurtmuseum.nl",
      "meer_info_telnr": "0302318292",
      "meer_info_email": "info@volksbuurtmuseum.nl",
      "meer_info_wanneer": "alle openingstijden",
      "reserveren_url": "",
      "reserveren_telnr": "",
      "reserveren_email": "",
      "reserveren_info": "",
      "reserveren_info_html": "",
      "pashouder_tips": "",
      "pashouder_tip_html_": "",
      "mag_uitgelicht_worden": true,
      "is_dezelfde_dag_inwisselbaar": true,
      "offline_verzilvering": true,
      "online_verzilvering": true,
      "online_verzilveringswijze": "Kortingscode", // { Kortingscode, PasnummerEnBeveiligingscode }
      "online_verzilveringsurl": "https://intermediad.nl/webshop/x",
      "aanbieders": [
        {
          "id": 1042,
          "naam": "Nederlands Volksbuurtmuseum",
          "url": "http://www.volksbuurtmuseum.nl",
          "telnr": "0302318292",
          "email": "lysette@volksbuurtmuseum.nl",
          "straat": "Waterstraat",
          "huisnummer": "27a",
          "postcode": "3511BW",
          "plaats": "Utrecht",
          "afbeeldingen": [
            {
              "id": 3297,
              "name": "afbeelding_web_groot_03.png",
              "cdn_url": "https://cdn.intermediad.com/afbeelding_web_groot_03.png",
              "medium": "Web",
              "size": "Groot"
            }
          ],
          "locaties": [
            {
              "id": 3943,
              "titel": "Volksbuurtmuseum",
              "straat": "Waterstraat",
              "huisnummer": "27a",
              "postcode": "3511BW",
              "latitude": 52.095262,
              "longitude": 5.114757,
              "plaats": {
                "id": 3214,
                "naam": "Utrecht",
                "gemeente": "Amsterdam",
                "gemeentecode": "0363"
              }
            }
          ],
          "tarieven": [
            {
              "id": 7322,
              "label": "Leeftijd 4 t/m 12 jaar",
              "alle_leeftijden": false,
              "minimum_leeftijd": 4,
              "maximum_leeftijd": 12,
              "voorbeeld_tarief": false,
              "normaal_tarief": 5.0,
              "korting_type": "Percentage",
              "percentage": 40.0,
              "bedrag": 2.0,
              "korting_tarief": 3.0
            }
          ]
        }
      ],
      "tarieven": [
        {
          "id": 6429,
          "label": "Leeftijd 4 t/m 12 jaar",
          "alle_leeftijden": false,
          "minimum_leeftijd": 4,
          "maximum_leeftijd": 12,
          "voorbeeld_tarief": false,
          "normaal_tarief": 5.0,
          "korting_type": "Percentage",
          "percentage": 20.0,
          "bedrag": 1.0,
          "korting_tarief": 4.0
        }
      ],
      "locaties": [
        {
          "id": 3943,
          "titel": "Volksbuurtmuseum",
          "straat": "Waterstraat",
          "huisnummer": "27a",
          "postcode": "3511BW",
          "latitude": 52.095262,
          "longitude": 5.114757,
          "plaats": {
            "id": 3214,
            "naam": "Utrecht",
            "gemeente": "Amsterdam",
            "gemeentecode": "0363"
          }
        }
      ],
      "aanbodtags": [
        {
          "id": 521,
          "naam": "Binnen",
          "is_filter": true,
          "sort_order": 10
        }
      ],
      "doelgroepen": [
        {
          "id": 521,
          "naam": "Binnen",
          "sort_order": 10
        }
      ],
      "afbeeldingen": [
        {
          "id": 3291,
          "name": "afbeelding_web_groot_01.png",
          "cdn_url": "https://cdn.intermediad.com/afbeelding_web_groot_01.png",
          "medium": "Web",
          "size": "Groot"
        }
      ],
      "aanbodlink": {
        "id": 832,
        "naam": "Andere aanbieding",
        "kortingszin": "Onbeperkt gratis toegang museum 65+"
      }
    }
    ```
