CFLAGS  = -std=c99
CFLAGS += -g
CFLAGS += -Wall
CFLAGS += -Wextra
CFLAGS += -pedantic
CFLAGS += -Werror

VFLAGS  = --quiet
VFLAGS += --tool=memcheck
VFLAGS += --leak-check=full
VFLAGS += --error-exitcode=1

LDFLAGS = -lm

test: tests.out
	@./tests.out

memcheck: tests.out
	@valgrind $(VFLAGS) ./tests.out
	@echo "Memory check passed"

clean:
	rm -rf *.o *.out *.out.dSYM

tests.out: test/test_run_length_encoding.c src/run_length_encoding.c src/run_length_encoding.h
	@echo Compiling $@
	@$(CC) $(CFLAGS) src/run_length_encoding.c test/vendor/unity.c test/test_run_length_encoding.c -o tests.out $(LDFLAGS)
