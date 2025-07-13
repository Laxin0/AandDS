https://studfile.net/preview/8739480/page:15/#31 - Всякое полезное
# 1.Абстрагирование данных. Концепция типа данных.
Обрабатываемая информация на компьютере представляет собой абстракцию некоторой части реального мира, в них игнорируются некоторые свойства и характеристики реальных объектов, не существенные для решаемой задачи. Поэтому абстракция – это одновременно упрощение.  При решении задачи нужно определить множество данных, описывающих реальную ситуацию, затем способ представления информации (средствами эвм).  Язык программирования описывает некоторую абстрактную вычислительную машину, понимающую термины этого языка, что соответствует какому-то уровню абстракции от объектов, используемых реальной ЭВМ. Следовательно; работая с таким «языком высокого уровня», программист освобождается от вопросов представления чисел.

Каждая константа, переменная, выражение или функция бывают определенного типа. Этот тип существенным образом характеризует множество значений, к которому при­надлежит константа, которые может принимать переменная или выражение или которые может вырабатывать функция.

1. Расположение в памяти
2. Допустимые значения
3. Операции над типом

Типы данных
- базовые
- статические (массив, век, рекорд)
- динамические
- файловые

# Массив - фундаментальная структура данных. Отображение массива на оперативную память, выравнивание, упаковка.

Массив:
- Располагается в памяти непрерывно
- Все его компоненты — одного типа
- `at(i) -> val`

Массив — также структура с так называемым _слу­чайным доступом,_ все его компоненты могут выбираться произвольно   и   являются   одинаково  доступными.

Округление числа занимаемых слов до бли­жайшего целого называется **выравниванием**. Выравнивание понижает коэффициент  использования па­мяти.

Коэффициент можно значительно увеличить, помещая в каж­дое слово более одной компоненты массива. Этот прием на­зывается **упаковкой**.
# 2. Записи (record)- фундаментальные структуры. Отображение записи на ОП, упакованная запись.
- непрерывно
- поля разного типа
- `get/set` 

Если несколько компонент записи умещаются в одном слове памяти, то может идти речь об упаковке.

# Представление множества, как фундаментальной структуры данных, в память машины.

Фундаментальная структура данных — множество. Соответствующий тип опи­сывается следующим образом:

type Т = set of Т0 Значениями переменной х типа Т являются множества эле­ментов типа То. Множество всех подмножеств множества То называется множеством-степенью Т0. Таким образом, тип Т — это множество-степень своего базового типа То. Примеры: type intset  set of 0.. 30; type charset — set of char. На  всех множествах определены следующие элементар­ные операции: * пересечение множеств,   +  объединение множеств,  —    разность множеств, in    принадлежность множеству. Пересечение  и   объединение  двух   множеств  часто назы­вают   соответственно   умножением   и   сложением множеств. Множество s наилучшим образом представляется в па­мяти машины с помощью характеристической функции. Характеристическая функция — это массив логических зна­чений, i-я компонента которого означает наличие или отсут­ствие i-го значения базового типа в множестве s. Размер этого массива равен кардинальному числу базового типа множества. Представление множеств их характеристической функцией позволяет реализовать операции объединения, пересечения и разности двух множеств с помощью элементарных логиче­ских  операций.

**Множество** — это неупорядоченное хранилище уникальных элементов.

**Характеристики:**
Высокая скорость проверки принадлежности
Эффективное использование памяти
Уникальность элементов

**Способы реализации:**
Через битовые массивы
С помощью хэш-таблиц
Используя деревья

### Особенности хранения

**При хранении множества учитывается:**
Тип элементов
Размер множества
Требуемые операции
Эффективность доступа

**Важные аспекты:**
Оптимизация памяти
Быстрота операций добавления/удаления
Эффективность проверки наличия элемента

# 3. Алгоритм линейного поиска элемента в массиве и его оптимизация - установка «барьера».

```cpp
int Find(int arr[], int n, int z){
	for(int i = 0; i < n, ++i){
		if ==
			return i
	}
	return -1
}
```

Установка барьера
```cpp
int Find(int arr[], int n, int z){
	int last = arr[n-1];
	arr[n-1] = z;
	int i = 0;
	while(arr[i] != z)
		++i;
	return i < n-1 ? i : (last == z ? n-1 : -1);
}
```

