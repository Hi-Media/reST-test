.. _test:

====
Test
====

Lorem ipsum dolor sit amet, consectetur adipiscing elit.
Nam rhoncus at sem non finibus. Sed ac porta ex. Vestibulum sollicitudin purus sit amet massa malesuada pulvinar.
Nullam a euismod quam, ut feugiat justo. In sed cursus sapien, quis pulvinar eros. Nunc ut erat augue.
Vivamus non tortor eleifend, tempor ex in, malesuada nisi. Pellentesque fringilla congue mollis.

* Donec quis fringilla leo.
  Etiam consequat est in dui placerat ultricies. Cras varius quam et tortor viverra suscipit.
  Integer placerat et odio eu bibendum. Vivamus interdum accumsan auctor.
  Sed gravida maximus odio ut condimentum.
* bla bla

Donec quis fringilla leo.
Etiam consequat est in dui placerat ultricies. Cras varius quam et tortor viverra suscipit.
Integer placerat et odio eu bibendum. Vivamus interdum accumsan auctor.
Sed gravida maximus odio ut condimentum.
Quisque nec risus erat. Nulla facilisi.
Praesent ut sem ex.

Lorem ipsum dolor sit amet, consectetur adipiscing elit.
Nam rhoncus at sem non finibus. Sed ac porta ex. Vestibulum sollicitudin purus sit amet massa malesuada pulvinar.
Nullam a euismod quam, ut feugiat justo. In sed cursus sapien, quis pulvinar eros. Nunc ut erat augue.
Vivamus non tortor eleifend, tempor ex in, malesuada nisi. Pellentesque fringilla congue mollis.

.. note:: This is a note.

.. hint:: This is a admonition of type `hint`.

.. tip:: This is a admonition of type `tip`.

.. warning:: Warning, this is very **important**!

.. seealso:: This is a admonition of type `seealso`.

.. seealso::

   Module :py:mod:`zipfile`
      Documentation of the :py:mod:`zipfile` standard module.

   `GNU tar manual, Basic Tar Format <http://link>`_
      Documentation for tar archive files, including GNU tar extensions.

------
Images
------

Simple images
-------------

.. code-block:: rest

    .. image:: images/hipay_fullservice.png
        :alt: logo HiPay Fullservice
        :width: 1446px
        :height: 308px
        :scale: 25 %

.. image:: images/hipay_fullservice.png
    :alt: logo HiPay Fullservice
    :width: 1446px
    :height: 308px
    :scale: 25 %

|
|

Figures, with optional caption and legend
-----------------------------------------

.. code-block:: rest

    .. figure:: images/hipay_fullservice.png
        :alt: logo HiPay Fullservice
        :width: 1446px
        :height: 308px
        :scale: 25 %

        Figure: This is the caption of the figure (a simple paragraph).

        The legend consists of all elements after the caption. In this
        case, the legend consists of this paragraph.

.. figure:: images/hipay_fullservice.png
    :alt: logo HiPay Fullservice
    :width: 1446px
    :height: 308px
    :scale: 25 %

    Figure: This is the caption of the figure (a simple paragraph).

    The legend consists of all elements after the caption. In this
    case, the legend consists of this paragraph.

----
Code
----

Bloc XML: ``.. code-block:: xml``

.. code-block:: xml
    :linenos:

    <?xml version="1.0" encoding="UTF-8"?>
    <response>
        <state>completed</state>
        <reason/>
        <forward_url/>
        <test>false</test>
        <mid>00035167042</mid>
        <attempt_id>2015</attempt_id>
        <authorization_code>59351</authorization_code>
        ...
    </response>

Bloc HTML: ``.. code-block:: html``

.. code-block:: html
    :linenos:

    <form name="test">
    <!-- hidden field to store blackbox -->
      <input type="text" name="device_fingerprint" id="ioBB">
    </form>
    <!-- Include JavaScript fingerprint library -->
    <script language="javascript" src="https://secure-gateway.allopass.com/gateway/toolbox/fingerprint">
    </script>

Bloc PHP: ``.. code-block:: php``

.. code-block:: php
    :linenos:

    <?php
    define('API_ENDPOINT', 'https://secure-gateway.allopass.com/rest/v1');
    define('API_USERNAME', '<API login>');
    define('API_PASSWORD', '<API password>');

    $credentials = API_USERNAME . ':' . API_PASSWORD;
    $resource    = API_ENDPOINT . '/order';

    // create a new cURL resource
    $curl = curl_init();

Bloc JSON: ``.. code-block:: json``

.. code-block:: json
    :linenos:

    {
      "state":"completed",
      "reason":"",
      "forwardUrl":"",
      "test":"false",
      "mid":"00035167042",
      "attemptId":"1",
      "authorizationCode":"59351",
      "..."
    }

Bloc INI: ``.. code-block:: ini``

.. code-block:: ini
    :linenos:

    state = completed
    reason =
    test = false
    mid = 00001326581
    attempt_id = 1
    authorization_code = test123

Bloc Bash (Shell): ``.. code-block:: bash``

.. code-block:: bash
    :linenos:

    $ curl https://secure-gateway.allopass.com/rest/v1/transaction/432241108734 \
        -u "<your API username>:<your API password>"

-----
Lists
-----

Definition list
---------------

what
  Definition lists associate a term with
  a definition.

how
  The term is a one-line phrase, and the
  definition is one or more paragraphs or
  body elements, indented relative to the
  term.
  Blank lines are not allowed
  between term and definition.

  Another paragraph.

