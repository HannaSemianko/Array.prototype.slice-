# Array.prototype.slice-
Конспект

Метод slice() предназначен для копирования элементов массива согласно указанным индексам.

Возвращает новый массив, состоящий из скопированных элементов исходного массива.

Синтаксис: array.slice([start[, end]]), где

start – индекс элемента, с которого метод начинает копирование;

end – индекс элемента, до которого заканчивается копирование. Сам элемент с индексом end не включается.

Особенности индексов:

По умолчанию оба равны 0. Если не передавать никаких значений индексов в метод, новый массив будет возвращен точной копией исходного.
Если один из индексов отрицательный, он указывает смещение от конца массива.
Если индекс start больше, чем длина массива, то будет возвращен пустой массив.
Если индекс end отсутствует, то метод slice() извлечет все элементы до конца массива.
const arr = ['f', 's', 't', 'w', 'q'];
console.log(arr.slice()); // ["f", "s", "t", "w", "q"], индексы не переданы => мы получили новый массив – копию исходного
console.log(arr.slice(1, 3)); // ["s", "t"], в новый массив вошли элементы с индексами 1 и 2, индекс end 3 не включен
console.log(arr.slice(2)); // ["t", "w", "q"], задан только индекс start, 
// поэтому все элементы будут извлечены, начиная с него и до конца массива
console.log(arr.slice(-2)); // ["w", "q"], индекс start – отрицательное число => 
// будут извлечены 2 последних элемента массива
console.log(arr.slice(0, -3)); // ["f", "s"], в новый массив будут включены элементы, 
// начиная с индекса 0 до третьего элемента с конца массива, 
// но не включая его самого
console.log(arr.slice(6)); // [], индекс start имеет значение большее, чем длина массива  => возвращен пустой массив
Правила копирования элементов массива:

Для строк и чисел будет скопировано их значение, и изменение значения элемента в одном массиве никак не повлияет на другой.
Для данных типа object будут скопированы только их ссылки. object у нас один, а ссылок на него две. В данном случае изменения, сделанные в object в одном массиве, будут автоматически изменять свойства этого же object в другом массиве.
Если к любому из массивов, исходному или его копии, полученной методом slice(), добавить новый элемент, то это не вызовет изменений в другом.
Рассмотрим, как работают правила копирования на следующих примерах.

Задание 1. Дан массив строк arr. Необходимо вернуть новый массив, который бы содержал все элементы исходного массива. Затем добавить в конец получившегося массива длину исходного массива arr. Вывести значения обоих массивов в консоль.

const arr = ['raw', 'line', 'queue', 'seat'];
const newArr = arr.slice(); // делаем копию элементов исходного массива 
newArr.push(arr.length); // добавляем в конец нового массива длину массива arr
console.log(arr); // ["raw", "line", "queue", "seat"]
console.log(newArr); // ["raw", "line", "queue", "seat", 4]
// добавление элемента в копию массива не вызвало изменений в исходном

Задание 2. Дан объект obj и массив arr. Необходимо создать новый массив, который бы включал в себя первые два элемента исходного. Затем изменить свойство name объекта obj в новом массиве на 'Elvis'. Вывести данное свойство obj каждого массива в консоль.

const obj = {
  name: 'Joey',
  age: 30,
};
const arr = ['person', obj, 1, 33021]; // элемент с индексом 1 - объект
console.log(arr[1].name); // "Joey", получаем значение свойства name объекта obj в исходном массиве
const newArr = arr.slice(0, 2); // делаем копию подмассива из первых двух элементов arr
newArr[1].name = 'Elvis'; // меняем свойство name объекта obj в новом массиве
console.log(arr[1].name); // "Elvis"
console.log(newArr[1].name); // "Elvis"
// Видим, что в итоге в двух массивах свойство объекта name изменилось, 
// потому что объект у нас один, а в массивах содержаться ссылки на него.

Задание 3. Дан массив чисел и строк arr. Сделать копию последних двух элементов массива и вернуть их новым массивом. Убедиться, что значение последнего элемента исходного массива строго равно значению последнего элемента нового массива.

const arr = ['umbrella', 2, 3, 'zipper'];
const newArr = arr.slice(-2);
console.log(arr[arr.length - 1] === newArr[newArr.length -1]); // true
// У примитивных типов данных копируется их значение, соответственно, 
// скопированные элементы строго равны друг другу.
Подробнее читайте здесь:

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/slice
