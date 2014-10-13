.. _test:

Test
====

.. note:: This is a note.

.. hint:: This is a admonition of type `hint`.

.. tip:: This is a admonition of type `tip`.

.. warning:: Warning, this is very **important**!

.. seealso:: This is a admonition of type `seealso`.

Images are simple pictures:

.. image:: images/hipay_fullservice.png

A figure add to an image an optional caption and an optional legend:

.. figure:: images/hipay_fullservice.png
   :alt: logo HiPay Fullservice

   This is the caption of the figure (a simple paragraph).

   The legend consists of all elements after the caption. In this
   case, the legend consists of this paragraph.

To create a `symbolic link` to use at the command line.

::

    ln -s  "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/subl

Bloc XML v1:

.. code-block:: ruby
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

Bloc XML v2:

.. code:: xml
    :number-lines: 1

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

Bloc XML v3:

.. highlight:: xml
    :linenothreshold: 1

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

Definition lists:

what
  Definition lists associate a term with
  a definition.

how
  The term is a one-line phrase, and the
  definition is one or more paragraphs or
  body elements, indented relative to the
  term. Blank lines are not allowed
  between term and definition.
