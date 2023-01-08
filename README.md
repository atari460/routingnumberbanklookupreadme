# Routing number bank lookup API documentation

## Request Type: GET

## Optional Params:

**format -** if you don’t put this, it will default to json. if you need an XML response, add the query param into the url like this api/v1/121000248?format=xml

**paymentType -** if you don’t put this, it will default to ACH. Bank information is a little different depending on whether you’re trying to use the ACH system or the Wire Transfer system. You define what you want here. For example, if you need the Wire Transfer information, you’d add the query param into the url like this api/v1/121000248?paymentType=wire. Generally, ACH info is the most commonly used so if you don’t know what any of this stuff means, just leave this blank and let it default to ACH.

## Examples:

### 1. I want the Wire Transfer info for the routing number 121000248 and I want it in JSON format:

**Request:** GET api/v1/121000248?paymentType=wire&format=json

**Response:**
```
{
  “status”: “success”,
  “data”: {
    “routingNumber”: “121000248”,
    “paymentType”: “wire”,
    “name”: “Wells Fargo Bank, Na”,
    “telegraphicName”: “WELLS FARGO NA”,
    “location”: “San Francisco, CA”,
    “city”: “San Francisco”,
    “state”: “CA”,
    “fundsTransferEligible”: “Eligible”,
    “bookEntrySecuritiesTransferEligible”: “Eligible”,
    “lastUpdated”: “Feb 17, 2020”
  }
}
```

### 2. I want the ACH info for the routing number 121000248 and I want it in XML format:

**Request:** GET api/v1/121000248?paymentType=ach&format=xml
**Response:**
```
<bankInfo>
  <status>success</status>
  <data>
    <routingNumber>121000248</routingNumber>
    <paymentType>ach</paymentType>
    <name>Wells Fargo Bank, Na</name>
    <addressFull>255 2nd Ave South, Minneapolis, MN 55479</addressFull>
    <street>255 2nd Ave South</street>
    <city>Minneapolis</city>
    <state>MN</state>
    <zip>55479</zip>
    <phone>800-745-2426</phone>
    <active>Active</active>
    <lastUpdated>Feb 17, 2020</lastUpdated>
  </data>
</bankInfo>
```
