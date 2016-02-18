CFLAGS=-DMAIN_TEST_FOR_CSV -I../bstring -Wall -g

csvparse: csvparse.c bstrlib.o
	$(CC) $(CFLAGS) $^ -o $@

csvparse.i: csvparse.c
	$(CC) $(CFLAGS) -C -E $^ > $@

bstrlib.o: ../bstring/bstrlib.c
	$(CC) $(CFLAGS) -fpic -c $<

libbstrlib.so: bstrlib.o
	$(CC) $(CFLAGS) -shared -Wl -soname $@ -o $@ $<

