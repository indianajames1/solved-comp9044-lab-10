Download Link: https://assignmentchef.com/product/solved-comp9044-lab-10
<br>



Before the lab you should re-read the relevant lecture slides and their accompanying examples.

Create a new directory for this lab called lab10, change to this directory, and fetch the provided code for this week by running these commands:

$ <strong>mkdir lab10</strong>

$ <strong>cd lab10</strong>

$ <strong>2041 fetch lab10</strong>

Or, if you’re not working on CSE, you can download the provided code as a <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/lab/10/provided.zip">zip</a> <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/lab/10/provided.zip">file</a> or a <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/lab/10/provided.tar">tar</a> <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/lab/10/provided.tar">file</a><a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/lab/10/provided.tar">.</a>

Write a Shell program, which_webserver.sh which given the URL of 1 or more webservers as command-line arguments prints what software the webserver is running, as indicated by the server field returned in a request to the web server.

Match the output and behaviour in the example below exactly:

<table width="961">

 <tbody>

  <tr>

   <td width="961">$ <strong>./which_webserver.sh https://www.unsw.edu.au</strong> https://www.unsw.edu.au Apache/2.4.34 (Red Hat) OpenSSL/1.0.1e-fips PHP/5.6.25$ <strong>./which_webserver.sh https://www.google.com</strong> https://www.google.com gws$ <strong>./which_webserver.sh https://www.netflix.com</strong> https://www.netflix.com nq_website_nonmember-prod-release b2b0bc7b-bffd-4024-b8b8-d060e658f2ac $ <strong>./which_webserver.sh https://www.abc.net.au https://www.sydney.edu.au http://www.bom.gov.au</strong> https://www.abc.net.au Apache/2.4.43 (Unix) https://www.sydney.edu.au Apache http://www.bom.gov.au Apache</td>

  </tr>

 </tbody>

</table>

Hint

<strong>man curl</strong>

<h1>Assumptions</h1>

Your answer must be Shell. You can not use other languages such as Perl, Python or C.

No error handling is necessary.

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest which_webserver</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab10_which_webserver which_webserver.sh</strong>

before Tuesday 11 August 21 00 to obtain the marks for this lab exercise.

Write a Shell program, make_tree.sh which is given the pathname of a directory tree.

It should search this directory tree for directories containing a makefile.

For each of these directories it shouldprint the directory pathname and then run <strong>make</strong> in the directory.

Match the output and behaviour in the examples below exactly:




<table width="961">

 <tbody>

  <tr>

   <td width="961">$ <strong>unzip /web/cs2041/20T2/activities/make_tree/examples.zip</strong>$ <strong>find simple</strong> simple simple/b.c simple/Makefile$ <strong>./make_tree.sh simple/</strong> Running make in simple clang -Wall   -c -o b.o b.c clang -Wall -o p b.o $ <strong>find medium</strong> medium medium/a medium/a/x.c medium/a/h.c medium/a/Makefile medium/a/l.c medium/b medium/b/b.c medium/b/j.c medium/b/k.c medium/c medium/c/p.c medium/c/Makefile $ <strong>./make_tree.sh medium</strong> Running make in medium/a clang -Wall   -c -o h.o h.c clang -Wall   -c -o l.o l.c clang -Wall   -c -o x.o x.c clang -Wall -o c h.o l.o x.o Running make in medium/c clang -Wall   -c -o p.o p.c clang -Wall -o d p.o$ <strong>find hard</strong> hard hard/a hard/a/p.c hard/a/r.c hard/a/Makefile hard/a/q.c hard/b hard/b/b hard/b/b/b hard/b/b/b/b hard/b/b/b/b/b hard/b/b/b/b/r.c hard/b/b/b/b/Makefile hard/c hard/c/d hard/c/d/o.c hard/c/d/Makefile hard/c/e hard/c/e/a.c hard/c/e/b.c hard/c/e/f hard/c/e/f/a.c hard/c/e/f/Makefile $ <strong>./make_tree.sh hard</strong> Running make in hard/a clang -Wall   -c -o p.o p.c clang -Wall   -c -o r.o r.c clang -Wall   -c -o q.o q.c clang -Wall -o b p.o r.o q.o Running make in hard/b/b/b/b clang -Wall   -c -o r.o r.c clang -Wall -o r r.o Running make in hard/c/d clang -Wall   -c -o o.o o.c clang -Wall -o m o.o Running make in hard/c/e/f clang -Wall   -c -o a.o a.c clang -Wall -o i a.o</td>

  </tr>

 </tbody>

</table>

The test directories are also available as a <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/make_tree/examples.zip">zip</a> <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/make_tree/examples.zip">file</a>

