# Содержание {#содержание .TOC-Heading}

[1 Цель работы [1](#цель-работы)](#цель-работы)

[2 Задание [1](#задание)](#задание)

[3 Выполнение лабораторной работы
[1](#выполнение-лабораторной-работы)](#выполнение-лабораторной-работы)

[4 Выполнение заданий для самостоятельной работы
[7](#выполнение-заданий-для-самостоятельной-работы)](#выполнение-заданий-для-самостоятельной-работы)

[5 Выводы [11](#выводы)](#выводы)

[6 Список литературы [11](#список-литературы)](#список-литературы)

# 1 Цель работы

Приобретение практических навыков работы в Midnight Commander. Освоение
инструкций языка ассемблера mov и int.

# 2 Задание

1.  Основы работы с mc
2.  Подключение внешнего файла

# 3 Выполнение лабораторной работы

**Основы работы с mc**

Открываю Midnight Commander, введя в терминал mc:

![](media/image1.png){width="3.297104111986002in"
height="2.655282152230971in"}

Рис 1

Перехожу в каталог \~/work/arch-pc/, используя файловый менеджер mc:

![](media/image2.png){width="3.8763265529308835in"
height="0.9706277340332459in"}

Рис 2

С помощью F7 создаю каталог lab05:

![](media/image3.png){width="2.9851213910761154in"
height="1.5507731846019248in"}

Рис 3

![Рис 4](media/image4.png "fig:"){width="4.083333333333333in"
height="0.7698086176727909in"}

Рис 4

Пользуясь строкой ввода и командой touch создаю файл lab5-1.asm:

![](media/image5.png){width="2.9480205599300087in"
height="0.3128127734033246in"}

Рис 5

![](media/image6.png){width="4.083333333333333in"
height="0.7615212160979877in"}

Рис 6

С помощью функциональной клавиши F4 открою файл lab5-1.asm для
редактирования в nano:

![](media/image7.png){width="2.9835695538057743in"
height="1.061330927384077in"}

Рис 7

Ввожу в файл код программы для запроса строки у пользователя:

![](media/image8.png){width="4.083333333333333in"
height="2.921201881014873in"}

Рис 8

С помощью функциональной клавиши F3 открываю файл для просмотра, чтобы
проверить, что файл содержит текст программы:

![](media/image9.png){width="4.083333333333333in"
height="3.044870953630796in"}

Рис 9

Транслирую текст программы файла в объектный файл командой nasm -f elf
lab5-1.asm:

![](media/image10.png){width="3.547071303587052in"
height="0.368672353455818in"}

Рис 10

Выполняю компоновку объектного файла с помощью команды ld -m elf_i386 -o
lab5-1 lab5-1.o:

![](media/image11.png){width="3.266842738407699in"
height="0.368672353455818in"}

Рис 11

Я запускаю получившийся исполняемый файл:

![](media/image11.png){width="3.266842738407699in"
height="0.368672353455818in"}

Рис 12

Программа выводит строку "Введите строку:" и ждет ввода с клавиатуры, я
ввожу мои ФИО:

![](media/image12.png){width="1.6958923884514436in"
height="0.368672353455818in"}

Рис 13

**Подключение внешнего файла in_out.asm**

Скачиваю файл in_out.asm со страницы курса в ТУИС:

![Рис 14](media/image13.png "fig:"){width="4.083333333333333in"
height="0.7205872703412074in"}

Рис 14

С помощью функциональной клавиши F5 копирую файл in_out.asm из каталога
Downloads в каталог lab05. Потом копирую файл lab5-1.asm в тот же
каталог, но с другим именем (lab5-2.asm) :

![Рис 15](media/image14.png "fig:"){width="4.083333333333333in"
height="1.5803499562554681in"}

Рис 15

![Рис 16](media/image15.png "fig:"){width="4.083333333333333in"
height="1.701971784776903in"}

Рис 16

Изменяю содержимое файла lab5-2.asm в редакторе nano, чтобы в программе
использовались подпрограммы из внешнего файла in_out.asm (и также
использую подпрограммы sprintLF, sread и quit):

![](media/image16.png){width="3.2417443132108485in"
height="2.359990157480315in"}

Рис 17

Я транслирую текст программы файла в объектный файл командой nasm -f elf
lab5-2.asm и выполняю я компоновку объектного файла с помощью команды ld
-m elf_i386 -o lab5-2 lab5-2.o. Я запускаю получившийся исполняемый
файл. Программа выводит строку "Введите строку" и ждет ввода с
клавиатуры:

![](media/image17.png){width="3.2931496062992127in"
height="0.37878827646544183in"}

Рис 18

Я ввожу мои ФИО:

![](media/image17.png){width="3.6531911636045495in"
height="0.7364720034995625in"}

Рис 19

В файле lab5-2.asm заменяю подпрограмму sprintLF на sprint, транслирую и
запускаю получившийся исполняемый файл:

![](media/image18.png){width="3.5162182852143484in"
height="2.5013976377952756in"}

Рис 20

![](media/image17.png){width="3.417159886264217in"
height="0.4924245406824147in"}

Рис 21

Разница в том, что после строки "Введите строку" нет дополнительной
строки:

![](media/image19.png){width="1.8770133420822397in"
height="0.37840004374453196in"}

Рис 22

# 4 Выполнение заданий для самостоятельной работы

Создаю копию файла lab5-1.asm с именем lab5-1-0.asm с помощью клавиши
F5:

![Рис 23](media/image20.png "fig:"){width="4.083333333333333in"
height="1.5192300962379703in"}

Рис 23

С помощью клавиши F4, открываю созданный файл для редактирования в nano.
Изменяю программу так, чтобы кроме вывода приглашения и запроса ввода,
она выводила вводимую пользователем строку:

![](media/image8.png){width="4.083333333333333in"
height="2.921201881014873in"}

Рис 24

Код программы:

    SECTION .data
    msg: DB 'Введите строку', 10

    msgLen: EQU $-msg

    SECTION .bss
    buf1: RESB 80

    SECTION .text
    GLOBAL _start
     _start:

    mov eax,4
    mov ebx,1
    mov ecx,msg
    mov edx,msgLen
    int 80h

    mov eax,3
    mov ebx,0
    mov ecx,buf1
    mov edx,80
    int 80h

    mov eax,4
    mov ebx,1
    mov ecx,buf1
    mov edx,buf1
    int 80h

    mov eax,1
    mov ebx,0
    int 80h

Я транслирую и запускаю получившийся исполняемый файл:

![](media/image10.png){width="4.083333333333333in"
height="0.42440944881889764in"}

Рис 25

![](media/image11.png){width="3.6523654855643044in"
height="0.41217957130358707in"}

Рис 26

![](media/image21.png){width="4.083333333333333in"
height="0.3437707786526684in"}

Рис 27

Программа запрашивает ввод, ввожу мои ФИО, далее программа выводит
введенные данные:

![](media/image12.png){width="3.071706036745407in"
height="0.667762467191601in"}

Рис 28

Создаю копию файла lab5-2.asm с именем lab5-2-1.asm с помощью
функциональной клавиши F5 и открываю созданный файл для редактирования.
Изменяю программу так, чтобы кроме вывода приглашения и запроса ввода,
она выводила вводимую пользователем строку:

![](media/image16.png){width="3.680409011373578in"
height="2.6793372703412075in"}

Рис 29

Код программы:

    %include 'in_out.asm'
    SECTION .data
    msg: DB 'Введите строку', 10

    msgLen: EQU $-msg

    SECTION .bss
    buf1: RESB 80

    SECTION .text
    GLOBAL _start
     _start:

    mov eax,msg
    call sprint

    mov ecx,buf1
    mov edx,80

    call sread
    mov eax,4
    mov ebx,1
    mov ecx,buf1
    int 80h
    call quit

Я транслирую и запускаю получившийся исполняемый файл:

![](media/image22.png){width="3.185845363079615in"
height="0.33561570428696413in"}

Рис 30

![](media/image11.png){width="2.973924978127734in"
height="0.33561570428696413in"}

Рис 31

![](media/image21.png){width="4.083333333333333in"
height="0.3437707786526684in"}

Рис 32

![](media/image23.png){width="2.084899387576553in"
height="0.6725481189851269in"}

Рис 33

# 5 Выводы

При выполнении данной лабораторной работы я приобрела практические
навыки работы в Midnight Commander, а также освоила инструкции языка
ассемблера mov и int.

# 6 Список литературы

[Архитектура
ЭВМ](https://esystem.rudn.ru/pluginfile.php/2089085/mod_resource/content/0/%D0%9B%D0%B0%D0%B1%D0%BE%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%BD%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%20%E2%84%965.%20%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D1%8B%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B%20%D1%81%20Midnight%20Commander%20%28%29.%20%D0%A1%D1%82%D1%80%D1%83%D0%BA%D1%82%D1%83%D1%80%D0%B0%20%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D1%8B%20%D0%BD%D0%B0%20%D1%8F%D0%B7%D1%8B%D0%BA%D0%B5%20%D0%B0%D1%81%D1%81%D0%B5%D0%BC%D0%B1%D0%BB%D0%B5%D1%80%D0%B0%20NASM.%20%D0%A1%D0%B8%D1%81%D1%82%D0%B5%D0%BC%D0%BD%D1%8B%D0%B5%20%D0%B2%D1%8B%D0%B7%D0%BE%D0%B2%D1%8B%20%D0%B2%20%D0%9E%D0%A1%20GNU%20Linux.pdf)
