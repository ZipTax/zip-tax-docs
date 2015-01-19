Request URL
===========

The API request URL is used to form your request to the API from your application. 

.. note:: Please consult the documentation for your application language for making HTTP requests.

Base URL
--------

The base request URL consists of three parts.

+------------+-----------------+
| Subdomain  | api.zip-tax.com |
+------------+-----------------+
| Action     | /request        |
+------------+-----------------+
| Version    | /v20            |
+------------+-----------------+

These three parts form the basic URL for the API request::

	http://api.zip-tax.com/request/v20
	
Complete Request URL
-------------------

The Zip-Tax.com API URL consists of the following GET Request parameters which are used in the request.


+-------------+----------+-------------------------------------------------------------------+
| key         | required | Your account API key                                              |
+-------------+----------+-------------------------------------------------------------------+
| postal code | required | The 5 digit postal code. *NOTE: Include leading zeros*            |
+-------------+----------+-------------------------------------------------------------------+
| state       | optional | The 2 letter state code. *Example: CA for California*             |
+-------------+----------+-------------------------------------------------------------------+
| city        | optional | The full city name                                                |
+-------------+----------+-------------------------------------------------------------------+
| format      | optional | The return format. Valid formats are JSON or XML. *Default: JSON* |
+-------------+----------+-------------------------------------------------------------------+

Here is a sample of a fully formatted URL used in the request::

	http://api.zip-tax.com/request/v20?key=1234567890&postalcode=90265&state=CA&format=JSON
	
Use this url to make an HTTP GET request to the API. 

Check out the :doc:`api_response` documentation to learn more about the API response format.
