.. _test:

====
Test
====

.. note:: This is a note.

.. hint:: This is a admonition of type `hint`.

.. tip:: This is a admonition of type `tip`.

.. warning:: Warning, this is very **important**!

.. seealso:: This is a admonition of type `seealso`.

.. versionadded:: 2.5
    The *spam* parameter.

.. versionchanged:: 2.5
    The *spam* parameter.

.. deprecated:: 3.1
    Use :func:`spam` instead.

.. seealso::

   Module :py:mod:`zipfile`
      Documentation of the :py:mod:`zipfile` standard module.

   `GNU tar manual, Basic Tar Format <http://link>`_
      Documentation for tar archive files, including GNU tar extensions.

------
Images
------

Images are simple pictures:

.. image:: images/hipay_fullservice.png
   :name: my picture


A figure add to an image an optional caption and an optional legend:

.. figure:: images/hipay_fullservice.png
    :alt: logo HiPay Fullservice

    This is the caption of the figure (a simple paragraph).

    The legend consists of all elements after the caption. In this
    case, the legend consists of this paragraph.


To create a `symbolic link` to use at the command line.

::

    ln -s  "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/subl

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

-----
Lists
-----

Definition lists:

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

  test ligne

:what:
  Definition lists associate a term with
  a definition.

:how:
  The term is a one-line phrase, and the
  definition is one or more paragraphs or
  body elements, indented relative to the
  term. Blank lines are not allowed
  between term and definition.

------
Tables
------

===================== 	===========================================================================
Field Name        		Description
===================== 	===========================================================================
Notification URL		The URL or IP on which you want to receive server-to-server notifications.
---------------------  	---------------------------------------------------------------------------
Request method			The method you wish to receive the requests:

					      - XML
					      - HTTP POST
--------------------- 	---------------------------------------------------------------------------
Desired notifications	Payment Card Industry Data Security Standards
=====================  	===========================================================================


.. table:: Truth table for "not"

   =====  =====
     A    not A
   =====  =====
   False  True
   True   False
   =====  =====

---------
Footnotes
---------

This is a test [1]_

This is another test [2]_

.. rubric:: Footnotes

.. [1] Text of the first footnote.
.. [2] Text of the second footnote.

------
Index
------
The :term:`API` is based on REST principles.
