| URI                                                                   | Method | Returns                          |
| --------------------------------------------------------------------- | ------ | -------------------------------- |
| [/aanbod/v1/activiteiten](#retrieve-activiteiten)                     | GET    | list of activiteiten             |
| [/aanbod/v1/activiteiten/:id](#retrieve-activiteit)                   | GET    | single activiteit by id          |
| [/aanbod/v1/aanbiederactiviteiten](#retrieve-aanbiederactiviteiten)   | GET    | list of aanbiederactiviteiten    |
| [/aanbod/v1/aanbiederactiviteiten/:id](#retrieve-aanbiederactiviteit) | GET    | single aanbiederactiviteit by id |

## **Retrieve activiteiten**

Returns json data about activiteiten.

- **URL**

  /aanbod/v1/aanbiedingen

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `API-Key`

- **URL Params**

  **Optional:**

  `limit=[integer]` <br /> `offset=[integer]` <br /> `activiteit_nummer=[integer]` <br />

- **Success Response:**

  - **Code:** 200 <br />
    **Content:**

  ```javascript
  {
    "number_of_items": 10,
    "activiteiten": [
      {
        "id": 4324,
        "activiteitnummer": 1003,
        ...
  ```

  see [/aanbod/v1/activiteiten/:id](#retrieve-activiteit) for activiteit entity details

## **Retrieve activiteit**

Returns json data about an activiteit.

- **URL**

  /aanbod/v1/activiteiten/:id

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `API-Key`

- **URL Params**

  `:id`

- **Success Response:**

  - **Code:** 200 <br />
    **Content:**

    ```javascript
    {
      "id": 4324,
      "activiteitnummer": 1003,
      "actie_soort": "Activiteit",
      "actie_jaar": 2019,
      "titel": "Sport",
      "pijler": "Sport",
      "startdatum": "2017-07-01T00:00:00.0000000",
      "einddatum": "2020-06-30T00:00:00.0000000",
      "doelgroepen": [
        {
          "id": 984,
          "naam": "12 t/m 18 jaar",
          "sort_order": 10
        }
      ],
      "aanbodtags": [
        {
          "id": 754,
          "naam": "Leuk met kinderen",
          "is_filter": true,
          "sort_order": 20
        }
      ]
    }
    ```

## **Retrieve aanbiederactiviteiten**

Returns json data about aanbiederactiviteiten.

- **URL**

  /aanbod/v1/aanbiederactiviteiten

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `API-Key`

- **URL Params**

  **Required:**

  `aanbieding_nummer=[integer]` **OR** `activiteit_nummer=[integer]`

  **Optional:**

  `limit=[integer]` <br /> `offset=[integer]`

- **Success Response:**

  - **Code:** 200 <br />
    **Content:**

  ```javascript
  {
    "number_of_items": 10,
    "activiteiten": [
      {
        "id": 4324,
        "activiteitnummer": 1003,
        ...
  ```

  see [/aanbod/v1/aanbiederactiviteit/:id](#retrieve-aanbiederactiviteit) for aanbiederactiviteit entity details

## **Retrieve aanbiederactiviteit**

Returns json data about an aanbiederactiviteit.

- **URL**

  /aanbod/v1/aanbiederactiviteiten/:id

- **Method:**

  `GET`

- **Headers**

  **Required:**

  `API-Key`

- **URL Params**

  `:id`

- **Success Response:**

  - **Code:** 200 <br />
    **Content:**

    ```javascript
    {
        "id": 4324,
        "activiteitnummer": 1003,
        "publicatienummer": 321920,
        "titel": "Sport",
        "startdatum": "2017-07-01T00:00:00.0000000",
        "einddatum": "2020-06-30T00:00:00.0000000",
        "meer_info_url": "https://www.volksbuurtmuseum.nl",
        "meer_info_telnr": "0302318292",
        "meer_info_email": "info@volksbuurtmuseum.nl",
        "meer_info_wanneer": "alle openingstijden",
        "reserveren_url": "",
        "reserveren_telnr": "",
        "reserveren_email": "",
        "reserveren_info": "",
        "pashouder_tips": "",
        "aanbieder": {
            "id": 1042,
            "naam": "Nederlands Volksbuurtmuseum",
            "url": "http://www.volksbuurtmuseum.nl",
            "telnr": "0302318292",
            "email": "lysette@volksbuurtmuseum.nl",
            "straat": "Waterstraat",
            "huisnummer": "27a",
            "postcode": "3511BW",
            "plaats": "Utrecht"
        },
        "locaties": [
            {
                "id": 3943,
                "titel": "Volksbuurtmuseum",
                "straat": "Waterstraat",
                "huisnummer": "27a",
                "postcode": "3511BW",
                "gemeente": "Utrecht",
                "latitude": 52.095262,
                "longitude": 5.114757,
                "plaats": {
                    "id": 943,
                    "naam": "Utrecht"
                }
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
        ]
    }
    ```
