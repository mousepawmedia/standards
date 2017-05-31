MousePaw Media Standards
=====================

MousePaw Media has authored a number of standards to guide their
ongoing software development efforts. These standards are
made freely available for the benefit of the open source
community, and the programming community at large.

The most notable of these standards include:

 - CSI: Commenting Showing Intent
 - LIT: Live-In Testing
 - QTM: Quantified Task Management

More information can be found on the [Standards][1] page.

Standards Board
-------------
 - Audrey Henry
 - Nate Groggett
 - Anne McDonald
 - Jason C. McDonald
 - Scott Taylor

Standards Format
-------------
The standards are all written in RestructuredText format,
to be compatible with Sphinx. The root of the repository contains
a makefile which can be used to generate the documents.

On a Unix system, you can use the following commands:

    $ make html # Create HTML version.
    $ make latex # Create LaTEX version.
    $ make latexpdf # Create PDF via LaTEX.
    $ make man # Create man pages.
    $ make epub # Create e-book.

There are additional make targets as well. To see the complete list, simply run...

    $ make

Feedback
-------------
These standards are written and maintained by the
MousePaw Media Standards Board. Feedback is welcome
via email (developers@mousepawgames.com).

You can also frequently find us in the #mousepawgames
channel on Freenode.

Pull requests to this repository are not accepted. If
you wish to propose a change, email your patch to us
at the address above.

For more information about contributing to MousePaw Media
projects, see [mousepawgames.com/opensource][2].

License
-------------
The MousePaw Media Standards are made available via the
Creative Commons Attribution-ShareAlike ([CC BY-SA 4.0][3]) license.

The project is owned and maintained by [MousePaw Media][2].

[1]: http://www.mousepawgames.com/standards
[2]: http://www.mousepawgames.com/opensource
[3]: https://creativecommons.org/licenses/by-sa/4.0/