<table>

 <tbody>

  <tr>

   <td width="51"></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

If make_tree.sh is give extra command line arguments they should be passed to each make command, for example:

<table width="961">

 <tbody>

  <tr>

   <td width="961">$ <strong>cat simple/Makefile </strong>CC=clang CFLAGS=-Wallp: b.o$ <strong>(CC) $(CFLAGS) -o <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="684c28">[email protected]</a> $^</strong>.PHONY: cleanclean:     rm -f b.oclobber: clean     rm -f p$ <strong>./make_tree.sh medium clobber</strong> Running make in medium/a rm -f h.o l.o x.o rm -f cRunning make in medium/c rm -f p.o rm -f d$ <strong>./make_tree.sh hard clean</strong> Running make in hard/a rm -f p.o r.o q.oRunning make in hard/b/b/b/b rm -f r.oRunning make in hard/c/d rm -f o.oRunning make in hard/c/e/f rm -f a.o</td>

  </tr>

 </tbody>

</table>

Hint

Use <strong>find</strong> to find all Makefiles in the directory tree.

<h1>Assumptions</h1>

You can assume makefiles are named <strong>Makefile</strong>

Your answer must be Shell. You can not use other languages such as Perl, Python or C.

No error handling is necessary.

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest make_tree</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab10_make_tree make_tree.sh</strong>

before Tuesday 11 August 21 00 to obtain the marks for this lab exercise.

Write a Shell program, compress_if_needed.sh which takes the pathnames of 0 or more files as command line arguments.

It should compresses each file with xz if and only if, this results in a smaller file.

Match the output and behaviour in the example below exactly:

<table width="961">

 <tbody>

  <tr>

   <td width="961">$ <strong>unzip /web/cs2041/20T2/activities/compress_if_needed/examples.zip</strong>$ <strong>ls -l file*</strong>-rw-r–r– 1 andrewt andrewt 4096 Aug  3 17:10 file1.bin-rw-r–r– 1 andrewt andrewt 4096 Aug  3 17:10 file2.bin$ <strong>./compress_if_needed.sh file1.bin file2.bin</strong> file1.bin 4096 bytes, compresses to 4156 bytes, left uncompressed file2.bin 4096 bytes, compresses to 2160 bytes, compressed$ <strong>ls -l file*</strong>-rw-r–r– 1 andrewt andrewt 4096 Aug  3 17:10 file1.bin-rw-r–r– 1 andrewt andrewt 2160 Aug  3 17:10 file2.bin.xz</td>

  </tr>

 </tbody>

</table>

The two test files are also available as a <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/compress_if_needed/examples.zip">zip</a> <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/activities/compress_if_needed/examples.zip">file</a>

<h1>Assumptions</h1>

Your answer must be Shell. You can not use other languages such as Perl, Python or C.

You should use xz’s default compression. xz has many options to change compression behaviour. Do not use these.

When you think your program is working, you can use autotest to run some simple automated tests:

$ <strong>2041 autotest compress_if_needed</strong>

When you are finished working on this exercise, you must submit your work by running give:

$ <strong>give cs2041 lab10_compress_if_needed compress_if_needed.sh</strong>

before Tuesday 11 August 21 00 to obtain the marks for this lab exercise.

When you are finished each exercises make sure you submit your work by running give.

You can run give multiple times. Only your last submission will be marked.

Don’t submit any exercises you haven’t attempted.

If you are working at home, you may find it more convenient to upload your work via <a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">g</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">ive</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">‘</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">s</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">web</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">interface</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/give.php">.</a>

Remember you have until Tuesday 11 August 21 00 to submit your work.

You cannot obtain marks by e-mailing your code to tutors or lecturers.

You check the files you have submitted <a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/student/">here</a><a href="https://cgi.cse.unsw.edu.au/~cs2041/20T2/student/">.</a>

Automarking will be run by the lecturer several days after the submission deadline, using test cases different to those autotest runs for you. (Hint: do your own testing as well as running autotest.)

<a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">After</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">automarking</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">is</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">run</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">by</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">the</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">lecturer</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">you</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">can</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">view</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">y</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">our</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">results</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">here</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">.</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php"> The</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">resulting</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">mark</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">will</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">also</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">be</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">available</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">via</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">g</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">ive</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">‘</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">s</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">web interface</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">.</a>

<h1>Lab Marks</h1>

When all components of a lab are automarked you should be able to view the the marks <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">via</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">g</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">ive</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">‘</a><a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">s</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">web</a> <a href="https://cgi.cse.unsw.edu.au/~give/Student/sturec.php">interface</a> or by running this command on a CSE machine:

$ <strong>2041 classrun -sturec</strong>


