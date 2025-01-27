**LINQ** : Language Integrated Query
- type safe queries
- query to object `IEnumerable<T>` _(not generic `IEnumerable`)_
- LINQ to remote SQL `iQueryable<T>`
- Set of Query Operator `Extension Methods`

Instead of creating our custom method
```csharp
public static IEnumerable<Employee> Filter
	(this IEnumerable<Employee> source, Predicate<Employee>) {..}
```
We Can rely on LINQ
```csharp
public static IEnumerable<TSource> Where<TSource>
	(this IEnumerable<TSource> source, Predicate<TSource>) {..}
```
## Ways to Write LINQ statements
Write LINQ statements using
#### Method Syntax
1. Extension method
```csharp
var result = numbers.Where(x => x % 2 == 0);
```
2. Enumerable Method <br> _( both Extension method and Query Syntax convert into it in IL language )_
```csharp
var result = Enumerable.Where(numbers, x => x % 2 == 0);
```
#### 3. Query Syntax
Compiler convert it to `Method Syntax`
```csharp
var result = from n in numbers // Range
			 where n % 2 == 0  // Filter
			 select n;         // Select
```
---
`evenNums` kept in memory as a expression act as wrapper containing reference to the `numbers` and `Where` Decorator, so every edit on the `source` before enumeration Taken into consideration 
```csharp
var numbers = new List<int> { 1, 2, 3, 4, 5 };
// Construction (lazy loading)
var evenNums = numbers.Where(x => x % 2 == 0);
numbers.Add(6);
// enumeration (immediate execution)
foreach (var e in evenNums)
    Console.WriteLine(e);
    // 2, 4, 6
```