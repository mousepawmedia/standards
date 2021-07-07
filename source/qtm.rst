Quantified Task Management [QTM]
#######################################

**Version:** 2.0.0

**Last Updated:** 2021-07-07

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

What's New in This Version
--------------------------------

* Clarify Priority.
* Added Distance.
* Improve Friction, drop ``f0``.
* Improve Relativity, drop ``r0``.
* Add Energy Points.

Measures
================================

QTM consists of six measures:

* Priority: How soon?
* Gravity: How important?
* Distance: How much effort?
* Friction: How many available resources?
* Relativity: How much uncertainty?
* Volatility: How long did the bug go undiscovered?

Distance, Friction, and Relativity combine into Energy Points, which
can be used as the points measure for Agile methodologies.

.. _qtm_priority:

Priority
---------------------------------

**Priority** refers to **how soon** this task needs to be accomplished.
A task can be a low priority temporarily, and yet still have a high Gravity.

* **p5: Emergency.** Reserved for escalating a task above all other
  priorities; "drop everything and do this!"

* **p4: Now.** The usual top priority, and whatever is currently
  being worked on.

* **p3: Next.**  Tasks that should be completed in the current sprint,
  after current ``p4`` and ``p5`` tasks.

* **p2: Later.** Tasks that might not be completed in the current sprint.

* **p1: Eventual.** Tasks which are not slated for the current sprint.

* **p0: Wishlist.** Tasks that don't necessarily need to be completed.

* **pT: Triage.** Tasks which are not yet prioritized.

If you're using a more traditional Kanban board, you may be able to skip
implementing Priority.

.. _qtm_gravity:

Gravity (Importance)
-----------------------------------

A task's **Gravity** is its **importance to project goals**, including
stability and ease-of-use. It plays an important role in planning. This is
the only measure over which a client should have *direct* control.

This measure is especially useful when selecting features for removal to
expedite project completion.

* **g5: Critical.** Project can't exist without. Must be completed, period.
  Should *never* include aesthetic and convenience functionality.

* **g4: Significant.** Must be completed, only cut if desperate. Includes only
  functional requirements which directly improve on g5 features.
  (No bells-and-whistles.)

* **g3: Major.** Non-essential, but should be completed if time permits.
  "Polishing" tasks, and the most important bells-and-whistles.

* **g2: Minor.** Not slated for current release, but may be g4 or g5 for next
  release.

* **g1: Trivial.** "Would be nice" tasks; these take backseat to the
  completion of all other tasks. Should contain only tasks that could reasonably
  belong in the project at *some point*; this is the pool for selecting g3 tasks
  for future releases.

* **g0: Wishlist.** All other tasks which have been properly discussed, but
  no higher Gravity rating could be determined.

* **gΣ: Sum of all subtasks.** Use this for umbrella tasks that don't
  have a Gravity of their own. The Gravity will be the sum of the Gravity scores
  of its subtasks.

* **gT: Triage.** Proposed and unconfirmed tasks.

..  NOTE:: Gravity is discussed in detail in an article by
    Lead Developer Jason C. McDonald entitled
    `Three Ground Rules for Sane Project Planning <https://dev.to/codemouse92/three-ground-rules-for-sane-project-planning-37g9>`_

.. _qtm_distance:

Distance (Effort)
-----------------------------------

**Distance** is a measure of **how much effort** it would take to complete
a task, *given full domain knowledge*. The qualifier is important, as it
allows developers to achieve consensus on Distance despite differences in
their knowledge and skill level.

Distance measures effort in terms of time frame relative to the team's
sprint length, although it should be understood that *effort* is being
measured, rather than the timeframe itself. This is not a deadline.

* **d5: Exceeds Sprint.** Indicates task should almost certainly be broken
  down into subtasks.

* **d4: Within Sprint.**

* **d3: Within Half-Sprint.**

* **d2: Within Quarter-Sprint.** For sprints longer than two weeks, this can
  also be "Within Week".

* **d1: Within Session.** Work can be completed in one sitting.

* **dT: Triage Distance.**

There is no ``d0`` because all work requires some degree of effort.

.. _qtm_friction:

Friction (Available Help)
-----------------------------------

Friction is a quantified measure of difficulty, based on how many resources
are available to help complete a task, versus how much innovation (new
invention and experiementation) will be needed. The overall health of the
source code — good practice, patterns, clean coding — should also be taken
into account.

Friction should always be objective and empirical; it should never involve
the developer's actual experience level.

* **f5: Jungle.** Uncharted territory. You're on your own.

