.. _Chap1-APIOverview:

==========================
Chapter 1 - API Overview
==========================

The API is based on REST principles; thus it is very easy to write and test applications. 

How to access the API : 

- Use your browser to access URLs,
- Use almost any HTTP client in any programming language, to interact with the API.

------------------------
Security Considerations
------------------------
HiPay TPP REST API service is protected :

- to ensure that only authorized Merchants use it,
- to prevent payment information from being compromised.

PCI DSS Requirements
====================
Description
  HiPay TPP REST API allows to send payment data ; that means that the system will be transmitting,
  and possibly storing card data. 

Storage (SAD) information
  The Card Schemes, American Express, Discover Financial Services, JCB International, MasterCard Worldwide and
  Visa Inc. have never permitted the storage of sensitive data (track data and/or CVV2).
  It is prohibited under "Requirement 3" of the Payment Card Industry Data Security Standard (PCI DSS).

Warning
  Merchants who store Sensitive Authentication Data (SAD) are exposed to fines from the Card Schemes.
  
Security management data
  If the Secure Vault API is used, the merchant demonstrates that the system can handle this data securely and 
  that he is  taking full responsibility for your PCI DSS compliance.   
 
Contact
  For further information on PCI security standards, please visit http://www.pcisecuritystandards.org.

 
Encrypted Communication
=======================
Description
  HiPay TPP provides all REST API methods over SSL (Secure Sockets Layer).

Guarantees
  All data transmitted between HiPay TPP and the Merchant system is encrypted (256-bit encryption using a DigiCert certificate).
  
IP Restriction
==============
Description
  When a request is sent to the API, the IP address or IP address range from where the connection was made is verified. 
   - If it matches with the IP address supplied by the Merchant at a previous stage (in the Merchant Interface: Technical Integration Section), the request will be processed. 
   - In the case of missing or incorrect information, the server will respond with an appropriate error message, indicating the error in the request

.. Important:: When your IP address is changed, do not forget to ensure that all new IP addresses are configured for your account. If not, your server requests will be rejected..

Authentication
==============
  Only authenticated users and system components are allowed to access to the Secure Gateway API.