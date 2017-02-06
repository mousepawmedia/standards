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

Relativity/Black Hole Probability (Uncertainty)
----------------------------------------------------------
It can be easy to predict how much effort and time will go into a task, or
it can be very hard. Relativity is essentially a measure of how accurate the
predictions are. A task becomes a black hole when you have absolutely no idea
how much time the task will take.

A good rule of thumb: you will know the relativity within the first hour of
working on a task.

- **``r0``: No chance of black hole.** No relativity.
- **``r1``: Low black hole probability.** Low relativity.
- **``r2``: Moderate black hole probability.** Moderate relativity.
- **``r3``: High black hole probability.** High relativity.
- **``r4``: Definite black hole.** Total relativity.
- **``r5``: Collapsing.** Task needs to be abandoned or re-factored - it is
  probably impossible in its current state.

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
