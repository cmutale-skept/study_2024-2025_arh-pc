# Содержание {#содержание .TOC-Heading}

[1 Цель работы [1](#цель-работы)](#цель-работы)

[2 Задание [1](#задание)](#задание)

[3 Выполнение лабораторной работы
[1](#выполнение-лабораторной-работы)](#выполнение-лабораторной-работы)

[4 Выполнение самостоятельной работы
[9](#выполнение-самостоятельной-работы)](#выполнение-самостоятельной-работы)

[5 Выводы [11](#выводы)](#выводы)

[6 Список литературы [11](#список-литературы)](#список-литературы)

# 1 Цель работы

Цель лабораторной работы -- приобретение навыков написания программ с
использованием циклов и обработкой аргументов командной строки.

# 2 Задание

1.  Реализация циклов в NASM
2.  Обработка аргументов командной строки

# 3 Выполнение лабораторной работы

**1. Реализация циклов в NASM**

Создаю каталог для программам лабораторной работы № 8, перехожу в него и
создаю файл lab8-1.asm:

![](media/image1.png){width="4.058333333333334in" height="1.175in"}

Рис 1

В файле lab8-1.asm вставляю код программы, которая показывает, как
инструкция loop использует регистр ecx в качестве счетчика и на каждом
шаге уменьшает его значение на единицу:

![](media/image2.png){width="4.866666666666666in"
height="3.720138888888889in"}

Рис 2

Создаю исполняемый файл:

![](media/image3.png){width="4.533333333333333in"
height="1.4333333333333333in"}

Рис 3

При запуске, программа выводит значение регистра ecx:

![](media/image4.png){width="4.258333333333334in" height="2.275in"}

Рис 4

Изменяю текст программы, чтобы она показала, что использование регистра
ecx в теле цилка loop может привести к некорректной работе программы:

![](media/image5.png){width="4.675in" height="4.441666666666666in"}

Рис 5

Создаю исполняемый файл:

![](media/image3.png){width="3.7333333333333334in" height="1.225in"}

Рис 6

При запуске, программа выводит бесконечное значение, которое не
соответсвует значению N введенному с клавиатуры:

![](media/image6.png){width="3.966666666666667in" height="1.05in"}

Рис 7

![](media/image7.png){width="2.0694444444444446in"
height="4.098898731408574in"}

Рис 8

Для использования регистра ecx в цикле и сохранения корректности работы
программы можно использовать стек. Изменяю текст программы добавив
команды push и pop:

![Рис 9](media/image8.png "fig:"){width="4.083333333333333in"
height="1.7786876640419949in"}

Рис 9

Создаю исполняемый файл:

![](media/image9.png){width="3.9833333333333334in" height="1.125in"}

Рис 10

При запуске, программа выводит значение, которое соответсвует значению N
введенному с клавиатуры:

![](media/image10.png){width="4.058333333333334in" height="0.9in"}

Рис 11

![](media/image11.png){width="3.533333333333333in"
height="1.5583333333333333in"}

Рис 12

**2. Обработка аргументов командной строки**

Создаю файл lab8-2.asm:

![](media/image12.png){width="2.7583333333333333in"
height="1.0166666666666666in"}

Рис 13

Ввожу в него текст программы, которая выводит на экран аргументы
командной строки:

![](media/image13.png){width="4.6in" height="3.433333333333333in"}

Рис 14

Создаю исполняемый файл и запускаю его:

![](media/image14.png){width="3.6166666666666667in" height="2.3in"}

Рис 15

Создаю файл lab8-3.asm:

![](media/image15.png){width="2.8833333333333333in"
height="0.6333333333333333in"}

Рис 16

Ввожу в него текст программы, которая выводит на экран сумму аргументов:

![Рис 17](media/image16.png "fig:"){width="4.083333333333333in"
height="3.9449146981627297in"}

Рис 17

Создаю исполняемый файл и запускаю его:

![](media/image17.png){width="3.066666666666667in"
height="0.7416666666666667in"}

Рис 18

![](media/image18.png){width="2.9833333333333334in" height="0.675in"}

Рис 19

Изменяю текст программы, чтобы она выводила произведение аргументов:

![](media/image19.png){width="4.583333333333333in"
height="6.383333333333334in"}

Рис 20

Создаю исполняемый файл и запускаю его:

![](media/image20.png){width="3.933333333333333in"
height="1.4166666666666667in"}

Рис 21

# 4 Выполнение самостоятельной работы

Создаю файл task8.asm:

![](media/image21.png){width="2.716666666666667in" height="0.7in"}

Рис 22

В него пишу программу, которая находит сумму значений функции f(x) =
5(2 + x)\$ для некоторых значении x (вариант 10):

![Рис 23](media/image22.png "fig:"){width="4.083333333333333in"
height="5.059935476815398in"}

Рис 23

Код программы:

    %include 'in_out.asm'

    SECTION .data
    msg: DB 'Функция: f(x)=5(2+x)', 0
    Sum: DB 'Результат: ',0
    SECTION .text
    global _start
    _start:
    mov eax, msg
    call sprintLF

    pop ecx         
    pop edx        
    sub ecx,1 
    mov esi, 0
               
    next:
    cmp ecx,0h 
    jz _end    
               
    pop eax   
    call atoi  
    add eax,2
    mov ebx,5
    mul ebx
    add esi,eax
    loop next 

    _end:

    mov eax,Sum
    call sprint

    mov eax, esi 
    call iprintLF
     
    call quit

Создаю исполняемый файл и запускаю его. Программа выводит сумму
f(1)+f(2)+f(1):

![](media/image23.png){width="3.9833333333333334in"
height="1.2583333333333333in"}![Изображение выглядит как текст, Шрифт,
снимок экрана](media/image24.png){width="3.9814260717410326in"
height="0.8583333333333333in"}

Рис 24

# 5 Выводы

При выполнение данной работы я освоила использование циклов и обработку
аргументов командной строки.

# 6 Список литературы

[Архитектура
ЭВМ](https://esystem.rudn.ru/pluginfile.php/2089095/mod_resource/content/0/%D0%9B%D0%B0%D0%B1%D0%BE%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%BD%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%20%E2%84%968.%20%D0%9F%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5%20%D1%86%D0%B8%D0%BA%D0%BB%D0%B0.%20%D0%9E%D0%B1%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%BA%D0%B0%20%D0%B0%D1%80%D0%B3%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D0%BE%D0%B2%20%D0%BA%D0%BE%D0%BC%D0%B0%D0%BD%D0%B4%D0%BD%D0%BE%D0%B9%20%D1%81%D1%82%D1%80%D0%BE%D0%BA%D0%B8..pdf)
