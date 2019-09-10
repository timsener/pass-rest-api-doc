**Toon aanbieding**
----
  Returns json data about aanbiedingen.

* **URL**

  /aanbod/v1/aanbiedingen

* **Method:**

  `GET`
  
*  **URL Params**

   **Required:**
 
   `id=[integer]`

* **Data Params**

  None

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{ id : 12, name : "Michael Bloom" }`
 
* **Error Response:**

  * **Code:** 404 NOT FOUND <br />
    **Content:** ```javascript
    {
    "number_of_items": 10,
    "aanbiedingen": [
        {
            "id": 2,
            "aanbiedingnummer": 1000,
            "publicatienummer": 1000,
            "aanbieding_type": "_default",
            "inwisselbaarheid": "One",
            "actie_soort": "Kortingsactie",
            "actie_jaar": 2019,
            "pijler": "Computer",
            "titel": "Testactie",
            "beschrijving": "Dit is een test voor CDN afbeeldingen",
            "publicatie_datum": "2017-05-30T22:00:00.000Z",
            "start_datum": "2019-06-30T22:00:00.000Z",
            "eind_datum": "2020-06-30T21:59:59.000Z",
            "kortingszin": "Dit is een test",
            "meer_info_url": "http://www.ict2b.nl",
            "meer_info_telnr": "0172-436152",
            "meer_info_email": "cees@ict2b.nl",
            "pashouder_tips": "geen",
            "mag_uitgelicht_worden": false,
            "is_dezelfde_dag_inwisselbaar": false,
            "aanbieders": [
                {
                    "id": 4,
                    "naam": "Testpartner ICT2B",
                    "url": "http://www.ict2b.nl",
                    "telnr": "0172436152",
                    "straat": "Anna van Burenlaan",
                    "huisnummer": "28",
                    "postcode": "2404 GM",
                    "plaats": "Alphen aan den Rijn",
                    "afbeeldingen": [
                        {
                            "id": 1,
                            "cdn_url": "https://7c598269ce4399c1f4280cb647822944.lswcdn.net/Scherm_klein.png",
                            "medium": "Web",
                            "size": "Small"
                        },
                        {
                            "id": 2,
                            "cdn_url": "https://7c598269ce4399c1f4280cb647822944.lswcdn.net/Scherm_groot.png",
                            "medium": "Web",
                            "size": "Large"
                        }
                    ],
                    "tarieven": [
                        {
                            "id": 16,
                            "label": "leeftijd 4 t/m 12 jaar",
                            "alle_leeftijden": false,
                            "minimum_leeftijd": 4,
                            "maximum_leeftijd": 12,
                            "voorbeeld_tarief": false,
                            "normaal_tarief": 5,
                            "korting_type": "Percentage",
                            "percentage": 20,
                            "korting_tarief": 4
                        }
                    ]
                }
            ],
            "tarieven": [],
            "locaties": [
                {
                    "id": 2,
                    "titel": "Testpartner ICT2B",
                    "straat": "Anna van Burenlaan",
                    "huisnummer": "28",
                    "postcode": "2404GM",
                    "plaats": "Alphen aan den Rijn",
                    "plaats_id": 140,
                    "gemeente": "Overige Gemeenten",
                    "latitude": 52.1330914,
                    "longitude": 4.6530632
                }
            ],
            "aanbodtags": [
                {
                    "id": 1,
                    "naam": "Leuk",
                    "is_filter": false,
                    "sort_order": 0
                }
            ],
            "doelgroepen": [],
            "afbeeldingen": [
                {
                    "id": 1,
                    "cdn_url": "https://7c598269ce4399c1f4280cb647822944.lswcdn.net/Scherm_klein.png",
                    "medium": "Web",
                    "size": "Small"
                },
                {
                    "id": 2,
                    "cdn_url": "https://7c598269ce4399c1f4280cb647822944.lswcdn.net/Scherm_groot.png",
                    "medium": "Web",
                    "size": "Large"
                }
            ]
        },
        ```

  OR

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** `{ error : "You are unauthorized to make this request." }`

* **Sample Call:**

  ```javascript
    $.ajax({
      url: "/users/1",
      dataType: "json",
      type : "GET",
      success : function(r) {
        console.log(r);
      }
    });
  ```