MongoDB Job Store for Quartz.NET
================================
Thanks to @chrisdrobison for handing over this project.

## Basic Usage

```cs
NameValueCollection properties = new NameValueCollection
{
    { "quartz.scheduler.instanceName", "Notifications" },
    { "quartz.threadPool.type", "Quartz.Simpl.SimpleThreadPool, Quartz" },
    { "quartz.threadPool.threadCount", "5" },
    { "quartz.threadPool.threadPriority", "Normal" },
    { "quartz.jobStore.type", "Quartz.Spi.MongoDbJobStore.MongoDbJobStore, Quartz.Spi.MongoDbJobStore" },
    { "quartz.jobStore.connectionString", "mongodb://localhost:27017/quartz" },
    { "quartz.jobStore.collectionPrefix", "Q_" },
    { "quartz.serializer.type", "json" }
};

var schedulerFactory = new StdSchedulerFactory(properties);
var scheduler = await schedulerFactory.GetScheduler();

await scheduler.Start();
```

## Nuget

```
Install-Package Quartz.Spi.MongoDbJobStore
```