# 4. Алгоритм бинарного поиска по ключу в массиве и пути повышения его эффективности.
$O(\log{n})$
```cpp
int Find(int arr[], int l, int r, int z){
	if (l>r) return -1;
	int m = (r-l)/2;
	if (arr[m] == z){
		return m;
	}else if (arr[m] < z){
		return Find(arr, l, m-1, z);
	}else{
		return Find(arr, m+1, r, z);
	}
}
```
# 5. Алгоритм прямого поиска подстроки в строке.
## Поиск подстроки
```cpp
char[] str = "";
char[] subStr = "";

for(int i = 0; i < n-m; ++i){
	int j = 0; 
	for(int j = 0; j < m;){
		if (str[i+j] == subStr[j])
			++j;
		else
			break;
	}
	if (j == m) return i;
}
return -1;
```

# 6. Сортировка: общие понятия, классификация, характеристики, цели.
Сортировка - это процесс упорядочивания элементов в списке или наборе данных по определенному признаку или правилу. Сортировка применяется для систематизации данных, повышения эффективности поиска и обработки информации, а также для обеспечения определенного порядка при работе с данными. 
$x_1, ..., x_n$ -> $x_1 \leq x_2 \leq ... \leq x_n$

##### Общие понятия:
- **Элементы:**
    Данные, которые необходимо отсортировать (числа, слова, объекты и т.д.).

- **Признак сортировки:**
    Характеристика, по которой производится упорядочивание (например, числовое значение, алфавит, размер, цвет и т.д.).

- **Ключ сортировки:**
    Значение, используемое для сравнения элементов при сортировке.

- **Алгоритм сортировки:**
    Набор правил и инструкций, определяющих порядок, в котором элементы будут переупорядочены. 


##### Классификация:
Сортировки можно классифицировать по разным признакам:

- **По типу данных:**
    Сортировка чисел, строк, объектов, сложных структур данных. 

- **По устойчивости:**
    Устойчивая сортировка сохраняет порядок элементов с одинаковыми ключами, неустойчивая – нет. 

- **По способу реализации:**
    Сортировка вставками, сортировка выбором, сортировка пузырьком, сортировка слиянием, быстрая сортировка и т.д. 

- **По используемой памяти:**
    Сортировка на месте (in-place) и сортировка с использованием дополнительной памяти. 

##### Характеристики:
- **Время выполнения:**
    Определяет скорость работы алгоритма сортировки (оценивается в терминах Big O notation).

- **Требования к памяти:**
    Объем дополнительной памяти, необходимой для работы алгоритма.

- **Устойчивость:**
    Свойство сохранять порядок равных элементов.

- **Простота реализации:**
    Легкость написания и понимания алгоритма. 

##### Цели:

- **Упорядочивание данных:**
    Организация данных в определенном порядке для удобства восприятия и обработки. 

- **Повышение эффективности поиска:**
    Ускорение процесса поиска нужных элементов в отсортированном списке.

- **Оптимизация обработки данных:**
    Обеспечение возможности выполнения операций над данными в определенном порядке. 

- **Подготовка данных для дальнейшей обработки:**
    Некоторые алгоритмы требуют отсортированные данные для своей работы.
# Сортировка массива прямым включением.
Для каждого элемента двигаем влево до тех пор, пока не встанет на свое место или в начало.

![[Pasted image 20250711134135.png]]
## Сортировка вставками
```cpp
for(int i = 1; i < n; ++i){
	for(int j = i; j > 0; --j){
		if(arr[j] < arr[j-1])
			swap(arr, j, j-1);
		else
			break;
	}
}
```

# 7. Алгоритм сортировки двоичным включением – модификация прямого включения. Блок-схема.

Можно ускорить сортировку вставками (включением): Быстро найти место вставки т.к. массив отсортирован (Использовать бинарный поиск)
```cpp
// Сортировка бинарными вставками
void bin_insert(int a[], int n) {
    int i, j, m, R, L, x;
    
    for (i = 1; i < n; i++) {
        x = a[i];
        L = 0;
        R = i;
        
        while (L < R) {
            m = (L + R) / 2; // Находим индекс среднего элемента
            if (a[m] <= x) {
                L = m + 1;
            } else {
                R = m;
            }
        }
        
        // Сдвигаем массив с позиции R до i-1 на одну позицию вправо
        for (j = i; j > R; j--) {
            a[j] = a[j - 1];
        }
        
        a[R] = x;
    }
}
```
# 8. Сортировка массива прямым выбором (блок-схема алгоритма).
Проходим от 1го до N, находим справа от i минимальный и меняем его с концом отсортированной последовательности слева.
![[Pasted image 20250710201850.png]]

