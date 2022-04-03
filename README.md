# Asm-task

## Задание
В этом репозитории есть пример двух программ на ассемблере:
* Программа `hello.asm` — это программа выводящая строку "Hello, world". В ней подробно прокомментирована каждая строчка.
* Программа `add.asm` — это программа, которая выполняет сложение двух длинных чисел.

Вам необходимо разобраться в этих примерах и написать на их основе программы, выполняющие вычитание и умножение беззнаковых длинных чисел.

## Обзор
Обратите внимание, что приведенные примеры заточены на конкретную архитектуру процессора (x86\_64), конкретный ассемблер (`nasm`) и операционную систему (`Linux`).

> Разрешается писать программы под другие архитектуры, ассемблеры и операционные системы, при этом вам придется самим переписать код на нужную архитектуру и разобраться как сделать ввод-вывод. Если вы будете делать программу под архитектуру отличную от x86\_64 или i386, предварительно согласуйте это с преподавателями. При этом вам нужно будет предоставить корректные тесты под эту архитектуру, если с существующими тестами возникнут проблемы.

Для того, чтобы запустить примеры и написать свое решение вам понадобится любой 64-битный дистрибутив Linux. Чтобы проверить битность вашего дистрибутива, можно исполнить команду:
```console
$ uname -m
```
Если команда выводит x86\_64, то система 64-битная, если i386 или i686 — 32-битная.

## Инструкция по работе
Все действия в инструкциях совершаются из папки с данным файлом

* Модифицируйте файлы `sub.asm` и `mul.asm`, чтобы они выполняли вычитание и умножение.
* Если хотите собрать код без какого-либо файла, то закомментируйте в `CMakeLists.txt` строчки, связанные с ними

### Инструкция по сборке
```console
$ sudo apt install binutils g++ cmake nasm
$ ./build.sh
```

### Запуск примеров
```console
$ ./hello
Hello, world!
$ ./add
10000000000000000000000000000000000000
100000000000000000000000000000000000000000000000000000000000000
100000000000000000000000010000000000000000000000000000000000000
``` 

## Примечания
1. `mul` и `sub` должны работать с беззнаковыми числами максимальной длины 128 qword (input). При этом результат `mul` (output) в данном случае может быть длины 256 qword и это должно корректно обрабатываться.
2. Уменьшаемое в `sub` всегда не меньше вычитаемого.
3. Программу можно реализовать по-разному, но если в вашем решении можно будет соптимизировать потребление памяти на стеке (или в `.data`), то вы будете вынуждены делать правки.
4. Вы не можете считывать числа, тратя на это больше памяти, чем требуется. 
