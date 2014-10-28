.. _AppendixF-DeclineReasonsAndErrorCodes:

=============================================
Appendix F - Decline Reasons And Error Codes
=============================================

The HiPay TPP payment gateway can return multiple errors for any operation.

.. table:: Table: Configuration errors
  :class: table-with-wrap
  
  ========  ===============================  ========================================================================  ===================================
  Code      Message                          Description                                                               Correcting this error
  ========  ===============================  ========================================================================  ===================================
  1000001   Incorrect Credentials	         Username and/or password is incorrect	                                   This error can be caused by an incorrect API username or an incorrect API password. Make sure that all of these values are correct. For your security, HiPay TPP does not report exactly which of these values might be erroneous. This error can be caused by an incorrect API username or an incorrect API password. Make sure that all of these values are correct. 	           This error can be caused by an incorrect API username or an incorrect API password. Make sure that all of these values are correct. For your security, HiPay TPP does not report exactly which of these values might be erroneous.
  1000002   Incorrect Signature              The :term:`signature` that was sent does not match the requested format.	
  1000003   Account Not Active               Account is inactive
  1000004   Account Locked                   Account is locked
  1000005   Insufficient Permissions         You do not have permission to make this API call
  1000006   Forbidden Access                 API access is disabled for this account
  1000007   Unsupported Version              API version is not supported
  1000008   Temporarily Unavailable          The gateway is temporarily unavailable                                    Please try later
  1000009   Not Allowed                      The request was rejected due to :term:`IP restriction`.                   Ensure the IP addresses of your servers are configured for your account.
  ========  ===============================  ========================================================================  ===================================


.. table:: Table: Validation errors
  :class: table-with-wrap
  
  ========  ===============================  ========================================================================
  Code      Message                          Description                                                            
  ========  ===============================  ========================================================================
  1010001   Method Not Allowed               The specified HTTP Method is not allowed for this API call
  1010101   Required Parameter Missing       A required parameter is missing.
  1010201   Invalid Parameter                A parameter is in an invalid format.
  1010202   Invalid Parameter                The parameter value exceeds the maximum number of characters allowed.
  1010203   Invalid Parameter                Parameter contains non alphabetic characters.
  1010204   Invalid Parameter                Parameter contains non numeric characters.
  1010205   Invalid Parameter                The specified parameter is expected to be in decimal format, but does not appear to be a valid decimal.
  1010206   Invalid Date                     The specified parameter does not seem to be a valid date.
  1010207   Invalid Time                     The specified parameter does not seem to be a valid time.
  1010208   Invalid IP Address               The merchant entered an IP address that was in an invalid format. The IP address must be in a format such as 123.456.123.456.
  1010209   Invalid Email Address            The merchant entered an email address that was in an invalid format.
  1010301   Invalid Soft Descriptor          The soft descriptor contains invalid characters
  ========  ===============================  ========================================================================

.. table::
  :class: table-with-wrap  

  ========  ===============================  ========================================================================  ===================================
  Code      Message                          Description                                                               Correcting this error
  ========  ===============================  ========================================================================  ===================================
  1020001   No route to acquirer             The requested payment product is not configured for your account.         Contact your account manager for resolution
  1020002   Unsupported ECI                  The specified :term:`ECI` is not supported by the gateway.	
  1020003   Unsupported Payment Product      The specified :term:`payment product` is not valid.                       Ensure you specified a valid product code.
  ========  ===============================  ========================================================================  ===================================