```cpp
void swap(int *arr, int i, int j){
	int t = arr[i];
	arr[i] = arr[j];
	arr[j] = t;
}

int[n] arr;

for(int j = 0; j < n; ++j){
	int minI = j;
	for (int i = minI; i < n; ++i){
		if(arr[i] < arr[minI])
			minI = i;
	}
	swap(arr, j, minI);
}
```

# 9. Сортировка массива с помощью прямого обмена (пузырьковая сортировка)- блок-схема алгоритма.
![[Pasted image 20250711141826.png]]
Сложность: $O(n^2)$

```cpp
int[] arr;
for(int i = n; i > 0; --i){
	for(int j = 1; j < i; ++j){
		if (arr[j-1] > arr[j])
			swap(arr, j-1, j);
	}
}
```

Можно завершить, если перестановок не было
# 10. Алгоритм шейкерной сортировки (блок-схема алгоритма). 
```cpp
int[] arr;
for(int i = n; i > 0; --i){
	int k = 1;
	for(int j = k; j < i; ++j){
		if (arr[j-1] > arr[j])
			swap(arr, j-1, j);
	}

	for(int l = i-1; l > k; --l){
		if(arr[l] < arr[l-1])
			swap(arr, l, l-1);
	}
}
```



# 11. Улучшенный метод сортировки – сортировка Шелла (блок-схема алгоритма).
Основная идея алгоритма заключается в сортировке элементов массива, отстоящих друг от друга на расстоянии h. Этот процесс называется h-сортировкой или сортировкой с уменьшающимися расстояниями.

Каждая h-сортировка программируется как сортировка простыми вставками. Затем h уменьшается и повторяется сортировка заново. Процесс заканчивается, когда h уменьшается до 1.

```cpp
for(int h = K; h <= 1; --h){
	for(int i = h; i < n; ++i){
		for(int j = i; j > 0; j -= h){
			if(arr[j] < arr[j-h])
				swap(arr, j, j-h);
			else
				break;
		}
	}
}
```

# 12. Сортировка деревом. Сдвигающий алгоритм Флойда и его применение для построения пирамиды и получения упорядоченности элементов с помощью пирамиды.
```cpp

void heapify(int arr[], int n, int i) {
    int largest = i;  // Инициализируем наибольший элемент как корень
    int l = 2*i + 1;  // левый = 2*i + 1
    int r = 2*i + 2;  // правый = 2*i + 2

    // Если левый дочерний элемент больше корня
    if (l < n && arr[l] > arr[largest])
        largest = l;

    // Если правый дочерний элемент больше, чем самый большой элемент на данный момент
    if (r < n && arr[r] > arr[largest])
        largest = r;

    // Если самый большой элемент не корень
    if (largest != i) {
        swap(arr[i], arr[largest]);
        // Рекурсивно преобразуем в двоичную кучу затронутое поддерево
        heapify(arr, n, largest);
    }
}

// Основная функция для пирамидальной сортировки
void heapSort(int arr[], int n) {
    // Построение кучи (перестраиваем массив)
    for (int i = n / 2 - 1; i >= 0; i--)
        heapify(arr, n, i);

    // Один за другим извлекаем элементы из кучи
    for (int i=n-1; i>=0; i--) {
        // Перемещаем текущий корень в конец
        swap(arr[0], arr[i]);
        // Вызываем heapify на уменьшенной куче
        heapify(arr, i, 0);
    }
}
```
Процесс сортировки
5.	Построение пирамиды из исходного массива
6.	Извлечение максимального элемента из корня
7.	Замена его последним элементом
8.	Восстановление свойства пирамиды
9.	Повторение шагов 2-4



# 13. Сортировка с помощью разделения – QuickSort, (блок – схема разделения и ее рекурсивное использование в общей процедуре QuickSort).
$O(n\log{n})$

```cpp
int[] arr;

//Хоара (любой элемент)

// Способ выбора Ломуто
void partition(int *arr, int i, int j){ // i | pivot
	int pivot = j;
	int low = i;
	for(int i = low; i < pivot; ++i){
		if(arr[i] < arr[pivot]){
			swap(arr, i, low);
			low++;
		}
	}
	swap(arr, pivot, low);
	return low;
}

void quick_sort(int *arr, int j, int k){
	if(j >= k) return
	int i = partition(arr, j, k);
	quick_sort(arr, j, i-1);
	quick_sort(arr, i+1, k);
}

quick_sort(arr, 0, n-1);
```

