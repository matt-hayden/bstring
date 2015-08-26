PH's original comments at http://bytes.com/topic/c/answers/635736-csv-parsing-paul-hsieh-michael-b-allen

The pointer to my program should be up to date and functioning. The
makefile is meant for WATCOM C/C++. However, creating your own
makefile for *nux should be totally trivial. You just need to compile
and link the modules bstrlib.o and csvparse.o from their corresponding
C files. The official Bstrlib library also contains this parser in
the examples archive which includes a makefile for Linux.

The first version of my parser was actually based on the logic of
Michael's parser, but significantly augmented for correctness.
However, even then it was far from perfect. Last year I did a total
rewrite of the program to match the correct CSV grammar that I
derived. It appears to be bug free, it is fast, and it is easy to
understand. I don't have any idea if Michael's parser is correct
these days (it used to fail at reading quoted CRs), but it certainly
was not at the time he original wrote it. I think his is also limited
in the number of columns that can be correctly read.

For mine, only the makefile has "Windowcisms" (actually DOSisms).
The .c and .h sources are portable.

http://www.pobox.com/~qed/bcsv.zip


Original ReadMe
===============

This is a just a simple demo of CSV file reading and parsing.  It demonstrates
a couple of features of Bstrlib.  1) The use of bStreams means that the file
interface is flexible, yet has very low overhead on bulk transfers.  2) The
use of reference bstrings means that the baseline memory usage is minimized,
and that some operations such as just searching can happen without additional
unnecessary copy overhead.  3) All loops have built-in maximum length 
delimiters, as opposed to scanning for '\0's at each character; this 
generally leads to higher performance on modern microprocessors.

A derived specification for the CSV file format (which I was unable to find
other satisfactory sources for) has been included.  Also included are the 
necessary sources, the Win32 binary csvparse.exe, and the test files used to 
test the programs correctness.