.. table:: Table: Error codes relating to the Checkout Process
  :class: table-with-wrap  
 
  ========  ===============================  ===============================================================================================  ===================================
  Code      Message                          Description                                                                                      Correcting this error
  ========  ===============================  ===============================================================================================  ===================================
  3000001   Unknown Order                    Order not found.
  3000002   Unknown Transaction              Transaction not found.
  3000003   Unknown Merchant                 Merchant account does not exist.
  3000101   Unsupported Operation            Unsupported :term:`Operation`                                                                   Retry the request with a supported operation
  3000102   Unknown IP Address               The IP address cannot be detected. Transaction cannot be processed without a valid IP address.
  3000201   Suspicion of fraud               The transaction has been rejected by the financial institution for reasons of suspected fraud.
  3030001   Fraud Suspicion                  The transaction has been rejected by HiPay for reasons of suspected fraud.  
  3040001   Unknown Token                    The specified :term:`token` was not found in the secure vault.
  3010001   Unsupported Currency             Currency is not supported	Retry the request with a supported currency
  3010002   Amount Limit Exceeded            The amount exceeds the maximum amount allowed for a single transaction                          Reattempt the request with a lower amount
  3010003   Max Attempts Exceeded            You have exceeded the maximum number of payment attempts for this order	
  3010004   Duplicate Order                  Order was already processed
  3010005   Checkout Session Expired         This session has expired. Order is no longer valid.
  3010006   Order Completed                  Order has already been completed
  3010007   Order Expired                    Order has expired
  3010008   Order Voided                     Order is voided
  ========  ===============================  ===============================================================================================  ===================================
 

.. table:: Table: Error codes relating to Maintenance Operations
  :class: table-with-wrap  
 
  ========  =================================================================  ==============================================================================================  ===================================
  Code      Message                                                            Description                                                                                     Correcting this error
  ========  =================================================================  ==============================================================================================  ===================================
  3020001   Authorization Expired                                              :term:`Authorization` has expired
  3020002   Amount Limit Exceeded                                              Amount specified exceeds allowable limit                                                        Reattempt the request with a lower amount
  3020101   Not Enabled                                                        :term:`Capture` feature is not enabled for the merchant                                         Contact your account manager for resolution
  3020102   Not Allowed                                                        You cannot capture this type of transaction
  3020103   Not Allowed                                                        You cannot partially capture this type of transaction
  3020104   Permission Denied                                                  You do not have permission to capture this transaction                                          You are not the owner of this transaction.
  3020105   Currency of capture must be the same as currency of authorization  Ensure that the currencies are the same, and retry the request
  3020106   Authorization Completed	                                           Authorization has already been completed	
  3020107   No More	                                                           Maximum number of allowable captures has been reached. No more capture for the authorization.
  3020108   Invalid Amount                                                     The capture amount must be a positive amount                                                    Reattempt with a positive amount
  3020109   Amount Limit Exceeded                                              The capture amount must be less than or equal to the original transaction amount                Reattempt the request with a lower amount
  3020110   Amount Limit Exceeded                                              The partial capture amount must be less than or equal to the remaining amount                   Reattempt the request with a lower amount
  3020111   :term:`Operation` Not Permitted                                    The transaction is closed.
  3020112   Operation Not Permitted	                                           This transaction cannot be processed because it has been denied by the fraud rule set           You cannot capture a payment after it has been denied by the Fraud Protection Service
  3020201   Not Enabled                                                        :term:`Refund` feature is not enabled for the merchant                                          Contact your account manager for resolution
  3020202   Not Allowed                                                        You cannot refund this type of transaction
  3020203   Not Allowed                                                        You cannot partially refund this type of transaction	
  3020204   Permission Denied                                                  You do not have permission to refund this transaction                                           You are not the owner of this transaction.
  3020205   Currency Mismatch                                                  The refund must be the same currency as the original transaction                                Ensure that the currencies re the same, and retry the request
  3020206   Already Refunded                                                   This transaction has already been fully refunded	
  3020207   No More                                                            Maximum number of allowable refunds has been reached. No more refund for the transaction.
  3020208   Invalid Amount                                                     The refund amount must be a positive amount                                                     Reattempt with a positive amount
  3020209   Amount Limit Exceeded                                              The refund amount must be less than or equal to the original transaction amount                 Reattempt the request with a lower amount
  3020210   Amount Limit Exceeded                                              The partial refund amount must be less than or equal to the remaining amount                    Reattempt the request with a lower amount
  3020211   Operation Not Permitted                                            The transaction is closed.
  3020212   Too Late                                                           You are over the time limit to perform a refund on this transaction
  3020301   Not Enabled                                                        Reauthorization feature is not enabled for the merchant                                         Contact your account manager for resolution
  3020302   Not Allowed                                                        Reauthorization is not allowed for this type of transaction	
  3020303   Cannot Reauthorize                                                 You can reauthorize only the original authorization, not a reauthorization	
  3020304   Max Limit Exceeded                                                 Maximum number of reauthorization allowed for the authorization is reached	
  3020401   Not Allowed                                                        You cannot void this type of transaction	
  3020402   Cannot Void                                                        You can void only the original authorization, not a reauthorization
  3020403   Authorization Voided                                               Authorization has already been voided
  ========  =================================================================  ==============================================================================================  ===================================

