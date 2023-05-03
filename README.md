Download Link: https://assignmentchef.com/product/solved-cs143-project-1
<br>
<h1>1           Overview of the Programming Project</h1>

This assignment asks you to write a short Cool program. The purpose is to acquaint you with the Cool language and to give you experience with some of the tools used in the course.

A machine with only a single stack for storage is a <em>stack machine</em>. Consider the following very primitive language for programming a stack machine:

<table width="354">

 <tbody>

  <tr>

   <td width="81"><em>Command</em></td>

   <td width="274"><em>Meaning</em></td>

  </tr>

  <tr>

   <td width="81"><em>int</em></td>

   <td width="274">push the integer <em>int </em>on the stack</td>

  </tr>

  <tr>

   <td width="81">+</td>

   <td width="274">push a ‘+’ on the stack</td>

  </tr>

  <tr>

   <td width="81">s</td>

   <td width="274">push an ‘s’ on the stack</td>

  </tr>

  <tr>

   <td width="81">e</td>

   <td width="274">evaluate the top of the stack (see below)</td>

  </tr>

  <tr>

   <td width="81">d</td>

   <td width="274">display contents of the stack</td>

  </tr>

  <tr>

   <td width="81">x</td>

   <td width="274">stop</td>

  </tr>

 </tbody>

</table>

The ‘d’ command simply prints out the contents of the stack, one element per line, beginning with the top of the stack. The behavior of the ‘e’ command depends on the contents of the stack when ‘e’ is issued:

<ul>

 <li>If ‘+’ is on the top of the stack, then the ‘+’ is popped off the stack, the following two integers are popped and added, and the result is pushed back on the stack.</li>

 <li>If ‘s’ is on top of the stack, then the ‘s’ is popped and the following two items are swapped on the stack.</li>

 <li>If an integer is on top of the stack or the stack is empty, the stack is left unchanged.</li>

</ul>

The following examples show the effect of the ‘e’ command in various situations; the top of the stack is on the left:

<table width="197">

 <tbody>

  <tr>

   <td width="130"><em>stack before</em></td>

   <td width="66"><em>stack after</em></td>

  </tr>

  <tr>

   <td width="130">+ 1 2 5 <em>s…</em></td>

   <td width="66">3 5 <em>s…</em></td>

  </tr>

  <tr>

   <td width="130"><em>s </em>1 + + 99<em>…</em></td>

   <td width="66">+ 1 + 99</td>

  </tr>

  <tr>

   <td width="130">1 + 3<em>…</em></td>

   <td width="66">1 + 3<em>…</em></td>

  </tr>

 </tbody>

</table>

You are to implement an interpreter for this language in Cool. Input to the program is a series of commands, one command per line. Your interpreter should prompt for commands with &gt;. Your program need not do any error checking: you may assume that all commands are valid and that the appropriate number and type of arguments are on the stack for evaluation. You may also assume that the input integers are unsigned. Your interpreter should exit gracefully; do not call abort() after receiving an x.

You are free to implement this program in any style you choose. However, in preparation for building a Cool compiler, we recommend that you try to develop an object-oriented solution. One approach is to define a class StackCommand with a number of generic operations, and then to define subclasses of StackCommand, one for each kind of command in the language. These subclasses define operations specific to each command, such as how to evaluate that command, display that command, etc. If you wish, you may use the classes defined in atoi.cl in the [cool root]/examples directory to perform string to integer conversion. If you find any other code in [cool root]/examples that you think would be useful, you are free to use it as well.

We wrote a solution in approximately 200 lines of Cool source code. This information is provided to you as a rough measure of the amount of work involved in the assignment—your solution may be either substantially shorter or longer.

<h1>2           Sample Session</h1>

The following is a sample compile and run of our solution (substitute the root directory of your workspace for [cool root]).

% [cool root]/bin/coolc stack.cl atoi.cl

% [cool root]/bin/spim -file stack.s

SPIM Version 5.6 of January 18, 1995

Copyright 1990-1994 by James R. Larus (<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="214d405354526142520f564852420f444554">[email protected]</a>).

All Rights Reserved.

See the file README a full copyright notice.

Loaded: [cool root]/lib/trap.handler

&gt;1

&gt;


&gt;2

&gt;s &gt;d s 2




1

&gt;e

&gt;e

&gt;d

3

&gt;x

COOL program successfully executed

<h1>3           Files and Directories</h1>

To get started with the programming assignments, download the starter code from the OpenClassroom website and extract it to a convenient directory on your local machine. Make sure you download the tarball that matches your particular machine architecture. You may also download the pieces of this assignment individually from the Resources page, but we strongly recommend that you download and use the complete tarball as is.

Once you have a working copy of the programming assignment source tree, change into the directory for the current assignment,

[cool root]/assignments/PA1/

Some of the files in the directory will be read-only (using symbolic links). You should not edit these files. In fact, if you make and modify private copies of these files, you may find it impossible to complete the assignment. See the instructions in the README file.

<h1>4           Testing</h1>

You can test your stack machine by comparing its output to that of our reference implementation using make test. Your stack machine should not produce any output aside from whitespace (which our testing harness will ignore), ‘&gt;’ prompts, and the output of a ‘d’ command.