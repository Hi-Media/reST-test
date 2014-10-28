.. _AppendixA-PaymentProduct:

.. include:: common.rst

============================
Appendix A - Payment Product
============================

.. table:: Table: Credit Cards (Category code: credit-card)
  :class: table-with-wrap

  =====================  =====================  =====  ==============  ===========  =====================
  Product Code           Brand Name             3-DS   :term:`Refund`  Recurring    Comment
  =====================  =====================  =====  ==============  ===========  =====================
  american- |_| express  American |_| Express   No     Yes             Yes
  cb                     Carte Bancaire         Yes    Yes             Yes          Accepted cards: Visa, MasterCard, Maestro.  Available only in France.
  mastercard             MasterCard             Yes    Yes             Yes
  visa                   Visa                   Yes    Yes             Yes
  =====================  =====================  =====  ==============  ===========  =====================

.. table:: Table: Debit Cards (Category code: debit-card)
  :class: table-with-wrap

  ================  =========================  =====  ==============  ===========  =====================
  Product Code      Brand Name                 3-DS   :term:`Refund`  Recurring    Comment
  ================  =========================  =====  ==============  ===========  =====================
  bcmc              Bancontact / Mister Cash   Yes    No              No           Available only in Belgium.
  maestro           Maestro                    Yes    Yes             Yes          MasterCard requires that your website implements 3-D Secure authentication in order for you to accept Maestro payments
  ================  =========================  =====  ==============  ===========  =====================


.. table:: Table: Real-Time Banking (Category code: realtime-banking)
  :class: table-with-wrap

  ===================  =========================  ==============  ======================  =====================
  Product Code         Brand Name                 :term:`Refund`  Recurring Available?    Comment
  ===================  =========================  ==============  ======================  =====================
  ideal                iDEAL                      No              No
  ing-homepay          ING Home'Pay               No              No
  sofort-uberweisung   Sofort Uberweisung         No              No
  przelewy24           Przelewy24                 Yes             No                      Available only in PLN currency.
  sisal                Sisal                      No              No                      Max amount 1000 EUR.
  dexia-directnet      Belfius Direct Net         No              No
  bank-transfer        TrustPay Banking           No              No
  ===================  =========================  ==============  ======================  =====================


.. table:: Table: E-Wallet (Category code: ewallet)
  :class: table-with-wrap

  ===================  ===================  =================  ======================  =====================
  Product Code         Brand Name           Refund Available   Recurring Available?    Comment
  ===================  ===================  =================  ======================  =====================
  qiwi-wallet          VISA QIWI Wallet     No                 No                      Available only in RUB currency.
  webmoney-transfer    WebMoney Transfer    No                 No                      Available only in RUB currency.
  yandex               Yandex.Money         No                 No                      Available only in RUB currency.
  ===================  ===================  =================  ======================  =====================
