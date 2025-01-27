**Projection** : refers to the operation of transforming an object into a new form that is going to be used
1. Construct a new type
2. project a new property
3. perform mathematical operation

> [!info]
> **DTO** acronym for Data Transfer Object
### 1. `Select`

```csharp
var result = employees.Select(x =>
{
    return new EmployeeDto
    {
        FName = x.FName
    };
});
```
### 2. `SelectMany`

```csharp
string[] sentences =
{
    "I love programming",
    "I go to school every day"
};
// Method Syntax
var words = sentences
    .SelectMany(x => x.Split())
    .Distinct();
// Query Selctor
var wordss = (from sentence in sentences
              from word in sentence.Split()
              select word).Distinct();
```
### 3. `Zip`

```csharp
string[] colorNames = { "Red", "Green", "Blue" };
string[] colorHex = { "FF0000", "00FF00", "0000FF" };
// Method Syntax
var colors = colorNames.Zip(colorHex, (name, hex) => $"{name} : {hex}");
// Query Selctor
var colors = from color in colorNames.Zip(colorHex)
             select $"{color.First} : {color.Second}";
```