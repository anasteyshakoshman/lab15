## Laboratory work XV

Данная лабораторная работа посвещена изучению инструментов статического и динамического анализа кода
```ShellSession
$ open http://cppcheck.sourceforge.net
```

## Tasks

- [x] 1. Ознакомиться со ссылками учебного материала
- [x] 2. Используя **cpplint** провести анализ проекта на **C++**
- [x] 3. Используя **Cppcheck** провести анализ проекта на **C++**
- [x] 4. Используя **OCLint** провести анализ проекта на **C++**
- [x] 5. Используя **Valgrind** провести анализ проекта на **C++**
- [x] 6. Составить отчет и отправить ссылку личным сообщением в **Slack**

```ShellSession
$ alias edit=vim                  #присваиваем edit=vim
$ cd anasteyshakoshman/workspace/projects                       #переходим в директорию с проектами
$ mkdir lab15 && cd lab15                       #создаём папку lab15 и переходим в неё
$ touch main.cpp && edit main.cpp    #создаём файл main.cpp и редактируем его ( пишем код)
```

# Cpplint - это скрипт на Питоне для автоматической проверки стиля кодирования 
```ShellSession
$ sudo apt-get install python.pip # устанавливаем python.pip
$ sudo pip install cpplint # устанавливаем cpplint с помощью команды pip
$ cpplint main.cpp #анализируем проект main.cpp с помощью cpplint
main.cpp:0: No copyright message found. You should have a line: "Copyright [year] <Copyright Owner>" [legal/copyright] [5] # нет сообщения о создателе
main.cpp:4: { should almost always be at the end of the previous line [whitespace/braces] [4] # скобка { должна стоять на предыдущей строке (в объявлении int main() )
main.cpp:5: Tab found; better to use spaces [whitespace/tab] [1] # найдена табуляция, желательно использовать пробел
main.cpp:6: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:7: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:7: { should almost always be at the end of the previous line [whitespace/braces] [4]
main.cpp:7: Missing space before { [whitespace/braces] [5] # потерян пробел после {
main.cpp:8: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:9: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:10: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:11: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:11: { should almost always be at the end of the previous line [whitespace/braces] [4]
main.cpp:11: Missing space before { [whitespace/braces] [5]
main.cpp:12: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:13: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:13: { should almost always be at the end of the previous line [whitespace/braces] [4]
main.cpp:13: Missing space before { [whitespace/braces] [5]
main.cpp:14: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:14: Consider using rand_r(...) instead of rand(...) for improved thread safety.
[runtime/threadsafe_fn] [2] # желательно использовать вместо функции rand() функцию rand_r()
main.cpp:15: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:16: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:17: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:18: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:19: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:19: { should almost always be at the end of the previous line [whitespace/braces] [4]
main.cpp:19: Missing space before { [whitespace/braces] [5]
main.cpp:20: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:21: Tab found; better to use spaces [whitespace/tab] [1]
main.cpp:22: Tab found; better to use spaces [whitespace/tab] [1]
Done processing main.cpp
Total errors found: 29
$ edit main.cpp #исправляем ошибки
$ cpplint main.cpp #проверка выполнена, ошибки не найдены
Done processing main.cpp
```
# Cppcheck - - это инструмент статического анализа исходного кода на языке Си и Си++. Анализатор Cppcheck выполняет множество различных видов проверок. Перечислим некоторые из них:
- Неправильное использование функций из Standard Template Library;
- Утечки памяти (Memory leaks);
- Утечки ресурсов (Resource leaks);
- Выход за границы массивов (Bounds checking for array overruns);
- Использование неинициализированных переменных;
- Использование устаревших функций;
- Проверка операций ввода/вывода (Check input/output operations);
- Разыменование нулевого указателя.
```ShellSession
$ edit main.cpp      # редактирую проект, создаю ошибку ображения к невыделенной памяти, для ее выявления с помощью cppcheck
$ sudo apt-get install cppcheck #устанавливаем cppcheck
$ cppcheck —version #смотрим версию
Cppcheck 1.80
$ cppcheck main.cpp #анализируем main.cpp с помощью cppcheck
Checking main.cpp ...
[main.cpp:13]: (error) Array 'mus[10]' accessed at index 12, which is out of bounds # обращение к невыделанный памяти
$ edit main.cpp #исправляем ошибки
$ $ cppcheck main.cpp # проверка выполнена, ошибки не найдены
Checking main.cpp ...
```
# Oclint - инструмент,  который проверяет программы на С, С++ и Objective-C на наличие следующих багов и ошибок:
- пустые конструкции if/else/try/catch/finally;
- неиспользуемые локальные переменные и параметры;
- использование кода с высокой цикломатической и NPath сложностью;
- избыточное использование конструкций if и ненужных скобок;
- использование длинных методов и длинных списков параметров;
- плохие практики написания кода — переназначение параметров, неправильное использование логики.
```ShellSession
$ edit main.cpp    # редактирую проект
$ cd ~           #
$ cd oclint-0.13        # переход в папку распакованного архива
$ sudo cp bin/oclint* /usr/local/bin/
$ sudo cp -rp lib/* /usr/local/lib/ 
$ cd anasteyshakoshman/workspace/projects/lab15
$ oclint main.cpp -- -c


OCLint Report

Summary: TotalFiles=1 FilesWithViolations=1 P1=0 P2=1 P3=3 

/home/stasya/anasteyshakoshman/workspace/projects/lab15/main.cpp:2:5: short variable name [naming|P3] Length of variable name `i` is 1, which is shorter than the threshold of 3             # короткое имя переменной (длина имени переменной `i` равна 1, что меньше порога 3)
/home/stasya/anasteyshakoshman/workspace/projects/lab15/main.cpp:2:5: short variable name [naming|P3] Length of variable name `j` is 1, which is shorter than the threshold of 3
/home/stasya/anasteyshakoshman/workspace/projects/lab15/main.cpp:6:13: dead code [basic|P2] 
/home/stasya/anasteyshakoshman/workspace/projects/lab15/main.cpp:3:5: collapsible if statements [basic|P3]              # сбрасываемые операторы if 
$ edit main.cpp      # исправление ошибок
$ oclint main.cpp -- -c           # ошибки не найдены


OCLint Report

Summary: TotalFiles=1 FilesWithViolations=0 P1=0 P2=0 P3=0 


[OCLint (http://oclint.org) v0.13]
```




