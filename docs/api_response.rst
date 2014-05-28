Response
========

Response Values
---------------

The API can be delivered in both JSON and XML formats by passing the desired format in the request. The API response will return a response code along with the API result set.

+------------------------------------------+---------------------------------------+
| **version**                              | The API version string [v10 or v20]   |
+------------------------------------------+---------------------------------------+
| **rCode** (json) or **code** (xml)       | The request response code             |
+------------------------------------------+---------------------------------------+
| **message**                              | Special service messages [deprecated] |
+------------------------------------------+---------------------------------------+
| **results** (json) or **response** (xml) | Special service messages [deprecated] |
+------------------------------------------+---------------------------------------+


Response Codes
--------------

This table represents the response codes [**rCode** (json) or **code** (xml)] returned from the API. 

.. note::

	The response codes are specific to the request and the response. The response codes do not relate to the result set.

+-----+---------------------+----------------------------------+
| 100 | SUCCESS             | Successful API Requet            |
+-----+---------------------+----------------------------------+
| 101 | INVALID_KEY         | Key format is not valid          |
+-----+---------------------+----------------------------------+
| 102 | INVALID_STATE       | State format is not valid        |
+-----+---------------------+----------------------------------+
| 103 | INVALID_CITY        | City format is not valid         |
+-----+---------------------+----------------------------------+
| 104 | INVALID_POSTAL_CODE | Postal code format is not valid  |
+-----+---------------------+----------------------------------+
| 105 | INVALID_FORMAT      | Query string format is not valid |
+-----+---------------------+----------------------------------+

For the API result documetation, please see the :doc:`api_results` section.

Response Results
----------------


JSON Sample Result
------------------


XML Sample Result
-----------------


