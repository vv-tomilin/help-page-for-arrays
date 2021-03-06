# Шпаргалка по работе с массивами в JavaScript
   
   
Ссылка на документацию **MDN** [со всеми методами массивов](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array)

Ссылка на материал на основе которого составлялась шпаргалка [смотреть](https://learn.javascript.ru/array-methods)
   
   
   
## Для перебора элементов

***
### ```forEach(func)``` – вызывает func для каждого элемента. Ничего не возвращает

Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

* Ничего не возвращает
* Выполняет функцию callback один раз для каждого элемента, находящегося в массиве в порядке возрастания индекса
* Функция callback не будет вызвана для удалённых или пропущенных элементов массива. Однако, она будет вызвана для элементов, которые присутствуют в массиве и имеют значение undefined
* Принимает 2 аргумента:
    * ```callback``` - Функция обратного вызова, которая будет выполнена один раз для каждого элемента в массиве. 
        - Функция принимает следующие параметры:
           * currentValue – значение текущего элемента
           * index – индекс массива текущего элемента (необязательный)
           * arr – массив, к которому принадлежит текущий элемент (по которому осуществляется проход)(необязательный)
    * ```thisValue```(необязательный параметр) - объект, на который может ссылаться ключевое слово this в функции callback. Если аргумент thisValue опущен, в качестве значения this используется undefined (в конечном счете this будет зависеть от обычных правил контекста выполнения функции).

> Примечание: Метод forEach не вызывает функцию для элементов массива, которые не имеют значений.

> Примечание: Помимо объектов массива, метод forEach может использоваться любым объектом, имеющим свойство length и обладающим численно проиндексированными именами свойств.

*Синтаксис:*

 ```javascript
 array.forEach(callback(currentValue, index, arr),thisValue);
 ```

Ссылка [на примеры](http://code.mu/ru/javascript/book/prime/enumeration/forEach/)
***


## Для преобразования массива

***
### ```map(func)``` – создаёт новый массив из результатов вызова func для каждого элемента

Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

* Позволяет применить заданную функцию для каждого элемента массива. При этом метод не изменяет исходный массив, а возвращает измененный
* В аргументы получает функцию, которая выполнится для каждого элемента массива. То, что вернет эта функция через return для элемента массива, станет новым значением этого элемента. Вторым необязательным аргументом принимает настройку контекста
* Аргументы: 
    * ```callback``` - Функция, вызываемая для каждого элемента массива arr. Каждый раз, когда callback выполняется, возвращаемое значение добавляется в new_array.
        - Функция callback, создающая элемент в новом массиве, принимает три аргумента:
            * currentValue - текущий обрабатываемый элемент массива
            * index (необязательный) - индекс текущего обрабатываемого элемента в массиве
            * array (необязательный) - массив, по которому осуществляется проход
    * ```thisArg``` - Необязательный параметр. Значение, используемое в качестве this при вызове функции callback

Ссылка [на примеры](http://code.mu/ru/javascript/manual/array/map/)
***

### ```sort(func)``` – сортирует массив «на месте», а потом возвращает его

Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

* Сортирует элементы массива на месте без создания копии массива
* Если sort() вызывается без аргументов, элементы массива располагаются в алфавитном порядке (точнее, на основе сравнения ASCII-кодов символов значений)
* Чтобы отсортировать массив, sort() вызывает функцию приведения типов String() для каждого элемента, а затем сравнивает возвращенные строки. Это происходит, даже если массив содержит только числа

     > **Пример:** 
     > ```javascript
     > var  values  =  [0, 1, 5, 10, 15];
     > values.sort();  
     > alert( values ); // [0, 1, 10, 15, 5]
     > ```

*Синтаксис:*

 ```javascript
 array.sort();
 ```

Ссылка на ресурс [по правилному применению](https://webformyself.com/raskryvaem-tajnu-javascript-sort/) метода и его нюансы
Ссылка [на примеры](https://wm-school.ru/js/array_sort.php)

***
### ```reverse()``` – «на месте» меняет порядок следования элементов на противоположный и возвращает изменённый массив

Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse)

* На месте обращает порядок следования элементов массива. Первый элемент массива становится последним, а последний — первым
* Возвращает изменённый массив с обратным порядком следования его элементов

> На заметку: При использовании метода reverse() новый массив не создается, а возвращается ссылка на текущий уже измененный массив 

*Синтаксис:*

 ```javascript
 array.reverse();
 ```
 
Ссылка [на примеры](https://wm-school.ru/js/array_reverse.php)

***

### ```split()``` - осуществляет разбиение строки в массив по указанному разделителю

> `НЕ ЯВЛЯЕТСЯ МЕТОДОМ МАССИВА !!! 
> ПРИМЕНЯЕТСЯ К СТРОКОВЫМ ОБЬЕКТАМ`

Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/String/split)

* Результатом применения метода является массив строк, разделенных там, где в строке string встречается separator. Аргумент separator не возвращается как часть какого-либо элемента массива
* Принимает 2 аргумента: 
       * ```separator``` - строка или регулярное выражение, по которому разбивается строка 
       * ```limit``` - Необязательный параметр. Целое число, определяющее ограничение на количество найденных подстрок. Метод split() всё равно разделяет строку на каждом сопоставлении с разделителем separator, но обрезает возвращаемый массив так, чтобы он содержал не более limit элементов
      

> Примечание: Если строка является пустой строкой, метод split() вернёт массив, состоящий из одной пустой строки, а не пустой массив.

*Синтаксис:*

 ```javascript
 string.split(separator, limit);
 ```

Ссылка [на примеры](http://code.mu/ru/javascript/manual/string/split/)

***
### ```join(separator)``` - преобразует все элементы массива в строки, объединяет их и возвращает получившуюся строку

Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/join)

* Принимает 1 необязательный аргумент `separator` - определяет строку, разделяющую элементы массива. В случае необходимости тип разделителя приводится к типу Строка. Если он не задан, элементы массива разделяются запятой ','. Если разделитель - пустая строка, элементы массива ничем не разделяются в возвращаемой строке
* Преобразует каждый из элементов массива в строку и затем выполняет конкатенацию этих строк, вставляя указанный разделитель между элементами. Метод возвращает результирующую строку. Элемент массива с типом undefined или null преобразуется в пустую строку.

*Синтаксис:*

 ```javascript
 string.split(separator, limit);
 ```
 
 Ссылка [на примеры](https://wm-school.ru/js/array_join.php)
 
 
***
### ```reduce(func, initial)``` – вычисляет одно значение на основе всего массива, вызывая func для каждого элемента и передавая промежуточный результат между вызовами

Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

* Применяет функцию к аккумулятору и каждому значению массива (слева-направо), сводя его к одному значению
* Возвращает накопленный результат с последнего вызова функции обратного вызова
* Используется для вычисления на основе массива какого-либо единого значения, иначе говорят «для свёртки массива»
* Применяет функцию `callback` по очереди к каждому элементу массива слева направо, сохраняя при этом промежуточный результа
* Аргументы: 
        * ```callback``` - функция, выполняющаяся для каждого элемента массива, принимает четыре аргумента:
               * `total` – значение из предыдущего вызова функции обратного вызова. Если значение `initialValue` предоставляется в метод `reduce`, то `total` является значением initialValue при первом вызове функции
               * `currentValue` – текущий обрабатываемый элемент массива
               * `currentIndex` – индекс текущего обрабатываемого элемента массива (необязательный)
               * `arr` – массив, к которому принадлежит текущий элемент (по которому происходит проход)(необязательный)
        * ```initialValue``` - Необязательный параметр. Объект, используемый в качестве первого аргумента при первом вызове функции `callback`
* При первом вызове функции, параметры `total` и `currentValue` могут принимать одно из двух значений:
        * Если при вызове `reduce()` передан аргумент `initialValue`, то значение `total` будет равным значению `initialValue`, а значение `currentValue` будет равным первому значению в массиве
        * Если аргумент `initialValue` не задан, то значение `total` будет равным первому значению в массиве, а значение `currentValue` будет равным второму значению в массиве
* Если массив пустой, а аргумент `initialValue` не указан, то будет сгенерировано исключение `TypeError`
* В случае, если массив состоит только из одного элемента и аргумент `initialValue` не указан, или если аргумент `initialValue` указан, но массив пустой, то будет возвращено одно это значение. При этом функции `callback` вызываться не будет
* При отсутствии аргумента `initialValue` в качестве первого значения берётся первый элемент массива, а перебор элементов начинается со второго

*Синтаксис:*

 ```javascript
 array.reduce(function callback(total, currentValue, currentIndex, arr), initialValue);
 ```
 
***Полезная [статья](https://medium.com/@stasonmars/как-работает-reduce-в-javascript-когда-его-нужно-применять-и-какие-крутые-вещи-можно-с-ним-b650c397bee6) про метод.***
 
 Ссылка [на примеры](https://wm-school.ru/js/array_reduce.php)
 Ссылка [на примеры](http://code.mu/ru/javascript/manual/array/reduce/)
 
***


## Для добавления/удаления элементов: 

***
### ```push (...items)``` – добавляет элементы в конец

Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/push)

* Возвращает новую длину массива (новое значение свойства length того массива, для которого был вызван метод)
* Присоединяет значения к массиву (в конец)
* Изменяет исходный массив, а не создаёт его модифицированную копию
* В аргументы принимает элементы, добавляемые в конец массива. Элементы добавляются в том порядке, в котором они были переданы методу


*Синтаксис:*

 ```javascript
 arr.push(element1, ..., elementN);
 ```

***

### ```pop()``` – извлекает элемент с конца

Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)

* Удаляет последний элемент из массива и возвращает его значение (или undefined, если массив пуст)
* Изменяет исходный массив, а не создаёт его модифицированную копию
* В аргументы ничего не принимает

*Синтаксис:*

 ```javascript
 arr.pop();
 ```
 ***
 
 ### ```shift()``` – удаляет первый элемент из массива и возвращает его значение
 
 Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)
 
 * Удаляет первый элемент массива, уменьшает индекс всех последующих элементов на единицу, уменьшает длину массива и возвращает удалённое им значение (или undefined, если массив пуст)
 * Изменяет исходный массив, а не создаёт его модифицированную копию
 * В аргументы ничего не принимает

*Синтаксис:*

 ```javascript
 arr.shift();
 ```
 ***
 
 ### ```unshift(...items)``` – добавляет один или более элементов в начало массива и возвращает новую длину массива
 
 Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)
 
 * Добавляет один или более элементов в начало массива и возвращает новую длину массива
 * Индексы всех элементов, изначально присутствующих в массиве, увеличиваются на единицу (если методу был передан всего один аргумент) или на число, равное количеству переданных аргументов
 * Изменяет исходный массив, а не создаёт его модифицированную копию
 * В аргументы принимает элементы, добавляемые в начало массива. Элементы добавляются в том порядке, в котором они были переданы методу

*Синтаксис:*

 ```javascript
 arr.unshift(element1, ..., elementN);
 ```

***

### ```splice(pos, deleteCount, ...items)``` – начиная с индекса pos, удаляет deleteCount элементов и вставляет items

Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/splice#syntax)

* Метод splice удаляет или добавляет элементы в массив. Можно только удалять элементы, только добавлять или делать и то и другое одновременно
* Метод изменяет сам массив и возвращает при этом массив удаленных элементов
* Первым параметром метод принимает номер элемента массива, который нужно удалить. Вторым параметром - сколько элементов массива следует удалить. Если его поставить в 0 - то элементы удалены не будут (только добавлены новые)
* Дальше через запятую идут элементы, которые нужно добавить в массив (являются необязательными параметрами). Эти элементы добавятся вместо удаленных элементов массива
* Если удаления не было (когда второй параметр 0) - элементы вставятся в массив начиная с той позиции, которая указана первым параметром метода
* Первый параметр может иметь отрицательное значение. В этом случае отсчет позиции начнется не с начала массива, а с конца. Причем, последний элемент имеет номер -1, предпоследний -2 и так далее

***Схема:***

*массив.splice(откуда удаляем, сколько элементов удаляем, [вставить элемент], [вставить элемент]...);*

*Синтаксис:*

 ```javascript
 arr.splice(pos, deleteCount, ...items);
 ```
 
 Ссылка [на примеры](http://code.mu/ru/javascript/manual/array/splice/)

***

### ```slice(start, end)``` – создаёт новый массив, копируя в него элементы с позиции start до end (не включая end)

Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

* Используется для копирования указанного участка из массива и возвращает новый массив содержащий скопированные элементы. Исходный массив при этом не меняется
* Принимает два аргумента, которые определяют начало и конец возвращаемого участка массива
* Копирует участок массива, начиная от start до end, не включая end
* Если указан только один аргумент, возвращаемый массив будет содержать все элементы от указанной позиции до конца массива
* Можно использовать отрицательные индексы - они отсчитываются с конца массива

*Синтаксис:*

 ```javascript
 arr.slice(0, 2);
 ```

Ссылка [на примеры](http://code.mu/ru/javascript/manual/array/slice/)

***

### ```concat(...items)``` – возвращает новый массив: копирует все члены текущего массива и добавляет к нему items. Если какой-то из items является массивом, тогда берутся его элементы

Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)

* Возвращает новый массив, состоящий из массива, на котором он был вызван, соединённого с другими массивами и/или значениями, переданными в качестве аргументов
* Не изменяет данный массив или любой из массивов, переданных в аргументах, а вместо этого возвращает поверхностную копию, содержащую копии тех элементов, что были объединены с исходными массивами. Элементы оригинальных массивов копируются в новый массив по следующим правилам:
   * Ссылки на объекты (но не фактические объекты): метод concat копирует ссылки на объекты в новый массив. И оригинал, и новый массив ссылаются на один и тот же объект. То есть, если объект по ссылке будет изменён, изменения будут видны и в новом, и в исходном массивах.
   * Строки, числа и булевы значения (но не объекты String, Number или Boolean): метод concat копирует значения строк и чисел в новый массив

> Примечание: Соединение массивов и/или значений в новый массив оставит соединяемые массивы/значения неизменными. Кроме того, любая операция над новым массивом (если только элемент не является ссылкой) не будет затрагивать исходные массивы и наоборот.

Ссылка [на примеры](http://code.mu/ru/javascript/manual/array/concat/)

***


## Для поиска среди элементов
***

### ```includes(value)``` – возвращает true, если в массиве имеется элемент value, в противном случае false

Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)

* Метод чувствителен к регистру символов
* Принимает 2 аргумента:
    * searchElement - искомый элемент
    * fromIndex (необязательный) - позиция в массиве, с которой начинать поиск элемента  searchElement. При отрицательных значениях поиск производится начиная с индекса array.length + fromIndex по возрастанию. Значение по умолчанию равно 0
* Возвращает - логическое значение true или false в зависимости от того содержит ли массив искомый элемент
* `includes()` специально сделан общим. Он не требует, чтобы this являлся массивом, так что он может быть применён к другим типам объектов (например, к массивоподобным объектам)

> Примечание: Если второй аргумент метода fromIndex больше или равен длине массива, то возвращается false. При этом поиск не производится.

> Основное отличие метода includes()ECMAScript 2016 от метода indexOf() заключается в том, что он возвращает логическое значение (true, или false), а не числовое значение (индекс элемента, или -1, если элемент не найден)


*Синтаксис:*

 ```javascript
 arr.includes(searchElement, fromIndex = 0);
 ```
 
 ***
 
 ### ```indexOf(searchElement, fromIndex)``` – ищет searchElement, начиная с позиции fromIndex, и возвращает его индекс или -1, если ничего не найдено
 
 Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)
 
 * Возвращает первый индекс, по которому данный элемент может быть найден в массиве или -1, если такого индекса нет
 * Метод чувствителен к регистру символов
 * Принимает 2 аргумента:
    * searchElement - искомый элемент
    * fromIndex (необязательный) - индекс, с которого начинать поиск. Если индекс больше или равен длине массива, возвращается -1, что означает, что массив даже не просматривается. Если индекс является отрицательным числом, он трактуется как смещение с конца массива. Обратите внимание: если индекс отрицателен, массив всё равно просматривается от начала к концу. Если рассчитанный индекс оказывается меньше 0, поиск ведётся по всему массиву. Значение по умолчанию равно 0, что означает, что просматривается весь массив
* Сравнивает искомый элемент searchElement с элементами в массиве, используя строгое сравнение (тот же метод используется оператором ===, тройное равно)

 *Синтаксис:*

 ```javascript
 arr.indexOf(searchElement, fromIndex = 0);
 ```
 
 Ссылка [на примеры](http://code.mu/ru/javascript/manual/string/indexOf/)
  
 
 ### ```lastIndexOf()``` - осуществляет поиск подстроки (указывается первым параметром) в строке. Поиск ведется с конца строки
 
 Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf)
 
 * Вернет позицию первого совпадения, а если оно не найдено, то вернет -1
 * Метод чувствителен к регистру символов
 * Принимает 2 аргумента:
     * `searchElement` - искомый элемент в массиве
     * `fromIndex`(необязательный параметр) - индекс, с которого начинать поиск в обратном направлении. Если индекс больше или равен длине массива, просматривается весь массив. Если индекс является отрицательным числом, он трактуется как смещение с конца массива. Обратите внимание: если индекс отрицателен, массив всё равно просматривается от конца к началу. Если рассчитанный индекс оказывается меньше 0, массив даже не просматривается. Значение по умолчанию равно длине массива, что означает, что просматривается весь массив

*Синтаксис:*

 ```javascript
 arr.lastIndexOf(searchElement, fromIndex = arr.length);
 ```

Ссылка [на примеры](http://code.mu/ru/javascript/manual/string/lastIndexOf/)

***

### ```find(func)```

Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/find)

* Возвращает значение первого найденного в массиве элемента, которое удовлетворяет условию переданному в callback функции.  В противном случае возвращается undefined
* Принимает 2 аргумента:
     * ```callback``` - Функция обратного вызова, которая будет выполнена один раз для каждого элемента в массиве, пока не вернет true, или не достигнет конца массива, возвращая при этом undefined. 
        - *Функция принимает следующие параметры:*
            * `currentValue` – значение текущего элемента
            * `index` – индекс массива текущего элемента
            * `arr` – массив, к которому принадлежит текущий элемент (по которому осуществляется проход)
     * ```thisValue```(необязательный параметр) - объект, на который может ссылаться ключевое слово this в функции callback. Если аргумент thisValue опущен, в качестве значения this используется undefined (в конечном счете this будет зависеть от обычных правил контекста выполнения функции)

> Примечание: Метод find() не вызывает функцию для элементов массива, которые не имеют значений

> Примечание: Метод find() не изменяет исходный массив

*Синтаксис:*

 ```javascript
 array.find(callback(currentValue, index, arr),thisValue);
 ```
 
 Ссылка [на примеры](https://wm-school.ru/js/array_find.php)

***

### ```filter(func)``` 

Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

* Выполняет цикл по индексам массива в порядке возрастания и вызывает callback для каждого элемента
* Возвращает новый массив, в который войдут только те элементы, для которых коллбэк вернет true
* Не изменяет сам массив (хотя функция callback может делать это)
* Принимает 2 аргумента:
     * ```callback``` - функция обратного вызова, которая будет выполнена один раз для каждого элемента в массиве. Если функция возвращает true, то элемент остаётся в массиве, если false, то удаляется
        - *Функция принимает следующие параметры:*
            * `currentValue` – значение текущего элемента
            * `index` – индекс массива текущего элемента (необязательный)
            * `arr` – массив, к которому принадлежит текущий элемент (по которому происходит проход)(необязательный)
     * ```thisValue```(необязательный параметр) - объект, на который может ссылаться ключевое слово this в функции callback. Если аргумент thisValue опущен, в качестве значения this используется undefined (в конечном счете this будет зависеть от обычных правил контекста выполнения функции).

*Синтаксис:*

 ```javascript
 array.filter(callback(currentValue, index, arr), thisValue);
 ```
 
 Ссылка [на примеры](http://code.mu/ru/javascript/book/prime/enumeration/filter/)
 
 ***
 
 ### ```findIndex()``` - похож на find, но возвращает индекс вместо значения
 
 Ссылка на [MDN](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)
 
 * Возвращает индекс в массиве, если элемент удовлетворяет условию проверяющей функции. В противном случае возвращается -1
 * Принимает 2 аргумента:
      * ```callback``` - Функция обратного вызова, которая будет выполнена один раз для каждого элемента в массиве. 
         - *Функция принимает следующие параметры:*
             * `currentValue` – текущий обрабатываемый элемент массива
             * `index` – индекс текущего обрабатываемого элемента массива (необязательный)
             * `arr` – массив, к которому принадлежит текущий элемент (по которому происходит проход)(необязательный)
      * ```thisArg``` (необязательный параметр) Объект, на который может ссылаться ключевое слово this в функции callback. Если аргумент thisArg опущен, в качестве значения this используется undefined (в конечном счете this будет зависеть от обычных правил контекста выполнения функции)
* Если он находит элемент массива, для которого функция возвращает логическое значение true, findIndex() возвращает индекс этого элемента массива (и не проверяет оставшиеся элементы массива)
* Диапазон элементов, обрабатываемых с помощью метода findIndex() устанавливается перед первым вызовом функции обратного вызова callback. Если элементы были добавлены к массиву после её вызова, то на таких элементах функция callback вызвана не будет
* Если существующие, непосещённые элементы массива изменяются функцией callback, то их значения, переданные в функцию, будут значениями на тот момент времени, когда метод findIndex посетит их

> Примечание: Функция callback вызывается только для индексов массива, имеющих присвоенные значения. callback не вызывается для индексов, которые были удалены или которым значения не присваивались.
 
> Примечание: Метод findIndex() не изменяет массив, для которого он был вызван.
 
*Синтаксис:*

 ```javascript
 array.findIndex(callback(currentValue, index, arr), thisArg);
 ```
 
 Ссылка [на примеры](https://wm-school.ru/js/array_findindex.php)
 
 ***
 
 
 


 
 
 
 
 
 
