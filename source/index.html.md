---
title: Zip-Tax.com API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell: Testing with cURL
#  - python
#  - php
#  - ruby
#  - java
#  - javascript
#  - csharp

toc_footers:
  - <a href='http://zip-tax.com/pricing'>Generate your API key</a>

#includes:
#  - errors

search: true
---

# Introduction

**Welcome to the Zip-Tax.com Sales Tax API**

By providing as little as a zip code, we can determine the sales tax rates for your customers in their specific geographical area. In most states, sales tax rates change many times throughout the year. Our service provides you with a method to get this information quickly and easily and with no maintenance. The ZipTax team is dedicated to providing you with the critical up-to-date information you need so you can focus on the important parts of your business.

Our Zip-Tax.com API is designed to allow programmers to submit a request to our servers from a website or application and retrieve response data from our databases. The format of the response can be returned as JSON or XML. Simply pass the desired format as part of the request. Zip-Tax.com works by submitting geographic information such as city, state, and zip code from your application or website. This data is used determine the correct sales tax information matching the provided location. Our service then returns that information to your application or website.

# Getting Started

> Request header requirement

```shell
curl --header "Accept:application/json"
```

The Zip-Tax.com sales tax API uses standard Representational State Transfer (REST) principles for maximum flexibility with a wide range of program languages.

To get started, simply follow this documentation to build a reuqest using the Zip-Tax.com Request URL, parse the API Response to validate the response codes, and use the API results in your application.

<aside class="notice">
For questions or comments about this documentation, please contact us at support@zip-tax.com.
</aside>

# API Subscription Types

## General API

The general Zip-Tax.com sales tax API allows jurisdiction lookups using any combination of zip code, city, and state. This API level does not provide full address level lookup and only provides county data via response. Note when using this method, multiple response values may be returned where multiple tax jurisdictions match the query inputs.

## Geo API (address level)

The GEO API version of Zip-Tax.com allows queries with full address lookup. This method returns only a single response with the address level sales tax jurisdiction in the response. This is the recommended subscription type for use with our API.

# Request

## Base URL

The API request URL is used to form your request to the API from your application.

The base request URL consists of three parts.

Subdomain | Action | Version
--------- | ------- | -----------
api.zip-tax.com | /request | /v40

### HTTP Request

> Base URL Example

```shell
curl --header "Accept:application/json" https://api.zip-tax.com/request/v40
```

`GET https://api.zip-tax.com/request/v40`

## General API

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
key | yes | Your API key
postalcode | yes | U.S. jurisdiction postal code (zip code)
state | optional | two letter state code i.e. CA = California
city | optional | full city name
format | optional | Default = json or specify xml

### Full Request Example (with query parameters)

> Request Example with Query Params

```shell
curl --header "Accept:application/json" https://api.zip-tax.com/request/v40?key=1234567890&postalcode=90264
```

This endpoint returns a sample request.

`GET https://api.zip-tax.com/request/v40?key=1234567890&postalcode=90264`


## Geo API

The Geo API requires an active GEO subscription. The API supports valid U.S addresses passed in as a single parameter, or split into multiple address parameters. Examples of both methods can be found below.

Note: The address parameter takes precedence. If present, the values of street, city, postalcode, and state are ignored.

### Split Address Parameters

Parameter | Required | Description
--------- | ------- | -----------
key | yes | Your API key
postalcode | yes | U.S. jurisdiction postal code (zip code)
street | optional | Full street address.
state | optional | two letter state code i.e. CA = California
city | optional | full city name
format | optional | Default = json or specify xml

This endpoint returns a sample request.

`GET https://api.zip-tax.com/request/v40?key=1234567890&street=1111%20S%20Figueroa%20St&city=Los%20Angeles&state=CA&postalcode=90015`

Note: All Parameters must be url encoded.

> Request Example with Split Address Query Params

```shell
curl --header "Accept:application/json" https://api.zip-tax.com/request/v40?key=1234567890&street=1111%20S%20Figueroa%20St&city=Los%20Angeles&state=CA&postalcode=90015
```

### Single Address Parameter

Parameter | Required | Description
--------- | ------- | -----------
key | yes | Your API key
address | yes | Full U.S. address

This endpoint returns a sample request.

`GET https://api.zip-tax.com/request/v40?key=1234567890&address=1111%20S%20Figueroa%20St,%20Los%20Angeles,%20CA%2090015`

Note: All Parameters must be url encoded.

