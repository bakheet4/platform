---
title: API Reference

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the EnayaPay API
---

# Introduction

Welcome to the EnayaPay API! You can use our API to access EnayaPay API endpoints.
# User Account Management
## Register

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/register/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd"
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key.

### HTTP Request

`POST https://sandbox.enayapay.com/api/v2.1/register/`

### Description

`the use of this endpoint to register new user using phone number as id verification .`

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg"
  }

```
### Body
```json
 {
    "user_phone": "2499++++++++",
    "user_name": "doctor",
    "user_password": "calicofdhfdsfsd"
  }


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
user_phone | required | user phone number | String
user_name | required | userName of user | String
user_password | required | user password | String


### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
201 | None | user created and otp will send in phone number
302 | None | user already registered
406 | `` {"details" : "your number not valid"} ``| phone number of user not valid
400 | `` { "details": {"user_password": [ "This field is required."]} } `` | Bad request occurred when forget parameter
502 | ```{"details" : "bad getway" }``` |  bad getway of sms getway
503 | ``` {"details" :"service not available"} ``` | when service not available


## verify

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/verify/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd"
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key.

### HTTP Request

`POST https://sandbox.enayapay.com/api/v2.1/verify/`
### Description 

``the use of this endpoint to verification user phone number that he used``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg"
  }

```
### Body
```json
 {
    "user_phone": "2499++++++++",
    "user_otp": "454345"
  }


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
user_phone | required | user phone number | String
user_otp | required | otp of user | String


### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ``` {"token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IjU3NTMwNyIsImV4cGlyeSI6IjIwMjEtMTEtMTMifQ.2uU8eOnw8biYxH55EblrTHOz5nM4rcP1kiIa7S46mFs","user_name": "doctor"} ```| user verified
203 | None | wrong otp
400 | ``{ "details": {"user_otp": ["This field is required."]} }``| Bad request occurred when forget parameter 
401 | None | your api key not valid
404 | ``` {"details": "user not registered"} ``` | user not register
503 | ``` {"details" :"service not available"} ``` | when service not available


## login

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/login/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd"
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key.


### HTTP Request
`POST https://sandbox.enayapay.com/api/v2.1/login/`

### Description

`` this endpoint use to access user account using password``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg"
  }

```
### Body
```json
 {
    "user_phone": "2499++++++++",
    "user_password": "dfdfsdfdsfs"
  }


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
user_phone | required | user phone number | String
user_password | required | password of user | String


### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ``` {"user_name": "doctor","status": "active"} ```| user authorized
203 | None | wrong password
400 | ``{ "details": {"user_password": ["This field is required."]} }``| Bad request occurred when forget parameter 
401 | None | your api key not valid
404 | ``` {"details": "user not registered"} ``` | user not register
503 | ``` {"details" :"service not available"} ``` | when service not available




## rest password

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/rest/password/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd , token: ffdfdsfsdfds "
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key and Token.


### HTTP Request
`POST https://sandbox.enayapay.com/api/v2.1/rest/password/`

### Description

`` this endpoint use to rest user password when he forget``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg",
    "token": "fsfsfkwoieriworiewriweiriwerieworioweir"
  }

```
### Body
```json
 {
    "user_phone": "2499++++++++",
    "user_password": "dfdfsdfdsfs"
  }


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
user_phone | required | user phone number | String
user_password | required | password of user | String


### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ``` {"user_name": "doctor","status": "active"} ```| user rest his password successful
203 | None | not valid token
400 | ``{ "details": {"user_password": ["This field is required."]} }``| Bad request occurred when forget parameter 
401 | None | your api key not valid
404 | ``` {"details": "user not registered"} ``` | user not register
503 | ``` {"details" :"service not available"} ``` | when service not available


## change password

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/change/password/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd , token: ffdfdsfsdfds "
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key and Token.


### HTTP Request
`POST https://sandbox.enayapay.com/api/v2.1/change/password/`

### Description

``this endpoint use to change user password that he used to access apllication .``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg",
    "token": "fsfsfkwoieriworiewriweiriwerieworiowe"
  }

```
### Body
```json
 {
    "current_password": "gfgfdgdfg",
    "new_password": "dfdfsdfdsfs"
  }


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
current_password | required | old password that user need to change | String
new_password | required | new_password that user need to change to it | String


### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ```{"details": "password updated successful"} ```| user changed his password successfully
203 | ``{"details": "wrong current password"}``| invalid old password
400 | ``{ "details": {"new_password": ["This field is required."]} }``| Bad request occurred when forget parameter 
401 | None | your api key not valid
404 | ``` {"details": "user not registered"} ``` | user not register
503 | ``` {"details" :"service not available"} ``` | when service not available

# Cards


## add card

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/cards/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd , token: ffdfdsfsdfds "
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key and Token.


