.. _Chap3-RESTAPIResources:

==============================
Chapter 3 - REST API Resources
==============================

The following table lists the REST API resources used.

==================================================================  =======================================================
Resource        		                                            Description
==================================================================  =======================================================
**POST**  /rest/v1/order	                                        Request a new order.
**POST**  /rest/v1/maintenance/transaction/{transaction_reference}  Perform a maintenance on an existing transaction
**POST**  /rest/v1/hpayment		                                    Request an order and initialize a hosted payment page
**GET**   /rest/v1/transaction						                Request information about an existant transaction.
==================================================================  =======================================================

-------------------
Request a New Order
-------------------
Overview

  To request a new order, make an HTTP POST request to the following resource URL.
  POST /rest/v1/order 


Order Parameters
----------------
.. table:: Table:Order-related parameters

====================  =========   =======  ======  =====================================================================================================================================================================================================================================================================
Field Name        	  Format[1]   Length   Req[#]  Description
====================  =========   =======  ======  =====================================================================================================================================================================================================================================================================
orderid               AN          32       M       Unique order id     
operation             AN                           Transaction type.
                                                   Indicates how you want to process the payment. The default transaction type is set in the Merchant Interface (Default payment procedure in the Integration section). A transaction type sent along with the transaction will overwrite the default payment procedure.
                                                   - **Sale** indicates transaction is sent for authorization, and if approved, is automatically submitted for capture.
                                                   - **Authorization** indicates this transaction is sent for authorization only. The transaction will not be sent for settlement until the transaction is submitted for capture manually by the Merchant
payment_product       AN                   M       The payment product (e.g., visa, mastercard, ideal).
                                                   Depending on the payment product, elements specific to the payment method are required (see following tables).
                                                   Refer to the appendices —*"Appendix A. Payment Products”*— for the full list of available payment products. 
description           AN          255      M       The order short description.     
long_description      AN                           Additional order description. 
currency              A           3        M       Base currency for this order (Default to EUR).
                                                   This three-character currency code complies with ISO 4217.
amount                R                    M       The total order amount. It should be calculated as a sum of the items purchased, plus the shipping fee (if present), plus the tax fee (if present).      
shipping              R                            The order shipping fee (Default to zero).
                                                   It can be omitted if the shipping fee value is zero.
tax                   R                            The order tax fee (Default to zero).
                                                   It can be omitted if the order tax value is zero.
cid                   AN                   M       Unique customer id.
                                                   *For fraud detection reasons.*
ipaddr                AN                   M       The IP address of your customer making a purchase.      
accept_url            AN                           The URL to return your customer to once the payment process is completed successfully.      
decline_url           AN                           The URL to return your customer to after the acquirer declines the payment.      
pending_url           AN                           The URL to return your customer to when the payment request was submitted to the acquirer but response is not yet available.       
exception_url         AN                           The URL to return your customer to after a system failure.     
cancel_url            AN                           The URL to return your customer to when he or her decides to abort the payment.       
http_accept           AN                           This element should contain the exact content of the HTTP "Accept" header as sent to the merchant from the customer's browser (Default to "*/*").    
http_user_agent       AN                           This element should contain the exact content of the HTTP "User-Agent" header as sent to the merchant from the customer's browser (Default to "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0)").      
device_fingerprint    AN                           This element should contain the value of the “ioBB” hidden field. (Please refer to *“Chapter 8: Device fingerprint integration”*)   
language              AN                           Locale code of your customer (Default to **en_GB** – English – Great Britain).
                                                   It may be used for sending confirmation emails to your customer or for displaying payment pages.
                                                   
                                                   Examples:
                                                   - en_GB 
                                                   - fr_FR 
                                                   - es_ES 
                                                   - it_IT 
                                                   - …
cdata1                AN                           Custom data. You may use these parameters to submit values you wish to receive back in the API response messages or in the notifications, e.g. you can use these parameters to get back session data, order content or user info.       
cdata2                                             
cdata3                                             
cdata4                                             
====================  =========   =======  ======  =====================================================================================================================================================================================================================================================================

..[1] The format of the element. Refer to "Table:Available formats of data elements” for the list of available formats.
..[#] Specifies whether an element is required or not.

Customer Parameters
-------------------
Overview

  The merchant can/must send the following customer information along with the transaction details. 

The following table lists the customer related parameters

.. table:: Table:Customer-related parameter

====================  =========   =======  ======  =====================================================================================================================================================================
Field Name        	  Format[1]   Length   Req[#]  Description
====================  =========   =======  ======  =====================================================================================================================================================================
email                 AN                   M       The customer's e-mail address.     
phone                 AN                           The customer's phone number.
birthdate             N           8                Birth date of the customer (YYYYMMDD).
                                                   **For fraud detection reasons.**
birthdate             A           1                Gender of the customer (M=male, F=female, U=unknown).    
firstname	          AN                   M       The customer's first name. 
lastname              AN                   M       The customer's last name.
recipientinfo         AN                           Additional information about the customer (e.g., quality or function, company name, department, etc.).      
streetaddress         AN                           Street address of the customer.
                                                   It can be omitted if the shipping fee value is zero.
streetaddress2        AN                           Additional address information of the customer (e.g., building, floor, flat, etc.).
city                  AN                           The customer's city.
state                 AN                           The USA state or the Canada state of the customer making the purchase. Send this information only if the address country of the customer is US (USA) or CA (Canada). 
zipcode               AN                           The zip or postal code of the customer.     
country               A           2        M       The country code of the customer.
                                                   This two-letter country code complies with ISO 3166-1 (alpha 2).                                  
====================  =========   =======  ======  =====================================================================================================================================================================

..[1] The format of the element. Refer to "Table:Available formats of data elements” for the list of available formats.
..[#] Specifies whether an element is required or not.


The following table lists the Parameters specific to shipping information

.. table:: Table:Parameters specific to shipping information

======================  =========  =======  =====================================================================================================================================================================
Field Name        	    Format     Length   Description                                                                                                                                                          
======================  =========  =======  =====================================================================================================================================================================
shipto_firstname        AN                  T                                                                                                                                       
shipto_lastname         AN                  The customer's phone number.                                                                                                                                         
shipto_recipientinfo    AN                  Birth date of the customer (YYYYMMDD).                                                                                                                               
                                            **For fraud detection reasons.**                                                                                                                                     
shipto_streetaddress    AN                  Gender of the customer (M=male, F=female, U=unknown).                                                                                                                
shipto_streetaddress2   AN                  The customer's first name.                                                                                                                                           
shipto_city             AN                  The customer's last name.                                                                                                                                            
shipto_state            AN                  Additional information about the customer (e.g., quality or function, company name, department, etc.).                                                               
shipto_zipcode          AN                  Street address of the customer.                                                                                                                                      
                                            It can be omitted if the shipping fee value is zero.                                                                                                                 
shipto_country          A           2       Additional address information of the customer (e.g., building, floor, flat, etc.).                                                                                  
======================  =========  =======  =====================================================================================================================================================================

..[1] The format of the element. Refer to "Table:Available formats of data elements” for the list of available formats.
..[#] Specifies whether an element is required or not.












	
	
 	
	
	
		
		