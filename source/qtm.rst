Quantified Task Management [QTM]
#######################################

Vision
===================================
For decades, programmers and managers have struggled to create a reliable
system of tracking tasks and bugs. Managers need quantified (countable) ways
to determine how much work has been done, and how long it will take until a
task or project is completed. Programmers need to be able to manage their time,
determine the importance of bugs and tasks, and predict release dates.

As depicted in Dreaming in Code by Scott Rosenberg, among many other books,
quantifying programming is extremely difficult. Some companies have tried
tracking lines of code written, but how should optimization (which actually
*removes* lines in the process of making the code more efficient) be tracked?
Others try to watch how many bugs were fixed or how many features are
completed. However, not all bugs and features are equal in size, importance,
or priority.

Three elusive main goals are needed for efficient project management:

- Quantification: It needs to be based in numbers.
- Granularity/Standardization: Everything must be measurable by the same system
  in order to make accurate comparisons. (We can't accurately compare equal sized
  crates, one filled with feathers, and the other with bowling balls.)
- Specificness: Over-generalization makes for less accuracy. The system should
  be able to track important task/bug metrics separately, not mush them all into
  one cover-all term.

Measures
================================

.. _qtm_priority:

Priority
---------------------------------
Priority refers to how soon this task needs to be accomplished. A task can be
a low priority temporarily, and yet still have a high Gravity.

- **``p0``: Wishlist.** Tasks that don't necessarily need to be completed.
- **``p1``: Eventual.** Lowest priority tasks.
- **``p2``: Soonish.** Tasks that don't necessarily need to be completed in
  the current development cycle.
- **``p3``: Normal.**  Tasks that should be completed in the current development
  cycle, after current ``p4`` and ``p5`` tasks.
- **``p4``: Important.** The usual top priority, and whatever is currently
  being worked on.
- **``p5``: Immediate.** Reserved for escalating a task above all other
  priorities; "drop everything and do this!"

.. _qtm_gravity:

Gravity (Importance)
-----------------------------------
A task's Gravity is its importance to ensuring the project is stable,
easy-to-use, and accomplishes all of its intended goals.

