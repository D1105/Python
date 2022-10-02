# 2. Встроенные типы и операции с ними



```python

# Дан список, заполненный произвольными целыми числами, получите новый список,
# элементами которого будут квадратные корни элементов исходного списка,
# но только если результаты извлечения корня не имеют десятичной части и
# если такой корень вообще можно извлечь
# Пример: Дано: [2, -5, 8, 9, -25, 25, 4]   Результат: [3, 5, 2]

import math
A = [2, -5, 8, 9, -0.25, 25, 4]
B = []
for i in A:
    if (abs(int(i)) == i) and (math.sqrt(i) == int(math.sqrt(i))):
        B.append(math.sqrt(i))
print(B)
```

    [3.0, 5.0, 2.0]



```python
# Напишите алгоритм, заполняющий список произвольными целыми числами
# в диапазоне от -100 до 100. В списке должно быть n - элементов.
# Подсказка:
# для получения случайного числа используйте функцию randint() модуля random

import random
a = []
n = int(input())
for i in range(n):
    a.append(random.randint(-100,100))
print(a)

```

    5
    [37, -71, 29, -4, 87]



```python
# Дан список, заполненный произвольными целыми числами.
# Получите новый список, элементами которого будут:
# а) неповторяющиеся элементы исходного списка:
# например, lst = [1, 2, 4, 5, 6, 2, 5, 2], нужно получить lst2 = [1, 2, 4, 5, 6]
# б) элементы исходного списка, которые не имеют повторений:
# например, lst = [1 , 2, 4, 5, 6, 2, 5, 2], нужно получить lst2 = [1, 4, 6]

lst = [1, 2, 4, 5, 6, 2, 5, 2]
lst2 = set(lst)
print(list(lst2))

lst3 = []
for i in lst:
    if (lst.count(i) == 1):
        lst3.append(i)
print(lst3)
```

    [1, 2, 4, 5, 6]
    [1, 4, 6]



```python
# Уравнение прямой вида y = kx + b задано в виде строки.
# Определить координату y точки с заданной координатой x.

equation = 'y = -12x + 11111140.2121'
x = 2.5
# вычислите и выведите y


eq = 'y = -12x + 11111140.2121'
x = 2.5

a0 = eq.find('=')+2
a1 = eq.find('x')
b0 = eq.find('+')+2
b1 = len(eq)
a = float(eq[a0:a1])
b = float(eq[b0:b1])

print(x*a+b)

```

    11111110.2121


# 3. Функции и работа с файлами



```python
#Напишите функцию, возвращающую ряд Фибоначчи с n-элемента до m-элемента. 
#Первыми элементами ряда считать цифры 1 1
def fibonacci(n, m):
    arr = [1,1]
    for i in range(1,m):
        arr.append(arr[i]+arr[i-1])
    arr = arr[n:m+1]
    return(arr)

a = fibonacci(4,7)
print(a)


```

    [5, 8, 13, 21]



```python
#Напишите функцию, сортирующую принимаемый список по возрастанию. 
#Для сортировки используйте любой алгоритм (например пузырьковый). 
#Для решения данной задачи нельзя использовать встроенную функцию и метод sort()

def sort_to_max(origin_list):
    arr = origin_list
    for i in range(len(arr)-1):
        for j in range(len(arr)-1-i):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
    return(arr)

a = sort_to_max([2, 10, -12, 2.5, 20, -11, 4, 4, 0])
print(a)

```

    [-12, -11, 0, 2, 2.5, 4, 4, 10, 20]



```python

# Дан шестизначный номер билета. Определить, является ли билет счастливым.
# Решение реализовать в виде функции.
# Билет считается счастливым, если сумма его первых и последних цифр равны.
# !!!P.S.: функция не должна НИЧЕГО print'ить


def lucky_ticket(ticket_number):
    number = str(ticket_number)
    if len(number) != 6:
        return('Error')
    first = number[0:3]
    last = number[3:6]
    a,b = 0,0
    for i in first:
        a += int(i)
    for j in last:
        b += int(j)

    if a == b:
        return('Билет счастливый')
    else:
        return('Билет не счастливый')

print(lucky_ticket(123006))
print(lucky_ticket(12321))
print(lucky_ticket(436751))
```


