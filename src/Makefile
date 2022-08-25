CC = gcc
STDFLAGS = -Wall -Wextra -Werror -std=c11




all: s21_math.a 

test: 
	$(CC) $(STDFLAGS) --coverage -c -g s21_math.c 
	ar rcs s21_math.a *.o
	ranlib s21_math.a
	$(CC) test.c s21_math.a -L./ --coverage -o test.out -lcheck
	./test.out

linter:
		cp ../materials/linters/CPPLINT.cfg CPPLINT.cfg
		python3 ../materials/linters/cpplint.py --extension=c *.c *.h

s21_math.a:
	$(CC) $(STDFLAGS) -c -g s21_math.c 
	ar rcs s21_math.a *.o
	ranlib s21_math.a

gcov_report: test
	lcov -t "report" -o report.info -c -d .
	genhtml -o report report.info

clean: 
	rm -rf *.gcda *.gcno *.gcov *.a *.out *.o ./report *.info

rebuild: clean all