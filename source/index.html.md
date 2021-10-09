# Introduction
Welcome to the Enaya Platform API! You can use our API to access Payment API endpoints, which can get information on various transactions, making a payment to various providers like card transfer,telecom services and electricity.

# Transfer
## Create Transaction order

```shell
# With shell, you can just pass the correct header with each request
curl "https://platform.enayapay.com/api/v2.2/payment/" \
  -H "app-key": gffdgdfgdfgdfgdfgdgd","secret-key":"ffdsgdsgdggd"
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your App key and Secret Key.

### HTTP Request

`POST https://platform.enayapay.com/api/v2.2/payment/`

### Description

`the use of this endpoint to transaction order to send money using enaya platform.`

### Headers
```json
 {
    "app-key": "fddfgdfgdfgdfgdfg",
    "secret-key": "sferwrewrewr"
  }

```
### Body
```json
 {
    "amount": 10,
    "return_url": "https://google.com",
    "cancel_url": "https://google.com"
  }


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
amount | required | amount that customer want to send | Float
return_url | required | auto return to this url after transaction successful | String
cancel_url | required | auto return to this url after transaction Failed | String


### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | `` {"id": "02f680796b2e66ba33d1c088c84c9f2b","status": "CREATED","links": [{ "href": "https://platform.enayapay.com/api/v2.2/payment/02f680796b2e66ba33d1c088c84c9f2b/approve/","rel": "approve", "method": "GET"}, { "href": "https://platform.enayapay.com/api/v2.2/payment/02f680796b2e66ba33d1c088c84c9f2b/", "rel": "self", "method": "GET" } ]}`` | transaction created successful 
400 | ``{"cancel_url": ["This field is required."]}`` | Bad request occurred when forget parameter
401 | ``{"detail": "Authentication credentials were not provided."}`` | your app-key or secret-key not valid
503 | ``` {"detail" :"service not available"} ``` | when service not available


## Transaction Order Details

```shell
# With shell, you can just pass the correct header with each request
curl "https://platform.enayapay.com/api/v2.2/payment/637b89c70a6d3ef3660f60878243/" \
  -H "app-key": gffdgdfgdfgdfgdfgdgd","secret-key":"ffdsgdsgdggd"
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your App key and Secret Key.

### HTTP Request

`GET https://platform.enayapay.com/api/v2.2/payment/637b89c70a629eb6f2660f60878235f/`

### Description

`the use of this endpoint to get transaction details base in order id.`

### Headers
```json
 {
    "app-key": "fddfgdfgdfgdfgdfg",
    "secret-key": "sferwrewrewr"
  }

```

### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ``{"id": "637b89c70a6d9eb6f2660f608782526b","status": "CREATED","amount": 10,"date_time": "2021-09-28T15:53:14.333526Z"}`` | transaction detail when status of order created
200 | ``{"id": "41ca2e587f53cc9dff551b97bc8a8320","amount": 10,"from_card": "************2173","to_card": "***************2173","currency": "SDG",  "date_time": "2021-09-28T14:33:24.609519Z"}`` | transaction detail when status of order PAYED
401 | ``{"detail": "Authentication credentials were not provided."}`` | your app-key or secret-key not valid
404 | ``{"detail": "your transaction id not found"}`` | when transaction id not vaild
503 | ``` {"detail" :"service not available"} ``` | when service not available