```python

# Даны четыре точки А1(х1, у1), А2(x2 ,у2), А3(x3 , у3), А4(х4, у4).
# Определить, будут ли они вершинами параллелограмма.(При задании точек в порядке обхода)

a1 = [0,0]
a2 = [2,4]
a3 = [9,4]
a4 = [7,0]


def is_a_prl(A1,A2,A3,A4):
    v_12=[a2[0]-a1[0], a2[1]-a1[1]]
    v_43=[a3[0]-a4[0], a3[1]-a4[1]]
    v_23=[a3[0]-a2[0], a3[1]-a2[1]]
    v_14=[a4[0]-a1[0], a4[1]-a1[1]]
    
    if (v_12 == v_43) and (v_23 == v_14):
        return("True")
    else:
        return("False")
    
print(is_a_prl(a1,a2,a3,a4))
    
    
```

    True


***

# 4. Полезные инструменты




```python
# Задание-1:
# Дан список, заполненный произвольными целыми числами. 
# Получить новый список, элементы которого будут
# квадратами элементов исходного списка
# [1, 2, 4, 0] --> [1, 4, 16, 0]

my_list = [1, 2, 4, 0]
new_list = []
for i in my_list[:]:
    new_list.append(i**2)
print(new_list)
print(my_list)
```

    [1, 4, 16, 0]
    [1, 2, 4, 0]



```python
# Задание-2:
# Даны два списка фруктов.
# Получить список фруктов, присутствующих в обоих исходных списках.

fruits_list_1 = ['banana', 'apple', 'grape']
fruits_list_2 = ['watermelon', 'orange', 'grape']
new_fruits_list = []

for i in fruits_list_1[:]:
    for j in fruits_list_2[:]:
        if i == j:
            new_fruits_list.append(i)
            
print(fruits_list_2)
print(fruits_list_1)
print(new_fruits_list)
    
```

    ['watermelon', 'orange', 'grape']
    ['banana', 'apple', 'grape']
    ['grape']



```python

# Дан список, заполненный произвольными числами.
# Получить список из элементов исходного, удовлетворяющих следующим условиям:
# + Элемент кратен 3
# + Элемент положительный
# + Элемент не кратен 4

my_list = [0, -1, 3, 12, -12, 1.2, -6]
new_list=[]
for i in my_list[:]:
    if i%3==0 and i%4!=0 and i>0:
        new_list.append(i)
print(my_list)
print(new_list)

```

    [0, -1, 3, 12, -12, 1.2, -6]
    [3]



