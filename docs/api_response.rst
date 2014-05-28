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

+---------+---------------------+----------------------------------+
| **100** | SUCCESS             | Successful API Requet            |
+---------+---------------------+----------------------------------+
| **101** | INVALID_KEY         | Key format is not valid          |
+---------+---------------------+----------------------------------+
| **102** | INVALID_STATE       | State format is not valid        |
+---------+---------------------+----------------------------------+
| **103** | INVALID_CITY        | City format is not valid         |
+---------+---------------------+----------------------------------+
| **104** | INVALID_POSTAL_CODE | Postal code format is not valid  |
+---------+---------------------+----------------------------------+
| **105** | INVALID_FORMAT      | Query string format is not valid |
+---------+---------------------+----------------------------------+


Response Results
----------------

+------------------+----------------------------------------------------+--------------+
| geoPostalCode    | Requested postal code                              | all versions |
+------------------+----------------------------------------------------+--------------+
| geoCity          | City                                               | all versions |
+------------------+----------------------------------------------------+--------------+
| geoCounty        | County                                             | all versions |
+------------------+----------------------------------------------------+--------------+
| geoState         | State                                              | all versions |
+------------------+----------------------------------------------------+--------------+
| taxSales         | Total sales tax                                    | all versions |
+------------------+----------------------------------------------------+--------------+
| taxUse           | Total use tax                                      | all versions |
+------------------+----------------------------------------------------+--------------+
| txbService       | Taxable service (values: null,Y,N,L)               | all versions |
+------------------+----------------------------------------------------+--------------+
| txbFreight       | Taxable freight (values: null,Y,N)                 | all versions |
+------------------+----------------------------------------------------+--------------+
| stateSalesTax    | Portion of total sales tax from the state level    | v20 only     |
+------------------+----------------------------------------------------+--------------+ 
| stateUseTax      | Portion of total use tax from the state level      | v20 only     |
+------------------+----------------------------------------------------+--------------+
| citySalesTax     | Portion of total sales tax from the city level     | v20 only     |
+------------------+----------------------------------------------------+--------------+
| cityUseTax       | Portion of total use tax from the city level       | v20 only     |
+------------------+----------------------------------------------------+--------------+
| cityTaxCode      | Applicable city tax code                           | v20 only     |
+------------------+----------------------------------------------------+--------------+
| countySalesTax   | Portion of total sales tax from the county level   | v20 only     |
+------------------+----------------------------------------------------+--------------+
| countyUseTax     | Portion of total use tax from the county level     | v20 only     |
+------------------+----------------------------------------------------+--------------+
| countyTaxCode    | Applicable county tax code                         | v20 only     |
+------------------+----------------------------------------------------+--------------+
| districtSalesTax | Portion of total sales tax from the district level | v20 only     |
+------------------+----------------------------------------------------+--------------+
| districtUseTax   | Portion of total use tax from the district level   | v20 only     |
+------------------+----------------------------------------------------+--------------+

JSON Sample Result
------------------
::

	{
	version: "v20",
	rCode: 100,
	results: [{
			geoPostalCode: "90265",
			geoCity: "MALIBU",
			geoCounty: "LOS ANGELES",
			geoState: "CA",
			taxSales: 0.090000003576279,
			taxUse: 0.090000003576279,
			txbService: "N",
			txbFreight: "N",
			stateSalesTax: 0.064999997615814,
			stateUseTax: 0.064999997615814,
			citySalesTax: 0,
			cityUseTax: 0,
			cityTaxCode: "",
			countySalesTax: 0.0099999997764826,
			countyUseTax: 0.0099999997764826,
			countyTaxCode: "19",
			districtSalesTax: 0.014999999664724,
			districtUseTax: 0.014999999664724
		},
		{
			geoPostalCode: "90265",
			geoCity: "PT DUME",
			geoCounty: "LOS ANGELES",
			geoState: "CA",
			taxSales: 0.090000003576279,
			taxUse: 0.090000003576279,
			txbService: "N",
			txbFreight: "N",
			stateSalesTax: 0.064999997615814,
			stateUseTax: 0.064999997615814,
			citySalesTax: 0,
			cityUseTax: 0,
			cityTaxCode: "",
			countySalesTax: 0.0099999997764826,
			countyUseTax: 0.0099999997764826,
			countyTaxCode: "19",
			districtSalesTax: 0.014999999664724,
			districtUseTax: 0.014999999664724
		},
		{
			geoPostalCode: "90265",
			geoCity: "TWAIN HARTE",
			geoCounty: "VENTURA",
			geoState: "CA",
			taxSales: 0.075000002980232,
			taxUse: 0.075000002980232,
			txbService: "N",
			txbFreight: "N",
			stateSalesTax: 0.064999997615814,
			stateUseTax: 0.064999997615814,
			citySalesTax: 0,
			cityUseTax: 0,
			cityTaxCode: "",
			countySalesTax: 0.0099999997764826,
			countyUseTax: 0.0099999997764826,
			countyTaxCode: "56",
			districtSalesTax: 0,
			districtUseTax: 0
		}]
	}

