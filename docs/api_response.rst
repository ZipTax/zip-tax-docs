Response
========

The Zip-Tax.com response can be delivered in both JSON and XML formats by passing the desired format in the request. The API response will return a :doc:api_response_codes along with the :doc:api_results.

+------------------------------------------+---------------------------------------+
| **version**                              | The API version string [v10 or v20]   |
+------------------------------------------+---------------------------------------+
| **rCode** (JSON) or **code** (XML)       | The request response code             |
+------------------------------------------+---------------------------------------+
| **message**                              | Special service messages [deprecated] |
+------------------------------------------+---------------------------------------+
| **results** (JSON) or **response** (XML) | Special service messages [deprecated] |
+------------------------------------------+---------------------------------------+