# Valgrind - контролирует использование памяти, например, вызовы malloc и free (или new и delete в C++). Если используется неинициализированная память, записывается за пределами концов массива, или не освобождается указатель, Valgrind может это обнаружить
```ShellSession
$ edit main.cpp    # редактирую проект, не особождаю указатель для выявления ошибки с помощью valgrind
$ sudo apt-get install valgrind
$ valgrind --version # узнаем версию
valgrind-3.13.0
$ g++ -c main.cpp     # компилиция проекта с помощью g++, создание обьектного файла main.o
$ ls main.omain.o
$ g++ main.o -o main
$ ./main
$ valgrind --tool=memcheck ./main      # общее использование кучи: 2 выделения, 1 frees 
==18295== Memcheck, a memory error detector
==18295== Copyright (C) 2002-2017, and GNU GPL'd, by Julian Seward et al.
==18295== Using Valgrind-3.13.0 and LibVEX; rerun with -h for copyright info
==18295== Command: ./main
==18295== 
==18295== 
==18295== HEAP SUMMARY:
==18295==     in use at exit: 10 bytes in 1 blocks
==18295==   total heap usage: 2 allocs, 1 frees, 72,714 bytes allocated
==18295== 
==18295== LEAK SUMMARY:
==18295==    definitely lost: 10 bytes in 1 blocks
==18295==    indirectly lost: 0 bytes in 0 blocks
==18295==      possibly lost: 0 bytes in 0 blocks
==18295==    still reachable: 0 bytes in 0 blocks
==18295==         suppressed: 0 bytes in 0 blocks
==18295== Rerun with --leak-check=full to see details of leaked memory
==18295== 
==18295== For counts of detected and suppressed errors, rerun with: -v
==18295== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)
$ rm -rf main.o      # удаление обьектного файла
$ rm -rf main        # удаление исполняемого файла
$ edit main.cpp      # исправление ошибки в main.cpp (освобожение памяти)
$ g++ -c main.cpp     # компилиция проекта с помощью g++, создание обьектного файла main.o
$ ls main.omain.o
$ g++ main.o -o main
$ ./main
$ valgrind --tool=memcheck ./main
$ valgrind --tool=memcheck ./main       # все блоки кучи были освобождены - утечек не было
==18325== Memcheck, a memory error detector
==18325== Copyright (C) 2002-2017, and GNU GPL'd, by Julian Seward et al.
==18325== Using Valgrind-3.13.0 and LibVEX; rerun with -h for copyright info
==18325== Command: ./main
==18325== 
==18325== 
==18325== HEAP SUMMARY:
==18325==     in use at exit: 0 bytes in 0 blocks
==18325==   total heap usage: 2 allocs, 2 frees, 72,714 bytes allocated
==18325== 
==18325== All heap blocks were freed -- no leaks are possible
==18325== 
==18325== For counts of detected and suppressed errors, rerun with: -v
==18325== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)
$ rm -rf main.o      # удаление обьектного файла
$ rm -rf main        # удаление исполняемого файла
```


## Links

- [Google C++ Style Guide](https://github.com/cpplint/cpplint)
- [Cppcheck Manual](http://cppcheck.sourceforge.net/manual.pdf)
- [Valgrind Quick Start Guide](http://valgrind.org/docs/manual/index.html)
-[OCLint Tutorial](http://docs.oclint.org/en/stable/intro/tutorial.html)

```
Copyright (c) 2017 Братья Вершинины
```
