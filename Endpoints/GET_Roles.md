# GET /Roles

#### Description

- Requires API Key: No
- Requires System Administrator: No
- Requires Counterpoint Registration option: No
- Requires Company Administrator: Yes

#### Sample Request

**URI**

`GET https://localhost:81/Roles`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and a list of Roles was returned.

#### Sample Response Body

```
{
  "roleList": [
    {
      "name": "Role1",
      "endpoints": [
        {
          "path": "/Customer",
          "verbsAllowed": [
            "POST"
          ]
        },
        {
          "path": "/Customer/{CustNo}/Address",
          "verbsAllowed": [
            "POST",
            "DELETE"
          ]
        },
        {
          "path": "/Customer/{CustNo}/Card",
          "verbsAllowed": [
            "POST",
            "DELETE"
          ]
        }
        ...
      ]
    },
    {
      "name": "Role2",
      "endpoints": [
        {
          "path": "/Company",
          "verbsAllowed": [
            "GET"
          ]
        },
        {
          "path": "/Document/{docid}",
          "verbsAllowed": [
            "GET"
          ]
        },
        {
          "path": "/GiftCardCode/{GiftCardCode}",
          "verbsAllowed": [
            "GET"
          ]
        },
        {
          "path": "/GiftCardCodes",
          "verbsAllowed": [
            "GET"
          ]
        }
      ]
    }
  ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**Role List**

Element | Datatype | Description
------- | -------- | -----------
roleList | List<Role> | A list of roles.

**Role object**

Element | Datatype | Description
------- | -------- | -----------
Name | string | The name of the role.
Endpoints | List<Endpoint> | A list of endpoints and verbs the role has access to.

**Endpoint object**

Element | Datatype | Description
------- | -------- | -----------
Path | string | The path of this endpoint.
VerbsAllowed | List<string> | A list of verbs available for this endpoint.
