# opentelemetry-dotnet-simple
This repository provides a simple example of a .NET Minimal API application instrumented with OpenTelemetry for collecting **traces**, **logs**, and **metrics**.


## **Prerequisites**

To run this project, ensure you have the following installed on your system:
- **.NET SDK 6 or later**: [Download .NET](https://dotnet.microsoft.com/download)

## **Expected Output**

When the application is running, a single request to `curl http://localhost:8080/rolldice` will produce the following consolidated output in the console:

- **Metrics**:
```
kestrel.connection.duration, Description: The duration of connections on the server., Unit: s
(2024-12-30T16:46:55.5120267Z, 2024-12-30T17:26:35.5047202Z] network.protocol.name: http network.protocol.version: 1.1 network.transport: tcp network.type: ipv6 server.address: ::ffff:172.17.0.2 server.port: 8080 Histogram
Value: Sum: 0.11888409999999999 Count: 11 Min: 0.0029772 Max: 0.0778763 
(-Infinity,0.01]:10
(0.01,0.02]:0
(0.02,0.05]:0
```

- **Logs**:
```
info: Program[0]"
Anonymous player is rolling the dice: 2
LogRecord.Timestamp:               2024-12-30T16:52:09.2573407Z
LogRecord.TraceId:                 9792d60161ed2155b08eabcb0e19732a
LogRecord.SpanId:                  cf570a949e7d2ab2
LogRecord.TraceFlags:              Recorded
LogRecord.CategoryName:            Program
LogRecord.Severity:                Info
LogRecord.SeverityText:            Information
LogRecord.Body:                    Anonymous player is rolling the dice: {result}
LogRecord.Attributes (Key:Value):
    result: 2
    OriginalFormat (a.k.a Body): Anonymous player is rolling the dice: {result}.."
```

- **Traces**:
```
Activity.TraceId:            be35a0ad7b40da9bc2454c7f789d5f55
Activity.SpanId:             e0cd1b1305a4084b
Activity.TraceFlags:         Recorded
Activity.DisplayName:        GET /rolldice/{player?}
Activity.Kind:               Server
Activity.StartTime:          2024-12-30T16:53:58.2128575Z
Activity.Duration:           00:00:00.0007445
Activity.Tags:
    server.address: localhost
    server.port: 8090
    http.request.method: GET
    url.scheme: http
    url.path: /rolldice..
```

## **Key File**

The **`Program.cs`** file includes the OpenTelemetry setup and demonstrates trace, log, and metric collection in a minimal API.


## **Followed Resource**
https://opentelemetry.io/docs/languages/net/getting-started/
