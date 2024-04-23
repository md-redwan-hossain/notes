-   If a private field is captured, name it with `_` prefix. Captured means it becomes a part of the class.

```csharp

public class Book(string amount){}
public class Book(string _amount){}

```
