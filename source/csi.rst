Commenting Showing Intent [CSI]
#######################################

**Version:** 1.2.1

**Last Updated:** 2019-08-26

The CSI (Commenting Showing Intent) Commenting Standards refers to a
style of code commenting which allows for the complete rewriting of a
program in any language, given only the comments. It is also a backhanded
reference to Crime Scene Investigation: putting the clues together to
recreate the whole event.

Purpose and Theory
=======================================

In many languages, it is considered “bad practice” to not comment code,
yet so many programmers fail to do it. Many more write comments to
themselves, but these comments are often cryptic at best. Still others write
comments that restate the functionality of the code.

Because of these problems, several practices exist which condemn comments in
most, or all, situations. This leads to code which becomes inexorably separated
from its specification.

The CSI Commenting Standard offers a non-language-specific standard
for writing comments.

..  NOTE:: Intent-Commenting is discussed in detail in an article by
    Lead Developer Jason C. McDonald entitled
    `To Comment Or Not To Comment <https://dev.to/codemouse92/to-comment-or-not-to-comment-3f7h>`_

Advantages
---------------------------------------

We're asking you to type twice, if not three times, as much as you do now.
What's the advantage to that?

1. CSI comments become a **living specification**, wherein the expected behavior
of the program and the actual functionality live in close proximity to one
another, and can be more easily kept in sync and up-to-date.

2. When you come back to your code after a long time away, you will be
able to find your footing much faster.

3. When other developers (or non-programmers) read your code or API
documentation, they will be able to understand it more thoroughly,
much quicker. This is vital to efficient code reviews and third-party
debugging.

4. You significantly reduce the entry learning curve for new contributors.
Because learning the code is much easier, individuals are able to start
making meaningful contributions more quickly.

5. You and your code reviewers will be able to desk-check, debug, and track
complicated logical thought patterns much quicker. Mismatches between intent
and actual behavior become evident.

6. When you are dealing with a complex logical process that you are trying
to write code for, you can start by writing your entire function in
CSI-compliant comments. Then, using these comments as a sort of pseudocode,
you can write the code under each comment.

7. You can translate your program into another computer language much quicker.
Again, by using the CSI-compliant comments, you can rewrite each line of
code to work in your programming language.

