..  _git:

Git Repository Standards
#######################################

..  _git_tools:

Tools
=======================================

We use the following tools:

- Git
- `GitLab <https://gitlab.mousepawmedia.com/>`_
- `Commitizen <https://commitizen-tools.github.io/commitizen/>`_:
    enforce Conventional Commits, maintain changelog and semantic versioning.
- `Branch Detective <https://pypi.org/project/branch-detective/>`_:
    detect which commits are different between branches; build merge request
    messages.

..  _git_strategies:

Git Strategies
============================================

Collaboration Workflow
---------------------------------------------

..  sidebar:: There are three reasons we do not exclusively use the trunk-based
    development strategy. First, our development cycles are slow, since our
    development team is entirely volunteer-based, so ongoing development of new
    features could easily block stability fixes to the current stable release.
    Second, we want to ensure that ongoing development does not block upstream
    projects which may require a stable release. Third, the added safeguards
    afforded by Gitflow mean that junior developers are not as easily able to
    "break production".

For testing and release purposes, we use the
`Gitflow <https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow>`_,
strategy. We reserve and protect three branches in our Git repositories:

- ``devel``  is for the latest development version.
- ``fresh`` is for the latest release candidate.
- ``stable`` is for the latest stable release.

For development purposes, however, we still use
`trunk-based development <https://www.atlassian.com/continuous-delivery/continuous-integration/trunk-based-development>`_
in relation to :code:`devel`, which we treat in the same manner as :code:`main`
in a standard trunk-based project.

In other words, we use trunk-based development against :code:`devel`, but
use Gitflow for handling actual releases.

..  _git_strategies_merge:

Merge Strategy
------------------------------------------------

We use the **rebase** merge strategy, meaning that a feature branch must be
rebased against :code:`devel` with `git rebase devel` before being merged.

We merge with fast-forward only (:code:`ff-only`), meaning we never create
dedicated merge commits.

Since we enforce Conventional Commits (see :ref:`git_commit`), we do NOT
squash commits.

..  _git_commits:

Commit Messages
============================================

Starting from January 2022, we require the
`Conventional Commits 1.0.0 <https://www.conventionalcommits.org/en/v1.0.0/>`_
standard to be used for all commit messages.

In short, a standard commit message will follow this template:

..  code:: text

    type(scope): commit title

    Detailed commit summary.
    This can span multiple lines.

    BREAKING CHANGE: Describe breaking change, if relevant.
    Co-Authored-By: Other Authors <other@example.com>, If Any <ifany@example.com>
    Refs: Ticket number or Discourse link

We utilize the :code:`BREAKING CHANGE` footer over only the :code:`!` annotation
on the type, although both may be used.

The possible types come from the `Angular style guide <https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#type>`_

- build: Changes that affect the build system, packaging, or external dependencies.
- ci: Changes to our CI/CD configuration files and scripts.
- docs: Documentation-only changes.
- feat: A new feature.
- fix: A bug fix.
- perf: A code change that improves performance.
- refactor: A code change that neither fixes a bug nor adds a feature.
- style: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc).
- test: Adding missing tests or correcting existing tests.

Each commit should have a single, well-defined purpose, and all changes within
the commit should relate to the purpose and the commit type. Where possible,
all related changes with a given purpose and type should be grouped into a
single commit.

..  _git_commits_changeset::

The Changeset Approach
--------------------------------------------

The goal of a Merge Request is not merely to modify code, but to present a
clean **changeset** of neat, well-structured commits. Typically, each
commit should be capable of passing all static analysis, linting, and automated
tests by itself.

You also want to avoid "confetti commits", such as multiple "fix typo" commits
in the same merge request.

In practice, it's very difficult to create such a clean set of commits on the
first try. Thankfully, you can modify your commits without losing your changes.

First, check how many commits you need to rework. Make sure you do not
modify any commits which are already on :code:`devel`, but rather only those
that were added in your current branch.

..  code-block:: bash

    git log

