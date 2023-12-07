MousePaw Media Standards
=====================

MousePaw Media has authored a number of standards to guide their
ongoing software development efforts. These standards are
made freely available for the benefit of the open source
community, and the programming community at large.

More information can be found on the [Standards][1] page.

Standards Format
--------------------------

The standards are all written in RestructuredText format,
to be compatible with Sphinx. The root of the repository contains
a makefile which can be used to generate the documents.

Building
----------------------------------

You must have Python 3 installed on your system, and you need to create a
virtual environment. On UNIX-based systems, you can run:

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r source/requirements.txt
```

Then you can run one of the following `make` commands:

```bash
make html # Create HTML version.
make latex # Create LaTEX version.
make latexpdf # Create PDF via LaTEX.
make man # Create man pages.
make epub # Create e-book.
```

There are additional make targets as well. To see the complete list, simply run...

```bash
make
```

Standards Board
-------------------------

**2016 Board**
 - Audrey Henry
 - Nate Groggett
 - Anne McDonald
 - Jason C. McDonald
 - Scott Taylor

**2018 Q1 Board**
 - Jason C. McDonald
 - Jarek Thomas
 - Bowen Volwiler
 - Sergio Ramirez

Feedback
-------------
These standards are written and maintained by the
MousePaw Media Standards Board. Feedback is welcome
via email (developers@mousepawmedia.com).

For more information about contributing to MousePaw Media
projects, see [mousepawmedia.com/opensource][2].

License
-------------
The MousePaw Media Standards are made available via the
Creative Commons Attribution-ShareAlike ([CC BY-SA 4.0][3]) license.

The project is owned and maintained by [MousePaw Media][2].

[1]: https://www.mousepawmedia.com/standards
[2]: https://www.mousepawmedia.com/developers
[3]: https://creativecommons.org/licenses/by-sa/4.0/