> Request Example with Single Address Param

```shell
curl --header "Accept:application/json" https://api.zip-tax.com/request/v40?key=1234567890&address=1111%20S%20Figueroa%20St,%20Los%20Angeles,%20CA%2090015

# Response Results

> Sample Response (json)

```json
{
  "version": "v40",
  "rCode": 100,
  "results": [
  {
    "geoPostalCode": "90264",
    "geoCity": "MALIBU",
    "geoCounty": "LOS ANGELES",
    "geoState": "CA",
    "taxSales": 0.095,
    "taxUse": 0.095,
    "txbService": "N",
    "txbFreight": "N",
    "stateSalesTax": 0.06,
    "stateUseTax": 0.06,
    "citySalesTax": 0,
    "cityUseTax": 0,
    "cityTaxCode": "",
    "countySalesTax": 0.0025,
    "countyUseTax": 0.0025,
    "countyTaxCode": "19",
    "districtSalesTax": 0.0325,
    "districtUseTax": 0.0325,
    "district1Code": "218",
    "district1SalesTax": 0,
    "district1UseTax": 0,
    "district2Code": "594",
    "district2SalesTax": 0.0225,
    "district2UseTax": 0.0225,
    "district3Code": "",
    "district3SalesTax": 0,
    "district3UseTax": 0,
    "district4Code": "19",
    "district4SalesTax": 0.01,
    "district4UseTax": 0.01,
    "district5Code": "",
    "district5SalesTax": 0,
    "district5UseTax": 0,
    "originDestination": "D"
    }
  ]
}
```

Name | Description | Version
---- | ------ | -----------
geoPostalCode	| Requested postal code | all
geoCity	| City | all
geoCounty	| County | all
geoState | State | all
taxSales | Total sales tax | all
taxUse | Total use tax | all
txbService | Taxable service (values: null,Y,N,L) | all
txbFreight | Taxable freight (values: null,Y,N) | all
stateSalesTax | Portion of total sales tax from the state level | v20+ only
stateUseTax | Portion of total use tax from the state level	| v20+ only
citySalesTax | Portion of total sales tax from the city level | v20+ only
cityUseTax | Portion of total use tax from the city level | v20+ only
cityTaxCode | Applicable city tax code | v20+ only
countySalesTax | Portion of total sales tax from the county level | v20+ only
countyUseTax | Portion of total use tax from the county level | v20+ only
countyTaxCode | Applicable county tax code | v20+ only
districtSalesTax| Portion of total sales tax from the district level | v20+ only
districtUseTax | Portion of total use tax from the district level | v20+ only
district1Code | District 1 tax code | v40+ only
district1SalesTax | Portion of total sales tax from district 1 level | v40+ only
district1UseTax | Portion of total use tax from district 1 level | v40+ only
district2Code | District 2 tax code | v40+ only
district2SalesTax | Portion of total sales tax from district 2 level | v40+ only
district2UseTax | Portion of total use tax from district 2 level | v40+ only
district3Code | District 3 tax code | v40+ only
district3SalesTax | Portion of total sales tax from district 3 level | v40+ only
district3UseTax | Portion of total use tax from district 3 level | v40+ only
district4Code | District 4 tax code | v40+ only
district4SalesTax | Portion of total sales tax from district 4 level | v40+ only
district4UseTax | Portion of total use tax from district 4 level | v40+ only
district5Code | District 5 tax code | v40+ only
district5SalesTax | Portion of total sales tax from district 5 level | v40+ only
district5UseTax | Portion of total use tax from district 5 level | v40+ only
originDestination | Location where a sale is taxed origin/destination (values: null,D,O) | v40+ only

# Response Codes

The Zip-Tax.com API returns the following response codes based on request results.

Code | Reason | Description
---- | ------ | -----------
100 | SUCCESS | Successful API Requet
101 | INVALID_KEY | Key format is not valid
102 | INVALID_STATE | State format is not valid
103 | INVALID_CITY  |  City format is not valid
104 | INVALID_POSTAL_CODE | Postal code format is not valid
105 | INVALID_FORMAT  |  Query string format is not valid
106 | API_ERROR | Api error
107 | FEATURE_NOT_ENABLED | Requested feature or version not enabled
108 | REQUEST_LIMIT_MET | Api request limit met
109 | ADDRESS_INCOMPLETE  | Missing address parameters

# Support

For questions or comments please contact us via email at: support@zip-tax.com.
