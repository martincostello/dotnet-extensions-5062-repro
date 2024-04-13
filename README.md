# dotnet/extensions#5062 Repro

Repro for [dotnet/extensions#5062](https://github.com/dotnet/extensions/issues/5062).

To reproduce the issue, run the following commands:

```console
dotnet publish
./artifacts/publish/dotnet-extensions-5062-repro/release/repro
```

The output should be similar to the following:

```console
> dotnet publish
Restore complete (1.2s)
You are using a preview version of .NET. See: https://aka.ms/dotnet-support-policy
  dotnet-extensions-5062-repro succeeded (19.3s) → artifacts\publish\dotnet-extensions-5062-repro\release\

Build succeeded in 20.7s

> ./artifacts/publish/dotnet-extensions-5062-repro/release/repro
Unhandled exception. System.MissingMethodException: Constructor on type 'Polly.Registry.ResiliencePipelineRegistryOptions`1[Microsoft.Extensions.Http.Resilience.Internal.HttpKey]' not found.
   at System.Activator.CreateInstance[T]() + 0x79
   at Microsoft.Extensions.Options.OptionsFactory`1.Create(String) + 0x2b
   at Microsoft.Extensions.Options.UnnamedOptionsManager`1.get_Value() + 0x9a
   at Polly.PollyServiceCollectionExtensions.<>c__6`1.<AddResiliencePipelineRegistry>b__6_0(IServiceProvider serviceProvider) + 0x35
   at Microsoft.Extensions.DependencyInjection.ServiceLookup.CallSiteRuntimeResolver.VisitRootCache(ServiceCallSite, RuntimeResolverContext) + 0x88
   at Microsoft.Extensions.DependencyInjection.ServiceLookup.CallSiteVisitor`2.VisitCallSite(ServiceCallSite, TArgument) + 0x95
   at Microsoft.Extensions.DependencyInjection.ServiceLookup.CallSiteRuntimeResolver.Resolve(ServiceCallSite, ServiceProviderEngineScope) + 0x3d
   at Microsoft.Extensions.DependencyInjection.ServiceProvider.CreateServiceAccessor(ServiceIdentifier) + 0x111
   at System.Collections.Concurrent.ConcurrentDictionary`2.GetOrAdd(TKey, Func`2) + 0xf3
   at Microsoft.Extensions.DependencyInjection.ServiceProvider.GetService(ServiceIdentifier, ServiceProviderEngineScope) + 0x44
   at Microsoft.Extensions.DependencyInjection.ServiceLookup.ServiceProviderEngineScope.GetService(Type serviceType) + 0x42
   at Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService(IServiceProvider, Type) + 0x78
   at Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService[T](IServiceProvider) + 0x29
   at Microsoft.Extensions.DependencyInjection.ServiceLookup.CallSiteRuntimeResolver.VisitRootCache(ServiceCallSite, RuntimeResolverContext) + 0x88
   at Microsoft.Extensions.DependencyInjection.ServiceLookup.CallSiteVisitor`2.VisitCallSite(ServiceCallSite, TArgument) + 0x95
   at Microsoft.Extensions.DependencyInjection.ServiceLookup.CallSiteRuntimeResolver.Resolve(ServiceCallSite, ServiceProviderEngineScope) + 0x3d
   at Microsoft.Extensions.DependencyInjection.ServiceProvider.CreateServiceAccessor(ServiceIdentifier) + 0x111
   at System.Collections.Concurrent.ConcurrentDictionary`2.GetOrAdd(TKey, Func`2) + 0xf3
   at Microsoft.Extensions.DependencyInjection.ServiceProvider.GetService(ServiceIdentifier, ServiceProviderEngineScope) + 0x44
   at Microsoft.Extensions.DependencyInjection.ServiceLookup.ServiceProviderEngineScope.GetService(Type serviceType) + 0x42
   at Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService(IServiceProvider, Type) + 0x78
   at Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService[T](IServiceProvider) + 0x29
   at Microsoft.Extensions.DependencyInjection.ResilienceHttpClientBuilderExtensions.CreatePipelineSelector(IServiceProvider, String) + 0x43
   at Microsoft.Extensions.DependencyInjection.ResilienceHttpClientBuilderExtensions.<>c__DisplayClass6_0.<AddResilienceHandler>b__0(IServiceProvider serviceProvider) + 0x19
   at Microsoft.Extensions.DependencyInjection.HttpClientBuilderExtensions.<>c__DisplayClass3_0.<AddHttpMessageHandler>b__1(HttpMessageHandlerBuilder) + 0x18
   at Microsoft.Extensions.Http.DefaultHttpClientFactory.<>c__DisplayClass17_0.<CreateHandlerEntry>g__Configure|0(HttpMessageHandlerBuilder) + 0x44
   at Microsoft.Extensions.Http.MetricsFactoryHttpMessageHandlerFilter.<>c__DisplayClass2_0.<Configure>b__0(HttpMessageHandlerBuilder) + 0x1a
   at Microsoft.Extensions.Http.LoggingHttpMessageHandlerBuilderFilter.<>c__DisplayClass6_0.<Configure>b__0(HttpMessageHandlerBuilder) + 0x20
   at Microsoft.Extensions.Http.DefaultHttpClientFactory.CreateHandlerEntry(String) + 0x1ba
   at System.Lazy`1.ViaFactory(LazyThreadSafetyMode) + 0xad
   at System.Lazy`1.ExecutionAndPublication(LazyHelper, Boolean) + 0x7e
   at System.Lazy`1.CreateValue() + 0xd6
   at Microsoft.Extensions.Http.DefaultHttpClientFactory.CreateHandler(String) + 0x2c
   at Microsoft.Extensions.Http.DefaultHttpClientFactory.CreateClient(String) + 0x22
   at Microsoft.Extensions.DependencyInjection.HttpClientBuilderExtensions.AddTransientHelper[TClient](IServiceProvider, IHttpClientBuilder) + 0x32
   at Microsoft.Extensions.DependencyInjection.ServiceLookup.CallSiteRuntimeResolver.VisitDisposeCache(ServiceCallSite, RuntimeResolverContext) + 0xe
   at Microsoft.Extensions.DependencyInjection.ServiceLookup.CallSiteVisitor`2.VisitCallSite(ServiceCallSite, TArgument) + 0xb7
   at Microsoft.Extensions.DependencyInjection.ServiceLookup.CallSiteRuntimeResolver.Resolve(ServiceCallSite, ServiceProviderEngineScope) + 0x3d
   at Microsoft.Extensions.DependencyInjection.ServiceProvider.GetService(ServiceIdentifier, ServiceProviderEngineScope) + 0xa3
   at Microsoft.Extensions.DependencyInjection.ServiceProvider.GetService(Type serviceType) + 0x2b
   at Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService(IServiceProvider, Type) + 0x5f
   at Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService[T](IServiceProvider) + 0x29
   at Program.<<Main>$>d__0.MoveNext() + 0x119
--- End of stack trace from previous location ---
   at Program.<Main>(String[] args) + 0x24
```
