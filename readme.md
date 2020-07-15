## **PASS API security**

## API Key

Retrieving data from the PASS REST API requires an API key provided by the PASS application. A PASS API Key is related to a specific PASS organisation. Additonally a PASS API Key can be configured for specific "pas soorten".

The `Aanbod` service only requires an API Key. Other services require an `AccessToken` or a `PasswordToken`. Please see [API Tokens](#api-tokens) for more information.

## API Tokens

An API AccessToken is required for a **pashouder** user to be able to get data from or post data to any of the services avaiable to a pashouder by providing an Authorization bearer header. See service [/token/v1/login](#retrieve-token) for more information on how to acquire a token for a pashouder.

Once a valid token has been acquired - the `Authorization` header can be formed as folows: "`Authorization: Bearer {access_token}`".

An AccessToken is valid for a specific period of time. Every time an AccessToken is succesfully used, the expiry date/time of the token is set to the maximum days configured in the API configuration.

## API AppBearer

A different type of authorization is possible using an AppBearer Authorization header. If a specific API key has been configured to allow this kind of authorization - it is possible to use Token based operations using a specific `AppBearer`. The AppBearer contains the API Key and a specific client number. The client number is used to create a specific context in which services are called.

The format of this type of `Authorization` header is as folows "`Authorization: AppBearer {api_key},{client_number}`" - where the {api_key} and {client_number} are separated by a comma.

## API Services Operations

| Service     | URI                                                                                  |  Method  | Description                                                     |
| ----------- | ------------------------------------------------------------------------------------ | :------: | --------------------------------------------------------------- |
| Aanbod      | [/aanbod/v1/aanbiedingen](aanbiedingen.md#retrieve-aanbiedingen)                     |  `GET`   | retrieve a list of aanbiedingen                                 |
| Aanbod      | [/aanbod/v1/aanbiedingen/:id](aanbiedingen.md#retrieve-aanbieding)                   |  `GET`   | retrieve a single aanbieding by id                              |
| Aanbod      | [/aanbod/v1/activiteiten](activiteiten.md#retrieve-activiteiten)                     |  `GET`   | retrieve a list of activiteiten                                 |
| Aanbod      | [/aanbod/v1/activiteiten/:id](activiteiten.md#retrieve-activiteit)                   |  `GET`   | retrieve a single activiteit by id                              |
| Aanbod      | [/aanbod/v1/aanbiederactiviteiten](activiteiten.md#retrieve-aanbiederactiviteiten)   |  `GET`   | retrieve a list of aanbiederactiviteiten                        |
| Aanbod      | [/aanbod/v1/aanbiederactiviteiten/:id](activiteiten.md#retrieve-aanbiederactiviteit) |  `GET`   | retrieve a single aanbiederactiviteit by id                     |
|             |                                                                                      |          |                                                                 |
| Aanvragen   | [/aanvragen/v2/pasaanvraag](aanvragen.md#initiate-pasaanvraag)                       |  `POST`  | initiate a new pasaanvraag                                      |
| Aanvragen   | [/aanvragen/v2/pasaanvraag/{uuid}](aanvragen.md#update-pasaanvraag)                  |  `POST`  | update an existing pasaanvraag                                  |
| Aanvragen   | [/aanvragen/v2/pasaanvraag/{uuid}](aanvragen.md#retrieve-pasaanvraag)                |  `GET`   | retrieve a pasaanvraag                                          |
| Aanvragen   | [/aanvragen/v2/document/{uuid}](aanvragen.md#upload-document)                        |  `POST`  | upload binary content for document                              |
|             |                                                                                      |          |                                                                 |
| Sales       | [/sales/v1/pashouder](sales.md#retrieve-pashouder)                                   |  `GET`   | retrieve a single pashouder by token                            |
| Sales       | [/sales/v1/pashouder](sales.md#update-pashouder)                                     |  `POST`  | update pashouder by token                                       |
| Sales       | [/sales/v1/registerpashouder](sales.md#register-pashouder)                           |  `POST`  | register pashouder to account                                   |
| Sales       | [/sales/v1/pas](sales.md#retrieve-pas)                                               |  `POST`  | retrieve pas details by pasnummer                               |
| Sales       | [/sales/v1/togglepas](sales.md#toggle-pas)                                           |  `POST`  | toggle pas status (block/unblock)                               |
|             |                                                                                      |          |                                                                 |
| Token       | [/token/v1/login](token.md#login)                                                    |  `POST`  | login using Basic authentication and return an AccessToken      |
| Token       | [/token/v1/login](token.md#logout)                                                   | `DELETE` | logout using Bearer authentication and expiring the AccessToken |
| Token       | [/token/v1/refresh](token.md#refresh)                                                |  `POST`  | refresh the given AccessToken expiry date                       |
| Token       | [/token/v1/passwordtoken](token.md#passwordtoken)                                    |  `GET`   | retrieve a password token by login_name                         |
| Token       | [/token/v1/changepassword](token.md#passwordtoken)                                   |  `POST`  | change password for pashouder related to provided PasswordToken |
|             |                                                                                      |          |                                                                 |
| Transacties | [/transactions/v1/aanbiedingen](transactions.md#retrieve-aanbieding-transactions)    |  `GET`   | retrieve transactions for aanbiedingen for pashouder            |
| Transacties | [/transactions/v1/budget](transactions.md#retrieve-budget-transactions)              |  `GET`   | retrieve transactions for budgetten for pashouder               |