# 14. Сортировка последовательностей. Прямое слияние (рекурсивный алгоритм)
*Merge Sort* — это эффективный алгоритм сортировки, основанный на принципе «разделяй и властвуй».

**Принцип работы**
1.	Разделение последовательности на две равные части
2.	Рекурсивная сортировка каждой части
3.	Слияние отсортированных частей в единую последовательность

##### Характеристики
**Временная сложность:**
•	O(n log n) — в среднем и худшем случае
•	O(n log n) — в лучшем случае

**Особенности:**
•	Устойчивая сортировка
•	Требует дополнительной памяти O(n)
•	Эффективна для больших массивов

Реализация на C++
```cpp
// Слияние двух отсортированных подмассивов
void merge(int arr[], int left, int mid, int right) {
    int n1 = mid - left + 1;  // размер левой части
    int n2 = right - mid;     // размер правой части

    // Временные массивы
    int* L = new int[n1];
    int* R = new int[n2];

    // Копируем данные во временные массивы
    for (int i = 0; i < n1; ++i)
        L[i] = arr[left + i];
    for (int j = 0; j < n2; ++j)
        R[j] = arr[mid + 1 + j];

    // Сливаем временные массивы обратно в arr[left..right]
    int i = 0, j = 0, k = left;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j])
            arr[k++] = L[i++];
        else
            arr[k++] = R[j++];
    }

    // Копируем оставшиеся элементы
    while (i < n1)
        arr[k++] = L[i++];
    while (j < n2)
        arr[k++] = R[j++];

    // Освобождаем временные массивы
    delete[] L;
    delete[] R;
}

// Рекурсивная сортировка слиянием
void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        int mid = (left + right) / 2;

        // Сортируем две половины
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);

        // Сливаем отсортированные половины
        merge(arr, left, mid, right);
    }
}

mergeSort(arr, 0, size - 1);

```

# 15. Рекурсия в алгоритмах. Организация и эффективность применения. Пример рекурсивного алгоритма.
*Рекурсия* — это метод решения задач, при котором функция вызывает сама себя для решения меньших подзадач.
### Основные понятия
**Базис рекурсии** — условие остановки рекурсивных вызовов
**Рекурсивное условие** — часть алгоритма, где происходит вызов функции
**Глубина рекурсии** — количество вложенных вызовов функции

### Преимущества рекурсии
**Простота реализации** сложных алгоритмов
**Читаемость кода** — часто более понятное описание задачи
**Естественность** для некоторых математических задач

### Недостатки рекурсии
**Затраты памяти** — каждый вызов занимает место в стеке
**Производительность** — накладные расходы на вызовы функций
**Переполнение стека** при большой глубине рекурсии

### Организация рекурсивных алгоритмов
Основные компоненты:
1.    Проверка базового случая
2.    Рекурсивный случай
3.    Возврат результата

Имеется специальный тип рекурсии, называемый «*хвостовой рекурсией*» (структура рекурсивного алгоритма такова, что рекурсивный вызов является последней выполняемой операцией в функции, а его результат непосредственно возвращается в качестве результата функции).

# 16. Полустатические структуры данных – организация очереди, стека, дека. Программирование элементарных операций.

## Стек
Last
In
First
Out

`push(s, v)` добавить в конец
`pop(s)` удалить с конца

```cpp
struct Stack{
	int data[100];
	int last;
	
}

Stack CreateStack(){
	Stack s;
	s.last = 0;
	return s;
}

bool Push(Stack* s, int v){
	if (s->last < sizeof(s->data)/sizeof(int)){
		s->data[s->last] = v;
		s->last++;
		return true;
	}
	return false;
}

Push(&s, 42);
Push(&s, 69);

bool Pop(Stack* s){ 
	if(s->last > 0){
		s->last--;
		return true;
	}
	return false;
}

int TopValue(Stack* s);

bool Empty(Stack *s){
	return s->last == 0;
}

// На основе списка
struct Stack{
	Node *head;
}

void Push(Stack *s, int v){ //FIXME: update s->head
	insert(s->head, nullptr, v);
}

void Pop(Stack *s){ //FIXME: update s->head
	remove(s->head, nullptr);
}
```

