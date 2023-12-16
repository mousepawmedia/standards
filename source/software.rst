Software Standards
####################################

Legend
=====================================

**Mandatory software is in boldface.** Mandatory software must be installed and configured
on your machine, and you should be prepared to use it as needed. You *may* use alternatives,
as long as your work is fully compatible with the mandatory software. Documentation assumes
you're using the mandatory software, unless otherwise noted. In-house support may be limited
for workflows with non-mandatory software.

Recommended alternative software is in regular face. If an alternative to mandatory software
is needed or desired, we recommend these be considered first. In-house support is still
generally available.

*Optional alternative software is in italics. In-house support for these is limited.*

`†` Transitional only, not for final file output.

`‡` Limited support, no in-house tech support.

`$` Proprietary, permitted but not officially supported by the company.
Should be used transitionally.

Software Recommendations
=====================================

Office Software
-------------------------------------

Office Suites
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **LibreOffice 6**
- *Calligra*
- *OpenOffice.org* ‡

Documents
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **LibreOffice Writer 6**
- *AbiWord*
- *Calligra Words*
- *OpenOffice.org Writer* ‡

Spreadsheets
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **LibreOffice Calc 6**
- *Calligra Sheets*
- *OpenOffice.org Calc* ‡

Presentations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **LibreOffice Impress 6**
- *Calligra Stage*
- *OpenOffice.org Impress* ‡

Flowcharts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Dia**
- LibreOffice Draw 6
- *Calligra Flow*
- *OpenOffice.org Draw* ‡

Office Database
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **LibreOffice Base 6**
- *Calligra Kexi*
- *OpenOffice.org Base* ‡

PDF Annotation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Xournal**

Math and Formulas
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- LibreOffice Math 6
- GeoGebra
- ZeGrapher
- *OpenOffice.org Math* ‡

Collaborative Editing
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Visual Studio Code: Live Share** (text/code only)
- Etherpad [DevNet] (text/code only)
- *AbiWord* ‡

Desktop Publishing
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Scribus**
- LibreOffice Writer 6
- *Calligra Words*
- *OpenOffice.org Writer* ‡

Mindmapping
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- Calligra Braindump
- Freemind

Desktop Email Client
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- Evolution
- Thunderbird
- *Geary*

Web Browser
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- Brave
- Firefox
- *Chromium*
- *Opera*
- *Vivaldi*

Emulator
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- VirtualBox

Graphics Design
-------------------------------------

Image Manipulation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **GIMP**

Screenshots
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- FlameshotJS
- *Shutter*

Raster Graphics
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- GIMP
- Krita (Calligra)

Vector Drawing
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Inkscape**
- *Calligra Karbon*

Photography
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Darktable**
- *RawTherapee*

Image Conversion
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- Converseen

3D Design
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Blender**

Video Editing
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Kdenlive**
- *Shotcut*
- *Pitvi*
- *OpenShot*
- *Roxio NXT Creator 2* $

Audio/Music
--------------------------------------

Recording and Editing
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Audacity**
- *Ardour DAW*
- *Apple GarageBand* $†

Music Creation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- LMMS
- Hydrogen
- Garritan $†
- *Apple GarageBand* $†

Music Score
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **MuseScore**

Programming
---------------------------------------

Text Editor
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Visual Studio Code**
- Atom
- Geany
- *KATE*
- *Nano*
- *Vim*
- *Brackets* ‡
- *Emacs* ‡
- *Sublime* $‡

Build Tools
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **CMake**

C/C++ IDE
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Visual Studio Code**
- *Atom*
- *Code::Blocks*
- *Geany*
- *Vim*
- *Anjuta* ‡
- *Brackets* ‡
- *CodeLite* ‡
- *Eclipse CDT* ‡
- *Emacs* ‡
- *Kdevelop* ‡
- *Netbeans* ‡
- *Sublime* $‡

C/C++ Debuggers and Dynamic Analysers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Visual Studio Code** (debugging frontend)
- **gdb** or **lldb**
- **KCacheGrind**
- **Valgrind**
- Bless Hex Editor
- Nemiver
- Sysprof

C/C++ Static Analysers and Formatters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **clang-format**
- **cppcheck**
- AStyle
- cccc

C/C++ Testing
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Goldilocks**

Containers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Docker**

RestructuredText IDE
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Visual Studio Code**
- *Atom*
- *Geany*
- *Vim*
- *Brackets* ‡

