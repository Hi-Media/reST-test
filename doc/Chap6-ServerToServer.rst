.. _Chap6-ServerToServer:

Chapter 6 - Server-to-Server
===========================

What is a Server-to-Server Notification?
----------------------------------------
:Description:
	In order to notify events related to your payment system, such as a new transaction 
	or a 3-D Secure transaction, our platform can send to your application
	a Server-to-Server notification.

Setup
-----
:Procedure:
	To set your Notification URL you must login into your Hipay TPP back office 
	and go to *Integration -> Notifications*.

:Login Screen:

.. image:: images/ServerToServer_LoginScreen.png

Configuration Parameters
------------------------
===================== 	===========================================================================
Field Name        		Description
===================== 	===========================================================================
Notification URL		The URL or IP on which you want to receive server-to-server notifications.
---------------------  	---------------------------------------------------------------------------
Request method			The method you wish to receive the requests:
							- XML
							- HTTP POST 
--------------------- 	---------------------------------------------------------------------------
Desired notifications	Payment Card Industry Data Security Standards
=====================  	===========================================================================

Response Fields
---------------
The following table lists and describes the response fields received on the notification call.

========================== 	===================================================================================================================================================================
Field Name        			Description
========================== 	===================================================================================================================================================================
state						transaction state. Value must be a member of the following list.
								-	completed
								-	pending
								-	declined
								-	error
								
							Please report to the following section below — Transaction Workflow — for further details.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
reason						optional element. Reason why transaction was declined.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
test						Payment Card Industry Data Security Standards
mid							your merchant account number (issued to you by HiPay TPP).
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
Attempt_id					attempt id of the payment.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
authorization_code			an authorization code (up to 35 characters) generated for each approved or pending transaction by the acquiring provider.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
transaction_rerefence		the unique identifier of the transaction.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
date_created				time when transaction was created.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
Date_updated				time when transaction was last updated.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
date_authorized				time when transaction was authorized.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
status						transaction status.
							A list of available statuses can be found in the appendices.
							appendices – Appendix B *Payment Status Definitions*.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
message						transaction message.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
authorized_amount			the transaction amount.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
captured_amount				captured amount.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
refunded_amount				refunded amount.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
decimals					decimal precision of transaction amount.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
currency					base currency for this transaction.
							This three-character currency code complies with ISO 4217.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
ip_address					the IP address of the customer making the purchase.				
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
ip_country					country code associated to the customer's IP address.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
device_id					unique identifier assigned to device (the customer's brower) by HiPay TPP.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
cdata1						custom data.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
cdata2						custom data.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
cdata3						custom data.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
cdata4						custom data.
-------------------------- 	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
avs_result					result of the Address Verification Service (AVS).
							Possible result codes can be found in the appendices
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
cvc_result					result of the CVC (Card Verification Code) check.
							Possible result codes can be found in the appendices
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------						
eci							Electronic Commerce Indicator (ECI).
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
payment_product				payment product used to complete the transaction.
							Informs about the payment_method section type
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
payment_method				See tables below for further details.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
Three_d_secure				optional element. Result of the 3-D Secure Authentication.
- eci						the 3-D Secure (3DS) electronic commerce indicator time when order was created.
- enrollment_status			the enrollment status. 
- enrollment_status 		the enrollment message
- authentication_status 	the authentication status. This field is only included if payment authentication was attempted and a value was received.
- authentication_message	the authentication message. This field is only included if payment authentication was attempted and a value was received.
_ authentication_token		this is a value generated by the card issuer as a token to prove that the cardholder was successfully authenticated.
- xid						a unique transaction identifier that is generated by the payment server on behalf of the merchant to identify the 3DS transaction.		
========================== 	===================================================================================================================================================================
