
------------------------------------------
Request details of an existing transaction
------------------------------------------
Description
  To consult the details of an existing transaction, make an HTTP GET request to the following resource.
  GET /rest/v1/transaction

URL Parameters
--------------

.. table::
  :class: table-with-wrap

  ==========================  ===========  =======  ========  ===============================================================================
  Field Name        	      Format [1]_  Length   Req [2]_  Description
  ==========================  ===========  =======  ========  ===============================================================================
  {transaction_reference}     N                               The unique identifier of the transaction.

                                                              Return the detail of an specific transaction. Please refer to the example to see the request rules.
  orderid                     AN            32                Merchant unique order id.

                                                              Return all the transactions related to an order id. Please refer to the example to see the request rules.
  ==========================  ===========  =======  ========  ===============================================================================

Response Fields
---------------

Please refer to section	on :ref:`Request a New Order` sub-chapter.

Examples
--------

The following are examples JSON and XML responses.

Transaction reference example Request:

.. code-block:: bash
    :linenos:

    $ curl https://secure-gateway.allopass.com/rest/v1/transaction/432241108734 \
        -u "<your API username>:<your API password>"

Order ID example Request:

.. code-block:: bash
    :linenos:

    $ curl https://secure-gateway.allopass.com/rest/v1/transaction?orderid=52035cec9bb77 \
        -u "<your API username>:<your API password>"

XML Response Example:

.. code-block:: xml
    :linenos:

    <response>
     <transaction>
       <state>completed</state>
       <reason/>
       <forward_url/>
       <test>true</test>
       <mid>00000000316</mid>
       <attempt_id>1</attempt_id>
       <authorization_code>no code</authorization_code>
       <transaction_reference>112822568975</transaction_reference>
       <date_created>2013-08-08T08:55:09+0000</date_created>
       <date_updated>2013-08-08 10:55:13+02</date_updated>
       <date_authorized>2013-08-08T08:55:13+0000</date_authorized>
       <status>116</status>
       <message>Authorized</message>
       <authorized_amount>2.00</authorized_amount>
       <captured_amount>0.00</captured_amount>
       <refunded_amount>0.00</refunded_amount>
       <decimals>2</decimals>
       <currency>EUR</currency>
       <ip_address>0.0.0.0</ip_address>
       <ip_country/>
       <device_id/>
       <cdata1><![CDATA[my data 1]]></cdata1>
       <cdata2><![CDATA[my data 2]]></cdata2>
       <cdata3><![CDATA[my data 3]]></cdata3>
       <cdata4><![CDATA[my data 4]]></cdata4>
       <avs_result/>
       <cvc_result/>
       <eci>7</eci>
       <payment_product>cb</payment_product>
       <payment_method>
         <token>6ce4138d2dc6377738cxxxxxxxxx424a2608ad</token>
         <brand>VISA</brand>
         <pan>411278******0544</pan>
         <card_holder>Jhon Doe</card_holder>
         <card_expiry_month>01</card_expiry_month>
         <card_expiry_year>2015</card_expiry_year>
         <issuer/>
         <country>FR</country>
       </payment_method>
       <three_d_secure/>
       <fraud_screening>
         <scoring>20</scoring>
         <result>accepted</result>
         <review/>
       </fraud_screening>
       <order>
         <id>52035cec9bb77</id>
         <date_created>2013-08-08T08:54:25+0000</date_created>
         <attempts>1</attempts>
         <amount>2.00</amount>
         <shipping>0.00</shipping>
         <tax>0.00</tax>
         <decimals>2</decimals>
         <currency>EUR</currency>
         <customer_id>52035cec9be4b</customer_id>
         <language>fr_FR</language>
         <email>customer@mail.com</email>
       </order>
     </transaction>
    </response>

.. rubric:: Footnotes

.. [1] The format of the element. Refer to "Table:Available formats of data elements” for the list of available formats.
.. [2] Specifies whether an element is required or not.
