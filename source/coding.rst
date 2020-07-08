Coding Standards
######################################

Repository and Versioning Conventions
======================================

Roles
---------------------------------------

The following roles are standardized in our repository and release management:

* Lead: The individual in charge of the department or a project. (Lead roles
  and hierarchy are defined in the MousePaw Media Employee Handbook, and are
  beyond the scope of this document.)

* Repository Master: A trained individual who is granted administrative control
  of the repositories and build system, and who is entrusted with deciding if
  and when to commit to protected branches.

* Trusted developer: All staff members, as well as any open source contributors
  who have been explicitly granted trust privileges by a staff member.

Branches
---------------------------------------

We reserve and protect three branches in our Git repositories:

* ``devel``  is for the latest development version.
* ``fresh`` is for the latest testing release.
* ``stable`` is for the latest stable release.

Any developer can push to ``devel``  with an approved code review from a
Trusted developer. However, only a Repository Master can push directly to
``devel``.

A Repository Master is the only individual who can push to ``fresh`` or
``stable``, and thus must be the one to land (commit) any code which passes
code review.

Versioning
--------------------------------------

Starting from January 2020, we use `Semantic Versioning <https://semver.org/>`_
for all software development projects. Our version numbers follow the format
``X.Y.Z``

* ``X`` is a major release, reserved for changes to the API or CLI.
* ``Y`` is a minor release, for releases with new features.
* ``Z`` is a patch release, for bugfix-only releases.

..  NOTE:: Fixing a bug in a non-released version does not qualify for a
    patch release number! For example, if a bug is fixed in ``2.4.0-beta2``,
    a bugfix would create ``2.4.0-beta3``, and *not* ``2.4.1-beta3``.

About Zero-Versions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Zero-Versions are versions at Major Release ``0``. They are considered
inherently unstable and feature incomplete, and thereby un-releasable. They
cannot be promoted to either ``fresh`` or ``stable``.

A project remains at a Zero-Version until it is considered complete and
stable enough to promote to ALPHA. The Major version remains at ``0``, but the
Minor and Bugfix versions can be incremented at the discretion of the Lead
and Repository Master.

When a version is deemed complete and stable enough to promote to an ALPHA,
the version number immediately jumps from ``0.N.N`` to ``1.0.0-alpha.N``,
and only ``N`` is incremented.

ALPHA Versions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

ALPHA versions are committed to the ``devel``  branch. They are generally
feature-frozen, and represent candidates for promotion to ``fresh``.

In versioning, ``-alpha.N` is amended for ALPHA-versions, where ``N`` is the
ALPHA version number. For example, in preparation for release of 2.4.0,
the first candidate of the development code for promotion to ``fresh``
would be version ``2.4.0-alpha.1``, and should be tagged as such.

If an additional feature is to be added to an ALPHA, it is kicked back down
to a Development version, and the ALPHA suffix is dropped. If it was promoted
to ``1.0.0-alpha.N`` from a Zero-Version, it will be reverted to the next
appropriate Zero-Version until the feature is considered stable enough to
warrent another ALPHA Release.

..  TODO:: Determine ALPHA candidacy/testing standards.

BETA Versions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

BETA versions are committed to the ``fresh`` branch. They are feature-frozen,
and are intended for testing, but are not yet considered stable enough to be
a "release candidate".

In versioning, ``-betaN`` is amended for BETA-versions, where ``N`` is the
BETA version number. For example, after ``2.4.0`` is first promoted to the
``fresh`` branch, it would be tagged ``2.4.0-beta.1``.

Additional features *may not be added* to a BETA. Once a version is promoted
from an ALPHA to a BETA, it should be considered feature-frozen, for better or
for worse. If the feature is considered to be a blocking feature to the Release,
the Release cycle should be *abandoned*, and the version kicked back down to
a development version on ``devel`` . It will then gain a new Minor release
number before it is promoted to ALPHA and BETA again.

..  TODO:: Determine BETA candidacy/testing standards.

Release Candidates
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

When a BETA version is believed to be stable enough for release, it would be
promoted to a Release Candidate (RC). It would remain in ``fresh``, but would
be considered a candidate for release to ``stable``.

In versioning, ``-rcN`` is amended for RC-versions, where ``N`` is the Release
Candidate number. For example, if ``2.4.0-beta.6`` is believed to be stable
after field testing, it should be promoted to ``2.4.0-rc.1``.

A Release Candidate is feature-frozen in the exact same manner as a BETA.
However, if a Release cycle is abandoned due to a missing feature, the
candidacy and testing processes should be audited.

..  TODO:: Determine RC candidacy/testing standards.

Releases
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Once a Release Candidate is confirmed to be stable enough for release, it
should be promoted to ``stable``, and the suffix dropped, leaving only the
``X.Y.Z`` version.

If a Lead Developer or Repository Master believes a Major or Minor Release is
stable enough to skip the ALPHA or BETA phase, they may do so. However, all
major and minor releases should always be tested at Release Candidate phase
before final release.

Patch Releases can be expedited directly to Release Candidate or Release phase
by a Lead Developer or Repository Master. Care should be taken in making this
call, however, as some bugfixes can break other things.

..  TODO:: Determine Release candidacy/testing standards.

Build Numbers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If build numbers needed, such as during Debian packaging, the build number
may be appended to the version in the format ``+YYYYMMDDHHMMSS``, where
``YYYY`` is the year, ``MM`` is the two-digit month number, ``DD`` is the
two-digit day number, ``HH`` is the two-digit hour in military time UTC,
and ``MM`` and ``SS`` are the two-digit minute and second respectively.

The build metadata and script files *are* considered part of the project,
and are versioned as Patch releases. Assuming the build metadata and script
files are unchanged, the build itself should *never* increment the build;
in that case, only the build number should be updated.

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