```python

# Вывести символы в нижнем регистре, которые находятся вокруг
# 1 или более символов в верхнем регистре.
# Т.е. из строки "mtMmEZUOmcq" нужно получить ['mt', 'm', 'mcq']

import re

line = 'mtMmEZUOmcqWiryMQhhTxqKdSTKCYEJlEZCsGAMkgAYEOmHBSQsSUHKvSfbmxULaysmNO'\
       'GIPHpEMujalpPLNzRWXfwHQqwksrFeipEUlTLeclMwAoktKlfUBJHPsnawvjPhfgewVzK'\
       'TUfSYtBydXaVIpxWjNKgXANvIoumesCSSvjEGRJosUfuhRRDUuTQwLlJJJDdkVjfSAHqn'\
       'LxooisBDWuxIhyjJaXDYwdoVPnsllMngNlmkpYOlqXEFIxPqqqgAWdJsOvqppOfyIVjXa'\
       'pzGOrfinzzsNMtBIOclwbfRzytmDgEFUzxvZGkdOaQYLVBfsGSAfJMchgBWAsGnBnWete'\
       'kUTVuPluKRMQsdelzBgLzuwiimqkFKpyQRzOUyHkXRkdyIEBvTjdByCfkVIAQaAbfCvzQ'\
       'WrMMsYpLtdqRltXPqcSMXJIvlBzKoQnSwPFkapxGqnZCVFfKRLUIGBLOwhchWCdJbRuXb'\
       'JrwTRNyAxDctszKjSnndaFkcBZmJZWjUeYMdevHhBJMBSShDqbjAuDGTTrSXZywYkmjCC'\
       'EUZShGofaFpuespaZWLFNIsOqsIRLexWqTXsOaScgnsUKsJxiihwsCdBViEQBHQaOnLfB'\
       'tQQShTYHFqrvpVFiiEFMcIFTrTkIBpGUflwTvAzMUtmSQQZGHlmQKJndiAXbIzVkGSeuT'\
       'SkyjIGsiWLALHUCsnQtiOtrbQOQunurZgHFiZjWtZCEXZCnZjLeMiFlxnPkqfJFbCfKCu'\
       'UJmGYJZPpRBFNLkqigxFkrRAppYRXeSCBxbGvqHmlsSZMWSVQyzenWoGxyGPvbnhWHuXB'\
       'qHFjvihuNGEEFsfnMXTfptvIOlhKhyYwxLnqOsBdGvnuyEZIheApQGOXWeXoLWiDQNJFa'\
       'XiUWgsKQrDOeZoNlZNRvHnLgCmysUeKnVJXPFIzvdDyleXylnKBfLCjLHntltignbQoiQ'\
       'zTYwZAiRwycdlHfyHNGmkNqSwXUrxGc'

result = re.split(r'[A-Z]', line)
result = [i for i in result_1 if i]
print(result)
```

    ['mt', 'm', 'mcq', 'iry', 'hh', 'xq', 'd', 'l', 's', 'kg', 'm', 's', 'v', 'fbmx', 'aysm', 'p', 'ujalp', 'z', 'fw', 'qwksr', 'eip', 'l', 'ecl', 'w', 'okt', 'lf', 'snawvj', 'hfgew', 'z', 'f', 't', 'yd', 'a', 'px', 'j', 'g', 'v', 'oumes', 'vj', 'os', 'fuh', 'u', 'w', 'l', 'dk', 'jf', 'qn', 'xoois', 'ux', 'hyj', 'a', 'wdo', 'nsll', 'ng', 'lmkp', 'lq', 'x', 'qqqg', 'd', 's', 'vqpp', 'fy', 'j', 'apz', 'rfinzzs', 't', 'clwbf', 'zytm', 'g', 'zxv', 'kd', 'a', 'fs', 'f', 'chg', 's', 'n', 'n', 'etek', 'u', 'lu', 'sdelz', 'g', 'zuwiimqk', 'py', 'z', 'y', 'k', 'kdy', 'v', 'jd', 'y', 'fk', 'a', 'bf', 'vz', 'r', 's', 'p', 'tdq', 'lt', 'qc', 'vl', 'z', 'o', 'n', 'w', 'kapx', 'qn', 'f', 'whch', 'd', 'b', 'u', 'b', 'rw', 'y', 'x', 'ctsz', 'j', 'nnda', 'kc', 'm', 'j', 'e', 'dev', 'h', 'h', 'qbj', 'u', 'r', 'yw', 'kmj', 'h', 'ofa', 'puespa', 's', 'qs', 'ex', 'q', 's', 'a', 'cgns', 's', 'xiihws', 'd', 'i', 'a', 'n', 'f', 't', 'h', 'qrvp', 'ii', 'c', 'r', 'k', 'p', 'flw', 'v', 'z', 'tm', 'lm', 'ndi', 'b', 'z', 'k', 'eu', 'kyj', 'si', 'sn', 'ti', 'trb', 'unur', 'g', 'i', 'j', 't', 'n', 'j', 'e', 'i', 'lxn', 'kqf', 'b', 'f', 'u', 'm', 'p', 'kqigx', 'kr', 'pp', 'e', 'xb', 'vq', 'mls', 'yzen', 'o', 'xy', 'vbnh', 'u', 'q', 'jvihu', 'sfn', 'fptv', 'lh', 'hy', 'wx', 'nq', 's', 'd', 'vnuy', 'he', 'p', 'e', 'o', 'i', 'a', 'i', 'gs', 'r', 'e', 'o', 'l', 'v', 'n', 'g', 'mys', 'e', 'n', 'zvd', 'yle', 'yln', 'f', 'j', 'ntltignb', 'oi', 'z', 'w', 'i', 'wycdl', 'fy', 'mk', 'q', 'w', 'rx', 'c']



