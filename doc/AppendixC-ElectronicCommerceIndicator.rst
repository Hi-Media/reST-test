.. _AppendixC-ElectronicCommerceIndicator:

===========================================
Appendix C - Electronic Commerce Indicator
===========================================

Description
  The :term:`ECI` indicates the security level at which the payment information is processed between the cardholder and merchant. 

The table below lists the available indicators as they are supposed to be sent along with each :term:`authorization` request.

.. table:: Table: Electronic Commerce Indicators
  :class: table-with-wrap
  
  =======  ==========================================  =====================
  ECI      Name                                        Description
  =======  ==========================================  =====================
  1        MO/TO (Card Not Present)                    The merchant received the customer's financial details over the phone or via fax/mail, but he does not have the customer's card at hand.
  2        Recurring MO/TO                             The first transaction of the customer was a Mail Order / Telephone Order transaction; i.e. the customer gave his financial details over the phone or via mail/fax to the merchant. Either the merchant stores the details by himself or these details are stored in our system using an Alias and is performing another transaction for the same customer (recurring transaction).
  3        Installment Payment                         Partial payment of goods/services that have already been delivered, but will be paid for in several spread payments.
  4        Manually Keyed (Card Present)               The customer is physically present in front of the merchant. The merchant has the customer's card within easy reach. The card details are manually entered; the card is not swiped through a machine.
  7        Secure E-commerce with SSL/TLS Encryption   The payment transaction was conducted over a secure channel (for example, :term:`SSL`/TLS), but payment authentication was not performed, or when the issuer responded that authentication could not be performed.
  9        Recurring E-commerce                        The first transaction of the customer was an e-Commerce transaction; i.e. the customer entered his financial details himself on a secure website (either the merchant's website or our secure platform). Either the merchant stores the details by himself or these details are stored in our system using an Alias and is now performing another transaction for the same customer (recurring transaction), using the Alias details.
  =======  ==========================================  =====================
