
----------------------
Maintenance Operations
----------------------

Description
  To perform maintenance on an existing transaction, make an HTTP POST request to the following resource (see :term:`Operation`)
  
  ``POST /rest/v1/maintenance/transaction/{transaction_reference}``

The payment gateway supports the following types of maintenance transactions.

.. _Types of maintenance transactions:

.. table:: Table: Types of maintenance transactions
  :class: table-with-wrap

  ==================  =============================================================================================================================================================================================================================================
  Operation Type      Description
  ==================  =============================================================================================================================================================================================================================================
  :term:`capture`     A request instructing the payment gateway to capture a previously-authorized transaction, i.e. transfer the funds from the customer's bank account to the merchant's bank account. This transaction is always preceded by an authorization.
  :term:`refund`      A request instructing the payment gateway to refund a previously captured transaction. A captured transaction can be partly or fully refunded.
  :term:`cancel`      A request instructing the payment gateway to cancel a previously-authorized transaction. Only authorized transactions can be canceled, captured transactions must be refunded.
  ==================  =============================================================================================================================================================================================================================================

URL Parameters
--------------

=========================  =======  =======  ====  =================================
Parameter                  Format   Length   Req   Description
=========================  =======  =======  ====  =================================
{transaction_reference}    N                 M     The unique identifier of the transaction.
=========================  =======  =======  ====  =================================

Request Parameters
------------------

.. table::
  :class: table-with-wrap

  =========================  =======  =======  ====  =================================
  Parameter                  Format   Length   Req   Description
  =========================  =======  =======  ====  =================================
  :term:`operation`          A                 M     The type of operation to process.

                                                     For further information, report to the previous table - :ref:`Types of maintenance transactions`
  amount                     R                 C     Operation amount (e.g., 10.00).

                                                     Amount is required for partial maintenances. Do not specify amount for full captures or refunds.
  =========================  =======  =======  ====  =================================

Response Fields
---------------

The following table lists and describes the response fields.

.. table::
  :class: table-with-wrap

  ============================  =====================================================================================================================================
  Field Name                    Description
  ============================  =====================================================================================================================================
  :term:`operation`             Value is fixed to :term:`capture`, :term:`refund` or :term:`cancel`
  ----------------------------  -------------------------------------------------------------------------------------------------------------------------------------
  test                          True if the transaction is a testing transaction, otherwise false.
  mid                           Your merchant account number (issued to you by HiPay TPP).
  ----------------------------  -------------------------------------------------------------------------------------------------------------------------------------
  authorizationCode (json)
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------
  authorization_code (xml)      An :term:`authorization` code (up to 35 characters) generated for each approved or pending transaction by the acquiring provider.
  ----------------------------  -------------------------------------------------------------------------------------------------------------------------------------
  transactionReference (json)
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------
  transaction_reference (xml)   The unique identifier of the transaction.
  ----------------------------  -------------------------------------------------------------------------------------------------------------------------------------
  dateCreated (json)
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------
  date_created (xml)            Time when transaction was created.
  ----------------------------  -------------------------------------------------------------------------------------------------------------------------------------
  dateUpdated (json)
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------
  date_updated (xml)            Time when transaction was last updated (maintenance date).
  ----------------------------  -------------------------------------------------------------------------------------------------------------------------------------
  dateAuthorized (json)
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------
  date_authorized (xml)         Time when transaction was authorized.
  ----------------------------  -------------------------------------------------------------------------------------------------------------------------------------
  status                        Transaction status. A list of available statuses can be found in the appendices.
  message                       Transaction message.
  ----------------------------  -------------------------------------------------------------------------------------------------------------------------------------
  authorizedAmount (json)
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------
  authorized_amount (xml)       The transaction amount.
  ----------------------------  -------------------------------------------------------------------------------------------------------------------------------------
  capturedAmount (json)
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------
  captured_amount (xml)         The captured amount.
  ----------------------------  -------------------------------------------------------------------------------------------------------------------------------------
  refundedAmount
  refunded_amount (xml)         The refunded amount.
  ----------------------------  -------------------------------------------------------------------------------------------------------------------------------------
  decimals                      Decimal precision of transaction amount.
  currency                      Base currency for this transaction. This three-character currency code complies with ISO 4217.
  ============================  =====================================================================================================================================

Examples
--------

The following are examples JSON and XML responses.

Example Request

.. code-block:: ini
    :linenos:

  	$ curl https://secure-gateway.allopass.com/rest/v1/maintenance/transaction/432241108734 \
  	    -u "<your API username>:<your API password>" \
   	    -X POST \
   	    -d "operation=capture" \
   	    -d "amount=10.00"


XML Response Example

.. code-block:: xml
    :linenos:

   	<response>
   	  <operation>capture</operation>
   	  <test>false</test>
   	  <mid>00001234567</mid>
   	  <authorization_code>549554</authorization_code>
   	  <transaction_reference>432241108734</transaction_reference>
   	  <date_created>2013-03-07T12:31:09+0000</date_created>
   	  <date_updated>2013-03-07T15:44:08+0000</date_updated>
   	  <date_authorized>2013-03-07T12:31:12+0000</date_authorized>
   	  <status>117</status>
   	  <message>Capture Requested</message>
   	  <authorized_amount>460.50</authorized_amount>
   	  <captured_amount>40.00</captured_amount>
   	  <refunded_amount>0.00</refunded_amount>
   	  <decimals>2</decimals>
   	  <currency>EUR</currency>
   	</response>

JSON Response Example

.. code-block:: json
    :linenos:

   	{
   	  "operation":"capture",
   	  "test":"false",
   	  "mid":"00001234567",
   	  "authorizationCode":"549554",
   	  "transactionReference":"432241108734",
   	  "dateCreated":"2013-03-07T12:31:09+0000",
   	  "dateUpdated":"2013-03-07T15:48:28+0000",
   	  "dateAuthorized":"2013-03-07T12:31:12+0000",
   	  "status":"117",
   	  "message":"Capture Requested",
   	  "authorizedAmount":"460.50",
   	  "capturedAmount":"50.00",
   	  "refundedAmount":"0.00",
   	  "decimals":"2",
   	  "currency":"EUR"
	}

.. rubric:: Footnotes

.. [1] The format of the element. Refer to "Table:Available formats of data elements” for the list of available formats.
.. [2] Specifies whether an element is required or not.
