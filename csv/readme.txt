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

