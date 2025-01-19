# Threading
## Asynchronous Programming
### Example 1
define `CustomEventArgs`
```csharp
public class CustomEventArgs : EventArgs
{
    public int Parameter1 { get; }
    public string Parameter2 { get; }
    public CustomEventArgs(int parameter1, string parameter2)
    {
        Parameter1 = parameter1;
        Parameter2 = parameter2;
    }
}
```
Inside `Class Program`
```csharp
public delegate void CallbackEventHandler(object sender, CustomEventArgs e);
```
```csharp
public static event CallbackEventHandler CallbackEvent;
```
```csharp
static async Task Main()
{
    CallbackEvent += OnCallbackReceived;

    Task PerformTask = PerformAsyncOperation(CallbackEvent);

    Console.WriteLine("Doing Some Other Work");

    await PerformTask;

    Console.WriteLine("Done");

    Console.ReadLine();
}
```
```csharp
static async Task PerformAsyncOperation(CallbackEventHandler callback)
{
    await Task.Delay(2000);

    CustomEventArgs eventArgs = new CustomEventArgs(42, "Hello from event");

    callback?.Invoke(null, eventArgs);
}
```
```csharp
static void OnCallbackReceived(object sender, CustomEventArgs e)
{
    Console.WriteLine($"Event Recieved {e.Parameter1}, {e.Parameter2}");
}
```