```python

# Вывести символы в верхнем регистре, слева от которых находятся
# два символа в нижнем регистре, а справа - два символа в верхнем регистре.
# Т.е. из строки 
# "GAMkgAYEOmHBSQsSUHKvSfbmxULaysmNOGIPHpEMujalpPLNzRWXfwHQqwksrFeipEUlTLec"
# нужно получить список строк: ['AY', 'NOGI', 'P']
# Решить задачу двумя способами: с помощью re и без.

line_2 = 'mtMmEZUOmcqWiryMQhhTxqKdSTKCYEJlEZCsGAMkgAYEOmHBSQsSUHKvSfbmxULaysm'\
       'NOGIPHpEMujalpPLNzRWXfwHQqwksrFeipEUlTLeclMwAoktKlfUBJHPsnawvjPhfgewV'\
       'fzKTUfSYtBydXaVIpxWjNKgXANvIoumesCSSvjEGRJosUfuhRRDUuTQwLlJJJDdkVjfSA'\
       'HqnLxooisBDWuxIhyjJaXDYwdoVPnsllMngNlmkpYOlqXEFIxPqqqgAWdJsOvqppOfyIV'\
       'jXapzGOrfinzzsNMtBIOclwbfRzytmDgEFUzxvZGkdOaQYLVBfsGSAfJMchgBWAsGnBnW'\
       'etekUTVuPluKRMQsdelzBgLzuwiimqkFKpyQRzOUyHkXRkdyIEBvTjdByCfkVIAQaAbfC'\
       'vzQWrMMsYpLtdqRltXPqcSMXJIvlBzKoQnSwPFkapxGqnZCVFfKRLUIGBLOwhchWCdJbR'\
       'uXbJrwTRNyAxDctszKjSnndaFkcBZmJZWjUeYMdevHhBJMBSShDqbjAuDGTTrSXZywYkm'\
       'jCCEUZShGofaFpuespaZWLFNIsOqsIRLexWqTXsOaScgnsUKsJxiihwsCdBViEQBHQaOn'\
       'LfBtQQShTYHFqrvpVFiiEFMcIFTrTkIBpGUflwTvAzMUtmSQQZGHlmQKJndiAXbIzVkGS'\
       'euTSkyjIGsiWLALHUCsnQtiOtrbQOQunurZgHFiZjWtZCEXZCnZjLeMiFlxnPkqfJFbCf'\
       'KCuUJmGYJZPpRBFNLkqigxFkrRAppYRXeSCBxbGvqHmlsSZMWSVQyzenWoGxyGPvbnhWH'\
       'uXBqHFjvihuNGEEFsfnMXTfptvIOlhKhyYwxLnqOsBdGvnuyEZIheApQGOXWeXoLWiDQN'\
       'JFaXiUWgsKQrDOeZoNlZNRvHnLgCmysUeKnVJXPFIzvdDyleXylnKBfLCjLHntltignbQ'\
       'oiQzTYwZAiRwycdlHfyHNGmkNqSwXUrxGC'

result = re.findall(r'[a-z]{2}([A-Z]+)[A-Z]{2}', line_2)
print(result)
```

    ['AY', 'NOGI', 'P', 'UBJ', 'K', 'C', 'EG', 'RR', 'S', 'B', 'XE', 'G', 'B', 'U', 'KR', 'I', 'VI', 'SMX', 'ZC', 'T', 'CCEU', 'ZWLF', 'I', 'E', 'SQQZ', 'Q', 'WLALH', 'Q', 'Y', 'SZMWS', 'NGE', 'M', 'E', 'H']



```python

# Матрицы в питоне реализуются в виде вложенных списков:
# Пример. Дано:
matrix = [[1, 0, 8],
          [3, 4, 1],
          [0, 4, 2]]
          
# Выполнить поворот (транспонирование) матрицы
# Пример. Результат:
# matrix_rotate = [[1, 3, 0],
#                  [0, 4, 4],
#                  [8, 1, 2]]

# Суть сложности hard: Решите задачу в одну строку



print(list(map(list,zip(*matrix))))
```

    [[1, 3, 0], [0, 4, 4], [8, 1, 2]]