XML Sample Result
-----------------
::

	<?xml version="1.0" encoding="UTF-8" ?>
	<ziptax>
		<version>v20</version>
		<code>100</code>
		<message></message>
			<response>
			<geoPostalCode>90265</geoPostalCode>
			<geoCity>MALIBU</geoCity>
			<geoCounty>LOS ANGELES</geoCounty>
			<geoState>CA</geoState>
			<taxSales>0.090000003576279</taxSales>
			<taxUse>0.090000003576279</taxUse>
			<txbService>N</txbService>
			<txbFreight>N</txbFreight>
			<stateSalesTax>0.064999997615814</stateSalesTax>
			<stateUseTax>0.064999997615814</stateUseTax>
			<citySalesTax>0</citySalesTax>
			<cityUseTax>0</cityUseTax>
			<cityTaxCode></cityTaxCode>
			<countySalesTax>0.0099999997764826</countySalesTax>
			<countyUseTax>0.0099999997764826</countyUseTax>
			<countyTaxCode>19</countyTaxCode>
			<districtSalesTax>0.014999999664724</districtSalesTax>
			<districtUseTax>0.014999999664724</districtUseTax>
		</response>
			<response>
			<geoPostalCode>90265</geoPostalCode>
			<geoCity>PT DUME</geoCity>
			<geoCounty>LOS ANGELES</geoCounty>
			<geoState>CA</geoState>
			<taxSales>0.090000003576279</taxSales>
			<taxUse>0.090000003576279</taxUse>
			<txbService>N</txbService>
			<txbFreight>N</txbFreight>
			<stateSalesTax>0.064999997615814</stateSalesTax>
			<stateUseTax>0.064999997615814</stateUseTax>
			<citySalesTax>0</citySalesTax>
			<cityUseTax>0</cityUseTax>
			<cityTaxCode></cityTaxCode>
			<countySalesTax>0.0099999997764826</countySalesTax>
			<countyUseTax>0.0099999997764826</countyUseTax>
			<countyTaxCode>19</countyTaxCode>
			<districtSalesTax>0.014999999664724</districtSalesTax>
			<districtUseTax>0.014999999664724</districtUseTax>
		</response>
			<response>
			<geoPostalCode>90265</geoPostalCode>
			<geoCity>TWAIN HARTE</geoCity>
			<geoCounty>VENTURA</geoCounty>
			<geoState>CA</geoState>
			<taxSales>0.075000002980232</taxSales>
			<taxUse>0.075000002980232</taxUse>
			<txbService>N</txbService>
			<txbFreight>N</txbFreight>
			<stateSalesTax>0.064999997615814</stateSalesTax>
			<stateUseTax>0.064999997615814</stateUseTax>
			<citySalesTax>0</citySalesTax>
			<cityUseTax>0</cityUseTax>
			<cityTaxCode></cityTaxCode>
			<countySalesTax>0.0099999997764826</countySalesTax>
			<countyUseTax>0.0099999997764826</countyUseTax>
			<countyTaxCode>56</countyTaxCode>
			<districtSalesTax>0</districtSalesTax>
			<districtUseTax>0</districtUseTax>
		</response>
	</ziptax>