At this point, you should open a text document and plan out your new commits.
Look at your existing commit messages, as well as your changes themselves.
Write a good commit message for each commit you plan to create, and save
anything useful from your existing commit messages (which you're about to undo).

Next, undo your commits with the following command, where :code:`#` is the
number of commits to undo. You'll also stash and reapply your changes, so you
have a backup in case of a mistake.

..  code-block:: bash

    git reset --soft HEAD~#
    git stash push -um "Changes before reworking commits"
    git stash apply

Your changes are now all _uncommitted_. You can begin building your new commits.
There are a couple of good ways to do this.

The first is to use your IDE (such as Visual Studio Code) to actually _revert_
any pending changes you don't want in any given commit. Modify your pending
changes using the source control panel to only reflect the changes you want in
the one commit. Then, run your static analysis tools, tests, and so on, and
create your commit. Once you've done that, run :code:`git stash apply` again to
recover any other pending changes. Resolve merge conflicts that have formed,
and repeat the process with the next commit.

The other way is to use the command line to interactively pick the changes
you want to include:

..  code-block:: bash

    git add -p .

Once you've added the changes you want, stash the rest and commit.

..  code-block:: bash

    git stash push -um "Changes after <title of commit>"
    git commit

Run your static analysis tools, linters, tests, and so on. Fix any errors
directly, amending your commit as necessary.

Then, apply your last stash...

..  code-block:: bash

    git stash apply

And repeat for the next commit.

If at any point during either process, you realize you forgot to include a
change in a previous commit, you can go back and modify that commit. Finish
your current commit first, stash if necessary (to get a clean repository),
and then run the following, where :code:`#` is a number greater than or
equal to how many commits back the oldest commit you want to change is:

..  code-block:: bash

    git rebase -i HEAD~#

This will open a file listing the commits to be changed. Find the commit(s)
you want to modify, and change :code:`pick` to :code:`edit` next to them.
Save and close the file. You will now be guided through the rebase process
by the command line prompts (so read them carefully!)

..  _git_mergerequest:

Merge Requests
============================================

Changes to :code:`devel` should be proposed by creating a Merge Request on
our GitLab instance. This Merge Request should include one or more commits.

A Merge Request should be related to a single primary goal, generally a single
task in our issue tracker. It may include other minor improvements, but should
NOT include changes for multiple issues, unless those issues are unavoidably
related.

Every Merge Request must…

1. Accomplish the goals(s) it was designed to accomplish.

2. Comply with Conventional Commits for all commit messages.

3. Be rebased against the latest version of devel (or whatever branch is targeted), and all conflicts resolved (:code:`$ git pull origin devel `). (We do NOT use the “squash” or “merge” Git strategies.)

4. Have binaries and unnecessary cruft untracked and removed. (Keep an eye on .gitignore!)

5. Compile and run properly. (Confirmed via the CI/CD Pipeline.)

6. Be free of compiler errors and warnings; for C++, must compile with -Wall -Wextra -Werror. (Confirmed via the CI/CD Pipeline.)

7. For C++, be Valgrind pure, meaning no memory leaks are detected. (Confirmed via the CI/CD Pipeline.)

8. Comply with Coding and Technical standards.

9. Include tests validating the accomplishment of goals in (1). These tests must be written in the project’s test framework, if relevant.

10. Be fully Commenting-Showing Intent commented.

11. Have an up-to-date build script (generally CMake) if relevant.

12. Be reviewed, built, tested, and approved by at least one trusted reviewer.

13. Have up-to-date Sphinx documentation, which compiles with no warnings.

14. Have all reviewer comments processed and marked “Done”.

..  _git_versioning:

Versioning
============================================

Starting from January 2020, we use `Semantic Versioning 2.0.0 <https://semver.org/>`_
for all software development projects. Our version numbers follow the format
``X.Y.Z``

- ``X`` is a major release, reserved for changes to the API or CLI.
- ``Y`` is a minor release, for releases with new features.
- ``Z`` is a patch release, for bugfix-only releases.

We use Commitizen to automatically generate semantic versions from Conventional
Commit messages.

..  _git_versioning_zero:

About Zero-Versions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Zero-Versions are versions at Major Release ``0``. They are considered
inherently unstable and feature incomplete, and thereby un-releasable. They
cannot be promoted to either ``fresh`` or ``stable``.

A project remains at a Zero-Version until it is considered complete and
stable enough to promote to version ``1``.

To enforce this rule, projects at version zero should **NEVER** have
:code:`BREAKING CHANGE` commits. When it is time to promote the project
to version 1, a single, dedicated commit with an insignificant change should
be created with `BREAKING CHANGE`.
