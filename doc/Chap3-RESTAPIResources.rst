.. _Chap3-RESTAPIResources:

==================
REST API Resources
==================

The following table lists the REST API resources used.

==================================================================  =======================================================
Resource        		                                            Description
==================================================================  =======================================================
**POST**  /rest/v1/order	                                        Request a new order.
**POST**  /rest/v1/maintenance/transaction/{transaction_reference}  Perform a maintenance on an existing transaction
**POST**  /rest/v1/hpayment		                                    Request an order and initialize a :term:`hosted payment page`
**GET**   /rest/v1/transaction						                Request information about an existant transaction.
==================================================================  =======================================================

**Contents:**

.. toctree::
    :maxdepth: 2

    Chap3-RESTAPIResources-requestNewOrder
    Chap3-RESTAPIResources-maintenanceOperations
    Chap3-RESTAPIResources-initializeHostedPaymentPage
    Chap3-RESTAPIResources-requestDetails
