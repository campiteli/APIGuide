# NCRCounterpointAPI
Repository for NCR Counterpoint API Documentation

## Installation
In progress

## Requirements
Any instance of the NCR Counterpoint API server can connect to multiple NCR Counterpoint installations and companies. In order for the server to work against an NCR Counterpoint company, the following requirements must be met:
* The NCR Counterpoint API server must be installed and running on an open http port
* The NCR Counterpoint API server must have read/write access to the TLD folder for the company. This can be on a separate machine accessible via a UNC path
* The NCR Counterpoint API server must have administrative access to the company database
* The company the server is connecting to must have the API user option enabled in its registration.ini file. There are some limited functions that will work without the API user option, but the bulk of the endpoints do require the registration option. See the documentation for an individual endpoint to determine if it requires the registration.ini option for use.
* Client applications or scripts using the API must provide a valid API Key, which is installed on the API Server, and included in the "APIKey" header for the request. See the page on APIKeys for more information. There are some limited functions that will work without an API Key, but the bulk of the endpoints do require an API Key to be provided. See the documentation for an individual endpoint to determine if it requires an APIKey for use.

## Configuration and Administration
In progress

## Company vs. System Administration requests
Due to the fact that a single API server can connect to mulitiple distinct NCR Counterpoint installations and companies, for security purposes there are some endpoints accessible only to system administrators, and others only accessible to company level users. See documentation on an individual endpoint to determine if system administrator or company level authorization is required.

System administrator logins are identifiable by the lack of a company name/alias prefix on their username. Upon install, there is a default system administrator with the username "admin", and the password (TBD). Users will be required to change the admin password upon their first login to the NCR Counterpoint API Management Console. Administrative functionality generally does not require an API Key or registration.ini option in order to be used.

## Common http Request elements
### Authorization
The NCR Counterpoint API uses standard http basic authentication to validate NCR Counterpoint credentials in each call. Per basic authentication requirements, each call must contain an "Authorization" header in the following format:

`Authorization : Basic UUFUZXN0R29sZi5NR1I6UGFzc3dvcmQx`

The value after the word "Basic" is a base64 encoded (not encrypted) string containing the username and password of the NCR Counterpoint user for which the request is being submitted. For all company level requests, the company name/alias must be provided as a prefix to the user name in the format <CompanyAlias>.<UserName>. For instance, if my company alias is "QATestGolf", my Counterpoint user name is "MGR", and my Counterpoint password is "password1", I'll form the authentication string as such:

`QATestGolf.MGR:password1`

Base64 encoding the above string will yield "UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx", which is the string included in the sample Basic authentication example above.

**NOTE** Base64 encoding is not a form of encryption and does not provide security. All data included an an NCR Counterpoint API request and response is encoded via the use of SSL. You can find a 3rd party website to experiment with base64 encoding and decoding [here](https://www.base64encode.org/).

If no authorization header is submitted with the request, or an invalid username or password is submitted, the request will fail with a `401 Invalid username or password` http response.

## Common http Response codes

## Endpoints

### System Administration Endpoints
`/APIKey`

`/APIKeys`

`/Database`

`/Databases`

### Company Endpoints
`/Company`

`/Customer`

`/CustomerControl`

`/Customers`

`/Document`

`/EC`

`/ECCategories`

`/GiftCard`

`/GiftCardCode`

`/GiftCardCodes`

`/GiftCards`

`/InventoryControl`

`/Item`

`/ItemCategories`

`/ItemCategory`

`/Items`

`/PayCode`

`/PayCodes`

`/Store`

`/TaxCodes`

`/User`

`/Workgroup`