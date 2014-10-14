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

Login Screen:

.. image:: images/ServerToServer_LoginScreen.png
.. image:: images/hipay_fullservice.png

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
state						transaction state.
							Value must be a member of the following list.
								-	completed
								-	pending
								-	declined
								-	error
								
							Please report to the following section below — Transaction Workflow — for further details.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
reason						optional element. Reason why transaction was declined.
--------------------------	-------------------------------------------------------------------------------------------------------------------------------------------------------------------
test						Payment Card Industry Data Security Standards
========================== 	===================================================================================================================================================================







