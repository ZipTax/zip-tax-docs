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

Welcome to the Zip-Tax.com Sales Tax API

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
api.zip-tax.com | /request | /v30

### HTTP Request

> Base URL Example

```shell
curl --header "Accept:application/json" https://api.zip-tax.com/request/v30
```

`GET https://api.zip-tax.com/request/v30`

### Query Parameters (body data)

Parameter | Required | Description
--------- | ------- | -----------
key | yes | Your API key
postalcode | yes | U.S. jurisdiction postal code (zip code)
state | optional | two letter state code i.e. CA = California
city | optional | full city name
format | optional | Default = json or specify xml

### Additional Query Parameters (requires geo plan)

Parameter | Required | Description
--------- | ------- | -----------
address | optional | Full address. Available only with GEO subscription.


## Full Request Example (with query parameters)

> Request Example with Query Params

```shell
curl --header "Accept:application/json" https://api.zip-tax.com/request/v30?key=1234567890&postalcode=90264
```

This endpoint returns a sample request.

`GET https://api.zip-tax.com/request/v30?key=1234567890&postalcode=90264`

# Response Codes

The Zip-Tax.com API returns the following response codes based on request results.


Code | Reason | Description
---- | ------ | -----------
100 |	SUCCESS	| Successful API Requet
101	| INVALID_KEY	| Key format is not valid
102	| INVALID_STATE	| State format is not valid
103	| INVALID_CITY	| City format is not valid
104	| INVALID_POSTAL_CODE	| Postal code format is not valid
105 | INVALID_FORMAT | Query string format is not valid

# Response Results

> Sample Response (json)

```json
{
  "version": "v30",
  "rCode": 100,
  "results": [
    {
      "geoPostalCode": "90264",
      "geoCity": "MALIBU",
      "geoCounty": "LOS ANGELES",
      "geoState": "CA",
      "taxSales": 0.0925,
      "taxUse": 0.0925,
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
      "districtSalesTax": 0.03,
      "districtUseTax": 0.03
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
districtSalesTax | Portion of total sales tax from the district level | v20+ only
districtUseTax | Portion of total use tax from the district level | v20+ only

# Support

For questions or comments please contact us via email at: support@zip-tax.com.