## Очередь
First
In
First
Out

```cpp
struct Queue{
	int data[100];
	int last;
	int first;
	int lenght = 100;
}

если ласт бкдет совпадать с ферст, ферст = -1. 
bool Push(Queue *q, int v){
	if((q->last + 1) % q->length != q->first){ 
		q->data[q->last] = v;
		q->last = (q->last+1) % q->lenght;
		return true;
	}
	return false;
}

bool Pop(Queue *q){
	q->first = (q->first + 1) % q->lenght;
	return true;
}
```

На основе списка
```cpp
struct Queue{
	Node *head;
	Node *tail;
}

void Push(Queue *q, int v){
	q->tail = insert(q->head, q->tail, v);
}

void Pop(Queue *q){
	new_head = q->head->next;
	remove(q->head, q->tail);
	q->head = new_head;
}
```

## Дек
Двухсторонняя очередь 
```cpp
struct Deck {
    int data[100];
    int first = -1;
    int last = 0;
    int length = 100;
};

// Проверка: дек пуст
bool isEmpty(Deck* d) {
    return d->first == -1;
}

// Добавить в конец
bool PushBack(Deck* d, int v) {
    if ((d->last + 1) % d->length == d->first) return false; // переполнение

    if (isEmpty(d)) {
        d->first = d->last = 0;
    } else {
        d->last = (d->last + 1) % d->length;
    }

    d->data[d->last] = v;
    return true;
}

// Добавить в начало
bool PushFront(Deck* d, int v) {
    if ((d->last + 1) % d->length == d->first) return false; // переполнение

    if (isEmpty(d)) {
        d->first = d->last = 0;
    } else {
        d->first = (d->first - 1 + d->length) % d->length;
    }

    d->data[d->first] = v;
    return true;
}

// Удалить с начала
bool PopFront(Deck* d) {
    if (isEmpty(d)) return false;

    if (d->first == d->last) {
        d->first = -1;
    } else {
        d->first = (d->first + 1) % d->length;
    }

    return true;
}

// Удалить с конца
bool PopBack(Deck* d) {
    if (isEmpty(d)) return false;

    if (d->first == d->last) {
        d->first = -1;
    } else {
        d->last = (d->last - 1 + d->length) % d->length;
    }

    return true;
}
```


# 17. Организация линейного списка. Программирование элементарных операций: включение и исключение элементов, проход по списку.
## Список
1. не рядом в памяти
2. Динамическая структура

Между узлами связь может быть односторонней (Односвязный)
Туда - обратно (Двусвязный)

```cpp
struct Node{
	int value;
	Node *next;
}

Node *NewNode(int n){
	Node *node = new Node();
	node->value = n;
	node->next = nullptr;
	return node;
}

void DeleteNode(Node *node){
	if(node != nullptr)
		delete node;
}

Node *head;
while (head->next != nullptr){ // Проход
	head = head->next;
}
```

Сложность $O(n)$

```cpp
// Helps to get length more easily
struct List{
	Node *head;
	int count;
}
```

#### Вставка
```cpp
Node *insert(Node *head, Node *p, int xVal){
	// p - после которого хотим вставить, ести null => в начало
	if(p == nullptr){
		Node *x = NewNode(xVal);
		x->next = head;
		return x;
	}
	
	Node *x = NewNode(xVal);
	x->next = p->next;
	p->next = x;
	return x;
}

insert(head, nullptr, 42); // to insert first
```

#### Удаление
```cpp
void Remove(Node *head, Node *p){
	Node *x = p->next;
	if (p == nullptr){
		if (head != nullptr){
			DeleteNode(head);
			return;
		}
	}
	if (x != nullptr){
		p->next = x->next;
		DeleteNode(x);
	}
}
```

# 18 Линейный упорядоченный список, на примере построения алфавитно-частотного словаря.

Двусвязные
```cpp
// Узел списка
struct Node {
    string word;
    int frequency;
    Node* next;
};

// Вставка слова в упорядоченный список
void insertOrdered(Node*& head, const string& word) {
    Node* current = head;
    Node* prev = nullptr;

    // Поиск места вставки или существующего слова
    while (current && current->word < word) {
        prev = current;
        current = current->next;
    }

    // Если слово уже есть — увеличиваем частоту
    if (current && current->word == word) {
        current->frequency++;
        return;
    }

    // Создаем новый узел
    Node* newNode = new Node{word, 1, current};

    // Вставка в начало списка
    if (!prev) {
        head = newNode;
    } else {
        prev->next = newNode;
    }
}

// Освобождение памяти
void deleteList(Node* head) {
    while (head) {
        Node* temp = head;
        head = head->next;
        delete temp;
    }
}
```

