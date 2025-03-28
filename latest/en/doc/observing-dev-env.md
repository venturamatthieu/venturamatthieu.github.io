# Observing what's append on dev env

Before starting with application observability, you have to implement a connector with a library.

Cloud native foundation support a project, take a look to https://opentelemetry.io/

## Logging
To be compliant between services, a log structure should have at least these properties :

- Name of the Service
- Name of the logged-in User
- Log level
- IP Address
- Correlation Id
- Time at which the message arrived
- Time Taken

And more
- Name of the method
- Call Stack
- HTTP Code

## Tracing

Tracing are very use full for detecting perfomance issue.

![](https://www.elastic.co/guide/en/kibana/current/apm/images/apm-transaction-sample.png)

### What tracing mean ?

**Request**: This denotes how various cloud applications, microservices, and other functions communicate with each other

**Span**: This informs about the work done by a single service with respect to time intervals and corresponding meta-data.
These are the basic building blocks of trace.

**Trace**: This implies the end-to-end user requests which consist of single or multiple spans.

**Tag**: These are the pieces of information (meta-data) associated with each span (recorded along the path) that
provide a detailed overview of the actions performed during a span.

For example, the following is an example Trace made up of 8 Spans:

~~~
Causal relationships between Spans in a single Trace


        [Span A]  ←←←(the root span)
            |
     +------+------+
     |             |
 [Span B]      [Span C] ←←←(Span C is a `ChildOf` Span A)
     |             |
 [Span D]      +---+-------+
               |           |
           [Span E]    [Span F] >>> [Span G] >>> [Span H]
                                       ↑
                                       ↑
                                       ↑
                         (Span G `FollowsFrom` Span F)

~~~

## Metric
Logs can tell you what happened in the system at a certain time.

Metrics contain low-resolution data. This may include a count of parameters (such as requests, errors, and so on)
and measures of resources (such as CPU and memory utilization).

Metrics are identified by two key pieces of information:
- A metric name
- A set of key-value pairs called tags or labels

You could have technical metric or business.

### Example for resource
- CPU/Memory Utilization: Usage of the system’s core resources.
- Host Count: Number of hosts/pods that are running your system (used to detect availability issues due to pod crashes).
- Live Threads: Threads spawned in your service (used to detect issues in multi-threading).
- Heap Usage: Heap memory usage statistics (can help debug memory leaks).

### Example for business
- Request Rate: Rate of requests to the APIs.
- Error Rate: Rate of errors being thrown by the APIs.
- Latency: Time taken to process requests by the APIs.

## Dashboard and alert

After collecting logs, traces or metric, you can create a dashboard on a tool.
This dashboard will be coded in a specific file.
For example on Grafana, documentation explain how to do that, https://grafana.com/docs/grafana/latest/http_api/dashboard/
