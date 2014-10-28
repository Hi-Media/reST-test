.. _Chap5-RedirectPages:

==============
Redirect Pages
==============

-----------------------------------------------
Redirect your customer to a page of your choice
-----------------------------------------------

Description
  The redirect pages are pages to which HiPay TPP redirects your customer's browser after
  the transaction is processed if it was made out of your website (:term:`hosted payment page`,
  local payments, :term:`3-D Secure` authentication, etc.).

Objective
  Typically, this is a secure page on your site. The main purpose is to redirect
  your customers back to your website once they have completed a payment.

--------------------
Redirect pages setup
--------------------

Description
  You can find redirect pages configuration over *Integration -> Redirect Pages* on your HiPay TPP back-office.
  You can overwrite the default redirect pages by sending custom URLs along with the order details in
  your requests to the payment gateway *(please refer to 3.1 section)*.

----------------------
Default redirect pages
----------------------

.. table::
  :class: table-with-wrap

  =====================  ===============================================================================================================================================================================================================================
  Field Name             Description
  =====================  ===============================================================================================================================================================================================================================
  Accept page            Page to redirect your customer if transaction was successful.
  Decline page           Page to redirect your customer if transaction was refused.
  Pending page           Page to redirect your customer if transaction is pending [1]_.
  :term:`Cancel` page    Page to redirect your customer if transaction was cancelled.
  Exception page         Page to which the customer's browser is redirected after a system failure or when the payment gateway is temporarily unavailable. If page is not defined, the default page for exceptions is displayed by the payment gateway.
  =====================  ===============================================================================================================================================================================================================================

-------------------
Feedback Parameters
-------------------

Description
  Select this option if you want that HiPay TPP send back the transaction parameters to your redirect pages
  for further processing within your own website.

Procedure
  To activate this option you MUST specify at least an *Accept Page* URL.
  Sent parameters are included in your redirect pages on HTTP GET.

-----------
Fields sent
-----------

The following table lists and describes the fields sent to your redirect pages.

.. table::
  :class: table-with-wrap

  ==========================  =================================================================================================================================================================================
  Field Name                  Description
  ==========================  =================================================================================================================================================================================
  orderid                     Unique identifier of the order as provided by Merchant.
  cid                         Unique identifier of the customer as provided by Merchant.
  state                       Transaction state. Value must be a member of the following list.

                              - completed
                              - pending
                              - declined
                              - error


                              Please report to the following section below - Transaction Workflow - for further details.
  --------------------------  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  status						Transaction status. A list of available statuses can be found in the appendices.
  --------------------------  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  test                        1 if the transaction is a testing transaction, otherwise 0.
  reference                   The unique identifier of the transaction.
  approval                    An :term:`authorization` code (up to 35 characters) generated for each approved or pending transaction by the acquiring provider.
  authorized                  Time when transaction was authorized.
  ip                          The IP address of the customer making the purchase.
  country                     Country code associated to the customer's IP address.
  lang                        Language code of the customer.
  email                       Email address of the customer.
  cdata1                      Custom data.
  cdata2                      Custom data.
  cdata3                      Custom data.
  cdata4                      Custom data.
  score                       Total score assigned to the transaction (main risk indicator).
  --------------------------  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  fraud                       The overall result of risk assessment returned by the Payment Gateway.

                              Value must be a member of the following list:

                              - pending:             rules were not checked.
                              - accepted:            transaction accepted.
                              - blocked:             transaction rejected due to system rules.
                              - :term:`challenged`:  transaction has been marked for review.
  --------------------------  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  review                      The decision made when the overall risk result returns challenged. An empty value means no review is required.

                              Value must be a member of the following list:

                              - Pending:  a decision to release or cancel the transaction is pending.
                              - Allowed:  the transaction has been released for processing.
                              - Denied:   the transaction has been cancelled.
  --------------------------  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  avscheck                    Result of the Address Verification Service (AVS). Possible result codes can be found in the appendices
  cvscheck                    Result of the CVC (Card Verification Code) check. Possible result codes can be found in the appendices
  pp                          Payment product used to complete the transaction. Informs about the payment_method section type.
  eci3ds                      The 3-D Secure (3DS) electronic commerce indicator
  veres                       The 3-D Secure (3DS) enrollment status.
  pares                       The 3-D Secure (3DS) authentication status. This field is only included if payment authentication was attempted and a value was received.
  cardtoken                   Card token.
  cardbrand                   Card brand. (e.g., VISA, MASTERCARD, AMERICANEXPRESS, MAESTRO).
  cardpan                     Card number (up to 19 characters).Note that, due to the :term:`PCI DSS` security standards, our system has to mask credit card numbers in any output (e.g., ``************4769``).
  cardexpiry                  Card expiry year and month (YYYYMM).
  cardcountry                 Bank country code where card was issued. This two-letter country code complies with ISO 3166-1 (alpha 2).
  ==========================  =================================================================================================================================================================================

.. rubric:: Footnotes

.. [1] Please refer to Appendix B Payment status definitions
