.. _AppendixB-PaymentStatus:

===========================
Payment Status Definitions
===========================

This is a list of the various payment status names and a description of what each payment status name means.

.. table:: Table: Transaction statuses
  :class: table-with-wrap
  
  ================  =================  =====  ==============  ===========  =====================
  Product Code      Brand Name         3-DS   :term:`Refund`  Recurring    Comment
  ================  =================  =====  ==============  ===========  =====================
  american-express  American Express   No     Yes             Yes
  cb                Carte Bancaire     Yes    Yes             Yes          Accepted cards: Visa, MasterCard, Maestro.  Available only in France.
  mastercard        MasterCard         Yes    Yes             Yes
  visa              Visa               Yes    Yes             Yes
  ================  =================  =====  ==============  ===========  =====================

Diagram

.. image:: images/TransactionFlow_3Dsecure.jpeg
   :name: transaction flow 3Dsecure
  