.. _Chap5-RedirectPages:

Chapter 5 - Redirect Pages
===========================

Redirect your customer to a page of your choice
------------------------------------------------
:Description:
	The redirect pages are pages to which HiPay TPP redirects your customer's brower after
	the transaction is processed if it was made out of your website (hosted payment page, 
	local payments, 3-D Secure authentication, etc.).

:Objective:
	Typically, this is a secure page on your site. The main purpose is to redirect 
	your customers back to your website once they have completed a payment.

	
Redirect pages setup
--------------------
:Description:
	You can find redirect pages configuration over *Intergation -> Redirect Pages* on your HiPay TPP back-office.
	You can overwrite the default redirect pages by sending custom URLs along with the order details in 
	your requests to the payment gateway *(please refer to 3.1 section)*.

	
Default redirect pages
-----------------------
===================== 	===========================================================================
Field Name        		Description
===================== 	===========================================================================
Accept page				Page to redirect your customer if transaction was successful.
Decline page			Page to redirect your customer if transaction was refused.
Pending page			Page to redirect your customer if transaction is pending .
Cancel page				Page to redirect your customer if transaction was cancelled.
Exception page			Page to which the customer's browser is redirected after a system failure or when the payment gateway is temporarily unavailable.
							If page is not defined, the default page for exceptions is displayed by the payment gateway.
=====================  	===========================================================================

Feedback Parameters
-------------------

:Description:
	Select this option if you want that HiPay TPP send back the transaction parameters to your redirect pages
	for further processing within your own website.

:Procedure:
	To activate this option you “MUST” specify at least an “Accept Page” URL.
	Sent parameters are included in your redirect pages on HTTP GET.

Fields sent
-----------

The following table lists and describes the fields sent to your redirect pages.
========================== 	===================================================================================================================================================================
Field Name        			Description
========================== 	===================================================================================================================================================================
orderid						unique identifier of the order as provided by Merchant.
cid							unique identifier of the customer as provided by Merchant.
state						transaction state. Value must be a member of the following list.
								-	completed
								-	pending
								-	declined
								-	error
								
							Please report to the following section below — Transaction Workflow — for further details.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
status						transaction status. A list of available statuses can be found in the appendices.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
test						1 if the transaction is a testing transaction, otherwise 0.
reference					the unique identifier of the transaction.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
approval					an authorization code (up to 35 characters) generated for each approved or pending transaction by the acquiring provider.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
authorized					time when transaction was authorized.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
ip							the IP address of the customer making the purchase.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
country						country code associated to the customer's IP address.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
lang						language code of the customer.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
email						email address of the customer.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
cdata1						custom data.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
cdata2						custom data.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
cdata3						custom data.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
cdata4						custom data.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
score						total score assigned to the transaction (main risk indicator).
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
fraud						The overall result of risk assessment returned by the Payment Gateway.
								Value must be a member of the following list.
									-	pending 	:rules were not checked.
									-	accepted	:transaction accepted.
									-	blocked		:transaction rejected due to system rules.
									-	challenged	:transaction has been marked for review.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------						
review						The decision made when the overall risk result returns challenged. An empty value means no review is required.
								Value must be a member of the following list.
									-	Pending 	:a decision to release or cancel the transaction is pending.
									-	allowed	 	:the transaction has been released for processing.
									-	Denied		:the transaction has been cancelled.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
avscheck				    result of the Address Verification Service (AVS). Possible result codes can be found in the appendices
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
cvscheck					result of the CVC (Card Verification Code) check. Possible result codes can be found in the appendices
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
pp							payment product used to complete the transaction. Informs about the payment_method section type.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
eci3ds						the 3-D Secure (3DS) electronic commerce indicator
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
veres						the 3-D Secure (3DS) enrollment status.
pares						the 3-D Secure (3DS) authentication status. This field is only included if payment authentication was attempted and a value was received.
cardtoken					card token.
cardbrand					card brand. (e.g., VISA, MASTERCARD, AMERICANEXPRESS, MAESTRO).
cardpan						card number (up to 19 characters).Note that, due to the PCI DSS security standards, our system has to mask credit card numbers in any output (e.g., ************4769).
cardexpiry					card expiry year and month (YYYYMM).
cardcountry					bank country code where card was issued. This two-letter country code complies with ISO 3166-1 (alpha 2).

