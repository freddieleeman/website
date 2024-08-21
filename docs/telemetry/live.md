---
sidebar_position: 6
---

# Live Tracing 

Stalwart Mail Server includes a powerful Live Tracing & Logging feature designed to provide administrators with real-time insights into all server activity. This feature operates as an HTTP endpoint utilizing Server-Sent Events (SSE), also known as Event Streams, to deliver a continuous flow of structured logs and traces directly to the client. By accessing this endpoint, administrators can observe and monitor every aspect of the mail server's operations as they happen, enabling prompt diagnostics, performance monitoring, and issue resolution.

One of the key advantages of the Live Tracing & Logging feature is its flexibility. Administrators can apply filters to the live trace stream to focus only on specific spans or logs that are of interest. This targeted approach allows for efficient monitoring, ensuring that you capture relevant data without being overwhelmed by the volume of logs typically generated by a busy mail server.

For the best experience and ease of use, it is recommended to access this feature through the [WebAdmin](/docs/management/webadmin/overview) interface. The WebAdmin tool is optimized to format these live events, presenting the information in a user-friendly manner. With WebAdmin, administrators can effortlessly manage the live stream, apply filters, and visualize the server activity, making it the preferred method for utilizing the Live Tracing & Logging capabilities of Stalwart Mail Server.

:::tip Enterprise feature

This feature is available exclusively in the Enterprise Edition of Stalwart Mail Server and not included in the Community Edition.

:::

## Endpoint

Stalwart Mail Server provides a dedicated API endpoint for accessing real-time tracing and logging data, allowing administrators to monitor server activity as it occurs. This endpoint, which is accessible at `/api/tracing/live`, returns a continuous stream of [events](/docs/telemetry/events), each encoded in JSON format. These events contain structured logs and traces of the mail server’s activities, providing detailed insights into every aspect of the server's operations. The event stream is transmitted using the Server-Sent Events (SSE) protocol, which allows for real-time delivery of logs directly to the client.

### Parameters

The endpoint supports a flexible filtering mechanism to help administrators focus on specific types of events or activities. Filters can be applied globally or on a per-key basis to tailor the live stream according to specific criteria.

- The `filter` parameter allows you to apply a broad filter across all structured event keys. This is useful when you want to monitor events that match a particular pattern or value across multiple keys. The filter syntax follows a simple key=value format, and multiple filters can be combined to narrow down the results. For example `/api/tracing/live?filter=error`.
- For more precise filtering, you can apply granular filters to specific [keys](/docs/telemetry/events#key-types) within the structured events. This allows you to target specific types of activities or logs based on criteria such as IP addresses, domain names, user agents, and more. For example `/api/tracing/live?remote-ip=192.168.1.1&domain=example.org`.


### Response Format

The events returned by the `/api/tracing/live` endpoint are encoded in JSON format. Each event includes a variety of structured keys that describe different aspects of the server's activity. The exact structure and content of the events depend on the server's current operations and the filters applied.
