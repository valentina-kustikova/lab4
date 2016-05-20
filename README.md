﻿# Реализация приоритетной очереди на основе различных структур данных и ее применение для построения остовного дерева графа с помощью алгоритма Крускала

## Содержание

* [Постановка задачи](#Постановка-задачи)
* [Руководство пользователя](#Руководство-пользователя)
	* [Использование реализации алгоритма Дейкстры](#Использование-реализации-алгоритма-Дейкстры)
	* [Использование реализации алгоритма Крускала](#Использование-реализации-алгоритма-Крускала)
* [Руководство программиста](#Руководство-программиста)
	* [Используемые технологии](#Используемые-технологии)
	* [Общая структура репозитория](#Общая-структура-репозитория)
	* [Описание структуры решения](#Описание-структуры-решения)
	* [Описание структур данных](#Описание-структур-данных)
		* [D-куча](#d-куча)
		* [Бинарное дерево](#Бинарное-дерево)
			* [Бинарное поисковое дерево](#Бинарное-поисковое-дерево)
			* [АВЛ-дерево](#АВЛ-дерево)
		* [Таблицы](#Таблицы)
			* [Просматриваемые таблицы](#Просматриваемые-таблицы)
			* [Упорядоченные таблицы](#Упорядоченные-таблицы)
		* [Приоритетная очередь](#Приоритетная-очередь)
		* [Разделенные множества](#Разделенные-множества)
	* [Описание алгоритмов](#Описание-алгоритмов)
		* [Пирамидальная сортировка](#Пирамидальная-сортировка)
		* [Алгоритм Дейкстры](#Алгоритм-Дейкстры)
		* [Алгоритм Крускала](#Алгоритм-Крускала)
	* [Программная реализация структур данных](#Программная-реализация-структур-данных)
		* [Программная реализация d-кучи](#Программная-реализация-d-кучи)
		* [Программая реализация бинарного поискового дерева](#Программая-реализация-бинарного-поискового-дерева)
		* [Программая реализация АВЛ-дерева](#Программая-реализация-АВЛ-дерева)
		* [Программая реализация просматриваемых таблиц](#Программая-реализация-просматриваемых-таблиц)
		* [Программая реализация упорядоченных таблиц](#Программая-реализация-упорядоченных-таблиц)
		* [Программая реализация приоритетной очереди](#Программая-реализация-приоритетной-очереди)
		* [Программая реализация разделенных множеств](#Программая-реализация-разделенных-множеств)
	* [Представление графа](#Представление-графа)
* [Заключение](#Заключение)
* [Литература](#Литература)


##Постановка задачи

1. Разработать статичесие библиотеки, реализующие слудующие структуры данных:
	* d-куча;
	* бинарное поисковое дерево;
	* авл-сбалансированное дерево;
	* просматриваемая таблица;
	* упорядоченная таблица;
	* приоритетная очередь, основанная на d-куче;
	* приоритетная очередь, основанная на бинарном сбалансированном дереве;
	* приоритетная очередь, основанная на упорядоченной таблице;
	* разделенные множества.
2. Написать тестирующую программу для каждой структуры данных с помощью Google C++ Testing Framework.
3. Написать приложение для демонстрации работы d-кучи (пирамидальная сортировка).
4. Написать приложение для демонстрации работы приоритетной очереди, основанной на d-куче (алгоритм Дейкстры):
	* входные данные - связный неориентированный взвешенный граф без петель со стартовой вершиной;
	* выходные данные - список расстояний до каждой вершины графа;
5. Написать приложение для демонстрации работы каждой приоритетной очереди и разделенных множеств (алгоритм Крускала):
	* входные данные - связный неориентированный взвешенный граф без петель;
	* выходные данные - граф, представляющий минимальное остовное дерево для исходного графа.

##Руководство пользователя

###Использование реализации алгоритма Дейкстры

####Запуск приложения и ввод данных

Программа предназначена для поиска кратчийших путей во взвешенном неориентированном графе от некоторой вершины, называемой текущей, до всех остальных вершин графа.
Для запуска приложения нужно открыть исполняемый файл `sample_Dijkstra.exe`.
Программа попросит ввести количество вершин графа и ребра с весом. Также будет запрошен номер вершины, являющейся стартовой. Результатом будет вывод вектора, содержащего номера вершин, что предшествуют вершинам, являющимся индексами вектора, для построения дерева, позволяющего восстановить обход и вывод списка расстояний от стартовой вершины до каждой из следующих вершин в порядке возрастания номера.

####Пример:

Рассмотрим граф:

![graph](https://raw.githubusercontent.com/Alexander-Khlybov/lab4/master/Rept/graph.png)

Для рассматриваемого графа алгоритм считает расстояния от вершины №1 до всех остальных вершин (ребра, через которые проходит кратчайший путь до вершины, помечены цветом этой вершины):

![graph_Dijkstra](https://raw.githubusercontent.com/Alexander-Khlybov/lab4/master/Rept/graph_Dijkstra.png)

#####Шаг 1
Ввод количества вершин графа

![Dijkstra1](https://raw.githubusercontent.com/Alexander-Khlybov/lab4/master/Rept/Dijkstra1.png)

#####Шаг 2
Ввод ребер и их весов

![Dijkstra2](https://raw.githubusercontent.com/Alexander-Khlybov/lab4/master/Rept/Dijkstra2.png)

#####Шаг 3
Выбор стартовой вершины

![Dijkstra3](https://raw.githubusercontent.com/Alexander-Khlybov/lab4/master/Rept/Dijkstra3.png)

#####Шаг 4
Вывод результата и завершение работы программы

![Dijkstra4](https://raw.githubusercontent.com/Alexander-Khlybov/lab4/master/Rept/Dijkstra4.png)

###Использование реализации алгоритма Крускала

####Запуск приложения и ввод данных

Программа предназначена для построения минимального остовного дерева для взвешенного неориентированного графа. 
Для запуска приложения нужно открыть исполняемый файл `sample_Kruskal.exe`.
Программа попросит ввести количество вершин графа и ребра с весом. Результатом работы программы будет вывод списка ребер, составляющих минимальное остовное дерево.

####Пример

Рассмотрим граф:

![graph](https://raw.githubusercontent.com/Alexander-Khlybov/lab4/master/Rept/graph.png)

Для рассматриваемого графа алгоритм строит дерево, выделенное зеленым цветом:

![graph_Kruskal](https://raw.githubusercontent.com/Alexander-Khlybov/lab4/master/Rept/graph_Kruskal.png)

#####Шаг 1
Ввод количества вершин графа

![Kruskal1](https://raw.githubusercontent.com/Alexander-Khlybov/lab4/master/Rept/Kruskal1.png)

#####Шаг 2
Ввод ребер и их весов

![Kruskal2](https://raw.githubusercontent.com/Alexander-Khlybov/lab4/master/Rept/Kruskal2.png)

#####Шаг 3
Выбор базы для приоритетной очереди

![Kruskal3](https://raw.githubusercontent.com/Alexander-Khlybov/lab4/master/Rept/Kruskal3.png)

#####Шаг 4
Вывод результата и завершение работы программы

![Kruskal4](https://raw.githubusercontent.com/Alexander-Khlybov/lab4/master/Rept/Kruskal4.png)

##Руководство программиста

###Используемые технологии
- среда разработки Microsoft Visual Studio Community (2015);
- фреймворк для написания автоматических тестов Google Test;
- система контроля версий Git.

###Общая структура репозитория
* [`gtest`](https://github.com/Alexander-Khlybov/lab4/tree/master/gtest) - библиотека GoogleTest.
* [`src`](https://github.com/Alexander-Khlybov/lab4/tree/master/src) - директория для размещения файлов исходноо кода.
* [`include`](https://github.com/Alexander-Khlybov/lab4/tree/master/include) - директория для размещения заголовочных файлов.
* [`sample`](https://github.com/Alexander-Khlybov/lab4/tree/master/samples) - директория для размещения исходных кодов приложений.
* [`test`](https://github.com/Alexander-Khlybov/lab4/tree/master/test) - директория для размещения тестов.
* [`sln`](https://github.com/Alexander-Khlybov/lab4/tree/master/sln/) - директория с файлими решений (на данный момент Visual Studio 2015).
* [`Rept`](https://github.com/Alexander-Khlybov/lab4/tree/master/Rept) - директория с материалами для отчета;
* Служебные файлы:
  * `.gitignore` - перечень расширений файлов, игнорируемых Git при добавлении файлов в репозиторий.

###Описание структуры решения
Решение состоит из 13 проектов:

* `gtest` - фреймворк Google Test;
* `d-heap_lib` - статическая библиотека, содержащая объявление и реализацию шаблонного класса D_HEAP.
* `disjoint-set_lib` - статическая библиотека, содержащая объявление и реализацию шаблонного класса DISJOINT_SET.
* `binary_search_tree_lib` - статическая библиотка, содержащая объявление и реализацию класса *BST*.
* `avl-tree_lib` - статическая библиотека, содержащая объявление и реализацию шаблонного класса *AVL_TREE*.
* `tables_lib` - статическая библиотека, содержащая объявление и реализацию шаблонных классов *TABLE*, *SCAN_TABLE*, *SORT_TABLE*.
* `graph_lib` - статическая библиотека, содержащая объявление и реализацию класса *GRAPH*.
* `priority_queue_lib` - статическая библиотека, содержащая объявление и реализацию шаблонных классов приоритетных очередей, основанных на разных структурах данных.
* `algorithms` - статическая библиотека, содержащая объявление и реализацию алгоритмов для примеров.
* `sampleDijkstra` - консольное приложение для демонстрации работы алгоритма Дейкстры.
* `sample_Kruskal` - консольное приложение для демонстрации работы алгоритма Крускала.
* `sample_d-heap` - консольное приложение для демонстрации работы пирамидальной сортировки.
* `test` - консольно приложение для проверки правильности реализации классов *D_HEAP*, *PRIORITY_QUEUE*, *DISJOINT_SET*.

###Описание структур данных

####D-куча

D-куча - завершенное d-арное дерево, содержащее набор однотипных элементов, со следующими свойствами:
- Каждый узел, не являющийся листом, за исключением, быть может, одного имеет ровно d потомков. Один узел, являющийся исключением, может иметь от 1 до d-1 потомка;
- Если h - глубина дерева, то для любого i = 1, ..., k-1 такое дерево имеет ровно d^i узлов глубины i;
- Количество узлов глубины k в дереве глубины k может варьироваться от 1 до d^k;
- Каждый узел имеет вес. Иначе говоря, каждому узлу дерева присвоен ключ такого типа данных, на котором определен порядок сравнения;
- Ключ элемента, приписанного узлу i, не превосходит ключа любого из своих потомков.
- 
####Бинарное дерево

#####Бинарное поисковое дерево
Бинарное поисковое дерево - это двоичное дерево, обладающее следующими свойствами:
* каждый узел имеет не больше двух потомков;
* любое поддерево является бинарным поисковым деревом;
* значение ключа любого узла левого поддерева меньше значения ключа корневого узла;
* значение ключа любого узла правого поддерева больше значения ключа корневого узла.

#####АВЛ-дерево
АВЛ-дерево - сбалансированное по высоте бинарное поисковое дерево, обладающее следующим свойством:
* для каждой вершины дерева высота её двух поддеревьев различается не больше чем на 1.

####Таблицы

#####Просматриваемые таблицы
Таблица - динамическая структура данных, хранящая однотипные элементы. Записи хранятся в векторе памяти в порядке добавления (добавление производится в конец таблицы). При удалении записи просиходит перепаковка (сдвиг всех записей ниже текущей на одну позицию вверх).

#####Упорядоченные таблицы
Упорядоченная таблица - это просматриваемая таблица, данные в которой отсортированы по невозрастанию/неубыванию ключей. Причем при вставке и удалении происходят перепаковки.

####Приоритетная очередь
Приоритетная очередь — это динамическая структура данных, содержащая элементы, каждый из которых имеет определенный приоритет. Элемент с более высоким приоритетом находится перед элементом с более низким приоритетом. Если у элементов одинаковые приоритеты, они распологаются в зависимости от своей позиции в очереди. 

####Разделенные множества
Разледенные множества - абстрактный тип данных, предназначенный для представления коллекции k попарно непересекающихся можеств.

###Описание алгоритмов

####Пирамидальная сортировка

1. Вектор значений переписывается в d-кучу.
2. Просматривается минимальный элемент кучи и кладется в результирующий вектор.
3. Минимальный элемент д-кучи меняется с последним.
4. Декрементируется размер д-кучи.
5. Погружение нулевого элемента.
6. Если размер кучи положителен, переход к п.2, иначе алгоритм завершается.

Таким образом вощвращаемый вектор значений будет отсортирован по неубыванию.

####Алгоритм Дейкстры

1. Задается взвешенный граф из n вершин.
2. Задается стартовая вершина CUR.
3. Создается вектор для отметки посещения вершины V (все элементы зануляются, V[CUR] = CUR).
4. Создается результирующий вектор расстояний DIST (все элементы устремлены в бесконечность, DIST[CUR] = 0).
5. Создается приоритетная очередь, в которую кладется расстояние от текущей вершины до неё же.
6. Пока очередь не пуста:
	1. Вынимается минимальный элемент.
	2. Если метка вынутого элемента больше метки, хранящейся в массиве DIST, переход к следующему шагу.
	3. По всем ребрам от текущей вершины: Если результирующее расстояние от смежной вершины больше, чем результирующее расстояние до вынутой в пункте 6.1 вершины в сумме с меткой ребра, вынутогов пункте 6.3, выполняем:
		1. В вектор V по номеру смежной вершины кладется значение вершины, вынутой на этапе 6.1.
		2. В вектор DIST по номету смежной вершины пишется новое значение расстояния, равное сумме результирующего расстояния до вынутой в пункте 6.1 вершины и меткои ребра, вынутогов пункте 6.3.
		3. Обработанное ребро кладется в очередь.

Результатом работы алгоритма становится вектор расстояний до каждой вершины графа (DIST) и вектор обхода вершин графа для получения указанных значений (V).

####Алгоритм Крускала

1. Задается взвешенный неориентированный граф из n вершин.
2. Создается приоритетная очередь из ребер графа (приоритет по метке ребра).
3. Содрается коллекция из множества вершин.
4. Вынимается ребро из приоритетной очереди.
5. Если вынутые вершины находятся не в одной коллекции:
	1. Объединяются коллекции, содержащие данные вершины.
	2. Вынутое ребро добавляется в результирующий набор ребер.
7. Если количество коллекций вершин больше количества компонент связности графа, переход к пункту 4, иначе алгоритм завершается.

В результате работы алгоритма имеется набор ребер, составляющих минимальное остовное дерево данного графа.

###Программная реализация структур данных

####Программная реализация d-кучи

В лабораторной работе d-куча представлена классом *D_HEAP*, содержащим нижеизложенные public-методы:
- `D_HEAP(int, int)` - конструктор. Принимает на вход стартовый размер вектора памяти для хранения d-кучи и арность.
- `D_HEAP(const D_HEAP<KeyType>&)` - конструктор копирования.
- `~D_HEAP (void)` - деструктор.
- `operator==(const D_HEAP<KeyType>&)const` - перегруженный оператор сравнения на равенство (требуется для проведения тестов).
- `operator!=(const D_HEAP<KeyType>&)const` - перегруженный оператор сравнения на неравенство (требуется для проведения тестов).
- `getSizeTree(void)const` - возвращает количество узлов, содержащихся в d-куче.
- `getNodeKey(int)const` - возврацает ключ узла, номер которого передан в качестве параметра.
- `getSizeReservedMem(void)const` - возвращает размер свободной памяти в выделенном ранее векторе памяти.
- `getD(void)const` - возвращает арность кучи.
- `swap(int, int)` - меняет местами узлы, индексы которых переданы в качестве параметров.
- `siftDown(int)` - выполняет погружение узла с индексом, указанным в качестве аргумента.
- `siftUp(int)` - выполняет всплытие узла с индексом, указанным в качестве аргумента.
- `insert(const KeyType&, mem_rc flag = ALLOW_MEMORY_REALLOCATION_WCV, int size = 0)` - производит вставку узла, переданного первым аргументом в дерево. Вторым параметром указывается правило обработки ситуации, когда вставляется узел в полное дерево:
	- `ALLOW_MEMORY_REALLOCATION_WYV` - разрешить выделить дополнительную память при вставке узла в полное дерево. Размер добавляемой памяти указывается в качестве третьего параметра.
	- `ALLOW_MEMORY_REALLOCATION_WCV` - разрешить выделить дополнительную память при вставке узла в полное дерево, однако третий аргумент метода в этом случае игнорируется, выделение же памяти будет таковым, что появляется место минимум под один узел, максимум под d узлов. Текущее значение выделения памяти будет таковым, чтобы выполнялись указанные условия и одно дополнительное: новый размер вектора памяти делится на арность кучи.
	- `PROHIBIT_MEMORY_REALLOCATION` - запретить выделение дополнительной памяти при вставке узла в полное дерево.
- `deleteMinElem(void)` - удаление узла с минимальным весом.
- `deleteElem(int)` - удаление узла дерева по индексу хранения в векторе памяти.
- `heapify(void)` - окучивание.
- `getTree(void)const` - возвращает вектор значений, содержащихся в векторе памяти, что хранит исходное дерево (требуется для тестирования).
- `operator<<(...)` - печать массива, хранящего значения узлов.

Класс реализован шаблонным, что позволяет хранить любого рода данные, для которых определен порядок сравнения.

####Программая реализация бинарного поискового дерева
Узел дерева представляется классом `NODE`, содержащим следующие поля:
* `KeyType data_` - данные.
* `NODE<KeyType>* left_` - указатель на левого потомка.
* `NODE<KeyType>* right_` - указатель на правого потомка.
* `NODE<KeyType>* parent_` - укаазатель на родителя.
* `short balance_` - показатель перевеса правого или левого поддерева (используется в АВЛ-дереве).

Бинарное поисковое дерево представлено классом *BST*, содержащим нижеизложенные методы:
* `getNodeForErasing(const KeyType&)` - вынимает из дерева узел, который требуется удалить.
* `recursiveErase(NODE<KeyType>*&)` - удаляет дерево.
* `copy(NODE<KeyType>*, NODE<KeyType>*)` - копирует дерево.
* `BST(void)` - конструктор.
* `BST(const BST<KeyType>& tree)` - конструктор копирования.
* `~BST(void)` - деструктор.
* `insert(const KeyType&)` - вставка нового элемента в дерево.
* `erase(const KeyType&)` - удаление узла из дерева по заданному ключу.
* `find(const KeyType&)const` - поиск узла дерева, содержащего указанный ключ.
* `findMin(NODE<KeyType>* node = NULL)const` - поиск минимального элемента в дереве, корень которого передан в качестве параметра.
* `findMax(NODE<KeyType>* node = NULL)const` - поиск максимального узла в дереве, корень которого передан в качестве параметра.
* `findPrev(NODE<KeyType>*)const` - поиск узла, являющегося предыдущим по значению для текущего.
* `findNext(NODE<KeyType>*)const` - поиск узла, являющегося следующим по значению для текущего.
* `getSize(void)const` - получение количества узлов в дереве.
* `recPostOrder(void)const` - обратный обход дерева.

Класс реализован шаблонным, что позволяет хранить любого рода данные, для которых определен порядок сравнения.

####Программая реализация АВЛ-дерева
АВЛ-дерево представлено классом *AVL_TREE*, наследуемым от класса *BST*, содержащим нижеизложенные методы:
* `getDepth(NODE<KeyType>* node = NULL)const` - получает глубину дерева, корень которого передан в качестве параметра.
* `doSingleLeftRotation(NODE<KeyType>*&)` - левый поворот.
* `doSingleRightRotation(NODE<KeyType>*&)` - правый поворот.
* `doDoubleLeftRotation(NODE<KeyType>*&)` - двойной левый поворот.
* `doDoubleRightRotation(NODE<KeyType>*&)` - двойной правый поворот.
* `updateLeftTree(NODE<KeyType>*&)` - преобразование левого поддерева (вызов правых поворотов).
* `updateRightTree(NODE<KeyType>*&)` - преобразование правого поддерева (вызов левых поворотов).
* `makeBalancing(NODE<KeyType>*&)` - балансировка дерева.
* `doRecursiveInsertion(NODE<KeyType>*&, NODE<KeyType>*)` - вставка узла в дерево.
* `getNodeForErasing(NODE<KeyType>*&, const KeyType&)` - вынимание из дерева узла для удаления.
* `AVL_TREE(void)` - конструктор.
* `AVL_TREE(const AVL_TREE<KeyType>& tree)` - сонструктор копирования.
* `AVL_TREE(const BST<KeyType>&)` - конструктор преобразования типа.
* `~AVL_TREE(void)` - деструктор.
* `erase(const KeyType&)` - переопределенный метод вставки узла.
* `insert(const KeyType&)` - переопределенный метод удаления узла.
* `eraseMin(void)` - метод удаления минимального узла.

Класс реализован шаблонным, что позволяет хранить любого рода данные, для которых определен порядок сравнения.

####Программая реализация просматриваемых таблиц
Запись в таблице представлена классом `TAB_RECORD`, содержащим в качестве поля ключ с определенным отношением порядка.
База для всех таблиц представлена классом *TABLE*, содержащим чисто виртуальные и виртуальные методы. Виртуальные методы с базовой реализацией:
* `isEmpty(void)const` - проверка таблицы на пустоту.
* `isFull(void)const` - проверка таблицы на полноту.
* `getCount(void)const` - получение текущего количества записей.
* `reset(void)` - установка индекса навигации в стартовую позицию.
* `goNext(void)` - перевод индекса навигации на следующую позицию.
* `isTabEnded(void)const` - проверка достижения индексом навигации конца таблицы.

Просматриваемые таблицы представлены классом *SCAN_TABLE*, содержащим нижеизложенные методы:
* `SCAN_TABLE(size_t size)` - конструктор (выделяет вектор памяди для хранения данных таблицы).
* `SCAN_TABLE(const SCAN_TABLE<DataType>& table)` - конструктор копирования.
* `~SCAN_TABLE(void)` - деструктор.
* `find(const DataType&)` - поиск записи с суказанным ключом.
* `insert(const TAB_RECORD<DataType>&)` - вставка новой записи.
* `erase(const DataType&)` - удаление записи из даблицы.
* `getCurrentRecord(void)const` - получение записи, закрепленной за индексом навигации.
* `eraseCurrentRecord(void)` - удаление записи, закрепленной за индексом навигации.

Класс реализован шаблонным, что позволяет хранить любого рода данные, для которых определен порядок сравнения.

####Программая реализация упорядоченных таблиц
Упорядоченные таблицы наследуются от класса *SCAN_TABLE* и представлены классом *SORT_TABLE*, содержащим нижеизложенные методы:
* `sort(void)` - сортировка данных (требуется для конструктора преобразования типа).
* `SORT_TABLE(size_t size)` - конструктор.
* `SORT_TABLE(const SORT_TABLE<DataType>& table)` - конструктор копирования.
* `SORT_TABLE(const SCAN_TABL<DataType>E& table)` - конструктор преобразования типа.
* `~SORT_TABLE(void)` - деструктор.
* `find(const DataType&)` - переопределенный метод поиска записи с указанным ключом (используется бинарный поиск).
* `insert(const TAB_RECORD<DataType>&)` - переопределенный метод вставки новой записи в таблицу.
* `erase(const DataType&)` - переопределенный метод удаления записи из таблицы.

Класс реализован шаблонным, что позволяет хранить любого рода данные, для которых определен порядок сравнения.

####Программая реализация приоритетной очереди
Приоритетная очередь представлена базовым абстрактным классом *PRIORITY_QUEUE*, от которого наследуются классы *PRIORITY_QUEUE_ON_D_HEAP*, *PRIORITY_QUEUE_ON_AVL_TREE*, *PRIORITY_QUEUE_ON_SORT_TABLE*, содержащие идентичные, но переопределенный методы:
* `PRIORITY_QUEUE_ON_*(void)` - конструктор (выделяет память под базовую структуру данных).
* `PRIORITY_QUEUE_ON_*(const PRIORITY_QUEUE_ON_*<KeyType>&)` - конструктор копирования.
* `~PRIORITY_QUEUE_ON_*(void)` - деструктор.
* `getSize(void)const` - получение количества элементов в очереди.
* `isEmpty(void)const` - проверка на пустоту.
* `isFull(void)const` - проверка на полноту.
* `pop(void)` - удаление элемента с наивысшим приоритетом.
* `push(const KeyType&)` - вставка элемента.
* `back(void)const` - простотр элемента с наивысшим приоритетом.

Классы реализованы шаблонными, что позволяет хранить любого рода данные, для которых определен порядок сравнения.

####Программая реализация разделенных множеств
Разделенные множества представлены классом *DISJOINT_SET*, содержащим следующие методы:
- `DISJOINT_SET<KeyType>(int)` - конструктор; принимает в качестве аргумента максимальное суммарное количество элементов множеств.
- `DISJOINT_SET<KeyType>(const DISJOINT_SET<KeyType>&)` - конструктор копирования.
- `~DISJOINT_SET<KeyType>(void)` - деструктор.
- `createSet(int)` - создает одноэлементное множество с элементом, указанным в качестве аргумента.
- `uniteSets(int, int)` - объединяет два множества (множества передаются номером главного элемента).
- `findSet(int)` - возвращает главный элемент множества, если элемент принадлежит какому-либо множеству, иначе -1.
- `getNumberOfSets(void)const` - возвращает текущее количество множеств (требуется для тестирования).
- `getUniversalSet(void)const` - возвращает вектор, хранящий структуру множеств (требуется для тестирования).
- `getSet(int)const` - возвращает вектор элементов, содержащихся в множестве, которое указано в качестве аргумента (множество задается главным элементом).
- `operator<<(...)` - выводит вектор, содержащий структуру множеств.

Представленный набор методов достаточен для проведения тестирования корректности представления и работы класса, а также использования его в иных алгоритмах.

###Представление графа
Ребро представляется классом-сущностью *EDGE*. Класс содержит три public-поля:
 * `first: size_t`.
 * `second: size_t`.
 * `distance: double`.
 Где first и second содержат связываемые вершины (в порядке неубывания), а distance - вес ребра.

Граф представлен классом *GRAPH*, содержащим нижеизложенные методы:
* `GRAPH(size_t)` - конструктор.
* `GRAPH(const GRAPH&)` - конструктор копирования.
* `~GRAPH(void)` - деструктор.
* `setDistance(size_t, size_t, double)` - устанавливает ребро графа.
* `getDistance(size_t, size_t)` - возвращает вес ребра графа (0, если ребра нет).
* `getNumOfVertices(void)` - возвращает число вершин графа.
* `eraseEdge(size_t, size_t)` - удалает ребро из графа, если оно присутствует.
* `fillGraph(void)` - метод заполнения графа (вручную).
* `createGraph(size_t, double, double)` - создание графа со случайными метками ребер.
* `getNumOfComponents(void)const` - получение количества компонент связности графа.
* `getAllEdges(void)` - возвращает множество всех ребер графа.
* `getSetOfEdges(size_t)` - возвращает множество пар: смежная вершина и расстояние до неё.
* `graphInfo(void)` - вывод информации о графе.
	* количество вершин;
	* количество ребер;
	* список ребер.

##Заключение
В ходе лабораторной работы были реализованы структуры данных "d-куча", "бинарное поисковое дерево", "АВЛ-сбалансированное дерево", "просматриваемая таблица", "упорядоченная таблицы" "приоритетная очередь" и "разделенные множества" с использованием шаблонных классов. Также написано тестирующее приложение, которое покрывает все методы, используемые в указанных классах (Все тесты успешно пройдены). Написаны консольные приложения:
* пирамидальная сортировка массива, заполняемого случайным образом;
* алгоритм Дейкстры для поиска кратчайших путей от некоторой стартовой вершины связного неориентированного взвешенного графа без петель до всех прочих с использованием приоритетной очереди, основанной на d-куче;
* алгоритм Крускала для построения минимального остовного дерева/леса неориентированного взвешенного графа без петель с использованием приоритетных очередей на базе d-кучи, упорядоченных таблиц и АВЛ-сбалансированных деревьев.

##Литература
1. Кормен Т., Лейзерсон Ч., Риверст Р., Штайн К. Алгоритмы. Построение и анализ. - М.: Издательский дом "Вильямс". - 2005. - 1290с.
2. Алексеев В.Е., Таланов В.А. Графы. Модели вычислений. Структуры данных: Учебник. – Нижний Новгород: Изд-во ННГУ, 2005. 307 с.