========================== 	===================================================================================================================================================================

Response fields specific to the payment product
-----------------------------------------------

:Credit Card payments:
		The following table lists and describes the response fields returned for transactions by credit/debit card.
	
========================== 	===================================================================================================================================================================
Field Name        			Description
========================== 	===================================================================================================================================================================
token 						Card token.
brand 						Card brand. (e.g., VISA, MASTERCARD, AMERICANEXPRESS, MAESTRO).
pan 						Card number (up to 19 characters). Note that, due to the PCI DSS security standards, our system has to mask credit card numbers in any output (e.g., 549619******4769).
card_holder 				Cardholder name.
card_expiry_month 			Card expiry month (2 digits).
card_expiry_year 			Card expiry year (4 digits).
issuer 						Card issuing bank name. Do not rely on this value to remain static over time. Bank names may change over time due to acquisitions and mergers.
country 					Bank country code where card was issued. This two-letter country code complies with ISO 3166-1 (alpha 2).
========================== 	===================================================================================================================================================================

:QIWI payments:
		The following table lists and describes the response fields returned for transactions by VISA QIWI Wallet.

========================== 	===================================================================================================================================================================
Field Name        			Description
========================== 	===================================================================================================================================================================
user						The Qiwi user's ID, to whom the invoice is issued. It is the user's phone number, in international format. Example: +79263745223
========================== 	===================================================================================================================================================================

Transaction Workflow
--------------------

:Description:
		The HiPay TPP payment gateway can process transactions through many different acquirers using different payment methods and involving some anti-fraud checks. 
		All these aspects change the transaction processing flow significantly for you.
		When you activate a server-to-server notification on Hipay TPP, you receive a response describing the transaction state. 
		Depending on the transaction state there are five options to action:

========================== 	===================================================================================================================================================================
Transaction state   		Description
========================== 	===================================================================================================================================================================
completed 					if the transaction state is completed you are done. This is the most common case for credit card transaction processing. Almost all credit card acquirers works in that way. Then you have to look into the status fied of the response to know the exact transaction status.
pending 					Transaction request was submitted to the acquirer but response is not yet available.
declined  					Transaction was processed and was declined by gateway.
error 						Transaction was not processed due to some reasons.
========================== 	===================================================================================================================================================================

Examples
--------

The following are examples XML and HTTP Post responses.

:XML Response Example:
		