# 19 Двусвязные списки; алгоритм поиска и включения в упорядоченном списке.
```cpp
// Структура узла двусвязного списка
struct Node {
    int data;
    Node* prev;
    Node* next;
};

// Вставка в упорядоченном порядке (по возрастанию)
void insertSorted(Node*& head, int value) {
    Node* newNode = new Node{value, nullptr, nullptr};

    // Пустой список или вставка в начало
    if (!head || value < head->data) {
        newNode->next = head;
        if (head)
            head->prev = newNode;
        head = newNode;
        return;
    }

    Node* current = head;
    while (current->next && current->next->data < value)
        current = current->next;

    newNode->next = current->next;
    newNode->prev = current;

    if (current->next)
        current->next->prev = newNode;
    current->next = newNode;
}

// Поиск элемента по значению
Node* search(Node* head, int value) {
    Node* current = head;
    while (current && current->data <= value) {
        if (current->data == value)
            return current;
        current = current->next;
    }
    return nullptr;
}

// Вывод списка
void printList(Node* head) {
    Node* current = head;
    while (current) {
        cout << current->data << " ";
        current = current->next;
    }
    cout << endl;
}

// Освобождение памяти
void freeList(Node*& head) {
    Node* current = head;
    while (current) {
        Node* next = current->next;
        delete current;
        current = next;
    }
    head = nullptr;
}
```
# 20. Динамические структуры – реальные структуры данных. Моделирование кольцевой очереди, кольцевого стека.
Уже было. Если надо прям динамические, то на основе связного списка

# 21. Структура данных куча. Основные операции.

```
        82
       /  \
     52    78
    /  \   /  \
  17  34 42   77
              / \
             15  4


```
Куча

```

82 78 52 77 42 17 34 15 4
       i
      / \
  2i+1  2i+2
```

```cpp
struct Heap{
	int keys[100];
	int length;
}

void Heapify(Heap *h, int i){ // ставим вместо i больший из 3х элементов: i и его 2х детей
	int left = 2*i+1;
	int right = 2*i+2;
	int max = i;
	if (left < h->lenght && h->keys[left] > h->keys[max]){
		max = left;
	}
	if (right < h->lenght && h->keys[right] > h->keys[max]){
		max = right;
	}
	if (max != i){
		swap(h->data, i, max); // Если АЙ не больший, то меняем с большим, и рекурсивно вызываем для большего, в котором АЙ
		Heapify(h, max);       // Потому что там мог разрушиться порядок
	}
}

void BuildHeap(Heap *h){ // O(n)
	for(int i = h->lenght/2; i >= 0; --i){ // Для каждого листа
		Heapify(h, i);
	}
}

void IncreasKey(Heap *h, int i, int key){
	h->keys[i] = key;
	int parent = (i - 1)/2;
	while (i > 0 && h->keys[i] > h->keys[parent]){
		swap(h->data, i, parent);
		i = parent;
		parent = (i-1)/2;
	}
}

void Insert(Heap *h, int key){
	h->lenght++;
	h->keys[h->lenght-1] = -1;
	IncreaseKey(h, h->lenght-1, key);
}

int ExtractMax(Heap *h){
	int max = h->keys[0];
	h->keys[0] = h->keys[h->lenght - 1];
	h->length--;
	Heapify(h, 0);
	return max;
}
```

#### Пирамидальная сортировка
$O(n\log{n})$

```cpp
for (int i = 0; i != h->length; ++i){
	int max = ExtractMax(h);
	h->keys[h->lenght-1] = max;
}
```

# 22. АТД очередь с приоритетами: основные операции.
*АТД "Очередь с приоритетами" (Priority Queue)* — это абстрактный тип данных, который хранит элементы с учётом их приоритета и поддерживает эффективное извлечение элемента с **наивысшим** (или **наинизшим**) приоритетом.  

### Основные операции
1. **`Insert` (Добавление)**  
   - Вставляет элемент с указанным приоритетом.  
   - Аналог `enqueue` в обычной очереди.  

2. **`ExtractMax` / `ExtractMin` (Извлечение максимума/минимума)**  
   - Возвращает и удаляет элемент с наивысшим (или наинизшим) приоритетом.  
   - Аналог `dequeue`, но с учётом приоритета.  

