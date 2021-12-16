# Algo3.teor

## Задача 1
### Условие
Найти в графе количество треугольников за O(E^1.5).
### Решение
Будем проходиться поиском в глубину по следующему алгоритму:
1) Для текущей вершины рассматриваем всех еще не посещенных соседей.
2) Запускаем поиск в глубину длины два, и если вершина, в которую мы пришли на глубине два, является текущей вершиной, то прибавляем один треугольник.
3) Помечаем текущую вершину как посещенную.
4) Запускаемся из другой, еще не посещенной, вершины.

Таким образом, алгоритм проходит не более |V| циклом (из каждой вершины в худшем случае), причем каждое ребро в алгоритме используется ровно один раз, то есть максимальная сложность внутри цикла O(|E|). Тогда получаем сложность O(|V||E|) = O(|E|^1.5).

## Задача 2
### Условие
Ориентировать неор граф так, чтобы он стал сильносвязным за O(V+E), или сказать, что это невозможно.
### Решение
Очевидно, что нельзя ориентировать требуемым способом граф, содержащий мосты (так как будет путь только в одну сторону), либо вовсе не являющийся связным. Тогда будем рассматривать графы без мостов, они будут реберно-двусвязными. Через обход в глубину из какой-то вершины X находим минимальное остовное дерево (тут возникает O(V + E)). Тогда достаточно будет ориентировать ребра остовного дерева по направлению к X, а остальные по направлению от X (O(E)). Тогда получаем сильносвязный граф, так как мы сможем по ребрам остовного дерева в одном направлении, а по остальным в обратном, то есть из любой вершины можно будет добраться в любую другую.

## Задача 3
### Условие
Разбить все ребра неорграфа на минимальное число путей за 𝒪(𝑉 + 𝐸).
### Решение
Заметим, что эта задача эквивалентна задаче о минимальном дополнении каждой компоненты связности графа до Эйлерова цикла, так как найдя Эйлеров цикл и удалив из него добавленные ребра, мы получим распавшийся на несколько новых путь. Их будет столько же, сколько ребер мы добавляли. Тогда дополним каждую компоненту связности до Эйлерова цикла, любым образом паросочетая вершины нечетной степени. Тогда получаем требуемую ассимптотику O(V + E).

## Задача 4
### Условие
Для каждой пары вершин в графе найти 𝑤[𝑎, 𝑏] – такой минимальный вес, что из 𝑎 в 𝑏 есть путь по рёбрам веса <= 𝑤[𝑎, 𝑏]. O(V^2)
### Решение
