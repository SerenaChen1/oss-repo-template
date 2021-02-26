all: dynamic_block static_block
clean:
	rm *.o dynamic_block static_block libstatic.a libshared.so
dynamic_block: program.o libshared.so
	cc program.o libshared.so -o dynamic_block -Wl,-rpath='$$ORIGIN'
static_block: program.o libstatic.a
	cc -o static_block program.o libstatic.a
libstatic.a: block.o
	ar -qc libstatic.a block.o
libshared.so: block.o
	cc -shared -o libshared.so block.o
block.o: source/block.c
	cc -fPIC -c source/block.c -o block.o
program.o: program.c
	cc -c program.c -o program.o
