Technical Standards
####################################

Languages
====================================

C++
------------------------------------------------
**Standard:** `C++17 ISO Standard <https://isocpp.org/std/the-standard>`_

**Compiler:** `Clang 9 (9.0 or later) <http://releases.llvm.org/9.0.0/tools/clang/docs/ReleaseNotes.html>`_
or `GNU GCC 7 (7.2 or later) <https://gcc.gnu.org/gcc-7/changes.html>`_

**Windows Compiler:** Clang (see above), either native or via WSL.

CSS
------------------------------------------------
**Standard:** `W3C CSS <https://www.w3.org/Style/CSS/>`_

**Version:** CSS3

Encoding
------------------------------------------------
**Standard:** `UTF-8 <http://unicode.org/resources/utf8.html>`_

HTML
------------------------------------------------
**Standard:** `W3C HTML5 <https://www.w3.org/html/>`_

**Version:** HTML5

Python
------------------------------------------------
**Standard:** `PEP 8 <https://www.python.org/dev/peps/pep-0008/>`_

**Version:** `3.7.x <https://www.python.org/downloads/release/python-375/>`_

XML
------------------------------------------------
**Standard:** `W3C XML <https://www.w3.org/XML/>`_

**Version:** 1.0

Libraries
================================================

+-----------------------------------------------------+----------------------------+---------+---------+----------------------------------+-----------+
| Library                                             | Use                        | Version | Binding | Source                           | License   |
+=====================================================+============================+=========+=========+==================================+===========+
| `Cairo <https://www.cairographics.org/>`_           | 2D graphics                | 1.16.0  | C/C++   | Package: :code:`libcairo2-dev`   | LGPL/MPL  |
+-----------------------------------------------------+----------------------------+---------+---------+----------------------------------+-----------+
| `CPGF <https://github.com/cpgf/cpgf>`_              | Reflection, Introspection  | 1.6.0   | C++     | Repo: :code:`libdeps`            | Apache v2 |
+-----------------------------------------------------+----------------------------+---------+---------+----------------------------------+-----------+
| `Eigen <http://eigen.tuxfamily.org/>`_              | Linear algebra             | 3.3.1   | C++     | Repo: :code:`libdeps`            | MPL2      |
+-----------------------------------------------------+----------------------------+---------+---------+----------------------------------+-----------+
| `eventpp <https://github.com/wqking/eventpp>`_      | Signals                    | 0.1.0   | C++     | Repo: :code:`libdeps`            | Apache v2 |
+-----------------------------------------------------+----------------------------+---------+---------+----------------------------------+-----------+
| `Opus <https://opus-codec.org/>`_                   | Audio codec                | 1.3.1   | C++     | Repo: :code:`libdeps`            | BSD-3     |
+-----------------------------------------------------+----------------------------+---------+---------+----------------------------------+-----------+
| `PySide2 <https://wiki.qt.io/Qt_for_Python>`_       | GUI                        | 5.11.x  | Python  | Pip: :code:`PySide2`             | LGPL      |
+-----------------------------------------------------+----------------------------+---------+---------+----------------------------------+-----------+
| `pugixml <http://pugixml.org/>`_                    | XML parsing                | 1.8     | C++     | Repo: :code:`libdeps`            | MIT       |
+-----------------------------------------------------+----------------------------+---------+---------+----------------------------------+-----------+
| `SDL <https://www.libsdl.org/>`_                    | Hardware abstraction layer | 2.0     | C/C++   | Package: :code:`libsdl2-dev`     | zlib      |
+-----------------------------------------------------+----------------------------+---------+---------+----------------------------------+-----------+

Operating System Support Targets
================================================

These show minimum specifications for a goal.

Support Goals:

- 5: Essential
- 4: High Priority
- 3: Moderate Priority
- 2: Low Priority
- 1: Collateral Support
- 0: No Support

+-----------------------+---------+--------+
| OS                    | Memory  | Goal   |
+=======================+=========+========+
| **Microsoft Windows** |         |        |
+-----------------------+---------+--------+
| Windows 95            | 256 MB  | 2      |
+-----------------------+---------+--------+
| Windows 98            | 256 MB  | 3      |
+-----------------------+---------+--------+
| Windows 2000          | 256 MB  | 3      |
+-----------------------+---------+--------+
| Windows ME            | 256 MB  | 3      |
+-----------------------+---------+--------+
| Windows XP SP1        | 256 MB  | 4      |
+-----------------------+---------+--------+
| Windows XP SP2        | 512 MB  | 5      |
+-----------------------+---------+--------+
| Windows XP SP3        | 512 MB  | 5      |
+-----------------------+---------+--------+
| Windows Vista         | 512 MB  | 5      |
+-----------------------+---------+--------+
| Windows 7             | 1 GB    | 5      |
+-----------------------+---------+--------+
| Windows 8             | (Any)   | 1      |
+-----------------------+---------+--------+
| Windows 8.1           | (Any)   | 1      |
+-----------------------+---------+--------+
| Windows 10            | (Any)   | 5      |
+-----------------------+---------+--------+
| **Apple Mac**         |         |        |
+-----------------------+---------+--------+
| OS X 10.0-10.3 PPC    | 256 MB  | 2      |
+-----------------------+---------+--------+
| OS X 10.4 PPC         | 256 MB  | 4      |
+-----------------------+---------+--------+
| OS X 10.4 Intel       | 256 MB  | 4      |
+-----------------------+---------+--------+
| OS X 10.5             | 512 MB  | 3      |
+-----------------------+---------+--------+
| OS X 10.6             | 1 GB    | 4      |
+-----------------------+---------+--------+
| OS X 10.7-10.10       | 2 GB    | 4      |
+-----------------------+---------+--------+
| **Linux**             |         |        |
+-----------------------+---------+--------+
| Ubuntu LTS            | 512 MB  | 5      |
+-----------------------+---------+--------+
| Debian                | 512 MB  | 4      |
+-----------------------+---------+--------+
| Puppy Linux           | 256 MB  | 3      |
+-----------------------+---------+--------+
| Fedora                | 1 GB    | 4      |
+-----------------------+---------+--------+
| OpenSUSE              | 1 GB    | 3      |
+-----------------------+---------+--------+
| SoaS                  | 1 GB    | 3      |
+-----------------------+---------+--------+

..  NOTE::We want to get a version of the RATS Game Engine working on a version
    of Linux that runs entirely from a USB stick. The idea is to make a
    "bootable" version of the game for users who cannot (or don't want to)
    install on their main operating system.

**For support consideration:**

- `Guadalinux <http://www.guadalinexedu.org/portal/>`_
- `Qimo4Kids <http://www.qimo4kids.com/>`_