.. code-block:: xml
    :linenos:

  	<?xml version="1.0" encoding="UTF-8"?>
  	<notification>
   	  <state>completed</state>
  	  <reason/>
   	  <test>true</test>
   	  <mid>00001326581</mid>
   	  <attempt_id>1</attempt_id>
   	  <authorization_code>test123</authorization_code>
   	  <transaction_reference>388997073285</transaction_reference>
   	  <date_created>2012-10-14T12:29:51+0000</date_created>
   	  <date_updated>2012-10-14T12:29:55+0000</date_updated>
   	  <date_authorized>2012-10-14T12:29:54+0000</date_authorized>
   	  <status>117</status>
   	  <message>Capture Requested</message>
   	  <authorized_amount>5.00</authorized_amount>
   	  <captured_amount>5.00</captured_amount>
   	  <refunded_amount>0.00</refunded_amount>
   	  <decimals>2</decimals>
   	  <currency>EUR</currency>
   	  <ip_address>83.167.62.196</ip_address>
   	  <ip_country>FR</ip_country>
   	  <device_id/>
   	  <cdata1><![CDATA[My data 1]]></cdata1>
   	  <cdata2><![CDATA[My data 2]]></cdata2>
   	  <cdata3><![CDATA[My data 3]]></cdata3>
   	  <cdata4><![CDATA[My data 4]]></cdata4>
   	  <avs_result/>
   	  <cvc_result/>
   	  <eci>9</eci>
   	  <payment_product>visa</payment_product>
   	  <payment_method>
   	    <token>ce5x096fx6xx05989x170x7x96f94432600491xx</token>
   	    <brand>VISA</brand>
   	    <pan>400000******0000</pan>
   	    <card_holder>Jhon Doe</card_holder>
   	    <card_expiry_month>07</card_expiry_month>
   	    <card_expiry_year>2015</card_expiry_year>
   	    <issuer>MY BANK</issuer>
   	    <country>FR</country>
   	  </payment_method>
   	  <three_d_secure>
   	    <eci>5</eci>
   	    <enrollment_status>Y</enrollment_status>
   	    <enrollment_message>Authentication Available</enrollment_message>
   	    <authentication_status>Y</authentication_status>
   	    <authentication_message>Authentication Successful</authentication_message>
   	    <authentication_token></authentication_token>
   	    <xid></xid>
   	  </three_d_secure>
   	  <fraud_screening>
   	    <scoring>120</scoring>
   	    <result>accepted</result>
   	    <review/>
   	  </fraud_screening>
   	  <order>
   	    <id>1381753783</id>
   	    <date_created>2012-10-14T12:29:51+0000</date_created>
   	    <attempts>1</attempts>
   	    <amount>5.00</amount>
   	    <shipping>10.00</shipping>
   	    <tax>0.98</tax>
   	    <decimals>2</decimals>
   	    <currency>EUR</currency>
   	    <customer_id>UID1381753791</customer_id>
   	    <language>fr_FR</language>
   	    <email>customer@mail.com</email>
   	  </order>
   	</notification>

:HTTP POST Response Example:
		
.. code-block:: xml
    :linenos:

   	state = completed
  	reason = 
  	test = false
  	mid = 00001326581
   	attempt_id = 1
   	authorization_code = test123
   	transaction_reference = 781357613392
   	date_created = 2012-10-14T13:10:36+0000
   	date_updated = 2012-10-14T13:10:38+0000
   	date_authorized = 2012-10-14T13:10:38+0000
   	status = 116
   	message = Authorized
   	authorized_amount = 5.00
   	captured_amount = 0.00
   	refunded_amount = 0.00
  	decimals = 2
   	currency = EUR
   	ip_address = 83.167.62.196
   	ip_country = FR
   	device_id = 
   	cdata1 = My data 1
   	cdata2 = My data 2
   	cdata3 = My data 3
   	cdata4 = My data 4
   	avs_result = 
   	cvc_result = 
   	eci = 7
   	payment_product = visa
   	payment_method[token] = ce5x096fx6xx05989x170x7x96f94432600491xx
   	payment_method[brand] = VISA
   	payment_method[pan] = 400000******0000
   	payment_method[card_holder] = Jhon Doe
   	payment_method[card_expiry_month] = 07
   	payment_method[card_expiry_year] = 2015
   	payment_method[issuer] = MYBANK 
   	payment_method[country] = FR 
   	three_d_secure[eci] = 5
   	three_d_secure[enrollment_status] = Y
   	three_d_secure[enrollment_message]=Authentication Available
   	three_d_secure[authentication_status]=Y
   	three_d_secure[authentication_message]=Authentication Successful
   	three_d_secure[authentication_token]=
   	three_d_secure[xid]=
   	fraud_screening[scoring] = 120
   	fraud_screening[result] = accepted
   	fraud_screening[review] = 
   	order[id] = 1381756231
   	order[date_created] = 2013-10-14T13:10:36+0000
   	order[attempts] = 1
   	order[amount] = 5.00
   	order[shipping] = 10.00
   	order[tax] = 0.98
   	order[decimals] = 2
   	order[currency] = EUR
   	order[customer_id] = UID1381756236
   	order[language] = fr_FR
   	order[email] = customer@mail.com

	
	
 	
	
	
		
		