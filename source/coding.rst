Coding Standards
######################################

C and C++
======================================

File Types
------------------------------------------------

* C++

  * Headers: ``.hpp``

  * Implementation: ``.cpp``

* C

  * Headers: ``.h``

  * Implementation: ``.c``

The reason behind this is so we can use C and C++ in parallel with one
another, without confusing what language any given file is written in.

Naming Conventions
------------------------------------------------

* Variables: ``lower_snake_case``

* Constants: ``SCREAMING_SNAKE_CASE``

* Functions: ``lower_snake_case``

* Classes: ``UpperCamelCase``

* Filenames: ``lower_snake_case``

Formatting
------------------------------------------------

..  NOTE:: We are currently debating whether to switch to OTBS.

* Use Allman bracketing and indentation style.

..  code-block:: c++

    if (x == y)
    {
        x++;
        foo();
    }
    else
    {
        x--;
        bar();
    }

* Avoid code beyond 80 characters. Never exceed 120 characters.

* Indentation should use tab characters (4 space width), with spaces for
  further alignment.

* A switch's block should be indented, and each case's block should be
  indented in the same manner.

* Line up lists so a) the start of list item lines align, and b) the end of
  list item lines roughly align. Each line should end with either a comma or,
  in the case of the last line, the closing token.

..  code-block:: c++

    string names[9] = {"Bob", "Fred", "Jim",
                       "Chris", "Dave", "Jack",
                       "Ozymandius", "Randall",
                       "Andrew"};

* Pointer and reference indicators ``*`` and ``&`` should be aligned to the
  type part of the statement, not the name.

* Insert space padding around operators.

* Insert space padding after parenthesis headers (after ``if``, ``switch``, etc.)

* One-line blocks (i.e. one line ``if`` statements) should still have brackets.

Comments
------------------------------------------------
* Use CSI Commenting Standard.

  * All functions and variables should have a doc comment at declaration.

  * CSI comment *every logical block*.

  * Header files and standalone implementation files should *always* have
    CSI-style description and license comments at the top.

* Use ``//`` and ``/* ... */`` for CSI comments.

* When a comment spans multiple lines, prefer multiline ``/* ... */`` comments.
  We recommend using line-leading ``* ``.

..  code-block:: c++

    /* This is a multiline comment
     * that spans multiple lines.
     * See how nice this looks?
     */

* Use ``///`` and ``/** ... */`` for doc comments.

  * Each parameter description in doc comments should be preceded by ``\param``
    on a new line.

  * The return description in doc comments should be preceded by ``\return``
    on a new line.

* Do not commit commented out code.

* Avoid inline comments whenever possible.

* Use ``//TODO``, ``//NOTE``, and ``//FIXME`` notation where necessary.

Structure
------------------------------------------------

* ``main.c`` and ``main.cpp`` should reside in the root directory.

* ``.h`` and ``.hpp`` files should be in an the ``include/`` directory. For
  libraries, header files should be in a ``<project>`` subfolder (i.e.
  ``include/anari/`` or ``include/pawlib/``).

* ``.c`` and ``.cpp`` files should be in the ``src/`` directory.

* Documentation files should be in the ``docs/`` directory.

Python
======================================
Based on `PEP8 <https://www.python.org/dev/peps/pep-0008>`_ and
`PEP257 <https://www.python.org/dev/peps/pep-0257/>`_.

.. WARNING: Indent with 4 spaces, NEVER tabs! Many IDEs can be configured
   to use "soft tabs," inserting 4 sapces when you press TAB.

Naming Conventions
------------------------------------------------

* Variables: ``lower_snake_case``

* Constants: ``SCREAMING_SNAKE_CASE``

* Functions: ``lower_snake_case``

* Classes: ``UpperCamelCase``

* Filenames/Modules: ``lower_snake_case`` (Underscores discouraged,
  however. Avoid when possible.)

Formatting
------------------------------------------------

* Four-space indentation ONLY.

* Avoid code beyond 80 characters. Use ``\`` as necessary to break lines.
  Never exceed 120 characters.

* Line up multi-line structures as follows, with the opening and closing
  brackets on separate lines, and the start of the items lined up. Each
  item *may* be on its own line, but this is not required.

..  code-block:: python

    names = [
        "Bob", "Fred", "Jim",
        "Chris", "Dave", "Jack",
        "Ozymandius", "Randall",
        "Andrew"
    ]

Comments
------------------------------------------------
* Include docstrings for all functions, classes, and modules, following
  `PEP257 <https://www.python.org/dev/peps/pep-0257/>`_

* Please avoid inline comments. Comment above lines.

* Use single line comments when possible. (``#``)

* Please comply with the CSI Commenting Standard as much as possible.

* Use ``#TODO``, ``#NOTE``, and ``#FIXME`` notation where necessary.

* All files should precede with CSI-style description docstrings and
  license comments.

* Do not commit commented out code.

Python Code Formatter
-----------------------------------------------

`black` should be used as the code formatter.
