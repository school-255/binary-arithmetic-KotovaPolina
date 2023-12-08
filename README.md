# Самостоятельная работа по двоичной арифметике

Для выполнения задания необходимо открыть этот файл в codespace и писать все заметки, решения и ответы прямо здесь. В каждом задании отведено место под заметки и ответ. Пример задания приведен ниже:

## Пример задания

Вычислите `x`:
```
x = 12 + 95*2
```

_место для заметок_

```
95*2 = 190
12+190 = 202
```

**Ответ:**
```
x = 202
```

**После выполнения работы не забудьте сохранить, зафиксировать (commit) и синхронизировать (push) изменения!**

---

## Задание 0

Записать свою дату рождения в формате `dd-mm-yyyy` и определить особые числа для своего варианта следующим образом:
```
N = ddmmyyyy
```

Например у меня (Ярмолинский А.М.) др 8 сен 2001, значит `N = 08092001`.

**Ответ:**
```C++
N = 15052006
```

## Задание 1

Перевести число `N` в формат `uint32_t` (беззнаковое 32-битное целое число) и представить в шестнадцатеричном виде.

_место для заметок_

```
00000000 11100101 10101100 11100110 - N в двоичной системе
E5ACE6 - N d 16-ричной системе
```

**Ответ:**
```C++
N = 0x00E5ACE6
```

## Задание 2

Вычислить:

```C++
NL = N << 3;
NR = N >> 2;
```

Считать `NL` и `NR` числами типа `uint32_t`.

> _Напоминание_: `<<` - логический сдвиг влево, `>>` - вправо

00000000 11100101 10101100 11100110
со сдвигом влево - 00000111 00101101 01100111 00110000
со сдвигом вправо - 00000000 00111001 01101011 00111001
``` 
место для заметок
```

**Ответ:**
```C++
NL = 0x072D6730
NR = 0x00396B39
```

## Задание 3

Система управления умным домом состоит из контроллера и восьми реле. Для управления реле в контроллере есть переменная типа `uint8_t`, каждый бит которой представляет состояние соответствующего реле:
```
S = abcdefgh
    ||||||||
    |||||||` реле 0
    ||||||`- реле 1
    |||||`-- реле 2
    ||||`--- реле 3
    |||`---- реле 4
    ||`----- реле 5
    |`------ реле 6
    `------- реле 7
```
Нулевое значение бита соответствует разомкнутому реле (реле выключено), единица - реле замкнуто (включено).

Определите маски для следующих операций над переменной состояния реле. Все реле, не упомянутые в строчке должны остаться неизменными:

```C++
S = S & Moff;    // выключить реле 1, 4 и 5, не трогая остальные
S = S | Mon;     // включить реле 2, 3, 6 и 7, не трогая остальные
S = S ^ Mtoggle; // переключить реле 0, 4 и 6, не трогая остальные
```

В ответе записать представление маски и в двоичном, и в шестнадцатеричном виде.

> `'&'` - побитовое И, `'|'` - побитовое ИЛИ, `'^'` - побитовое ИСКЛЮЧАЮЩЕЕ ИЛИ

Moff = 11001101
Mon = 11001100
Mtoggle = 01010001

```
место для заметок
```

**Ответ:**
```C++
Moff    = 0b11001101; // 0xCD
Mon     = 0b11001100; // 0xCC
Mtoggle = 0b01010001; // 0x51
```

## Задание 4

Используя ключ `k = 0x18` зашифровать дату своего рождения, записанную в формате: `31-12-2023`. Каждый символ считать закодированным по таблице ASCII.

В ответе написать строку из 10 символов, соответствующую зашифрованной дате.

15-05-2006
49 53 45 48 53 45 50 48 48 54
31 35 2D 30 35 2D 32 30 30 36

```
место для заметок
110001 110101 101101 110000               110010               110110
010010 010010 010010 010010               010010               010010
100011 100111 111111 100010 100111 111111 100000 100010 100010 100100

```

**Ответ:**
```
xxxxxxxxxx
```

## Задание 5

Представить число `N` в нормализованной форме в двоичной системе счисления.

**Задание на сообразительность**

Перевести число N в формат float (число с плавающей точкой единичной точности, 32 бита, стандарт IEEE 754) и представить в виде шестнадцатиричного числа (вида 0x89ABCDEF)

так число `-17.25` будет представлено в виде:
```
-17.25 =
-10001.01 =
-1.000101 * 2^4 =>

1|1000001 1|0001010 00000000 00000000
| \       / \                       /
|  \     /   ` Мантисса ( Z-1 = .000101)
|   \   /
|    `-------- Экспонента ( p = 4 + 127 = 131 )
`- Знаковый бит

11000001 10001010 00000000 00000000
   C1       8A       00       00

-17.25 -> (float)C18A0000
```

_место для заметок_

```
место для заметок
```

**Ответ:**
```
Nnorm = xxxx * 2^xxx
Nfloat = (float)XXXXXXXX
```

