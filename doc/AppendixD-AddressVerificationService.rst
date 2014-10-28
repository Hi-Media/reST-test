.. _AppendixD-AddressVerificationService:

==========================================
Appendix D - Add ress Verification Service
==========================================

Description
  The Address Verification Service (AVS) is a system that allows e-commerce merchants to check a cardholder's billing address. AVS provides merchants with a key indicator that helps verify whether or not a transaction is valid.

The table below lists the available result codes as returned in the API response messages.

.. table:: Table: AVS Result Codes
  :class: table-with-wrap

  ========  ===================  =====================
  Code      Description          What it means?
  ========  ===================  =====================
  *Blank*   Not applicable       No AVS response was obtained (Default value).
   Y        Exact Match          Street addresses and postal codes match.
   A        Partial Match        The street addresses match; the postal codes do not match. Either the request does not include the postal codes or postal codes are not verified due to incompatible formats.
   P        Partial Match        The postal codes match; the street addresses do not match. Either the request does not include the street addresses or street addresses are not verified due to incompatible formats.
   N        No Match             Neither the street addresses nor the postal codes match.
   C        Not Compatible       Street addresses and postal codes not verified due to incompatible formats.
   E        Not Allowed          AVS data is invalid or AVS is not allowed for this card type.
   U        Unavailable          Address information is unavailable for that account number, or the card issuer does not support AVS.
   R        Retry                Issuer :term:`authorization` system is unavailable, try again later.
   S        Not Supported        Card issuer does not support AVS.
  ========  ===================  =====================