3. **`Peek` / `GetMax` / `GetMin` (Просмотр)**  
   - Возвращает элемент с максимальным/минимальным приоритетом **без удаления**.  

4. **`ChangePriority` (Изменение приоритета)**  
   - Меняет приоритет существующего элемента (есть не во всех реализациях).  

5. **`IsEmpty` (Проверка на пустоту)**  
   - Возвращает `true`, если очередь пуста.  

6. **`Size` (Размер очереди)**  
   - Возвращает количество элементов.  

# 23. Деревья. Основные понятия. Двоичные деревья. Пример построения идеально сбалансированного дерева.

**Дерево** — это рекурсивная структура данных, состоящая из **узлов (nodes)**, связанных между собой **рёбрами (edges)**. Каждое дерево имеет **корневой узел (root)** и **дочерние узлы (children)**, которые могут быть поддеревьями. Узлы без детей называются **листьями (leaves)**.

*Высота дерева* - максимальный уровень узла.
*Степень вершины* - кол-во детей
*Степень дерева* - макс. степень вершины

Кучи бывают:
*Однородные* - все вершины одного рода (типа). *Разнородные* - наоборот
*Упорядоченные* - узлы по правилам размещаются (куча - не строгий порядок)

##### Графическое и логическое представление
Текстовое (a b ( e f ))
Отступами:
```
a
	b
	c
		d
	d
```

#### Двоичное дерево (степень 2)
Строго двоичное дерево - все вершины кроме листьев имеют степень 2

*Совершенное двоичное дерево* - строго двоичное дерево все листья которого расположены на одном уровне.

*Идеально сбалансированное дерево* — дерево, где **высота** левого и правого поддеревьев различается не более чем на 1.
```
    // идеально сбалансированное дерево:
    //       4
    //     /   \
    //    2     6
    //   / \   / \
    //  1   3 5   7
```

левый меньше корня, правый больше корня

# 24. Основные операции с двоичными деревьями. Способы обхода.
##### Обход дерева
```
    //       a
    //     /   \
    //    b     c
    //   / \    |
    //  d   e   f
    //      |  / \
    //      g h   i
```

- Сверху вниз (прямой) (root, left, right) (ABDEGCFHI)
- Слева направо (симметричный) (left, root, rigth) (DBGEAHFIC)
- Снизу вверх (обратный) (left, rigth, root) (DGEBHIFCA)



операции
- поиск ( идеально сбаллансированное двоичное дерево поиск $O(\log{n})$ )
- добавление элемента
- удаление элемента
# 25. Алгоритм поиска по ключу в двоичном дереве. Алгоритм поиска и включения элемента в двоичное дерево (рекурсивный).
```cpp
// Узел дерева
struct Node {
    int key;
    Node* left;
    Node* right;
};

// Рекурсивный поиск по ключу
Node* search(Node* root, int key) {
    if (!root || root->key == key)
        return root;
    if (key < root->key)
        return search(root->left, key);
    else
        return search(root->right, key);
}

// Рекурсивная вставка в BST
Node* insert(Node* root, int key) {
    if (!root) {
        Node* newNode = new Node{key, nullptr, nullptr};
        return newNode;
    }

    if (key < root->key)
        root->left = insert(root->left, key);
    else if (key > root->key)
        root->right = insert(root->right, key);
    // Если key == root->key — не вставляем дубликат (можно изменить при необходимости)

    return root;
}
```
# 26. Алгоритм исключения элемента из двоичного дерева (рекурсивный).
```cpp
// Структура узла дерева
struct Node {
    int key;
    Node* left;
    Node* right;
};

// Рекурсивная вставка
Node* insert(Node* root, int key) {
    if (!root)
        return new Node{key, nullptr, nullptr};
    if (key < root->key)
        root->left = insert(root->left, key);
    else if (key > root->key)
        root->right = insert(root->right, key);
    return root;
}

// Поиск минимального узла (используется при удалении)
Node* findMin(Node* root) {
    while (root && root->left)
        root = root->left;
    return root;
}

// Рекурсивное удаление узла по ключу
Node* remove(Node* root, int key) {
    if (!root) return nullptr;

    if (key < root->key)
        root->left = remove(root->left, key);
    else if (key > root->key)
        root->right = remove(root->right, key);
    else {
        // Найден узел для удаления
        if (!root->left && !root->right) {
            delete root;
            return nullptr;
        }
        else if (!root->left) {
            Node* temp = root->right;
            delete root;
            return temp;
        }
        else if (!root->right) {
            Node* temp = root->left;
            delete root;
            return temp;
        }
        // Случай с двумя детьми
        Node* temp = findMin(root->right);
        root->key = temp->key;
        root->right = remove(root->right, temp->key);
    }
    return root;
}
```


