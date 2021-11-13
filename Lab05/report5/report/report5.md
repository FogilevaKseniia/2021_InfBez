---
# Front matter
lang: ru-RU
title: "Отчёт по лабораторной работе №5"
subtitle: "дисциплина: Информационная безопасность"
author: "Фогилева ксения Михайловна"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: lualatex
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Изучение механизмов изменения идентификаторов, применения
SetUID- и Sticky-битов. Получение практических навыков работы в консоли с дополнительными атрибутами. Рассмотрение работы механизма
смены идентификатора процессов пользователей, а также влияние бита
Sticky на запись и удаление файлов.

# Выполнение лабораторной работы

1. Загрузила gcc и  отключите систему запретов до очередной перезагрузки системы. (рис.1)

![Рис. 1.](image/1.jpg){ #fig:001 width=70% }

2. Создала программу simpleid.c (рис.2).

![Рис. 2.](image/2.jpg){ #fig:002 width=70% }

3. Скомпилировала и выполнила программу simpleid, затем запустила id. Результаты совпали. (рис.3).

![Рис. 3.](image/3.jpg){ #fig:003 width=70% }

4. Создала программу simpleid2.ca (рис.4).

![Рис. 4.](image/4.jpg){ #fig:004 width=70% }

5. . Скомпилировала и запустила simpleid2.c (рис.5).

![Рис. 5.](image/5.jpg){ #fig:005 width=70% }

6. Повысила права, выполнила команды, выполнила проверку правильности выполнения команд, запустила simpleid2 и id (рис.6).

![Рис. 6.](image/6.jpg){ #fig:006 width=70% }

7. Проделайте тоже самое относительно SetGID-бита (рис.7).

![Рис. 7.](image/7.jpg){ #fig:007 width=70% }

8. Создала программу readfile.c (рис.8).

![Рис. 8.](image/8.jpg){ #fig:008 width=70% }

9. Смените владельца у файла readfile.c (рис.9).

![Рис. 9.](image/9.jpg){ #fig:009 width=70% }

10. Проверила, что пользователь guest не может прочитать файл readfile.c. (рис.10)

![Рис. 10.](image/10.jpg){ #fig:010 width=70% }

11. Сменила у программы readfile владельца и установила SetU’D-бит. Проверила, может ли программа readfile прочитать файл readfile.c (рис.11).

![Рис. 11.](image/11.jpg){ #fig:011 width=70% }

12. Проверила, может ли программа readfile прочитать файл /etc/shadow (рис.12)

![Рис. 12.](image/12.jpg){ #fig:012 width=70% }

13. Выяснила, установлен ли атрибут Sticky на директории /tmp. От имени пользователя guest создала файл file01.txt в директории /tmp
со словом test. Просмотрела атрибуты у только что созданного файла и разрешила чтение и запись (рис.13)

![Рис. 13.](image/13.jpg){ #fig:013 width=70% }

14. Выполнила действия от имени пользователя guest2. Не получилось только удалить файл. (рис.14)

![Рис. 14.](image/14.jpg){ #fig:014 width=70% }

15. Выполнила команду, снимающую атрибут t (Sticky-бит) с
директории /tmp от имени суперпользователя. (рис.15).

![Рис. 15.](image/15.jpg){ #fig:015 width=70% }

16. Повторите предыдущие шаги от имени пользователя guest2, теперь можно удалить файл. (рис.16)

![Рис. 16.](image/16.jpg){ #fig:016 width=70% }

17. Повысила свои права до суперпользователя и вернула атрибут t на директорию /tmp. (рис. 17)

![Рис. 17.](image/17.jpg){ #fig:017 width=70% }

# Выводы

Изучила механизмы изменения идентификаторов, применения
SetUID- и Sticky-битов. Получила практическе навыки работы в консоли с дополнительными атрибутами. Рассмотрела работу механизма
смены идентификатора процессы пользователей, а также влияние бита
Sticky на запись и удаление файлов.
