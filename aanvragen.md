| URI                                                       | Method | Returns                             |
| --------------------------------------------------------- | ------ | ----------------------------------- |
| [/aanvragen/v2/pasaanvraag](#initiate-pasaanvraag)        | `POST` | initiate a new pasaanvraag          |
| [/aanvragen/v2/pasaanvraag/{uuid}](#update-pasaanvraag)   | `POST` | update an existing pasaanvraag      |
| [/aanvragen/v2/pasaanvraag/{uuid}](#retrieve-pasaanvraag) | `GET`  | retrieve a pasaanvraag              |

## **Initiate pasaanvraag**

Initiate a new pasaanvraag by identity and return json data about the pasaanvraag.

- **URL**

  /aanvraag/v2/pasaanvraag

- **Method:**

  `POST`

- **Headers**

  **Required:**

  `API-Key`

- **URL Params**

  None
  
- **Data Params**

  Initiating a new pasaanvraag requires an identity - this can be a BSN, GAN or pasnummer.
  
  | Name                 | Type       | Description                                                |
  | ---------------------| ---------- | ---------------------------------------------------------- |
  | **`identity`**       | `object`   | **Required**
  | &nbsp;&nbsp;`identity_type`      | `enum`     | **Required** identity type { 'BSN', 'GAN' or 'Pasnummer' } |
  | &nbsp;&nbsp;`identify_value`     | `string`   | **Required** identity value corresponding to the type      |

```javascript
	{
	    "identity": {
	        "identity_type": "BSN",
	        "identity_value": "26101982"
	    }
	}
```

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
	{
	    "aanvraag_id": 1003920,
	    "aanvraag_uuid": "3d89d793-dc61-4c0b-b18a-d5ba0ba126eb",
	    "aanvraag_status": "Concept",
	    "aanvrager": {
	        "geslacht": "M",
	        "initialen": "J",
		... 
    ```
	see [/aanvragen/v2/pasaanvraag](#retrieve-pasaanvraag) for pashouder entity details
	
- **Error Response:**

  - **Code:** 406 <br />
    **Message:** Element {identity} is required for a new request
  - **Code:** 406 <br />
    **Message:** No identity could be found by given identity values



## **Update pasaanvraag**

Updates a previously initiated pasaanvraag found by the provided uuid. Objects part of an update are described where column **Send?** indicates if a value can be provided or not.

- **URL**

  /aanvraag/v2/pasaanvraag/{uuid}

- **Method:**

  `POST`

- **Headers**

  **Required:**

  `API-Key`

- **URL Params**

  `uuid`
  
- **Data Params**

**Aanvrager**

| Name                                | Type        | Send? | Description                                                  |
| :---------------------------------- | :---------- | :---- | :----------------------------------------------------------- |
| **`aanvrager`**                     | object      | Yes   | |
| &nbsp;&nbsp;`geslacht`              | enum        | No    | { `M` male , `F` female, `U` other } |
| &nbsp;&nbsp;`initialen`             | string      | No    | |
| &nbsp;&nbsp;`voornaam`              | string      | No    | |
| &nbsp;&nbsp;`tussenvoegsel`         | string      | No    | |
| &nbsp;&nbsp;`achternaam`            | string      | No    | |
| &nbsp;&nbsp;`geboortedatum`         | string      | No    | ie `1974-06-14T00:00:00.000Z` as per ISO 8601 |
| &nbsp;&nbsp;`emailadres`            | string      | Yes   | **Required** email adres used to inform aanvrager about updates |
| &nbsp;&nbsp;`telefoonnummer`        | string      | Yes   | |
| &nbsp;&nbsp;`mobiel_nummer`         | string      | Yes   | |
| &nbsp;&nbsp;**`mailing`**           | object      | Yes   | |
| &nbsp;&nbsp;&nbsp;&nbsp;`ontvangen` | boolean     | Yes   | **Required** indicate if aanvrager wants to be part of a future mailing |

```javascript
    {
	    "aanvrager": {
	        "geslacht": "M",
	        "initialen": "J",
	        "voornaam": "John",
	        "tussenvoegsel": "",
	        "achternaam": "Doe",
	        "geboortedatum": "1982-10-26T00:00:00.000Z",
	        "emailadres": "j.doe@gmail.com",
	        "telefoonnummer": "0201234567",
	        "mobiel_nummer": "0612345678".
	        "mailing": {
	            "ontvangen": false
	        }
	    }
    }
```
    
**Partner**

| Name                                | Type        | Send? | Description                                                  |
| :---------------------------------- | :---------- | :---- | :----------------------------------------------------------- |
| **`partner`**                       | object      | Yes   | |
| &nbsp;&nbsp;`geslacht`              | enum        | No    | { `M` male , `F` female, `U` other |
| &nbsp;&nbsp;`initialen`             | string      | No    | |
| &nbsp;&nbsp;`voornaam`              | string      | No    | |
| &nbsp;&nbsp;`tussenvoegsel`         | string      | No    | |
| &nbsp;&nbsp;`achternaam`            | string      | No    | |
| &nbsp;&nbsp;`geboortedatum`         | string      | No    | ie `1974-06-14T00:00:00.000Z` as per ISO 8601 |
| &nbsp;&nbsp;`aanvragen`             | string      | Yes   | **Required**indicate if partner is part of aanvraag |

```javascript
	{
		"partner": {
			"geslacht": "M",
			"initialen": "N",
			"voornaam": "Nick",
			"tussenvoegsel": "van",
			"achternaam": "Wieren",
			"geboortedatum": "1982-10-26T00:00:00.000Z",
			"aanvragen": true
		}
	}
```

**Kinderen**

```javascript
	{
		"kinderen": [
			{
				"aanvraag_pashouder_id": 1234,
				"geslacht": "M",
		      	"initialen": "N",
		      	"voornaam": "Nick",
		      	"tussenvoegsel": "van",
		      	"achternaam": "Wieren",
		      	"geboortedatum": "1982-10-26T00:00:00.000Z",
		      	"aanvraag_categorie": "Minimapas kind met tegoed",
		      	"aanvragen": true
			}		
		]
	}
```
    
**Woonadres**
This address cannot be changed as it is provided by the datasource of the given `{identity}`.

| Name                                | Type        | Send? | Description                                                  |
| :---------------------------------- | :---------- | :---- | :----------------------------------------------------------- |
| **`woonadres`**                     | object      | No    | |
| &nbsp;&nbsp;`postcode`              | string      | No    | |
| &nbsp;&nbsp;`huisnummer`            | string      | No    | |
| &nbsp;&nbsp;`huisnummer_toevoeging` | string      | No    | |
| &nbsp;&nbsp;`straat`                | string      | No    | |
| &nbsp;&nbsp;`plaats`                | string      | No    | |

```javascript
	{	
		"woonadres": {
			"postcode": "3311GR",
			"huisnummer": 300,
			"huisnummer_toevoeging": "A",
			"straat": "Spuiboulevard",
			"plaats": "Dordrecht"
		}
	}
```

**Postadres**
This address can be provided if an alternative address is required.

| Name                                | Type        | Send? | Description                                                  |
| :---------------------------------- | :---------- | :---- | :----------------------------------------------------------- |
| **`postadres`**                     | object      | Yes   | |
| &nbsp;&nbsp;`postcode`              | string      | Yes   | **Required** |
| &nbsp;&nbsp;`huisnummer`            | string      | Yes   | **Required** |
| &nbsp;&nbsp;`huisnummer_toevoeging` | string      | Yes   | |
| &nbsp;&nbsp;`straat`                | string      | Yes   | **Required** |
| &nbsp;&nbsp;`plaats`                | string      | Yes   | **Required** |

```javascript	
	{
		"postadres": {
			"postcode": "3311GR",
			"huisnummer": 300,
			"huisnummer_toevoeging": "A",
			"straat": "Spuiboulevard",
			"plaats": "Dordrecht"
		}
	}
```

**Feiten**
This object type can contain several type of facts differentiated by `{type_feit}`. For every fact, documents can- or have to be provided - see the table below for all fact types.

| Type feit              | Description                     | Number of docs  |
| :--------------------- | :------------------------------ | --------------- |
| Salaris                | Vast salaris                    | 1 |
| VariableLoon           | Variabel inkomen                | 3 |
| UitkeringAOW           | Uitkering of AOW                | 1 |
| Pensioen               | Pensioen                        | 1 |
| Anders                 | Andere inkomstenbronnen         | 1 |
| Overig                 | Overige bewijsstukken           | 1 |
| WSNP                   | Wet schuldsanering              | 1 |
| GezinsvervangendTehuis | Kind ingeschreven in tehuis     | 1 |
| Zorginstelling         | Ingeschreven in zorginstelling  | 1 |


| Name                                         | Type        | Send? | Description                                                  |
| :------------------------------------------- | :---------- | :---- | :----------------------------------------------------------- |
| **`feiten`**   	                           | `obj array` | Yes   | |
| &nbsp;&nbsp;`id`				                 | `string`    | Yes   | |
| &nbsp;&nbsp;`type_feit`                      | `enum`      | Yes   | **Required** resembles the type of fact - see table below |
| &nbsp;&nbsp;`hoogte_inkomen`                 | `decimal`   | Yes   | **Required** |
| &nbsp;&nbsp;`omschrijving`                   | `string`    | Yes   | |
| &nbsp;&nbsp;`verwijder`                      | `boolean`   | Yes   | Can be used to indicate `true` that the fact needs to be removed (requires `id`) |
| &nbsp;&nbsp;**`documenten`**                 | `obj array` | Yes   | |
| &nbsp;&nbsp;&nbsp;&nbsp;`id`                 | `string`    | Yes   | Provided by GPass after adding a new document - **Required** when updating a previously created document | also required for /aanvragen/v2/document/{uuid} |
| &nbsp;&nbsp;&nbsp;&nbsp;`document_naam`      | `string`    | Yes   | **Required** name of the file |
| &nbsp;&nbsp;&nbsp;&nbsp;`bestand_ontvangen`  | `boolean`   | No    | Indicates wether file has been received for document |
| &nbsp;&nbsp;&nbsp;&nbsp;`verwijder`          | `boolean`   | Yes   | Can be used to indicate `true` that the document needs to be removed (requires `id`)|

  ```javascript
	"feiten": [
		{
			"id": "5ef8090e1-8224-4c2a-a918-53a7f6c19d3c",
			"type_feit": "Salaris",
			"hoogte_inkomen": 1200,
			"omschrijving": "Mijn maandelijkse salaris",
			"verwijder": false,
			"documenten": [
				{
					"id": "6ef808f1-8224-4c2a-a918-53a7f6c23f5a",
					"document_naam": "Salarisstrook.pdf",
					"bestand_ontvangen": true,
					"verwijder": false
				}
			]
		}
	]
  ```

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
	{
	    "aanvraag_id": 1003920,
	    "aanvraag_uuid": "3d89d793-dc61-4c0b-b18a-d5ba0ba126eb",
	    "aanvraag_status": "Concept",
	    "aanvrager": {
	        "geslacht": "M",
	        "initialen": "J",
		... 
    ```
	see [/aanvragen/v2/pasaanvraag](#retrieve-pasaanvraag) for pashouder entity details
	
- **Error Response:**

  - **Code:** 406 <br />
    **Message:** Element {identity} is required for a new request
  - **Code:** 406 <br />
    **Message:** No identity could be found by given identity values


## **Retrieve pasaanvraag**

Retrieve an existing pasaanvraag by uuid and return json data about this pasaanvraag.

- **URL**

  /aanvraag/v2/pasaanvraag/{uuid}

- **Method:**

  `POST`

- **Headers**

  **Required:**

  `API-Key`

- **URL Params**

  `uuid`
  
- **Data Params**

  None

- **Success Response:**

  - **Code:** 200 <br />
    **Message:** OK <br />
    **Content:** <br />

    ```javascript
    {
        "aanvraag_id": 1000001,
        "aanvraag_uuid": "550e8400-e29b-41d4-a716-446655440000",
        "aanvraag_status": "Concept",
        "aanvraag_api_status": "Concept",
        "aanvrager": {
            "geslacht": "M",
            "initialen": "J",
            "voornaam": "Johan",
            "tussenvoegsel": "de",
            "achternaam": "Smit",
            "geboortedatum": "1970-04-01T00:00:00.0000000",
            "emailadres": "j.desmit@gmail.com",
            "telefoonnummer": "0123456789",
            "mobiel_nummer": "0612345678",
            "mailing": {
                "ontvangen": true
            },
            "aanvraag_categorie": "Minimapas volwassen"
        },
        "woonadres": {
            "postcode": "3311GR",
            "huisnummer": 300,
            "huisnummer_toevoeging": "",
            "straat": "Spuiboulevard",
            "plaats": "Dordrecht"
        },
        "postadres": {
            "postcode": "3311GR",
            "huisnummer": 300,
            "huisnummer_toevoeging": "",
            "straat": "Spuiboulevard",
            "plaats": "Dordrecht"
        },
        "partner": {
            "geslacht": "F",
            "initialen": "S",
            "voornaam": "Simone",
            "tussenvoegsel": "de",
            "achternaam": "Smit",
            "geboortedatum": "1972-05-20T00:00:00.0000000",
            "aanvraag_categorie": "Minimapas volwassen",
            "aanvragen": true
        },
        "kinderen": [
            {
                "aanvraag_pashouder_id": 1234,
                "geslacht": "M",
                "initialen": "J",
                "voornaam": "Jurre",
                "tussenvoegsel": "de",
                "achternaam": "Smit",
                "geboortedatum": "1972-05-20T00:00:00.0000000",
                "aanvraag_categorie": "Minimapas kind met tegoed",
                "aanvragen": true
            }
        ],
        "feiten": [
            {
                "id": "550e8400-e29b-41d4-a716-446655440000",
                "type_feit": "Salaris",
                "hoogte_inkomen": 1000.50,
                "omschrijving": "",
                "documenten": [
                    {
                        "id": "560e4400-e29b-41d4-a716-446655440000",
                        "document_naam": "document.pdf",
                        "bestand_ontvangen": true
                    }
                ]
            }
        ]
    }
    ```
	
- **Error Response:**

  - **Code:** 404 <br />
    **Message:** PasAanvraag for {aanvraag\_id}: [aanvraag\_id] not found **or** PasAanvraag for {aanvraag\_uuid}: [aanvraag\_uuid] not found
    
