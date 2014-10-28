
----------------------------------------
Initialize a :term:`hosted payment page`
----------------------------------------

Introduction
  To perform a hosted payment page, first step consist to make an HTTP POST request to the following resource.
  POST /rest/v1/hpayment

Payment page Workflow
---------------------

Description
  This resource creates an order and returns a forward URL. This forward URL is dedicated to display a payment page with customers’ CSS and validated payment products. After payment form validation, the checkout is processed.
  According to transaction state and *authentication_indicator* parameter (*please refer to "3-D Secure" chapter on “GatewayAPI documentation"*), main window is redirect to accept or decline page.


Order on a Hosted Payment Page
------------------------------

.. table:: 
  :class: table-with-wrap

  ==============================  ===========  =======  ========  ===============================================================================
  Field Name                      Format [1]_  Length   Req [2]_  Description
  ==============================  ===========  =======  ========  ===============================================================================
  orderid                         AN           32       M         Unique order id
  ------------------------------  -----------  -------  --------  -------------------------------------------------------------------------------
  :term:`operation`               AN           32       M         Transaction type. Indicates how you want to process the payment. The default transaction type is set in the Merchant Interface (Default payment procedure in the Integration section). A transaction type sent along with the transaction will overwrite the default payment procedure.
  \                                                               - **Sale** indicates transaction is sent for authorization, and if approved, is automatically submitted for :term:`capture`.
  \                                                               - **:term:`Authorization`** indicates this transaction is sent for authorization only. The transaction will not be sent for settlement until the transaction is submitted for :term:`capture` manually by the Merchant.
  ------------------------------  -----------  -------  --------  -------------------------------------------------------------------------------
  :term:`eci`                     N            1                  Electronic Commerce Indicator (ECI).
                                                                  The ECI indicates the security level at which the payment information is processed between the cardholder and merchant.
                                                                  Possible values:
                                                                  1 = MO/TO (Card Not Present)
                                                                  7 = E-commerce with :term:`SSL`/TLS Encryption
                                                                  A default ECI value can be set in the preferences page. An ECI value sent along in the transaction will overwrite the default ECI value. Refer to the appendices — "Electronic Commerce Indicator” — on “GatewayAPI” documentation to get further information.
  ------------------------------  -----------  -------  --------  -------------------------------------------------------------------------------
  authentication_indicator        N            1                  Indicates if the :term:`3-D Secure` authentication should be performed for this transaction. Can be used to overrule the merchant level configuration.
                                                                  0 = Bypass authentication
                                                                  1 = Continue if possible
  ------------------------------  -----------  -------  --------  -------------------------------------------------------------------------------
  payment_product_list            AN           255                The payment product list separated by a “,” (e.g., visa,mastercard,american-express). *Refer to the appendices — " Appendix A— on “GatewayAPI” documentation for the full list of available payment products.*
  payment_product_category_list   AN           255                The payment product category list separated by “,”. (e.g., credit-card,ewallet). \Refer to the appendices — "Appendix A. Payment Products” — on “GatewayAPI” documentation for the full list of available payment categories.*
  css                             AN           255                URL to merchant style sheet. Important: H**TTPS** protocol is required.
  template                        AN           32                 The template name.
                                                                  Possible values:
                                                                  - basic-js = For a full page redirection.
                                                                  - iframe-js = For an iframe integration.
  merchant_display_name           AN           32                 The merchant name displayed on payment page, otherwise the name is retrieved from order.
  display_selector                N            1                  Enable/disable the payment products selector.
                                                                  Possible values:
                                                                  0 = The selector is not displayed
                                                                  1 = The selector is displayed
  multi_use                       N            1                  Indicates the tokenization module if the credit card token should be generated either for a single-use or a multi-use.
                                                                  Possible values:
                                                                  1 = Generate a multi-use token
                                                                  0 = Generates a single-use token.
                                                                  While a single-use token is typically generated for a short time and for processing a single transaction, multi-use tokens are generally generated for recurrent payments.
  description                     AN           255      M         The order short description.
  long_description                AN                              Additional order description.
  currency                        A            3        M         Base currency for this order (Default to EUR). This three-character currency code complies with ISO 4217.
  amount                          R                     M         The total order amount. It should be calculated as a sum of the items purchased, plus the shipping fee (if present), plus the tax fee (if present). Minimal amount 1.00 EUR.
  shipping                        R                               The order shipping fee (Default to zero). It can be omitted if the shipping fee value is zero.
  tax                             R                               The order tax fee (Default to zero). It can be omitted if the order tax value is zero.
  cid                             AN                    M         Unique customer id. *For fraud detection reasons.*
  ipaddr                          AN                    M         The IP address of your customer making a purchase.
  accept_url                      AN                    M         The URL to return your customer to once the payment process is completed successfully.
  decline_url                     AN                    M         The URL to return your customer to after the acquirer declines the payment.
  pending_url                     AN                    M         The URL to return your customer to when the payment request was submitted to the acquirer but response is not yet available.
  exception_url                   AN                    M         The URL to return your customer to after a system failure.
  cancel_url                      AN                    M         The URL to return your customer to when he or her decides to abort the payment.
  http_accept                     AN                              This element should contain the exact content of the HTTP "Accept" header as sent to the merchant from the customer's browser (Default to "*/*").
  http_user_agent                 AN                              This element should contain the exact content of the HTTP "User-Agent" header as sent to the merchant from the customer's browser (Default to "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0)").
  language                        AN                              Locale code of your customer (Default to en_GB – English – Great Britain). This will be used to display payment page in correct language.
                                                                  Examples:
                                                                  - en_GB
                                                                  - fr_FR
                                                                  - es_ES
                                                                  - it_IT
                                                                  - …
  cdata1                          AN                              Custom data. You may use these parameters to submit values you wish to receive back in the API response messages or in the notifications, e.g. you can use these parameters to get back session data, user info, etc.
  cdata2
  cdata3
  cdata4
  ==============================  ===========  =======  ========  ===============================================================================

Customer Parameters
-------------------

Overview
  The merchant can/must send the following customer information along with the transaction details.

.. table:: Table: Customer-related parameters
  :class: table-with-wrap

  ==============================  ===========  =======  ========  ===============================================================================
  Field Name                      Format [1]_  Length   Req [2]_  Description
  ==============================  ===========  =======  ========  ===============================================================================
  email                           AN                    M         The customer's e-mail address.
  phone                           AN                              The customer's phone number.
  birthdate                       N            8                  Birth date of the customer (YYYYMMDD). *For fraud detection reasons.*
  ------------------------------  -----------  -------  --------  -------------------------------------------------------------------------------
  gender                          A            1                  Gender of the customer (M=male, F=female, U=unknown).
  firstname                       AN                    M         The customer's first name.
  lastname                        AN                    M         The customer's last name.
  recipientinfo                   AN                              Additional information about the customer (e.g., quality or function, company name, department, etc.).
  streetaddress                   AN                              Street address of the customer.
  streetaddress2                  AN                              Additional address information of the customer (e.g., building, floor, flat, etc.).
  city                            AN                              The customer's city.
  state                           AN                              The USA state or the Canada state of the customer making the purchase. Send this information only if the address country of the customer is US (USA) or CA (Canada).
  zipcode                         AN                              The zip or postal code of the customer.
  country                         A            2        M         The country code of the customer. This two-letter country code complies with ISO 3166-1 (alpha 2).
  ==============================  ===========  =======  ========  ===============================================================================

.. table:: Table: Parameters specific to shipping information
  :class: table-with-wrap

  ========================  =======  =======  ========================================================================================================================================
  Parameter                 Format   Length   Description
  ========================  =======  =======  ========================================================================================================================================
  shipto_firstname           AN               The first name of the order recipient.
  shipto_lastname            AN               The last name of the order recipient.
  shipto_recipientinfo       AN               Additional information about the order recipient (e.g., quality or function, company name, department, etc.).
  shipto_streetaddress       AN               Street address to which the order is to be shipped.
  shipto_streetaddress2      AN               The additional information about address to which the order is to be shipped (e.g., building, floor, flat, etc.).
  shipto_city                AN               The city to which the order is to be shipped.
  shipto_state               AN               The USA state or Canada state to which the order is being shipped. Send this information only if the shipping country is US (USA) or CA (Canada).
  shipto_zipcode             AN               The zip or postal code to which the order is being shipped.
  shipto_country             AN       2       Country code to which the order is being shipped. This two-letter country code complies with ISO 3166-1 (alpha 2).
  ========================  =======  =======  ========================================================================================================================================

Response Fields
---------------

The following table lists and describes the response fields.

.. table:: 
  :class: table-with-wra

  ============================  =====================================================================================================================================
  Field Name                    Description
  ============================  =====================================================================================================================================
  forwardUrl (json)
  forward_url (xml)             The hosted payment page URL
  ----------------------------  -------------------------------------------------------------------------------------------------------------------------------------
  test                          True if the transaction is a testing transaction, otherwise false.
  mid                           Your merchant account number (issued to you by HiPay TPP).
  cdata1                        Custom data.
  cdata2                        Custom data.
  cdata3                        Custom data.
  cdata4                        Custom data.
  Order                         Information about the customer and his order.
  Id                            Unique identifier of the order as provided by Merchant.
  dateCreated (json)
  date_created (xml)            Time when order was created.
  attempts                      Indicates how many payment attempts have been made for this order.
  amount                        The total order amount (e.g., 150.00). It should be calculated as a sum of the items purchased, plus the shipping fee (if present), plus the tax fee (if present).
  shipping                      The order shipping fee.
  tax                           The order tax fee.
  decimals                      Decimal precision of the order amount.
  currency                      This three-character currency code complies with ISO 4217
  customerId (json)
  customer_id (xml)             Unique identifier of the customer as provided by Merchant.
  language                      Language code of the customer.
  email                         Email address of the customer.
  ============================  =====================================================================================================================================

Response Fields
---------------
Illustration

:Login Screen:

.. image:: images/payment_page.jpeg

Examples
---------
The following are :term:`CSS` examples to customize your payment page.

PHP Signature Validation

.. code-block:: css
    :linenos:

    client-logo {                         // Add merchant logo
       display: block;
       width: 261px;
         height: 100px;
         background: url(“https://mysite.com/img/mylogo.png”);
    }
    body.script-body {               // Add merchant background
        background-image: url("https://mysite.com/img/background.jpg");
        background-position: center top;
        background-repeat: no-repeat;
    }
    .prefilled {                         // Hide prefilled fields (like card holder)
        display: none;14
    }

.. rubric:: Footnotes

.. [1] The format of the element. Refer to "Table:Available formats of data elements” for the list of available formats.
.. [2] Specifies whether an element is required or not.
