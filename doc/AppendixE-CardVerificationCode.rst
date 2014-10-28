.. _AppendixE-CardVerificationCode:

=====================================
Appendix E - Card Verification Code
=====================================

Description
  The CVC is available on the following credit and debit cards: Visa (Card Verification Value CVV2), MasterCard (Card Validation Code CVC2), Maestro, Diners Club, Discover (Card Identification Number CID), and American Express (Card Identification Number CID).

Procedure
  When the acquirer enables you to perform a CVC check, a result code (returned along with the response to authorization request) informs you on the CVC check status. 
  You evaluate the CVC result code that you received with the transaction authorization, and you take appropriate action based on all transaction characteristics.
  
Procedure
  When the acquirer enables you to perform a CVC check, a result code (returned along with the response to authorization request) informs you on the CVC check status. 
  You evaluate the CVC result code that you received with the transaction authorization, and you take appropriate action based on all transaction characteristics.
  
.. warning:: Only a few acquirers return specific CVC check results. For most acquirers, the CVC is assumed to be correct if the transaction is successfully authorized.

 
 The table below lists the available result codes as returned in the API response messages.
  
.. table:: Table: AVS Result Codes
  :class: table-with-wrap
  
  ========  ===================  =====================
  Code      Description          What it means?
  ========  ===================  =====================
  *Blank*   Not applicable       CVC check was not possible.
   M        Match                CVC match.
   N        No Match             CVC does not match.
   P        Not processed        CVC request not processed.
   S        Missing              CVC should be on the card, but the cardholder has reported that it isn't.
   U        Not supported        Card issuer does not support CVC.
  ========  ===================  =====================