bla
  Lorem ipsum dolor sit amet, consectetur adipiscing elit.

  * Nam rhoncus at sem non finibus.
    Sed ac porta ex. Vestibulum sollicitudin purus sit amet massa malesuada pulvinar.
  * Nullam a euismod quam, ut feugiat justo.

Lorem ipsum dolor
  * Nam rhoncus at sem non finibus.
    Sed ac porta ex. Vestibulum sollicitudin purus sit amet massa malesuada pulvinar.
  * Nullam a euismod quam, ut feugiat justo.

  Vivamus non tortor eleifend, tempor ex in, malesuada nisi.

Lorem ipsum dolor sit amet, consectetur adipiscing elit.
Nam rhoncus at sem non finibus. Sed ac porta ex. Vestibulum sollicitudin purus sit amet massa malesuada pulvinar.
Nullam a euismod quam, ut feugiat justo. In sed cursus sapien, quis pulvinar eros. Nunc ut erat augue.
Vivamus non tortor eleifend, tempor ex in, malesuada nisi. Pellentesque fringilla congue mollis.



.. _hlist:

Horizontal list
---------------

.. hlist::
    :columns: 3

    * A list of
    * short items
    * that should be
    * displayed
    * horizontally

------
Tables
------

Without title
-------------

.. _my-table-wo-title:

=====  =====
A      not A
=====  =====
False  True
True   False
=====  =====

With title
----------

.. _my-table-with-title:

.. table:: Table: Truth table for "not"

    =====  =====
    A      not A
    =====  =====
    False  True
    True   False
    =====  =====

With CSS classes
----------------

Raw version
~~~~~~~~~~~

.. table:: Table: raw version

  ====================  ===========  =======  ========  =====================================================================================================================================================================================================================================================================
  Field Name        	Format [1]_  Length   Req [2]_  Description
  ====================  ===========  =======  ========  =====================================================================================================================================================================================================================================================================
  orderid               AN           32       M         Unique order id
  :term:`operation`     AN                              Transaction type.

                                                        Indicates how you want to process the payment. The default transaction type is set in the Merchant Interface (Default payment procedure in the Integration section). A transaction type sent along with the transaction will overwrite the default payment procedure.

                                                        - **Sale** indicates transaction is sent for :term:`authorization`, and if approved, is automatically submitted for capture.
                                                        - **Authorization** indicates this transaction is sent for authorization only. The transaction will not be sent for settlement until the transaction is submitted for capture manually by the Merchant
  \                                                     Column 1 empty through ``\`` syntax.
  description           AN           255      M         - bla
                                                        - bla

                                                        An error message is displayed with an explanation of the error situation.
  long_description      AN                              - bla
                                                        - bla
  ====================  ===========  =======  ========  =====================================================================================================================================================================================================================================================================

With auto-wrap
~~~~~~~~~~~~~~

.. code-block:: rest

    .. table:: foo
      :class: table-with-wrap

.. table:: Table: with auto-wrap
  :class: table-with-wrap

  ====================  ===========  =======  ========  =====================================================================================================================================================================================================================================================================
  Field Name        	Format [1]_  Length   Req [2]_  Description
  ====================  ===========  =======  ========  =====================================================================================================================================================================================================================================================================
  orderid               AN           32       M         Unique order id
  :term:`operation`     AN                              Transaction type.

                                                        Indicates how you want to process the payment. The default transaction type is set in the Merchant Interface (Default payment procedure in the Integration section). A transaction type sent along with the transaction will overwrite the default payment procedure.

                                                        - **Sale** indicates transaction is sent for :term:`authorization`, and if approved, is automatically submitted for capture.
                                                        - **Authorization** indicates this transaction is sent for authorization only. The transaction will not be sent for settlement until the transaction is submitted for capture manually by the Merchant
  \                                                     Column 1 empty through ``\`` syntax.
  description           AN           255      M         - bla
                                                        - bla

                                                        An error message is displayed with an explanation of the error situation.
  long_description      AN                              - bla
                                                        - bla
  ====================  ===========  =======  ========  =====================================================================================================================================================================================================================================================================

-----------------
Cross-referencing
-----------------

To arbitrary locations in any document…

* Link to tables: :ref:`explicit title <my-table-wo-title>`, :ref:`my-table-with-title`.

* Link to section: :ref:`hlist`.

.. seealso:: http://sphinx-doc.org/markup/inline.html#cross-referencing-arbitrary-locations

-------------------
External link text
-------------------
`Link text <http://example.com/>`_
Refer to  ` the RFC 2616 HTTP Accept Header <http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.1/>`_ for details.
 
-------
Aliases
-------

.. seealso:: http://openalea.gforge.inria.fr/doc/openalea/doc/_build/html/source/sphinx/rest_syntax.html#more-about-aliases

-------------------
Non-breaking spaces
-------------------

1. Include ``common.rst`` file (in top of file):

.. code-block:: rest

    .. include:: common.rst

2. Insert ``␣|nbsp|␣`` or ``␣|_|␣``:

.. code-block:: rest

    Non-breaking |_| space.

HTML generated:

.. code-block:: html

    Non-breaking&nbsp;space.

---------
Footnotes
---------

This is a test [1]_

This is another test [2]_

.. rubric:: Footnotes

.. [1] Text of the first footnote.
.. [2] Text of the second footnote.

--------
Glossary
--------

``The :term:`API` is based on REST principles.``

The :term:`API` is based on REST principles.

-----
Index
-----

All glossary terms are in index by default.
To add one or more entries:

.. code-block:: rest

    The :index:`API` is based on REST principles.

The :index:`API` is based on REST principles.

:ref:`genindex`

.. seealso:: http://sphinx-doc.org/markup/misc.html#index-generating-markup