### HTTP Request
`POST https://sandbox.enayapay.com/api/v2.1/cards/`

### Description

``this endpoint use to add new card to your account``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg",
    "token": "fsfsfkwoieriworiewriweiriwerieworiowe"
  }

```
### Body
```json
 {
    "pan":"454567894567988",
    "label":"bakheet",
    "expiration_date":"0824",
    "default":1
  }


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
pan | required | number of card that user want to add | String
label | required | display name of card | String
expiration_date | required | expiration  date of card| String
default | required | to set card as default in use| string



### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
201 | ```{"id" :1}```| card added successfully
400 | ``{ "details": {"pan": ["This field is required."]} }``| Bad request occurred when forget parameter 
302 | None | card already added
401 | None | your api key not valid
404 | ``{"details": " user not registered"}`` | user not register
406 | ```{"details": "unknown card number"}``` | user card number not valid
503 | ``` {"details" :"service unvailable for now"} ``` | service disable for user 

## get cards

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/cards/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd , token: ffdfdsfsdfds "
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key and Token.


### HTTP Request
`GET https://sandbox.enayapay.com/api/v2.1/cards/`

### Description

``this endpoint use views all cards that user assgin to his account``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg",
    "token": "fsfsfkwoieriworiewriweiriwerieworiowe"
  }

```
### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ```[{"id": 1,"card_pan": "454567894567988","card_expiry": "0824","card_label": "bakheet","card_type": "International","card_image": "Screenshot_from_2021-07-08_14-33-58.png","default": 1}]```| all cards that user assign to his account
401 | None | your api key not valid
404 | ``{"details": " user not registered"}`` | user not register
503 | ``` {"details" :"service unvailable for now"} ``` | service disable for user 

## get card

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/card/1/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd , token: ffdfdsfsdfds "
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key and Token.


### HTTP Request
`GET https://sandbox.enayapay.com/api/v2.1/card/1/`

### Description

``this endpoint use view one card  base on card id that user assgin to his account``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg",
    "token": "fsfsfkwoieriworiewriweiriwerieworiowe"
  }

```
### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ```[{"id": 1,"card_pan": "454567894567988","card_expiry": "0824","card_label": "bakheet","card_type": "International","card_image": "Screenshot_from_2021-07-08_14-33-58.png","default": 1}]```|  view one card that user assign to his account
401 | None | your api key not valid
404 | ``{"details": " user not registered"}`` | user not register
503 | ``` {"details" :"service unvailable for now"} ``` | service disable for user 

## delete card

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/card/1/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd , token: ffdfdsfsdfds "
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key and Token.


### HTTP Request
`DELETE https://sandbox.enayapay.com/api/v2.1/card/1/`

### Description

``this endpoint use remove card  base on card id that user assgin to his account``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg",
    "token": "fsfsfkwoieriworiewriweiriwerieworiowe"
  }

```
### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
204 | ```{"details":"card has been deleted successfully"}```|  view one card that user assign to his account
401 | None | your api key not valid
404 | ``{"details": " user not registered"}`` | user not register
## balance inquiry

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/balance/inquiry/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd , token: ffdfdsfsdfds "
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key and Token.


### HTTP Request
`POST https://sandbox.enayapay.com/api/v2.1/balance/inquiry/`

### Description

``this endpoint use to provide information on the customer account balance``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg",
    "token": "fsfsfkwoieriworiewriweiriwerieworiowe"
  }

```
### Body
```json
 {
    "pan":"45456789456798893",
    "ipin":"rtewrrtertretretrtrwtwrt",
    "uuid":"fdfregregergerlkfjerfklerjfkgerjgjre",
    "expiration_date":"0824"
  }


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
pan | required | number of card that user want to known its balance | String
ipin | required | credential of customer | String
expiration_date | required | expiration  date of card| String
uuid | required | string



### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ```{"response_code": 0,"balance": 400,"response_status": "Successful","uuid": "fdfregregergerlkfjerfklerjfkgerjgjre"}```| account user informations
400 | ``{ "details": {"pan": ["This field is required."]} }``| Bad request occurred when forget parameter 
401 | None | your api key not valid
406 | ```{"response_code": 696,"response_message": "SYSTEM_ERROR"}``` | service provider errors with code
502 | ``` {"details" :"bad getway"} ``` | when service provider down 

# Telecoms


## Topup

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/telecom/110010001/topup/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd , token: ffdfdsfsdfds "
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key and Token.


### HTTP Request
`POST https://sandbox.enayapay.com/api/v2.1/telecom/110010001/topup/`

### Description

``this endpoint use to provide topup to customer base on payeeid ``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg",
    "token": "fsfsfkwoieriworiewriweiriwerieworiowe"
  }

