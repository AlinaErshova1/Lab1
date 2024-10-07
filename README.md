# Lab1
## Отчет по лабораторной работе № 1

#### № группы: `ПМ-2401`

#### Выполнила: `Ершова Алина Дмитриевна`

#### Вариант: `13`

### Cодержание:

- [Постановка задачи](#1-постановка-задачи)
- [Входные и выходные данные](#2-входные-и-выходные-данные)
- [Выбор структуры данных](#3-выбор-структуры-данных)
- [Алгоритм](#4-алгоритм)
- [Программа](#5-программа)
- [Анализ правильности решения](#6-анализ-правильности-решения)

### 1. Постановка задачи
>Набор бусинок диаметрами A, B, C, D, надетый на нить, пытаются протащить в указанном порядке через отверстие диаметром X. Какое количество бусинок удастся протащить через отверстие? На вход программы подаются натуральные числа X, A, B, C, D. 

Для решения данной задачи требуется рассмотрение 4-ех случаев:

-А. Если А больше Х выведем 0 т.к. не удалось протащить первую бусинку и следовательно не удастся перетащить и  последующие
Если А не больше Х, можем протащить первую бусинку. 

-Б. рассмотрим следующую бусинку

Если B больше Х выводим 1 т.к. одну бусинку (А) уже протащили, а B не пролазит => не пролезут и следующие
Если B не больше Х, то у нас получилось перетащить уже две бусинки

-C.рассмотрим следующую бусинку

Если С больше Х выводим 2 т.к. две бусинку (А и В) уже протащили, а С не пролазит => не пролезет и следующая
Если С не больше Х, то у нас получилось перетащить уже три бусинки

-D.рассмотрим последнюю бусинку

Если D больше Х выводим 3 т.к. три бусинку (А, В и С) уже протащили, а D не пролазит.
Если D не больше Х, то у нас получилось перетащить все четыре бусинки. Выводим 4.
### 2. Входные и выходные данные
#### Данные на вход
В условии сказано, что на вход поступают натуральные числа X, A, B, C, D. 

|	          |Тип	             |min значение |max значение    |
|-----------|------------------|-------------|----------------|
|X (Число 1)|	Натуральное число|	1          |	10<sup>9</sup>|
|A (Число 2)|	Натуральное число|	1          |	10<sup>9</sup>|
|B (Число 3)|	Натуральное число|	1          |	10<sup>9</sup>|
|C (Число 4)|	Натуральное число|	1          |	10<sup>9</sup>|
|D (Число 5)|	Натуральное число|	1          |	10<sup>9</sup>|

#### Данные на выход
Требуется вывести количетсво бусинок. Будет выведено целое число от 0 до 4, т.к. всего четыре бусинки.

|         | Тип                                | min значение | max значение   |
|---------|------------------------------------|--------------|----------------|
| Число 1 | Целое неотрицательное число        | 0            | 4              |

### 3. Выбор структуры данных

Программа получает 5 натуральных чисел. Поэтому для хранения выделю 5 переменных (`x`,`a`,`b`,`c` и `d`) типа `integer`.


|	          |название переменной|	Тип (в Java)|
|-----------|-------------------|-------------|
|X (Число 1)|	x	                |integer      |
|A (Число 2)|	a	                |integer      |
|B (Число 3)|	b                	|integer      |
|C (Число 4)|	c                	|integer      |
|D (Число 5)|	d	                |integer      |

Для вывода результата необязательно его хранить в отдельной переменной.

### 4. Алгоритм

#### Алгоритм выполнения программы:
1. **Ввод данных**
Программа считывает пять натуральных чисел, обозначенных как x,a,b,c и d

2. **“Защита от дурака”** 
Если введено хотя бы одно ненатуральное число, вывести “Введены не натуральные числа”

3. **Сравнение чисел и вывод результата**
Поочереди сравниваем числа с x, начиная с а.
-Если а больше х, выводим 0, т.к. не удастся протащить ни одну бусинку. 
Если а не больше, то сравниваем х с b. 
-Если b больше х, выводим 1, т.к. удалось протащить одну бусинку(а)Б но не удастся протащить b и последующие.
Если b не больше, сравниваем с c. 
-Если c больше х, выводим 2, т.к. удалось протащить только 2 бусинки (a и b), но не удалось протащить c и d.
Если не больше, сравниваем х с d. 
-Если d больше х выводим 3, т.к. удалось протащить три предыдущие бусинки, но не удалось протащить последнюю
Иначе выводим 4, т.к. получилось перетащить все бусинки.

#### Блок-схема

```mermaid
graph TD
    A([Начало]) --> B[/Ввести: x, a, b, c и d/]
    B --> C{a > x}
    C -- Нет --> D{b > x}
    D -- Нет --> E{c > x}
    E -- Нет --> F{d > x}
    F -- Нет --> G[/Вывод: 4/]
    F -- Да --> K[/Вывод: 3/]
    E -- Да --> H[/Вывод: 2/]
    D -- Да --> I[/Вывод: 1/]
    C -- Да --> J[/Вывод: 0/]
    G --> Z
    H --> Z
    I --> Z
    K --> Z
    J --> Z([Конец])
```

### 5. Программа
```java
import java.io.PrintStream;
import java.util.Scanner;
public class Main {
    public static Scanner in = new Scanner(System.in);
    public static PrintStream out = System.out;
    public static void main(String[] args) {
        //считывание пяти переменных x,a,b,c и d из консоли
        int x = in.nextInt();
        int a = in.nextInt();
        int b = in.nextInt();
        int c = in.nextInt();
        int d = in.nextInt();
        if (x<1 || a<1 || b<1 || c<1 || d<1) //"Защита от дурака"
            out.print("Введены не натуральные числа");
        else{
            if (a>x) //если а больше х, выводим 0 т.к. а не пролезла и следующие бусинки тоже не пролезут
                out.print(0);
            else{ //если а не больше х, то у нас получилось перетащить первую бусинку
                //переходим к следующей бусинке
                if (b>x) //если b больше х выводим 1
                    //т.к. пролезла только первая бусинка а, но не пролезет бусинка b и последующие
                    out.print(1);
                else{// если b не больше х, то у нас получится перетащить и эту бусинку
                    //уже перетащили 2 бусинки (а и b)
                    //переходим к следующей бусинке
                    if (c>x) //если с больше х выводим 2
                        //т.к. пролезли бусинки a и b, но не пролезет бусинка с и d
                        out.print(2);
                    else{// если с не больше х, то у нас получится перетащить и эту бусинку
                        //уже перетащили 3 бусинки (а, b и c)
                        // переходим к последней бусинке
                        if (d>x) //если d больше х, выводим 3,
                            //т.к. смогли перетащить три предыдущие бусинки, но не смогли перетащить d
                            out.print(3);
                        else //если d не больше х, то выводим 4.
                            //т.к. мы смогли перетащить все бусинки
                            out.print(4);
                    }
                }
            }
        }
    }
}
```

### 6. Анализ правильности решения

1)Тест на A>X

- **Input**:
        ```
        7 8 4 15 6
        ```
- **Output**:
        ```
        0
        ```
  
2)Тест на A<=X<B

- **Input**:
        ```
        10 8 11 3 4
        ```
- **Output**:
        ```
        1
        ```
  
3)Тест на A,B <= X < C 

- **Input**:
        ```
        10 8 4 15 6
        ```
- **Output**:
        ```
        2
        ```
  
4)Тест на A,B,C <= X < D

- **Input**:
        ```
        10 8 4 6 15
        ```
- **Output**:
        ```
        3
        ```
  
5)Тест на X >= A,B,C,D

- **Input**:
        ```
        15 6 7 8 9
        ```
- **Output**:
        ```
        4
        ```
  
6) Тест на дурака: X<1 или A<1 или B<1 или C<1 или D<1
   
- **Input**:
        ```
        5 -4 6 5 4
        ```
- **Output**:
        ```
        Введены не натуральные числа
        ```
