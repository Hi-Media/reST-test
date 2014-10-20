.. _readguide:
======================
How to read this guide
======================
-------------------------
Documentation Conventions
-------------------------

These conventions help to locate and interpret information.
This guide uses several typographic conventions to highlight certain words, phrases and point out
specific pieces of information.
The following table clarifies the conventions used across this guide.


.. table:: Table: Typographic conventions that apply across this guide

   ==============  =======================================================================================================================================================================================================================
   Convention      Meaning
   ==============  =======================================================================================================================================================================================================================
   ``Mono-space``  Source code, code examples, input to the command line, application output, code lines embedded in text, and variables and code elements.
   --------------  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   *Italic*        A term that is being defined or will be defined shortly.
   --------------  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   ...             Horizontal ellipsis points in sample code indicate the omission of part of the code (i.e. when you would normally expect additional code to appear, but such code would not be related to the example.)
   --------------  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   $               At the beginning of a command, indicates an operating system shell prompt.
   --------------  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   <placeholder>   Indicates placeholders, most often method or function parameters; these placeholders represent information that must be supplied by the implementation or the user. For command-line input, indicates parameter values.
   ==============  =======================================================================================================================================================================================================================


----------------------------
Abbreviations used in tables
----------------------------

The tables of this document describe data elements. These data elements are equivalent to parameters
in a query or to fields of a response message. The following table helps understanding the different
attributes (columns) that define a data element.


.. table:: Table: Description of data elements

   =============  ============================================================================================================
   Convention     Meaning
   =============  ============================================================================================================
   Field Name     Name of the data element
   Format         Format of the element
   Length         Maximum size of the data element.(i.e. a size of 6 means the data value cannot exceed six characters)
                  Note : there is no limitation on the length of the size, when no size is specified.
   Reg.           Specifies whether an element is required or not.
                  **M** = Mandatory -> must always be provided.
                  **C** = Conditional -> requirement depends on value or appearance of other elements.
   =============  ============================================================================================================



.. table:: Table: Available formats of data elements

   ===================  =========================================================  ===================
   Format Abbreviation  Description                                                Example
   ===================  =========================================================  ===================
   AN                   Alphanumeric characters (a-z, A-Z, 0-9)
   -------------------  ---------------------------------------------------------  -------------------
   A                    Alphabetic characters only (a-z, A-Z)
   N                    Numerical only
   R                    Decimal number with explicit decimal point, signed         12.34
   DT                   Date in the format YYYY-MM-DD                              2012-12-31
   TM                   Time in the format HH:MM with optional seconds (HH:MM:SS)  15:30
   ===================  =========================================================  ===================


--------------------------
Acronyms and Abbreviations
--------------------------
The following acronyms and abbreviations are used in this guide.

.. table:: Table: Acronyms and Abbreviations

   =============  =========================================================
   Acronym        Full Name
   =============  =========================================================
   BIN            Bank Identification Number
   -------------  ---------------------------------------------------------
   PAN            Primary Account Number
   -------------  ---------------------------------------------------------
   PCI DSS        Payment Card Industry Data Security Standards
   -------------  ---------------------------------------------------------
   REST           Representational State Transfer
   =============  =========================================================