```
### Body
```json
 {
    "pan":"43443455656653465",
    "ipin":"reretertrterty5rt45",
    "expiration_date":"0824",
    "phone_no":"0905450785",
    "amount": 300,
    "uuid":"rerrwerwerwerwerwerwrweRWrwrwr",
    "platform":"web"
    
}


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
pan | required | number of card that user want to py topup by it | String
ipin | required | credential of customer | String
expiration_date | required | expiration  date of card| String
amount | required | amount of topup that customer need to pay | Float
phone_no | required | phone number want to charge it | String
uuid | required | the key used to encrypt ipin| string
platform | required | platform that customer used to charge phone number | String


### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ```{"pan": "43443455656653465","acq_tran_fee": 0,"dynamic_fees": 0,"issuer_tran_fee": 0,"payment_info": "MPHONE= 2490905450785","response_message": "Approved","response_status": "Successful","amount": 300,tran_date_time": 55665455444,"uuid": "rerrwerwerwerwerwerwrweRWrwrwr","response_code": 0}```| Transaction done successfully
400 | ``{ "details": {"pan": ["This field is required."]} }``| Bad request occurred when forget parameter 
401 | None | your api key not valid
404 | | customer not registered
406 | ```{"response_code": 696,"response_message": "SYSTEM_ERROR"}``` | service provider errors with code
503 | ``` {"details" :"service unavailable"} ``` | service disable for now


## Inquiry

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/telecom/1100055511/inquiry/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd , token: ffdfdsfsdfds "
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key and Token.


### HTTP Request
`POST https://sandbox.enayapay.com/api/v2.1/telecom/1100055511/inquiry/`

### Description

``this endpoint use to provide information of cutomer account invoice ``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg",
    "token": "fsfsfkwoieriworiewriweiriwerieworiowe"
  }

```
### Body
```json
 {

    "phone_no":"0905450785"
    
}


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------

phone_no | required | phone number that customer want to known invoice for it | String


### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ```{"total_amount": 400,"contract_number": 34234235345,"acq_tran_fee": 0,"dynamic_fees": 0,"issuer_tran_fee": 0,"tran_date_time": 65475475}```| Transaction done successfully
400 | ``{ "details": {"phone_no": ["This field is required."]} }``| Bad request occurred when forget parameter 
401 | None | your api key not valid
404 | | customer not registered
406 | ```{"response_code": 696,"response_message": "SYSTEM_ERROR"}``` | service provider errors with code
503 | ``` {"details" :"service unavailable"} ``` | service disable for now


## Bill Payment

```shell
# With shell, you can just pass the correct header with each request
curl "https://sandbox.enayapay.com/api/v2.1/telecom/110010001/topup/" \
  -H "x-api-key: gffdgdfgdfgdfgdfgdgd , token: ffdfdsfsdfds "
```

> Make sure to replace `gffdgdfgdfgdfgdfgdgd` with your API key and Token.


### HTTP Request
`POST https://sandbox.enayapay.com/api/v2.1/telecom/110010001/topup/`

### Description

``this endpoint use by customers bill they invoices ``

### Headers
```json
 {
    "x-api-key": "fddfgdfgdfgdfgdfg",
    "token": "fsfsfkwoieriworiewriweiriwerieworiowe"
  }

```
### Body
```json
 {
    "pan":"43443455656653465",
    "ipin":"reretertrterty5rt45",
    "expiration_date":"0824",
    "phone_no":"0905450785",
    "amount": 300,
    "uuid":"rerrwerwerwerwerwerwrweRWrwrwr",
    "platform":"web"
    
}


```
### Parameters Description
Parameter | Default | Description | Type
--------- | ------- | ----------- | ----------
pan | required | number of card that user want to py topup by it | String
ipin | required | credential of customer | String
expiration_date | required | expiration  date of card| String
amount | required | amount of topup that customer need to pay | Float
phone_no | required | phone number want to charge it | String
uuid | required | the key used to encrypt ipin| string
platform | required | platform that customer used to charge phone number | String


### Response 
StatusCode | Response Data | Description  
--------- | ------- | ---------
200 | ```{"pan": "43443455656653465","acq_tran_fee": 0,"dynamic_fees": 0,"issuer_tran_fee": 0,"payment_info": "MPHONE= 2490905450785","response_message": "Approved","response_status": "Successful","amount": 300,tran_date_time": 55665455444,"uuid": "rerrwerwerwerwerwerwrweRWrwrwr","response_code": 0}```| Transaction done successfully
400 | ``{ "details": {"pan": ["This field is required."]} }``| Bad request occurred when forget parameter 
401 | None | your api key not valid
404 | | customer not registered
406 | ```{"response_code": 696,"response_message": "SYSTEM_ERROR"}``` | service provider errors with code
503 | ``` {"details" :"service unavailable"} ``` | service disable for now