# 5. Модули и библиотеки




```python
import os
import shutil
```


```python

# Напишите скрипт, создающий директории dir_1 - dir_9 в папке,
# из которой запущен данный скрипт.
# И второй скрипт, удаляющий эти папки.


print('Creating \n')
for j in range(1,10):
    new_dir = os.path.join(os.getcwd(),"dir_"+str(j))
    try:
        os.mkdir(new_dir)
        print("directory: '" + new_dir + "' created")
    except Exception as e:
         print("directory: " + new_dir + "exist")
            
print('\n')
print('Deleting \n')
for j in range(1,10):
    new_dir = os.path.join(os.getcwd(),"dir_"+str(j))
    try:
        os.removedirs(new_dir)
        print("directory: '" + new_dir + "' deleted")
    except Exception as e:
         print("deliting error" + new_dir)

```

    Creating 
    
    directory: '/Users/macbook/dir_1' created
    directory: '/Users/macbook/dir_2' created
    directory: '/Users/macbook/dir_3' created
    directory: '/Users/macbook/dir_4' created
    directory: '/Users/macbook/dir_5' created
    directory: '/Users/macbook/dir_6' created
    directory: '/Users/macbook/dir_7' created
    directory: '/Users/macbook/dir_8' created
    directory: '/Users/macbook/dir_9' created
    
    
    Deleting 
    
    directory: '/Users/macbook/dir_1' deleted
    directory: '/Users/macbook/dir_2' deleted
    directory: '/Users/macbook/dir_3' deleted
    directory: '/Users/macbook/dir_4' deleted
    directory: '/Users/macbook/dir_5' deleted
    directory: '/Users/macbook/dir_6' deleted
    directory: '/Users/macbook/dir_7' deleted
    directory: '/Users/macbook/dir_8' deleted
    directory: '/Users/macbook/dir_9' deleted



```python

# Напишите скрипт, отображающий папки текущей директории.


list_all = os.listdir()

print("Folders in current directory")

for folder in list_all:
    if os.path.isfile(folder) == False:
        print(folder)


```

    Folders in current directory
    .config
    Music
    .julia
    .local
    Creative Cloud Files
    Pictures
    .ipython
    Desktop
    Library
    .matplotlib
    .IdentityService
    .android
    PycharmProjects
    Public
    .anaconda
    CLionProjects
    Movies
    Applications
    opt
    .Trash
    .ipynb_checkpoints
    .jupyter
    Documents
    .rstudio-desktop
    .mono
    .vscode
    Downloads
    .continuum
    .conda


# 6. ООП



```python
# Написать класс для фигуры-треугольника, заданного координатами трех точек.
# Определить методы, позволяющие вычислить: площадь, высоту и периметр фигуры.
from math import sqrt

class triangle:
    def __init__(self, a, b, c):
        self.a = a
        self.b = b
        self.c = c
    
        self.ab = sqrt((a[0] - b[0])**2 + (a[1] - b[1])**2)
        self.bc = sqrt((b[0] - c[0])**2 + (b[1] - c[1])**2)
        self.ac = sqrt((a[0] - c[0])**2 + (a[1] - c[1])**2)
    
    def area(self):
             return 0.5*abs((self.a[0]-self.b[0])*(self.c[1]-self.a[1])-(self.c[0]-self.a[0])*(self.b[1]-self.a[1]))

    def height(self, side):
        if side in {'ab','bc','ac', 'ba', 'cb' , 'ca'}:
            if side == 'ab' or side == 'ba':
                return self.area()*2/self.ab
            elif side == 'bc' or side == 'cb':
                return self.area()*2/self.bc
            else:
                return self.area()*2/self.ac
        else:
            return('No such side')
        
    def perimeter(self):
        return self.ab + self.bc + self.ac
    
    
Test = triangle([0,0], [4,0], [4,2])
print(Test.area())
print(Test.perimeter())
print(Test.height('ab'))
```

    4.0
    10.47213595499958
    2.0

