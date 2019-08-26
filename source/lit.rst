Live-In Testing [LIT]
############################

**Version:** 1.0.0

**Last Updated:** 2016-05-31

Purpose
==========================
The phrase "unit testing" is far too overreaching, and is linked heavily to
the theory of Test-Driven Development. It is also intended for a very specific
purpose, but is often mis-applied to all built-in tests.

Because we need a testing standard that has no relation to TDD, we have created
the Live-In Testing Standard [LIT]. While it is our sole testing standard at
MousePaw Media, other projects may choose to use this standard alongside TDD,
as it is an unrelated standard.

Philosophy and Limitations
==================================
The main principle behind the Live-In Testing Standard is that all tests are
built into the code being tested, and are compiled alongside of it. Tests are
executed while the program is running.

There are several distinct advantages to this:

- Tests can be shipped with the software. Tech support can instruct users to
  run tests, in order to generate specific and useful debugging information.
  This information can in turn be used to fix the problem over the phone, or
  provide the necessary details to file a bug report.
- It is easier to extract useful information from a test output than from a
  log file.
- Benchmarking and (most) testing can be performed on all supported systems
  without the need to install special tools or applications.

Vocabulary
===========================

dependency
    a test that must be run before the current test.
lifetime
    a single test lifetime involves a single setup, any number of runs, and
    a single teardown.
repetition
    starting a single test one time generally has multiple repetitions.
    One consistency test may, for example, input the same scenario and
    validate the output 100 times in a single run of the test.
run
    a single time a test is executed by the developer or user.
scenario
    a complete and exact set of variables and conditions for running a test.
    Tests should control for all variables.
setup
    the actions taken to prepare a test to be run. Called once per lifetime.
teardown
    the actions taken once at the end of a test's lifetime, generally before
    the test object is deleted.

Implementation
=======================================
MousePaw Media' **Golilocks** library (a component of PawLIB) is designed
specifically for LIT in C++. **Blueshell** (upcoming in PawLIB 1.1) can be
used to quickly create a run-time interface for Goldilocks.

For other languages, the most important thing to remember about implementing
an LIT testing framework is that all tests are executed *on-demand* by the
user *during run-time*.

General Guidelines
========================================

- Each scenario should have a unique code. For example, an Edge Test that
  randomly generates six integers for the scenario might also use those six
  integers as its scenario code. ``3.13.9.15.39.779``

  - A given test may use any systems for generating the code, so long as the
    code is a) unique and b) can be used to duplicate the exact scenario in
    the test.
  - The test must be capable of re-running a scenario by an input scenario
    code. (Necessary for long-distance testing.)
  - Scenario codes must be made up of visible and recognizable characters
    (ideally Latin-alphanumeric with punctuation), and should be no more than 35 characters in length. (Again, necessary for long-distance testing.)
  - Particularly large scenarios may need to be randomly generated
    beforehand, hard-coded, and stored in a lookup table in order to make
    the scenario code practical.

- If a test relies on the proper functionality of a feature that is not being
  directly tested and validated, the test for that feature would be considered
  a dependency. For example, one must test file I/O before testing XML parsing,
  and XML parsing must be tested before using a test which writes a random XML
  file as part of scenario generation.

Test Types
=============================

Behavior Tests [B]
------------------------------
A Behavior Test tests a single common behavior or feature. These are generally
most useful for comparative testing. A single letter may follow the ID to
indicate which subversion of the test is being used.

Consistency Tests [C]
-----------------------------
A Consistency Test repeats one scenario a large number of times within known
limits, and ensures the output is valid and consistent. This is designed to
test features and catch Heisenbugs.

Guidelines
^^^^^^^^^^^^^^^^^^^^^^^^^
- Whether a scenario is random or crafted, the test should repeat that scenario
  exactly multiple times.
- The output of each repetition should be identical to the output of the last
  repetition.
- Find repetition limits first, and stay well within them.

Developer Tests [D]
------------------------------------
These are custom tests designed by a specific developer that don't fit in
another category.

Edge Test [E]
------------------------------------
Edge tests generate random scenarios for testing a given feature.

Guidelines
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- Each scenario should be unique and random, as far as is possible and
  practical.
- Crafted scenarios may be integrated into the test, as long as the test
  scenario is still random enough to potential end-user situations. (The
  danger of crafting a scenario is our implicit and innate tendency to avoid
  triggering problems in the code in our tests.)
- An edge test may either explicitly target the valid creation of non-error
  response, or error response, but not both in the same test.
- Edge tests should be written to target vulnerable situations, that is,
  situations that have a higher probability of failing in an unusual scenario.

Fatality Tests [F]
------------------------------------
Larger tests intended to trigger total program or system crashes.
Intended to find the hard limits of the software and its environment.
One example of this is to run a Consistency Test until the system's
resources are totally consumed. The results of a Fatality test are
generally useful in a) establishing checkpoints and failsafes that prevent
the software from crashing or taking out the system, and b) validating
comparability with a particular system.

Guidelines
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- These should NEVER be run automatically! (Must be run manually.)
- The interface should display an error before running.
- A Fatality Test should not be totally dependent on the program being
  tested. (Logfile writing is vital.)
- System Fatality Tests should be monitored closely, and designed to
  crash the system in a manner which allows the test data to be collected.
- Fatality Tests should always generate a scream-and-die situation,
  so that the cause of the crash can be validated.

Integration Tests [I]
----------------------------------
Smaller tests that are intended to ensure that connected classes are
communicating with one another properly, and that constructors and
initialization is functioning properly.

Guidelines
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- Works primarily through ping/pong scenarios, which ensure that two classes,
  objects, or programming structures are able to access each other appropriately.
- Integration tests with OOP situations would generally need to use specialized
  dynamic allocation of objects, thus allowing the scenario to be fully
  controlled by the test.
