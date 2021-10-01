---
# Front matter
title: "Отчет по лабораторной работе 2"
subtitle: "Дисциплина: Информационная безопасность"
author: "Фогилева Ксения Михайловна, НПИбд-02-18"

# Generic otions
lang: ru-RU
toc-title: "Содержание"

# Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

# Pdf output format
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
### Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Misc options
indent: true
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

Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных 
системах с открытым кодом на базе ОС Linux.

# Выполнение лабораторной работы

1. В установленной при выполнении предыдущей лабораторной работы операционной системе создала учётную запись пользователя guest (используя учётную запись 
администратора): useradd guest. (рис. [-@fig:001])

2. Задала пароль для пользователя guest (используя учётную запись администратора): passwd guest. (рис. [-@fig:001])

![Создание пользователя guest и задание ему пароля](image/1.jpg){ #fig:001 width=70% }

3. Вошла в систему от имени пользователя guest. (рис. [-@fig:002])

![Вход в систему под guest](image/2.jpg){ #fig:002 width=70% }

4. Определила директорию, в которой я нахожусь, командой *pwd*. (рис. [-@fig:003]) Это моя домашняя директория. Она в целом совпадает с приглашением командной 
строки: в командной строке есть guest (пользователь) и ~ (указывает на то, что мы находимя в домашней директории).

5. Уточнила имя моего пользователя командой whoami. (рис. [-@fig:003])

6. Уточнила имя моего пользователя, его группу, а также группы, куда он входит, командой *id*. (рис. [-@fig:003]) Выведенные значения uid, gid и др. 
запомнила. Выполнила команду *groups*. (рис. [-@fig:003]) Полученные значения совпадают с тем, что выдала *id*.

![Получение информации о guest](image/3.jpg){ #fig:003 width=70% }

7. Полученная информация об имени пользователя частично совпадает (само имя пользователя) с данными, выводимыми в приглашении командной строки, но является 
более подробной.

8. Просмотрела файл /etc/passwd: cat /etc/passwd. (рис. [-@fig:004]) 

![Файл /etc/passwd](image/4.jpg){ #fig:004 width=70% }

Нашла в нём свою учётную запись. (рис. [-@fig:005]) 

![Учётная запись guest в файле /etc/passwd](image/5.jpg){ #fig:005 width=70% }

Определила uid пользователя: 1001. Определила gid пользователя: 1001. Эти значения совпадают с полученными в предыдущих пунктах.

9. Определила существующие в системе директории: ls -l /home/. (рис. [-@fig:006]) Мне удалось получить список поддиректорий директории /home. Владельцы 
директорий имеют на них полные права. Группы и другие пользователи не имеют никаких прав на эти директории.

10. Проверила, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home: lsattr /home. (рис. [-@fig:006]) 

![Поддиректории директории /home. Их атрибуты](image/6.jpg){ #fig:006 width=70% }

Мне удалось увидеть расширенные атрибуты директории guest (моего пользователя). Расширенные атрибуты директорий других пользователей мне были не доступны.

11. Создала в домашней директории поддиректорию dir1: mkdir dir1. Определила командами *ls -l* и *lsattr*, какие права доступа и расширенные атрибуты были 
выставлены на директорию dir1. (рис. [-@fig:007])

![Поддиректория dir1](image/7.jpg){ #fig:007 width=70% }

12. Сняла с директории dir1 все атрибуты: chmod 000 dir1, и проверила с её помощью правильность выполнения команды *ls -l*. (рис. [-@fig:008])

13. Попыталась создать в директории dir1 файл file1: echo "test" > /home/guest/dir1/file1. (рис. [-@fig:008]) Я получила отказ в выполнении операции по 
созданию файла, т. к. мы сняли с директории все атрибуты (даже для владельцев), соответственно, я как владелец не могу вносить изменения в директории. 
Сообщение об ошибке никак не отразилось на создании файла, потому что он не был создан. Проверила командой *ls -l /home/guest/dir1* (рис. [-@fig:008]), 
действительно ли файл file1 не находится внутри директории dir1, но проверить не получилось, т. к. я не имею доступа к файлам директрии.

![Работа с правами директории dir1](image/8.jpg){ #fig:008 width=70% }

14. Заполнила таблицу «Установленные права и разрешённые действия» (рис. [-@fig:009]-[-@fig:012]), выполняя действия от имени владельца директории (файлов), определив 
опытным путём, какие операции разрешены, а какие нет. Если операция разрешена, занесла в таблицу знак «+», если не разрешена -- знак «-».
![Проверка прав доступа](image/9.jpg){#fig:009 width=90% }

![Установленные права и разрешённые действия 1](image/10.jpg){ #fig:010 width=90% }

![Установленные права и разрешённые действия 2](image/11.jpg){ #fig:011 width=90% }

![Установленные права и разрешённые действия 3](image/12.jpg){ #fig:012 width=90% }

15. На основании заполненной таблицы определила те или иные минимально необходимые права для выполнения операций внутри директории dir1, заполнила таблицу
«Минимальные права для совершения операций». (рис. [-@fig:013])

![Минимальные права для совершения операций](image/13.jpg){ #fig:013 width=70% }

# Выводы

Получила практические навыки работы в консоли с атрибутами файлов, закрепила теоретические основы дискреционного разграничения доступа в современных 
системах с открытым кодом на базе ОС Linux.

# Список литературы{.unnumbered}

1. Кулябов Д. С., Королькова А. В., Геворкян М. Н. Информационная безопасность компьютерных сетей. Лабораторная работа № 2. Дискреционное разграничение прав 
в Linux. Основные атрибуты