# String

> [!WARNING]  
> This page not finished yet

## String Instantiation
### 1. Quoted String Literals
```csharp
string str = "Hello";
```
### 2. String Constructor
```csharp
char[] letters = { 'H', 'e', 'l', 'l', 'o' };
string str = new string(letters);
```
### 3. Repeating Character
```csharp
string str = new string('M', 3); // MMM
```
### 4. Pointer to Signed Byte Array
```csharp
sbyte[] bytes = { 0x4D, 0x65, 0x74, 0x6F };
string str = null;
unsafe
{
    fixed(sbyte* ptr = bytes)
    {
        str = new string(ptr);
    }
}
```
### 5. Pointer to Character Array
```csharp
char[] letters = { 'M', 'e', 't', 'o' };
string str = null;
unsafe
{
    fixed (char* pchars = letters)
    {
        str = new string(pchars);
    }
}
```
### 6. Concatenation
```csharp
string str01 = "Hel" + "lo";
string str02 = $"{"Hel"}{"lo"}";
```
### 7. blank
```csharp
string text = "Hello";
string str = text.Substring(0, 3);
```
### 8. Formatted String
```csharp
string customer = "Ahmed";
DateTime date = DateTime.Now;
string str = String.Format(
    "Dear {}" +
    "\nAt {1:t} on {1:D}, ...",
    customer, date);
```
### 9. blank
```csharp
string cutomer = "Ahmed";
DateTime date = DateTime.Now;
string str = @"Dear Ahmed
At 2020 ....
....";
```
### 10. Raw String
```csharp
string str = """
    <nav>
        <li> </li>
        <li> </li>
    <nav>
    """;
```
> [!NOTE]  
> for using unsafe block you should assign it to true `<AllowUnsafeBlocks>true</AllowUnsafeBlocks>`<br>
> for using raw string ...
----
## String Intern Pool
### String Literals
```csharp
string str = "metigator";
```
`str` string type its value "metigator"
### String Object
```csharp
string str = new string("metigator");
```
`str` string type points to a string object