This measure is especially useful when performing a "featurectomy" (removing
features from a project to expidite it's completion.)

- **``g0``: Wishlist.** Proposed and unconfirmed tasks.
- **``g1``: Trivial.** "Would be nice" tasks; these take backseat to the
  completion of all other tasks. First to be cut.
- **``g2``: Minor.** "Polishing" tasks, bells and whistles. Ideally should be
  completed, but can be cut if necessary.
- **``g3``: Major.** Non-essential, but really should be completed if possible.
- **``g4``: Significant.** Must be completed, only cut if desperate.
- **``g5``: Critical.** Project can't exist without. Must be completed, period.
- **``gΣ``: Sum of all subtasks.** Use this for umbrella tasks that don't
  have a gravity of their own.

.. _qtm_friction:

Friction (Available Help)
-----------------------------------
Friction is a quantified measure of difficulty, based on how many resources
are available to help complete a task. This does not involve the person's
actual experience, as that varies from person to person.

The following table shows how this could work, rating each aid as Full, Some
(similar to goal), Little (dissimilar to goal), or None.

+--------+--------------+----------+-------------+-----------+------------+
| Rating | Name         | Docs     | Code        | Tutorials | Precedence |
+========+==============+==========+=============+===========+============+
| ``f0`` | Freeway      | Full     | Full        | Full      | Full       |
+--------+--------------+----------+-------------+-----------+------------+
| ``f1`` | Street       | Full     | Full        | Some      | Some       |
+--------+--------------+----------+-------------+-----------+------------+
| ``f2`` | Back Road    | Full     | Some/Little | Little    | Little     |
+--------+--------------+----------+-------------+-----------+------------+
| ``f3`` | Trail        | Some     | Little      | None      | Little     |
+--------+--------------+----------+-------------+-----------+------------+
| ``f4`` | Trailblazing | Little   | None        | None      | None       |
+--------+--------------+----------+-------------+-----------+------------+
| ``f5`` | Bushwhacking | None     | None        | None      | None       |
+--------+--------------+----------+-------------+-----------+------------+

.. _qtm_relativity:

Relativity/Black Hole Probability (Uncertainty)
----------------------------------------------------------
It can be easy to predict how much effort and time will go into a task, or
it can be very hard. We can call this uncertainty "flux". Relativity is
essentially a measure of how much flux is present in a task, and conversely,
how reliable our time and effort predictions are.

A task becomes a black hole when you have absolutely no idea how much time or
effort the task will require.

A good rule of thumb: you will know the relativity within the first hour of
working on a task.

- **``r0``: No chance of black hole.** No flux.
- **``r1``: Low black hole probability.** Probably safe.
- **``r2``: Moderate black hole probability.** Some flux, but looks possible
  to complete.
- **``r3``: High black hole probability.** Still possible to complete,
  but take caution.
- **``r4``: Almost-definite black hole.** Completion possible, but unlikely.
- **``r5``: Collapsing.** Bail out NOW. Task needs to be abandoned or
  re-factored - it is virtually impossible in its current state.

..  NOTE:: Relativity and flux are discussed in detail in an article by
    Lead Developer Jason C. McDonald entitled
    `Gallifreyan Software Project Management <https://dev.to/codemouse92/gallifreyan-software-project-management-29a1>`_

.. _qtm_volatility:

Volatility
----------------------------------------------------------
Cumulatively, Volatility measures how late in the development process bugs are
being caught. This can be used to spot issues in software quality processes,
and to provide an estimation of software stability.

Volatility has two parts, although only one is absolutely necessary. The first
is the Volatility measure on the bug itself, indicating what development
stage it was caught in.

- **``vn``: Not a bug.** Feature requests and other non-bug issues should
  *always* have this rating (or else ``v0`` if you can't implement ``vn``.)
- **``v0``: Caught in Design phase.** This means the bug was anticipated before
  coding even began.
- **``v1``: Caught in Coding phase.** This means the bug was caught before it
  reached a protected branch, such as ``master``.
- **``v2``: Caught in SQA (Testing) phase.** This means the bug landed a
  protected branch, such as ``master``, but was caught before reaching
  production.
- **``v3``: Caught in Production phase.** This means the bug actually shipped
  to end-users (i.e. it reached ``stable``).

The second part of Volatility is optional, but may be useful to certain teams.
*Origin* indicates which development stage the bug originated at.

- **`on`: Not a bug/Unknown** This should be used for non-bug issues, and
  also if the origin cannot be determined.
- **`o0`: Originated in Design phase.** This usually means the bug is a logic
  error or impossible expectation that formed during the pre-coding Design
  process.
- **`o1`: Originated in Coding phase.** Almost all bugs are created during the
  actual code-writing process.
- **`o2`: Originated in SQA (Testing) phase.** For example, if a bugfix made at
  this stage causes another bug to form, this would be the origin.
- **`o3`: Originated in Production phase.** This usually means the bug was
  created during the process of preparing `master` for shipment.

You can combine these two metrics to get the Adjusted Volatility [AV] score
for any bug::

    AV = v-o

The Adjusted Volatility allows you to account for how much opportunity
developers had to *catch* the bug. For example, a mistake made during
packaging is worth noting, but it isn't nearly as alarming as a bug introduced
in the design phase, but not caught until after it shipped to users.

Volatility's true strength is in project management. See :ref:`qtm_vscore`
to learn how to calculate and use this metric.

..  NOTE:: Volatility is based on the article
    `How I Measured The Software Testing Quality <https://dev.to/kashifkazi/how-i-measured-the-software-testing-quality-b60>`_
    and the subsequent comment chain.

.. _qtm_accomplishment:

Accomplishment
===============================

To get the best sense of what has been done by a developer in a given time
period, we'd look at the average Gravity, Priority, and Friction.

Here is a table of examples of the system in action.

Legend: ``measureTOTAL(AVERAGE))``

+-------+----------+----------+----------+---------------------------------------------+
| Tasks | Total G  | Total P  | Total F  | Conclusion                                  |
+=======+==========+==========+==========+=============================================+
| 5     | g21(4.2) | p8(1.6)  | f8(1.6)  | Important (but probably easy) overall       |
|       |          |          |          | accomplishments, though few of them         |
|       |          |          |          | needed to be done now. A good week's work.  |
+-------+----------+----------+----------+---------------------------------------------+
| 5     | g8(1.6)  | p21(4.2) | f8(1.6)  | The tasks were urgent right now, but        |
|       |          |          |          | not important in the big scheme of          |
|       |          |          |          | things. Probably easy. A good week's work.  |
+-------+----------+----------+----------+---------------------------------------------+
| 5     | g15(3)   | p15(3)   | f23(4.6) | Moderately important tasks, all             |
|       |          |          |          | extremely difficult. A HUGE                 |
|       |          |          |          | accomplishment.                             |
+-------+----------+----------+----------+---------------------------------------------+
| 20    | g20(1)   | p20(1)   | f20(1)   | A lot of tasks were done, but none          |
|       |          |          |          | were very urgent or important, and          |
|       |          |          |          | all were really easy. Not as                |
|       |          |          |          | impressive as the task count seems.         |
+-------+----------+----------+----------+---------------------------------------------+

These numbers have to be taken in context with other factors, of course, but
they give a MUCH more accurate picture than other management and tracking
methods.

.. _qtm_vscore:

Project Volatility Scoring
===============================

The Volatility metric is most useful in catching problems within an overall
project or team.

To calculate a project's Adjusted Volatility score, use the following equation::

    A = project Adjusted Volaility score
    M = project's Mean Volatility score
    b = number of bugs
    v = sum of all bug volatility scores
    o = sum of all bug origin scores

    A = (bv - bo)/b
    M = v/b

You may want to record both the project's Mean Volatility (``M``) and Adjusted
Volatility (``A``), as useful information can be garnered from both.

For example...

* A very high ``A`` indicates that many bugs are slipping past review
  processes.

* A high ``M`` and low ``A`` indicates that a lot of bugs are actually
  originating in SQL or Production phases.

Sometimes, tracking Origin just isn't useful for your team, in which case
you can just use ``M``.
