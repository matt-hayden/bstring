This program has been completely rewritten from scratch over the previous version.  The old state-machine implementation was hard to verify.  Rewriting it in a way that more directly corresponds to the CSV BNF basically reduced bugs down to nothing.  Here are the advantages:

	1) The code is now a good example that demonstrates the performance, and functionality of Bstrlib.

	2) The code is easier to maintain.

	3) The code just uses ISO C headers and functions, and should be generally portable to all platforms without issue.

	4) The file can be modified to be a linkable module (remove the definition for MAIN_TEST_FOR_CSV) as well as a stand-alone test application.

	5) The parser is completely incremental.  This means that row and column indexes are not range limited by any upper bound whatsoever.  It also means there is no requirement that memory for an entire field be allocated.  There is only a requirement that a single entry can be held (temporarily) in memory and is less that INT_MAX characters in length.

	6) A CSV writer is also included.  This is useful for verification purposes besides being just useful in of itself.