Collaboration/Pair Programming
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Visual Studio Code: Live Share**

Python IDE
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Visual Studio Code**
- *Atom*
- *Geany*
- *NINJA-IDE*
- *PyCharm Community Edition*
- *Vim*
- *Aptana* ‡
- *Brackets* ‡
- *Emacs* ‡
- *Eric* ‡
- *Pydev* ‡
- *Kdevelop* ‡
- *Spyder* ‡
- *Sublime* $‡

Python Debuggers and Dynamic Analysers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **pdb**
- *pudb*

Python Static Analysers and Formatters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **black**
- **flake8** (includes PyFlakes, pycodestyle, mccabe)
- bandit
- flake8-bandit
- flake8-datetimez
- flake8-docstrings
- flake8-pytest
- flake8-mypy
- flake8-regex
- flake8-requirements
- mypy
- pydocstyle
- *pylint*

Python Testing
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **pytest**
- **ward**

Version Control Software
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- **Git**
- **Arcanist**
- **Meld**
- Git Cola

Operating Systems
-------------------------------------

- Ubuntu
- *Debian*
- *Kubuntu*
- *Linux Mint*
- *Lubuntu*
- *Ubuntu Studio*
- *Xubuntu*
- *Arch Linux* ‡
- *Fedora* ‡
- *Windows 10 with WSL* ‡

Disallowed Software
=====================================

..  NOTE:: This list doesn't apply to open source contributors, although we
    strongly discourage use of the software below.

Why Disallow Software?
--------------------------------------

The idea of “Officially Disallowing” software for company use might initially
seem to be overkill, but there is a logic to it. The decision is, again, not
made lightly. In most cases, the software title in question contains security
and privacy issues, bugs, or compatibility issues that make its use a
significant business and development risk. In other cases, the software is
disallowed on grounds of licensing issues. Paying several thousand dollars
extra for commercial licensing is impractical when there is equivalent
open-source software available.

It is worth noting that, while not the sole factor, drastic conflicts in
business ethics were also taken into consideration. MousePaw Media is built
around the conviction that educational and creative technologies should be
accessible to everyone, not just those with a lot of money. Relying on
corporations whose business practices are at stark odds with this ethic is,
frankly, counter-intuitive.

Disallowed Software List
----------------------------------------

The following may NOT be used for company purposes, under any circumstances,
unless otherwise noted or unless special permission is given by a supervisor.
If you need more details, talk to Jason C. McDonald directly. (You are welcome
to use these for personal reasons all you want.

Adobe
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

No Adobe products may be used for development, due to licensing costs,
file-type compatibility, and ethical concerns. (All useful Adobe products have
an open-source equivalent in our present standards.) This includes Adobe Flash.

Autodesk
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

No Autodesk products may be used for development, due to licensing costs,
file-type compatibility, and ethical concerns. (All useful Autodesk products
have an open-source equivalent in our present standards.) This includes
AutoCAD, 3ds Max, Maya, and Sketchbook.

Existing files may be opened with personal copies of Autodesk software for
review and export purposes only.

MP3 File Format
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Due to licensing and patent concerns, the MP3 format may NOT be used for any
audio.

EXCEPTION: A copy (NOT the master) of the audio may be saved as an MP3 for
compatibility with third-party services and software. Distribution in MP3 is
only allowed if the distribution platform strictly requires that format.

Microsoft Internet Explorer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Due to serious security and performance issues, Microsoft Internet Explorer is
NOT to be used under any circumstances for company purposes, including (but not
limited to) accessing the staff network, company-commissioned web design, or
accessing any website for work-related reasons.

..  NOTE: Our web design standards only support IE collaterally.

Microsoft Office
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Due to some ODT compatibility issues, and a lack of in-company training and
support, Microsoft Office is NOT to be used on any company documents.

Trimble SketchUp (formerly Google SketchUp)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Due to licensing costs, SketchUp may only be used for internal idea drafting,
and is strongly discouraged even for this.

Microsoft Windows
----------------------------------------

As of 2019, due to revisions in the Terms of Service and Privacy Policies for
Microsoft, we have lifted the ban on Microsoft Windows. However, **we still
require Linux for development work**. In circumstances where Linux is directly
uninstallable on a work machine, Windows 10 with Windows Subsystem for Linux
may be used.
