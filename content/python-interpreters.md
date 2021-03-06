Title: A Short Primer on Assembers, Compilers and Interpreters
Date: 2018-10-10 10:00
Category: Concepts
Tags: interpreters, assembly, programming, C, high level languages, math
Slug: python-interpreters
Authors: Erik Oshaughnessy
Summary: summary pending
cover: images/featured/pb-guest.png
status: draft

In the dark early days of computers, hardware was expensive and
programmers were cheap. In fact, programmers were so cheap they
weren't even called "programmers" and were in fact usually
mathematicans, often graduate students. Early computers were used to
solve complex mathematical problems quickly, so student mathematicans
were a natural fit for the job of "programming".

First a little background on what a program is. If you've got a
handle on that, skip ahead.

Computers can't do anything by themselves, they require programs to
drive their behavior. Programs can be thought of as very detailed
recipes that take an input and produce an output. The steps in the
recipe are composed of instructions that operate on data. While that
sounds complicated, you probably know how this statement works:

  1 + 2 = 3

The plus sign is the "instruction" while the numbers 1 and 2 are the
data. Mathematically, the equal sign indicates that both sides of an
equation are "equivalent", however most computer languages use some
variant of equals to mean "assignment". If a computer were executing
that statment, it would store the results of the addition, the "3",
somewhere in memory.

Computers know how to do math with numbers and move data around the
machine's memory heirarchy. I won't say too much about memory except
to say it generally comes in two different flavors: fast & small, and
slow & big. CPU registers are very fast, very small and act as
scratch pads while main memory is typically very big and not nearly as
fast as register memory. CPUs shuffle the data they are working with
from main memory to registers and back again while a program executes.

So computers were very expensive and people were cheap. The
programmers spent endless hours translating hand written math into
computer instructions that the computer could execute. The very first
computers had terrible user interfaces, some only consisting of toggle
switches on the front panel where each computer instruction was
entered a word at a time by flipping the switches between 1 and 0. It
was time consuming and error prone. 

Eventually, a mathematician decided his time wasn't cheap and wrote a
program that would take as it's input a recipe expressed in terms
people could read and output a computer readable version. This was the
first "assembler" and it was very controversial. The people that owned
the expensive machines didn't want to "waste" compute time on a task
that people were already doing; cheaply, slowly, and with errors. Over
time, people came to appreciate the speed and accuracy of the
assembler versus the a hand-written program and the amount of "real
work" done with the computer increased.

While assembler programs were a big step up from toggling bit patterns
into the front panel of a machine, they were still pretty specialized.
The addition example from above might have looked something like this:

 01  MOVE R0, 1
 02  MOVE R1, 2
 03  ADD R0, R1, R2
 04  MOVE 64, R0
 05  STORE R2, R0

Each line is a computer instruction, beginning with a shorthand name
of the instruction followed by the data the instruction works on. This
little program will first "move" the value 1 into a register called R0,
then 2 into R1. Line 03 adds the contents of R0 and R1 and stores the
result value into register R2. Finally, lines 04 and 05 identify where
in main memory the result should be stored. This is one of the most
time consuming and error-prone parts of writing computer programs;
managing where in memory data is stored.

While better than writing computer instructions by hand, mathematicans
yearned to write programs like they were accustomed to writing
mathematical formulae. This drove the development of higher level
compiled languages, some of which are historical footnotes and others
are still in use today. Algo is one such footnote, while problems
continue to be solved with languages like FORTRAN and C.

These new "high level" langagues allowed programmers to write their
programs in simpler terms. In the C language, our addition assembly
program would be written as:

    int x;
    x = 1 + 2;

The first statement describes a piece of memory that the program
will use. In this case, the memory should be the size of an integer
and it's name is "x". The second statement is the addition, although
written "backwards". A C programmer would read that as "X is assigned
the result of one plus two". 

A new program, called a "compiler", would turn the program written in
a high level language into an assembly language version and then finally
run it thru the assembler to produce a machine-readable version of the
program. This composition of programs is often called a "tool chain",
in that one program's output is sent directly to another program's
input.

The huge advantage of compiled language over assembly language
programs was porting from one computer model or brand to another. In
the early days of computing there was an explosion of different types
of computing hardware from companies like IBM, Digital Equipment
Corporation, Texas Instruments, UNIVAC, Hewlet Packard and others.
None of these computers shared much in common besides needing to be
plugged in. Memory and CPU architectures differed wildly and it often
took man-years to translate programs from one computer to another.
With high level languages, it was only necessary to port the compiler
tool chain to the new platfrom. Once the compiler was available, the
program could be re-compiled for the new program with little or no
modification. It was truely revolutionary.

Life was very good now for programmers. It was much easier to express
the problems they wanted to solve using high level languages and the
cost of computer hardware was falling dramatically due to advances in
semiconductors and the invention of integrated chips. Computers were
getting faster and more capable in addition to become much less
expensive. At some point, in the late 80s possibly, there was an
inversion and programmers became more expensive than the hardware they
used.

Over time, a new programming model arose where a special program
called an "interpreter" would read a program and turn it into computer
instructions to be executed immediately. The interpreter takes the
program as input and interprets it into an intermediate form, much
like a compiler. Unlike a compiler, the interpreter then executes the
intermediate form of the program. This happens every time an interpreted
program runs, whereas a compiled program is only compiled one time and
the computer only has to execute the machine instructions "as written".

As a sidenote, when people say that "interpreted programs are slow",
that is the main source of the perceived lack of performance. Modern
computers are so amazingly capable that most people aren't usually
able to tell the difference between compiled and interpreted programs.

One example of a very popular interpreted language is Python. A
complete python expression of our addition problem would be:

   x = 1 + 2

While it looks and acts much like the C version, it lacks the variable
initialization statement. There are other differences which are beyond
the scope of this article, but you can see that we are able to write a
computer program that is very close to how a mathematician would write
it by hand with pencil and paper.

---

Keep Calm and Code in Python!

-- [Erik](pages/guests.html#erikoshaughnessy)
