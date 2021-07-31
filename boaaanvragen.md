| URI                                                       | Method | Returns                             |
| --------------------------------------------------------- | ------ | ----------------------------------- |
| [/aanvragen/v2/boaaanvraag](#initiate-boaaanvraag)        | `POST` | initiate a new boaaanvraag          |
| [/aanvragen/v2/boaupdate](#update-boaaanvraag)            | `POST` | webhook update for boaaanvraag      |

## **Initiate BOAAanvraag**

Initiate a new boaaanvraag.

- **URL**

  /aanvraag/v2/boaaanvraag

- **Method:**

  `POST`

- **Headers**

  **Required:**

  `API-Key`

- **URL Params**

  None
  
- **Data Params**

  Initiating a new boaaanvraag, requires a CBS code and e-mail address.

  | Name                 | Type       | Description                                                |
  | ---------------------| ---------- | ---------------------------------------------------------- |
  | `aanvraag_type`      | `enum`     | { **AANVRAAG** or **HERTOETSING** } |
  | `gemeente_code`      | `string`   | i.e. **0344**
  | `emailadres`         | `string`   | |

  ```javascript
    {
        "aanvraag_type": "AANVRAAG",
        "gemeente_code": "0344",
        "emailadres": "someone@somedomain.com"
    }
  ```

- **Success Response:**

  - **Code:** 200 <br />
    **Content:** <br />

    ```javascript
    {
        "result": {
            "code": 200,
            "message": "BOAAanvraag created with UUID: 51fc5c02-77f7-4104-830e-1d97a7b89441"
        }
    } 
    ```

- **Error Response:**

  - **Code:** 406 <br />
    **Message:** Element {someelement} is required (for all required elements)
  - **Code:** 406 <br />
    **Message:** Element {emailadres} is not valid a valid email address
  - **Code:** 406 <br />
    **Message:** No gemeente found for {gemeente_code} XXXX

<br />


## **Update BOAAanvraag**

Update status of an existing BOAAanvraag.

- **URL**

  /aanvraag/v2/boaupdate

- **Method:**

  `POST`

- **Headers**

  **Required:**

  `API-Key`
    
- **URL Params**

  `None`
  
- **Data Params**

  | Name                 | Type       | Description                                                |
  | ---------------------| ---------- | ---------------------------------------------------------- |
  | `case_id`            | `string`   | **Required** i.e. 'AGP-2021-123456' |
  | `event`              | `enum`     | **Required** { 'status-transitie' }
  | `created_at`         | `string`   | **Required** i.e. `1974-06-14T00:00:00.000Z` as per ISO 8601 |
  | **`payload`**        | `object`   | **Required**
  | &nbsp;&nbsp;`from`   | `string`   | { status } |
  | &nbsp;&nbsp;`to`     | `string`   | { status } |
    

  ```javascript
  {
    "case_id": "AGP-2021-123456",
    "event": "status-transitie",
    "created_at": "2019-08-24T14:15:22Z",
    "payload": {
        "from": "CASE_AANGEMAAKT",
        "to": "BESLUIT_GENOMEN"
  }
  ```

- **Success Response:**

  - **Code:** 200 <br />
    **Content:** <br />

    ```javascript
    {
        "result": {
            "code": 200,
            "message": "Case update for {case_id}: ASP-2021-WSONV0 has been processed"
        }
    }
    ```
	
- **Error Response:**

  - **Code:** 406 <br />
    **Message:** Element {someelement} is missing or empty
  - **Code:** 406 <br />
    **Message:** No case could be found for {case_id}: XXXX
  - **Code:** 406 <br />
    **Message:** Value for element {event} is unknown and cannot be processed
  - **Code:** 406 <br />
    **Message:** Element {payload} for the given {event} is missing or empty
  - **Code:** 406 <br />
    **Message:** Element for {event} \[status-transitie\] is invalid