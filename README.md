# Hangfire.RecurringJob

This is the a package that automatically registers hangfire recurring jobs, using source generator to build a single exention method to register the jobs in the progam.cs

## How to use it?
Install the [NuGet package](#) into your project
```
Install-Package IeuanWalker.Hangfire.RecurringJob
```

The attribute works on a class level, and the class just needs and `Execute()` method.
```csharp
[RecurringJob]
public class RecurringJob1
{
	public Task Execute()
	{
		throw new NotImplementedException();
	}
}

[RecurringJob("* * * *")]
public class RecurringJob2
{
	public void Execute()
	{
		throw new NotImplementedException();
	}
}

[RecurringJob("* * * *", "Priority")]
public class RecurringJob3
{
	public void Execute()
	{
		throw new NotImplementedException();
	}
}

[RecurringJob]
[RecurringJob("*/5 * * * *", "GMT", "Priority", "DataRetention")]
public class RecurringJob4
{
	public void Execute()
	{
		throw new NotImplementedException();
	}
}
```

Once a `RecurringJob` attribute has been added to your project a exention method will automatically be created to be added to you progam.cs
> The extention method name convention is AddRecurringJobsFrom + your assebly name
```csharp
services.AddRecurringJobsFromExampleProject();
```

Here is an example of what it looks like in use - 
![image](https://github.com/IeuanWalker/Hangfire.RecurringJob.Generator/assets/6544051/761f2076-bca9-4637-a7f9-c721b5799b67)