8. The code becomes collaterally useful for demonstrating the language
syntax and features themselves. Armed with an understanding of the goal, the
less experienced developer can more quickly surmise how the code works.
(See #4.)

CSI vs. Self-Commenting Code
-------------------------------------

"Self-Commenting Code" is a practice wherein a code's functionality is
self-evident. Through naming, structure, and various other techniques,
the immediate purpose becomes obvious to the reader. This is beneficial in
any language.

However, "Self-Commenting Code" is seldom capable of expressing the entire
intent, or "why", of the code.

- It is nearly impossible to express the *intended* behavior of the code;
only the *actual* behavior is evident, which can conceal logic errors.

- Code cannot imply the reason the current approach was taken over another.

- Code can seldom self-express its purpose in its larger context. Even attempting
to do so can lead to impractically long function and class names.

The CSI Standard should exist *alongside* Self-Commenting Code practices, not
*instead of*.

+-----------+-------------------+---------------------+
|           | CSI               | Self-Commenting     |
+===========+===================+=====================+
| Topic     | Intended          | Actual behavior.    |
|           | behavior.         |                     |
+-----------+-------------------+---------------------+
| Question  | **WHY** did we    | **WHAT** does the   |
|           | write this code?  | code do?            |
+-----------+-------------------+---------------------+
| Expresses | Language-agnostic | Language-specific   |
|           | specification.    | functionality.      |
+-----------+-------------------+---------------------+

CSI vs. Documentation
--------------------------------------
The CSI Commenting Standard **should not** be confused with documentation.

+----------+-------------------+---------------------+
|          | CSI               | Documentation       |
+==========+===================+=====================+
| Audience | Maintainers and   | End-Users and       |
|          | Developers        | End-Developers      |
+----------+-------------------+---------------------+
| Topic    | Intent and design | How to use the      |
|          | of code.          | software/API.       |
+----------+-------------------+---------------------+
| Question | **WHY** did we    | **WHAT** does the   |
|          | write this code?  | code do and **HOW** |
|          |                   | do we use it?       |
+----------+-------------------+---------------------+

However, these standards *may* be merged with API documentation standards,
to help produce better autodocs. The important distinction is that
**CSI comments state WHY**, and **doc comments state WHAT and HOW**.

Keeping Up-To-Date
----------------------------------------

A common argument against comments is that *"comments become outdated too
quickly"*, and *"maintaining comments takes extra work"*. However, proper
application of the CSI Commenting Standard avoids both of these problems.

1. When developers are in the habit of using this standard, the first step in
   modifying code is to update the intent-comment.

2. Developers spend considerably less time trying to recreate the intent of
   the previous developer(s), including their past selves. Only a portion of
   this time must be used to update the comments.

Format
========================================

C-Based Languages
---------------------------------------
For readability, CSI comments should use single-line comments only for
single-line statements. If more than one line is required, multi-line
comments should be used (if available in the language.)

It is recommended that each line in a multi-line comment start with an
aligned asterisk, as this improves the readability of the comment.

.. code-block:: c++

    /* This is a multi-line
     * comment with the
     * preceding asterisk.
     */

In any language, we strongly recommend leaving an extra space between the
comment token and the comment text, to aid in readability.

Python
---------------------------------------
CSI comments should not be confused with docstrings (see CSI vs.
Documentation). Line comments should be used for CSI. Placing the
comment above the code in question is recommended. Inline comments
are prone to causing an overrun of PEP 8's line length limits.

.. code-block:: c++

    # This is a CSI comment, describing intent.
    doSomething()

Commenting Style
------------------------------

Again, many of these principles can be applied to documentation comments
as well. The distinction is that CSI comments state **WHY**.

..  NOTE:: I have intentionally oversimplified the code examples to make
    them easy to quickly understand. Most real code is far less obvious
    in its intention at first glance.

Tone
--------------------------------
Comments should be written in a conversational tone, in the same manner that
the code might be explained to a newcomer. It should be free of
language-specific syntax as much as practical. This enables non-programmers
(and programmers from other languages) to understand the code more easily.

**BAD**

.. code-block:: c++

    // set box_width to equal the floor of items and 17
    int items_per_box = floor(items/17)

This merely restates the code in a generic way, and it entirely redundant
when paired with self-commented code. It also depends on the language
term "floor" - if a reader is unfamiliar with this term, they will have
to look it up just to understand the comment - a situation that we should
avoid as much as possible.

**BAD**

.. code-block:: c++

    // Find how many times 17 goes into y, without a remainder.
    int items_per_box = floor(items/17);

Now we know what the code is doing, in a language-agnostic fashion. As a
side benefit, the reader can also surmise what "floor" does, if he or she
were unfamiliar with the term.

However, this comment is still not true CSI, as it is only stating *WHAT*,
and not *WHY*. Furthermore, the self-commented code makes this redundant
to an average C++ developer.

**BEST**

.. code-block:: c++

    /* Divide our items among 17 boxes.
     * We'll deal with the leftovers later. */
    int items_per_box = floor(items/17);

Now we know *WHY* the code is here - we're dividing our items among
the boxes. We also know that this line isn't intended to handle the
extra items (thus why we are using ``floor()``).

If you imagine a lone maintainer looking to change this code to divide
the items among any number of boxes, the comment would make his change
obvious, even with a minimal understanding of the code...

.. code-block:: c++

    /* Divide our items among the specified number of boxes.
     * We'll deal with the leftovers later. */
    int items_per_box = floor(items/boxes);

Avoiding Vagueness
-----------------------------------------
CSI comments should specifically outline the programmer's logic and
reasoning. The more left unsaid and undefined, the less effective
the comment.

**BAD**

.. code-block:: c++

    // This tells us how much we can handle.
    int maximum_range = 27;

This is too vague, and redundant given the variable name. (I'm assuming this
isn't being clarified by immediately prior comments.)

**BETTER**

.. code-block:: c++

    // This tells us the maximum workable integer
    int maximum_range = 27;

This is still vague. If we didn't know exactly what "maximum workable integer"
meant in this context, we'd still be confused. (Again, assuming no context.)

**BEST**

.. code-block:: c++

    // Anything larger than this integer causes the algorithm to return 0.
    int maximum_range = 27;

Ahh, so the *algorithm* has a specific limitation! All becomes clear...

Humor
----------------------------------
Humor should not be suppressed, so long as it does not detract from clarity.
It makes the documentation a lot easier to read, because who likes dry
documentation?

The first rule of humor is applicable here, though: don't force it.
If you try to be funny, you won't be. The only point is to not force
yourself to be totally serious.

That said, don't be crass for crass' sake, as it may drive away others,
detracting from the whole point of this standard.

**ACCEPTABLE**

.. code-block:: c++

    /* We return -1 instead of 0 to avoid a
     * math error in the upcoming division. */
    return -1;

**BETTER**

.. code-block:: c++

    /* We return -1 instead of 0 to keep the
     * math gremlins happy in the upcoming division. */
    return -1;

Context
---------------------------------

Context is very useful in comments. Since we're aiming for a conversational
tone, it is okay for one comment to help explain the comment immediately
following. However, we do not want to become too reliant on context, as it
is yet one more thing the reader must keep track of.

The following would be good in a short function.

**EXAMPLE**

.. code-block:: c++

    /* count tracks the number of times the word “Bah”
     * appears in the given text. */

    // We encountered a “Bah”, increment the count.

    // Return the count.

The following would be better in a very large function.

**EXAMPLE**

.. code-block:: c++

    /* count tracks the number of times the word “Bah”
     * appears in the given text.
     */

    // We encountered a “Bah”, increment the count.

    // Return the count of “Bah” instances.

Length
--------------------------------

Obviously, the above practices will result in longer comments. This isn't a
bad thing, as it seriously increases the code's readability, and speeds up
debugging. Appropriate brevity comes with practice.

Bear this in mind: a single comment should state the **purpose** of a line or
block of code in plain English.

**ACCEPTABLE**

.. code-block:: c++

    /* Search through the list of integers we got from the user
     * and find the number of integers that are divisible by
     * both 5 and 7. Then, return the sum of those numbers. */
    int sum = 0;
    for(int i = 0; i < len; ++i)
    {
        if( !(nums[i]%5) && !(nums[i]%7) )
        {
            sum += nums[i];
        }
    }
    return sum;

This attempts to pack entirely too much information into one comment,
which slows us down. We now have to stop and determine what
``sum += nums[i]`` is doing, based on the big comment. It is also
lengthier than it needs to be.

**BEST**

.. code-block:: c++

    // Store the running sum.
    int sum = 0;

    // Search through the list of integers...
    for(int i = 0; i < len; ++i)
    {
    	// If the number is divisible by both 5 and 7...
    	if( !(nums[i]%5) && !(nums[i]%7) )
    	{
    		// Add it to our sum.
    		sum += nums[i];
    	}
    }

    // Return the final sum.
    return sum;

By spreading out the comments, we can see the intention behind each
piece of code. ``sums += nums[i]`` is obviously adding the number
we found to our running sum.

Spreading out comments also helps to ensure they are kept up-to-date. One of
the reasons programmers neglect to update comments is that they are not
in the immediate vicinity of their other changes.

Frequency and Necessity
-------------------------------------

The core standard is this: **comment everything at first**. Each logical step
should have an explanation. Yes, it doubles the size of your document, but you
(and other people) will be able to better read the code and documentation
later.

In a nutshell, aim to comment more lines of code, not to pack more into
one comment.

There may be a rare occasion where a line of code is so entirely obvious and
ordinary, a CSI comment would be redundant. However, before drawing this
conclusion in a given instance, ask yourself whether someone entirely
unfamiliar with the syntax and program would immediately know what the
*intent* was.

**OBVIOUS**

.. code-block:: python

    # Greet the user.
    print(welcome_message + username + ".")

This line of Python code is so obvious, we could choose to omit the comment
and still be CSI-compliant.

**MOSTLY-OBVIOUS**

.. code-block:: python

    # Display the status or error code from the rendering engine.
    print(get_status(render_engine))

This line is a little harder to parse, unless you know that our theoretical
function ``get_status()`` queries the object's status, and returns it as
a string. Even if we surmised that much, we might not know that error codes
are returned here as well (perhaps we're looking for that line!)

**NON-OBVIOUS**

.. code-block:: python

    # Display the result of the final step of calculation.
    print(str(foo%bar*baz))

We need the comment here to specify that we are actually completing the last
step of a calculation within our print statement.

Trimming Contents
----------------------------------

Commenting WHY instead of WHAT can be difficult, especially when you're familiar
with the code. It may be tempting to write vague comments, or even remove them,
as you work.

However, the purpose of the CSI standard is to inform the programmer who is
*not* presently familiar with the code. Therefore, we recommend the following:

1. Comment every logical statement while working. No exceptions!

2. Have someone unfamiliar with the code review the comments and suggest
   improvements. You may be able to do this yourself, if you leave the comments
   AND code alone for a couple of weeks first.

3. Using the insight from Step 2, rewrite WHAT comments to WHY, and eliminate
   entirely unnecessary comments.

Types of Comments
==================================

Declarations
----------------------------------
CSI-compliant source code should specify the purpose and intent of
variables and functions. As previously mentioned this can be merged with
documentation standards, especially because the resulting autodocs will
be far more usable.

..  NOTE:: If the name of a variable or function fully explains its intent,
    you may omit the comment as your documentation standard permits.

In these examples, we'll demonstrate combining CSI with a Doxygen-compatible
doc comment. To that aim, the comments below contain the names of the items
in question, in anticipation of the resultant autodocs.

**VARIABLE/CONSTANT**

.. code-block:: c++

    /** The SILVER_INTEREST_RATE constant stores the
     * monthly interest rate for Silver savings accounts.
     */
    const int SILVER_INTEREST_RATE = 1.06;

Preceding a variable or constant (especially the latter), we should state
its intent - its purpose for existing. While a good variable or constant name
tells us **what it is**, the comment should state **why it exists**.

**FUNCTION**

.. code-block:: c++

    /** The countBah function determines how many times
     * “BAH” appears in a given string.
     * \param the string to count "bah" in.
     * \return the number of times "bah" appeared.
     */
    int countBah(string inputText);

Immediately preceding a function declaration, its purpose should be stated, as
well as the purpose of the input values, in plain English.

Special Comments
--------------------------------

Using ``TODO``, ``NOTE``, and ``FIXME`` comments is common practice in
many languages, and many tools exist that generate lists from these.
The CSI standard recommends that these types of comments be used, and
follow the same tone as other comments when possible.
::

    // TODO: Expand the whatchamacallit to make whozits.
    // NOTE: Is there a faster way to produce thingamabobs?
    // FIXME: This math always seems to produce the result "2".

Entry Points
------------------------------

Major features should have entry points, which indicate where one should start
reading the code if they want to follow the entire call stack for a particular
function or feature. For example, if a game engine has a long process for
generating an animated character on the screen, the beginning of this process
- such as the function that initializes it - should have the comment...

.. code-block:: c++

    // ENTRY: Generate Animated Character

From this comment, the reader can follow each class, object, and function
through to the end to see the entire process.

In order for this to work, the call stack commenting should not have any
"gaps" (such as a virtual function) that do not have some comment to
indicate where the call stack continues in the code.

Entry points are not always practical, but where they are used, it will be
much easier for a developer who is unfamiliar with the code to find "where
to start".

Commenting Out Code
-------------------------------

It can be very easy to confuse a regular comment and commented out code.
There are two ways to clarify this action.

**EXPLANATION METHOD**

.. code-block:: c++

    // It would seem that float is better for this task.
    //int foo = 187;
    float foo = 187;

    // Just testing if we really need this function call at all.
    //refreshEverything();

Here, we add a preceding comment to explain why the code was commented out.
The benefit to this is that it helps you and other programmers recognize
and follow changes in program logic.

This method is ideal in languages where double-commenting (below) is
not possible.

**DOUBLE COMMENT METHOD**

.. code-block:: c++

    ////refreshEverything();

We can “double-comment” out the code. This is probably ideal in situations
where the commenting-out is temporary, and you don't want to have to write
an explanation.

**COMBINATION METHOD**

.. code-block:: c++

    // Just testing if we really need this function call at all.
    ////refreshEverything();

By combining the two methods, you can see what code was commented out,
while stating the reasons behind it.

This method is ideal in languages where double-commenting is possible.

**In any case, you should ultimately aim to remove commented-out code as
soon as possible.**

Top of Document
------------------------------

On the top of the document, the programmer should ideally list the project name
and version, module/class name and description, date last updated,
and authors (optionally). This may be adjusted to comply with documentation
needs and individual standards.

.. code-block:: c++

    /* Dohickey Class [Some Epic Project]
     * Version: 1.0
     *
     * This performs jazz on input data to produce whatzit.
     *
     * Last Updated: November 25, 2014
     * Author: Bob D. Example
     */


Immediately following in a separate multi-line comment, include copyright
and licensing terms. Because many licenses are extremely long, placing the
license comment separate from the main top-of-document comment allows for
the license to be collapsed in most code-folding-capable IDEs.

.. code-block:: c++

    /* LICENSE
     * Copyright (C) My Really Cool Software Company.
     * Licensing yada yada goes here.
     */
