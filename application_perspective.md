### Application performance management (agent based)

An Application Perspective (AP) is a power tool for monitoring, alerting, and analysis of a microservice environment. Each AP auto-generates a feature rich monitoring dashboard for the [golden signals](https://sre.google/sre-book/monitoring-distributed-systems/#xref_monitoring_golden-signals) and more. It organizes a team so they stay focused on the services they are interested in and aren’t distracted. Alerts, errors, and logs are scoped to an AP to focus the troubleshooting. From a security perspective, an organization can use an AP to limit visibility to infrastructure and services.

### Creating an Application

The Application Perspective is a unique capability of Instana. An AP creation wizard is       available for new users to easily create simple and frequently used types of APs. An advanced screen is available if you are familiar or proficient with Instana or you need to create a sophisticated AP. It is very easy to switch between these two modes without data loss.

To create an application perspective to view trace information that is gathered, complete either of the following steps:

Click Applications in the sidebar of the Instana UI, and then click +ADD > New Application Perspective.
Click New Application Perspective from the Applications pane in the Instana landing page.

### Simplified AP Creation using the Wizard

1. Simplified AP Creation using the Wizard
    * The AP Creation Wizard is an interactive, simple way to create an AP. It has three steps:
        1. Select a blueprint from the common use cases.
        2. Specify the application’s model by selecting the tags and values to identify the services or endpoints to include.
        3. Provide the final details to finish the creation.
    At any time you can switch to the advanced mode by selecting the button in the top right that says "Switch to Advanced Mode."

### Advanced AP Creation

All the data that is needed for an AP is entered in a single screen with the Advanced AP creation view. The steps within this view are:

1.  Enter a name for your application perspective.
2.  To define your application perspective using tags, click **Add filter.**

For tags to conjoin, choose between the AND or OR operator and use brackets. When using a mix of AND and OR conjunctions without brackets, AND conjunctions have the highest priority and are evaluated first. For example, the tag definitions tag.A AND tag.B OR tag.c AND tag.d is interpreted and processed as (tag.A AND tag.B) OR (tag.c AND tag.d).

Each call that matches the filters, including calls to any database or messaging services that are invoked within the application, is associated with this application perspective.

There is also an option to apply filters and group by the source or destination of a call.

Note: The service.name and endpoint.name tags, along with the infrastructure entity tags such as agent.tag or host.name can be applied to both the source and the destination of a call. By default, it's applied to the destination and it can be modified by using the edit filter dialog. An example for combining source and destination is for an application that groups calls which are issued from the agent.zone prod towards the agent.zone test.

* To include all the services that transitively fall downstream of those matched by the tags  you have specified, select **Include All Downstream Services**. Select **No Downstream Services** if only the filtered services are all to consider. Select **Immediate downstream database and messaging services** if the database or messaging services directly communicating with the selected services should be included in the AP.
* Select the default dashboard view

**Inbound calls:** Inbound calls are calls initiated from outside the application and where the destination service is part of the selected application perspective.

**All calls:** Results and metrics for not only calls at the application perspective boundary, but also those occurring within the application perspective.

By default, various dashboards such as the Summary tab, only show numbers for "Inbound Calls". Wherever the Inbound or All Calls selector is available on a dashboard, the perspective can be switched to All Calls. When selecting services and endpoints within an application perspective, the boundary setting is inherited.    

### Update an application perspective

Existing application perspectives can be updated or deleted. Note that once an application perspective is updated, the new configuration only applies to new incoming calls after the change. Calls and services that were included in the application before the change are not affected.

On the sidebar, click Applications and then select your application perspective.
Select the Configuration tab.

### Switching to Advanced Mode or back to Simple Mode

At any point you can switch from the simple wizard mode to the advanced mode using the button. In the Step 2 example above, selecting the advanced mode would present the screen shown as follows. All of the data that was previously entered is carried forward to this view. The reverse is also true -- if you were to select “Simple Mode” this data would not be lost either.

### Services

Instana traces and analyzes every request. Services and endpoints are automatically discovered, and relationships between services, endpoints, and your infrastructure are autocorrelated and stored in our [dynamic graph](https://www.ibm.com/docs/en/instana-observability/current?topic=instana-leveraging-dynamic-graph).

Based on the data that is collected from tracers and sensors, KPIs are calculated for calls, latency, and erroneous calls. KPIs help you discover the health of every individual service and then the health of your entire infrastructure.

Services are a part of application monitoring and provide a logical view of your system. Services are derived from infrastructure entities such as hosts, containers, and processes. Incoming calls are correlated to [infrastructure entities](https://www.ibm.com/docs/en/instana-observability/current?topic=applications-infrastructure-correlation) and enriched with infrastructure data; for example, the Kubernetes pod label or SpringBoot application name. After this infrastructure-linking processing step, a service mapping step maps the enriched calls to generate a service name per call based on a set of rules. Instana comes with an extensive set of [predefined rules](https://www.ibm.com/docs/en/instana-observability/current?topic=applications-services#predefined-rules) to generate the best possible service name for you automatically. To fine-tune the service mapping, you can create your own custom rules, see [customize service mapping](https://www.ibm.com/docs/en/instana-observability/current?topic=applications-services#customize-service-mapping).


Endpoints define the API of a service and provide a fine-grained view into what operations are exposed by the services. Every call to a service happens on a single endpoint. Every endpoint has a single, automatically discovered type: BATCH, SHELL, DATABASE, HTTP, MESSAGING, RPC. Like services, endpoints can be viewed through the lens of an application perspective.

The endpoint can be statically declared or can be based on call tags (in contrast to the service, which is typically determined using infrastructure tags, e.g. SpringBoot name). For example a combination of {call.http.method} {call.http.path} would be a typical endpoint of an HTTP service.

Another benefit for defining separate endpoints for a service is that, mainly with 'monoliths', services can include many different frameworks and technologies; HTTP/REST APIs, database access, message bus integration, etc. By creating at least endpoints per type of API, and possibly further breaking apart such as protocol details, metrics and statistics are captured per API type.

Instana automatically maps endpoints based on default rules. For more information, see [Endpoint mapping](https://www.ibm.com/docs/en/instana-observability/current?topic=applications-endpoints#endpoint-mapping).

### Traces, Calls and Span

A trace represents a single request and its path through a system of services. A trace can be a direct result of a request that is initiated by a customer’s browser, scheduled job, or any other internal execution. Each trace is made up of one or more calls.

A call represents communication between two services: a request and a response (asynchronous). Each call is a set of data and time measurements corresponding to a particular Remote Procedure Call (RPC) or service call. Within the Instana UI, each type of call is highlighted, such as HTTP, messaging, database, batch, or internal.

To capture the call data, both the caller and the callee side are measured, which is crucial in distributed systems. In distributed tracing, these individual measurements are called spans.

An internal call is a particular type of call that represents work that is done inside a service. It can be created from intermediate spans that are sent through custom tracing. If you prefer to implement custom tracing to write your own custom instrumentation, then Instana supports OpenTelemetry, OpenTracing, OpenCensus, Jaeger, Zipkin the Web Trace SDK or one of the language-based tracing SDKs.

Calls can represent operations that incurred in errors. For example, a call that represents an HTTP operation might result in a 5xx status code, or the invocation of an API through Java Remote Method Invocation (RMI) might result in an exception. Such calls are considered erroneous and are marked accordingly in the Instana UI as shown in the following image.

The name span is derived from Google’s Dapper paper and is short for timespan. Spans represent the timing of code executions, that is, an action with a start and end time. Span also contains a set of data that consists of both a timestamp and a duration. Different types of spans can have one or several sets of data that are complete with metadata annotations. Every trace model consists of a block of spans in a hierarchical set that is ordered by 64-bit identifiers and are used for reference between parent (caller) and child (callee) spans. In each trace, the first span serves as the root, and its 64-bit identifier is the identifier for the whole trace.

The first span of a particular service indicates that a call entered the service, and is called an entry span (in the Dapper paper, the entry span is named "server span"). Spans of calls that leave a service are called exit span (in the Dapper paper, exit span is named “client span”). In addition to entry and exit spans, intermediate spans mark significant sections of code, so the trace runtime can be clearly attributed to the correct code.

Each span has an associated type, such as HTTP call or database connection. Depending on the type of span, more contextual data are associated. To follow a sequence of spans across services, Instana sends correlation headers automatically with instrumented exits, and those correlation headers are automatically read by Instana’s entries. For more information, see HTTP Tracing Headers.

### Analyzing traces and calls

Examine traces in Unbounded Analytics, where you can investigate the traces and calls collected by Instana. To help you understand how an application behaves with each call, we monitor each one of those calls as they come in to the system.



## References

- [How to create an application perspective in Instana](https://www.ibm.com/docs/en/instana-observability/current?topic=applications-application-perspectives)
- [Services](https://www.ibm.com/docs/en/instana-observability/current?topic=applications-services)
- [Endpoints](https://www.ibm.com/docs/en/instana-observability/current?topic=applications-endpoints#endpoint-mapping)
- [Analyze Traces and Calls](https://www.ibm.com/docs/en/instana-observability/current?topic=applications-analyzing-traces-calls)
- [Concepts of tracing](https://www.ibm.com/docs/en/instana-observability/current?topic=monitoring-traces)
