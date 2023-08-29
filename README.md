MongoDB Job Store for Quartz.NET
================================
This version works on the more recent releases of mongo and quartz. The repositiory is published to nuget for easy referencing.

Thanks @ejlevin1 for providing a fix for the recent mongo/quartz version.
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