# 27. Сбалансированные АВЛ - деревья. Включение элемента и балансировка дерева (блок – схемы балансирующих поворотов). И 28. Исключение элемента из АВЛ – дерева; балансирующие повороты

Я ни черта не понимаю. Как же здорово, что материал на три пары можно уложить в одну, правда?)))))

При добавлении влево возможны случаи:

I:
	до     Hr < Hl
	после (Hr = Hl) | ничего не изменилось

II:
	до     Hl = Hr
	после (Hl - Hr = 1) | ничего не изменилось

III:
	до     Hl > Hr
	после (Hl - Hr = 2) | ничего не изменилось

![[Pasted image 20250713171030.png]]

```cpp
struct Node {
    int key;
    int height;
    Node* left;
    Node* right;

    Node(int k) : key(k), height(1), left(nullptr), right(nullptr) {}
};

int height(Node* node) {
    return node ? node->height : 0;
}

void updateHeight(Node* node) {
    if (node)
        node->height = 1 + max(height(node->left), height(node->right));
}

int getBalance(Node* node) {
    return node ? height(node->left) - height(node->right) : 0;
}

Node* rightRotate(Node* y) {
    Node* x = y->left;
    Node* T2 = x->right;

    x->right = y;
    y->left = T2;

    updateHeight(y);
    updateHeight(x);

    return x;
}

Node* leftRotate(Node* x) {
    Node* y = x->right;
    Node* T2 = y->left;

    y->left = x;
    x->right = T2;

    updateHeight(x);
    updateHeight(y);

    return y;
}

Node* leftRightRotate(Node* node) {
    node->left = leftRotate(node->left);
    return rightRotate(node);
}

Node* rightLeftRotate(Node* node) {
    node->right = rightRotate(node->right);
    return leftRotate(node);
}

// Вставка с балансировкой
Node* insert(Node* node, int key) {
    if (!node)
        return new Node(key);

    if (key < node->key)
        node->left = insert(node->left, key);
    else if (key > node->key)
        node->right = insert(node->right, key);
    else
        return node; // дубликаты не вставляем

    updateHeight(node);

    int balance = getBalance(node);

    // LL
    if (balance > 1 && key < node->left->key) / перекос влево и добавляли влево
        return rightRotate(node);

    // RR
    if (balance < -1 && key > node->right->key) перекос вправо и добавляли вправо
        return leftRotate(node);

    // LR
    if (balance > 1 && key > node->left->key) перекос влево но добавляли вправо
        return leftRightRotate(node);

    // RL
    if (balance < -1 && key < node->right->key) перекос право но добавляли влево
        return rightLeftRotate(node);

    return node;
}

Node* findMin(Node* node) {
    while (node && node->left)
        node = node->left;
    return node;
}

// Удаление с балансировкой
Node* remove(Node* root, int key) {
    if (!root)
        return root;

    if (key < root->key)
        root->left = remove(root->left, key);
    else if (key > root->key)
        root->right = remove(root->right, key);
    else {
        if (!root->left || !root->right) { // Лучше расписать по нормальному на два уловия
            Node* temp = root->left ? root->left : root->right;
            if (!temp) {
                temp = root;
                root = nullptr;
            } else {
                *root = *temp; // копируем содержимое
            }
            delete temp;
        } else {
            Node* temp = findMin(root->right);
            root->key = temp->key;
            root->right = remove(root->right, temp->key);
        }
    }

    if (!root)
        return root;

    updateHeight(root);

    int balance = getBalance(root);

    // LL
    if (balance > 1 && getBalance(root->left) >= 0)
        return rightRotate(root);

    // LR
    if (balance > 1 && getBalance(root->left) < 0)
        return leftRightRotate(root);

    // RR
    if (balance < -1 && getBalance(root->right) <= 0)
        return leftRotate(root);

    // RL
    if (balance < -1 && getBalance(root->right) > 0)
        return rightLeftRotate(root);

    return root;
}
```