.. table:: Table: Acquirer Reason Codes
  :class: table-with-wrap  
 
  ========  =================================================================  ==============================================================================================  
  Code      Message                                                            Description                                                                                   
  ========  =================================================================  ==============================================================================================
  4000001   Declined                                                           The transaction was declined by the acquirer
  4000002   Declined                                                           Payment was refused by the financial institution
  4000003   Insufficient Funds                                                 The shopper's account does not have sufficient funds.
  4000004   Technical Problem                                                  There was a problem processing this transaction.
  4000005   Communication Failure                                              This transaction cannot be processed
  4000006   Acquirer Unavailable                                               This transaction cannot be processed because the acquirer is temporarily unavailable.
  4000007   Duplicate Transaction                                              Transaction was already processed
  4000008   Payment cancelled by the customer                                  Transaction was cancelled by the customer.
  4000009   Invalid transaction                                                Transaction type not valid.
  4000010   Please call the acquirer support call number                       An issue occurred with your acquirer, please contact HiPay.
  4000011   Authentication failed. Please retry or cancel                      The authentication requested by the payment method was failed.
  4000012   No UID configured for this operation                               The payment method used for this transaction is not supported on actual account configuration.
  4010101   Refusal (No Explicit Reason)                                       Transaction declined by the card issuer with no explanation given as to the reason.
  4010102   Issuer Not Available                                               The authorization centre of the card issuer is not operational at this time.
  4010103   Insufficient Funds                                                 The cardholder does not have enough credit to make this payment.
  4010201   Transaction Not Permitted                                          Transaction not permitted for this type of card.
  4010202   Invalid Card Number                                                The transaction failed as a result of an invalid credit card number.
  4010203   Unsupported Card                                                   The type of card is not supported or is unknown.
  4010204   Card Expired                                                       Transaction declined because the expiry date on the card used for payment has already passed.
  4010205   Expiry Date Incorrect                                              Transaction declined because the expiry date of the card used for payment does not correspond with the correct date.
  4010206   CVC Required                                                       This transaction cannot be processed because no Card Verification Code was provided.
  4010207   CVC Error                                                          The transaction was declined because the CVC entered does not match the credit card.
  4010301   AVS Failed                                                         This transaction was refused because the AVS response returned the value of N, and the merchant account is not able to accept such transactions.
  4010302   Retain Card                                                        The bank placed a hold on purchases due to issue with the cardholder account.
  4010303   Lost or Stolen Card                                                Card blocked by the card issuer because the cardholder has reported it as being lost or stolen (potential fraud).
  4010304   Restricted Card                                                    The credit card is blacklisted by card association.
  4010305   Card Limit Exceeded                                                The transaction would exceed card monthly limit.
  4010306   Card Blacklisted                                                   The card was rejected by the bank’s fraud system.
  4010307   Unauthorised IP address country                                    The country IP address used is not authorized.
  4010309   Card not in authoriser’s database                                  The credit card number is not in an authorised cards database.
  ========  =================================================================  ==============================================================================================
