# Содержание {#содержание .TOC-Heading}

[1 Цель работы [1](#цель-работы)](#цель-работы)

[2 Задание [1](#задание)](#задание)

[3 Выполнение лабораторной работы
[1](#выполнение-лабораторной-работы)](#выполнение-лабораторной-работы)

[4 Выводы [14](#выводы)](#выводы)

[5 Список литературы [14](#список-литературы)](#список-литературы)

# 1 Цель работы

Цель этой работы - изучение команд условного и безусловного переходов.
Приобретение навыков написания программ с использованием переходов.
Знакомство с назначением и структурой файла листинга.

# 2 Задание

1.  Реализация переходов в NASM
2.  Изучение структуры файлы листинга

# 3 Выполнение лабораторной работы

**1. Реализация переходов в NASM**

Создаю каталог для программам лабораторной работы № 7, перехожу в него и
создаю файл lab7-1.asm:

![](media/image1.png){width="3.35in" height="1.2916666666666667in"}

Рис 1

Отркрываю файл lab7-1.asm и в него вставляю код программы, которая
показывает как работает jmp:

![](media/image2.png){width="4.083333333333333in"
height="6.893088363954505in"}

Рис 2

Создаю испольняемый файл и запускаю его. Программа выводит "сообщение №
2" и "сообщение № 3":

![](media/image3.png){width="3.8583333333333334in" height="1.575in"}

Рис 3

Изменяю текст программы:

![](media/image4.png){width="3.9027777777777777in"
height="5.636268591426072in"}

Рис 4

Создаю испольняемый файл и запускаю его. Программа выводит "сообщение №
2" и "сообщение № 1":

![](media/image5.png){width="4.741666666666666in"
height="1.8916666666666666in"}

Рис 5

Изменяю текст программы, чтобы она выводила "сообщение № 3", "сообщение
№ 2" и "сообщение № 1":

![](media/image6.png){width="3.564668635170604in"
height="7.176396544181977in"}

Рис 6

Создаю испольняемый файл и запускаю его:

![](media/image7.png){width="3.658333333333333in"
height="1.2666666666666666in"}

Рис 7

Создаю файл lab7-2.asm:

![](media/image8.png){width="3.8in" height="1.1in"}

Рис 8

В него вставляю код программы, которая определяет и выводит на экран
наибольшую из 3 целочисленных переменных:

![](media/image9.png){width="3.361111111111111in"
height="3.135365266841645in"}

Рис 9

![](media/image10.png){width="3.361111111111111in"
height="0.9556102362204725in"}

Рис 10

Создаю испольняемый файл и запускаю его:

![](media/image11.png){width="4.666666666666667in" height="1.625in"}

Рис 11

Проверяю работу для разных значений B:

![](media/image12.png){width="5.166666666666667in" height="2.75in"}

Рис 12

**2. Изучение структуры файлы листинга**

Создаю файл листинга для программы из файла lab7-2.asm:

![](media/image13.png){width="4.4in" height="1.1in"}

Рис 13

Открываю файл листинга lab7-2.lst с помощью mcedit:

![](media/image14.png){width="4.933333333333334in"
height="3.5166666666666666in"}

Рис 14

Это пример машинного кода сохранен в lab7-2.lst:

    20 000000F2 B9[0A000000]    mov ecx,B
    21 000000F7 BA0A000000      mov edx, 10
    22 000000FC E842FFFFFF      call sread      

В lab7-2.asm, эти строки пренадзначены для ввода значения B. 20- номер
строки, 000000F2- это смещение машинного кода от начала текущего
сегмента (адрес), B9\[0A000000\]- машинный код и mov ecx,B- исходнный
текст программы.

Когда я удаляю строку для сравнения A и C, выполняю трансляцию с
получением файла листинга, строка удаляется из файла .lst, и ничего не
добавляется:

![Рис 15](media/image15.png "fig:"){width="4.083333333333333in"
height="1.744912510936133in"}

Рис 15

![](media/image16.png){width="4.083333333333333in"
height="0.6511614173228346in"}

Рис 16

#Выполнение задания для самостоятельной работы

Создаю файл task1.asm:

![](media/image17.png){width="4.86819772528434in"
height="0.682577646544182in"}

Рис 17

В него вставляю код программы, которая определяет наименьшей из 3
целочисленных переменных a,b и c:

    %include 'in_out.asm'

    SECTION .data
    msg1 db "Наимеьшее число: ",0h
    A dd '41'
    B dd '35'
    C dd '62'

    SECTION .bss
    min resb 10

    SECTION .text
    GLOBAL _start

    _start:

    mov eax,B
    call atoi
    mov [B],eax

    mov ecx,[A]
    mov [min],ecx

    cmp ecx,[C]
    jl check_B
    mov ecx,[C]
    mov [min],ecx

    check_B:
    mov eax,min
    call atoi
    mov [min],eax

    mov ecx,[min]
    cmp ecx,[B]
    jl fin
    mov ecx,[B]
    mov [min],ecx

    fin:
    mov eax,msg1
    call sprint
    mov eax,[min]
    call iprintLF
    call quit

![](media/image18.png){width="5.341666666666667in" height="5.55in"}

Рис 18

Создаю исполняемый файл и проверяю его работу для значения переменых из
варианта 10:

![](media/image19.png){width="5.852576552930883in"
height="2.067081146106737in"}

Рис 19

# 4 Выводы

При выполнении лабораторной работы, я изучила команд условного и
безусловного переходов в NASM.

# 5 Список литературы

[Архитектура
ЭВМ](https://esystem.rudn.ru/pluginfile.php/2089087/mod_resource/content/0/%D0%9B%D0%B0%D0%B1%D0%BE%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%BD%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%20%E2%84%967.%20%D0%9A%D0%BE%D0%BC%D0%B0%D0%BD%D0%B4%D1%8B%20%D0%B1%D0%B5%D0%B7%D1%83%D1%81%D0%BB%D0%BE%D0%B2%D0%BD%D0%BE%D0%B3%D0%BE%20%D0%B8%20%D1%83%D1%81%D0%BB%D0%BE%D0%B2%D0%BD%D0%BE%D0%B3%D0%BE%20%D0%BF%D0%B5%D1%80%D0%B5%D1%85%D0%BE%D0%B4%D0%BE%D0%B2%20%D0%B2%20Nasm.%20%D0%9F%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5%20%D0%B2%D0%B5%D1%82%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B9..pdf)