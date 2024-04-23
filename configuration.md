```cs
public static class SomeService
{
    public static void AddSomeService(this IServiceCollection services, Action<ServiceOptions>? options = null)
    {
        options?.Invoke(new ServiceOptions());
    }
}

public class SomeServiceOptions
{
    public string Version { get; set; }
}

// in Program.cs
services.AddSomeService();
```