* **f4: Trail.** Little precendence and/or documentation. Mostly innovation,
  or work occurs in particularly unhealthy source code.

* **f3: Off-Road.** Some precendence and/or documentation. Work might occur
  in unhealthy source code, or significant innovation is required.

* **f2: Street.** Good precedence and/or documentation. Work likely occurs in
  healthy source code. Some innovation may still be required.

* **f1: Highway.** Low-skill tasks, tutorial-guided work, fixing typos.
  Work occurs in healthy source code.

There is no ``f0``, as all work involves some friction.

.. _qtm_relativity:

Relativity (Uncertainty)
----------------------------------------------------------

It can be easy to predict how much effort and time will go into a task, or
it can be very hard. We can call this uncertainty "flux". Relativity is
essentially a measure of how much flux is present in a task, and conversely,
how reliable our time and effort predictions are.

A task becomes a black hole when you have absolutely no idea how much time or
effort the task will require.

A good rule of thumb: you will know the relativity within the first hour of
working on a task.

* **r5: Collapsing/Black Hole.** Total flux. Task needs to be abandoned
  or re-factored, as it is virtually impossible in its current state.

* **r4: High.** Significant flux. Completion possible, but unlikely.

* **r3: Moderate.** Moderate flux. Completion within sprint is uncertain.

* **r2: Low.** Some flux, but completion within sprint is likely.

* **r1: Trivial.** Very little flux. Probably safe.

* **rT: Triage.** Relativity not yet determined for task.

There is no ``r0``, as one can virtually never say that a task is truly
without flux.

..  NOTE:: Relativity and flux (QTM v1) are discussed in detail in the article
    `Gallifreyan Software Project Management <https://dev.to/codemouse92/gallifreyan-software-project-management-29a1>`_

.. _qtm_energy:

Energy Points
---------------------------------------------------------

QTM can be used to inform the "points" used in Agile methodologies.
When the points are determined this way, they are known as **Energy Points**,
or just **Energy**.

The following formula is used to calculate Energy:

..  code-block:: text

    energy = (distance + friction) * relativity

A task's Energy score is a combination of direct effort (distance),
research and experimentation effort (friction), and the task's
uncertainty (relativity).

Over time, a developer will get used to how Energy maps to their individual
time and effort on a team. A more senior member of the team will be able to
complete more Energy Points worth of tasks in a work session than a junior
team member, in general.

Higher Energy tasks will also likely require more focus than lower Energy
tasks, even those of longer overall duration, due to Relativity. This fact
informs a developer when selecting work from the backlog to complete.
For example, if a developer is selecting work to do in the half hour before
a meeting, they would probably find they could make more meaningful progress on
an Energy 7 task than an Energy 25 task, even if both had the same Distance.

Finally, Energy is a good way to control how much work is selected for a
Sprint, because it explicitly takes Relativity and Friction into account,
rather than just overall effort.

.. _qtm_volatility:

Volatility
----------------------------------------------------------

Cumulatively, Volatility measures how late in the development process bugs are
being caught. This can be used to spot issues in software quality processes,
and to provide an estimation of software stability.

Volatility has two parts, although only one is absolutely necessary. The first
is the Volatility measure on the bug itself, indicating what development
stage it was caught in.

* **vN: Not a bug.** Feature requests and other non-bug issues should
  *always* have this rating (or else ``v0`` if you can't implement ``vN``.)

* **v0: Caught in Design phase.** This means the bug was anticipated before
  coding even began.

* **v1: Caught in Coding phase.** This means the bug was caught before it
  reached a protected branch, such as ``devel`` .

* **v2: Caught in SQA (Testing) phase.** This means the bug landed a
  protected branch, such as ``fresh`` , but was caught before reaching
  production.

* **v3: Caught in Production phase.** This means the bug actually shipped
  to end-users (i.e. it reached ``stable``).

The second part of Volatility is optional, but may be useful to certain teams.
*Origin* indicates which development stage the bug originated at.

* **oN: Not a bug/Unknown** This should be used for non-bug issues, and
  also if the origin cannot be determined.

* **o0: Originated in Design phase.** This usually means the bug is a logic
  error or impossible expectation that formed during the pre-coding Design
  process.

* **o1: Originated in Coding phase.** Almost all bugs are created during the
  actual code-writing process.

* **o2: Originated in SQA (Testing) phase.** For example, if a bugfix made at
  this stage causes another bug to form, this would be the origin.

* **o3: Originated in Production phase.** This usually means the bug was
  created during the process of preparing ``devel`` for shipment.

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