- Integration tests should use the same constructors and initializers that
  are used in normal program execution. Thus, the necessary code for
  Integration tests would have to be hard-coded into the regular program
  structure, though most of the special code would only be triggered by the
  test itself.

Proposed Tests [P]
---------------------------------
Any test that is written, but not yet adopted.

Stress Tests [S]
----------------------------------
Larger tests intended to break fragile code, to make sure they're stable.

Guidelines
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- Should find the breaking point of the targeted code or feature in all
  conceivable directions. Each direction may be split into a different test,
  depending on testing and project needs.
- Stress tests should never target a program or system crash. (See Fatality
  Tests).
- Should run as either an extreme Consistency test or Edge test, but not
  both in one test.
- Must write to an external log file, otherwise the information cannot be
  examined.

Test Suite Types
==============================

Regression Suite
------------------------------
A regression suite runs the minimum tests necessary to ensure that all
basic program functionality works as expected. A single suite may target
only the particular set of code or feature set affected by a change.
(For example, we might have a separate Layers Regression Suite.)

Guidelines
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- Made up of Consistency, Edge, and Integration tests only.
- A regression suite should be run on every Differential.
- Should only involve tests which can run quickly and automatically.

Use Suite
------------------------------
These are intended to simulate specific use cases. This allows us to ensure
that simultaneous use of features isn't going to create problems.

Guidelines
^^^^^^^^^^^^^^^^^^^^^^^^^^
- Made up of Consistency, Edge, and Integration tests only.
- Should ideally generate semi-crafted scenarios.
- May take longer to run than a Regression Suite, but should only involve
  tests which can run automatically.

Test Library Structure
================================

Naming
----------------------------
A test should have a unique identifier in addition to a name. The unique
identifier should start with a lowercase 't', and then it should indicate
the type and a number. In the case of Developer and Proposed,
initials are also required at the end. With Proposed tests, the intended
category should precede the number.

Examples:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
tD001-JCM
    A developer test by Jason C. McDonald (with the number 001).
tB051
    Behavior test 51.
tE105
    Edge test 105.
tS068
    Stress test 68.
tC971
    Consistency test 971.
tC679-pJCM
    A consistency test designed by Jason C. McDonald, but not yet officially
    adopted.

Namespaces
-----------------------------------
Each section of a project should be given its own "namespace" within test
names, to prevent conflicts.

Major sections might be assigned an ID, which can be tacked on
the beginning of the test name. For example, in the RATS Game Engine,
the following IDs are used.

+-----+----------------------------+
| ID  | Project/Subproject         |
+=====+============================+
| A   | Anari Graphics System      |
+-----+----------------------------+
| AP  | Anari: Punchline           |
+-----+----------------------------+
| P   | PawLIB                     |
+-----+----------------------------+
| Q   | Quicksilver                |
+-----+----------------------------+
| R   | Ratscript                  |
+-----+----------------------------+
| S   | Stormsound                 |
+-----+----------------------------+
| T   | Trailcrest                 |
+-----+----------------------------+
| TCE | Trailcrest: Content Engine |
+-----+----------------------------+
| TUE | Trailcrest: User Engine    |
+-----+----------------------------+
| TWE | Trailcrest: World Engine   |
+-----+----------------------------+
| X   | SIMPLEXpress               |
+-----+----------------------------+

For example, ``P-tB102`` would be a behavior test for PawLIB.

.. NOTE:: Depending on implementation, all tests for a particular project
   could be loaded into the test system on-demand.

It may frequently be necessary to further subdivide a project's tests.
The first one or two digits of the test ID can be used to indicate the
sector of the project. For example, within PawLIB, we use the following
numbers:

+----+--------------------+
| ID | Sector             |
+====+====================+
| 0x | Data Types         |
+----+--------------------+
| 01 | Trilean            |
+----+--------------------+
| 1x | Data Structures    |
+----+--------------------+
| 10 | FlexArray          |
+----+--------------------+
| 11 | FlexMap            |
+----+--------------------+
| 12 | FlexQueue          |
+----+--------------------+
| 13 | FlexStack          |
+----+--------------------+
| 14 | SimplyLinkedList   |
+----+--------------------+
| 15 | FlexBit            |
+----+--------------------+
| 16 | Pool               |
+----+--------------------+
| 20 | IOChannel          |
+----+--------------------+
| 30 | PawSort            |
+----+--------------------+
| 4x | OneString (Sector) |
+----+--------------------+
| 41 | OneChar            |
+----+--------------------+
| 42 | QuickString        |
+----+--------------------+
| 43 | OneString          |
+----+--------------------+
| 5x | Blueshell          |
+----+--------------------+
| 6x | Utilities          |
+----+--------------------+

Thus, looking again at ``P-tB102``, that would be a behavior test relating
to data structures. (We actually reserve the second digit for further
subtyping - ``10`` relates specifically to FlexArray.)

Adoption
-----------------------------
In many cases, tests should start as Proposed (``...-p???``). Then they are
added later by the lead developer to the official library. This is to prevent
conflicts when two developers add tests with the same name.

For example, ``tC679-pJCM`` would be a proposed test by Jason C. McDonald.

This step may be skipped if a single developer is working alone on a section.

Permanence
-----------------------------
Most tests, with the possible exception of Fatality and some Stress tests,
should remain in the code. This way, they can be run from a developer
terminal by the end-user, as a component of long-distance technical support.

For example, a tech support agent could ask the user to bring up a developer
Ratscript terminal (which would probably involve entering a unique key),
and then type test ``tC971``. The results could then be read back to the tech
support agent (i.e. ``FAILED: Could not create data structure.``, at which
point the exact cause of the problem on the user's computer can be pinpointed.
