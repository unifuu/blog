---
title: "Memo of gRPC"
date: 2024-05-17
tags: ["Go", "Memo", "RPC"]
---

## What is gRPC

gRPC is a modern open source high performance Remote Procedure Call (RPC) framework that can run in any environment.

## Why gRPC

### Performance

- It can be faster than REST due to its usage of HTTP/2, which allows for multiplexing multiple requests over a single connection, reducing latency.
- Protocol Buffers are more compact and efficient to serialize and deserialize compared to JSON, which can lead to lower bandwidth usage.

### Features

- Streaming: Both client-side and server-side can be beneficial for real-time data exchange or long-lived connections.

## New term

### HTTP/2

HTTP/2 is the second major version of the HTTP.

1. Binary Protocol

HTTP/2 is a binary protocol, whereas HTTP/1.1 is text-based. It means that data is represented in a more compact and efficient binary format, reducing overhead and improving parsing speed.

2. Multiplexing

It introduces multiplexing, allowing multiple requests and responses to be sent and received asynchronously over a single TCP connection. In HTTP/1.1, multiple connections were required to achieve parallelism, leading to increased latency and resource consumption.

3. Header Compression

HTTP/2 uses header compression to reduce overhead. In HTTP/1.1, headers are sent in plaintext for each request and response, which can result in significant overhead, especially for small payloads. HTTP/2 employs the HPACK compression algorithm to compress header fields, reducing the amount of data transmitted over the network.

4. Server Push

HTTP/2 supports server push, allowing servers to proactively send resources to clients before they are requested. This can improve performance by reducing the number of round trips required to fetch resources.

5. Stream Prioritization

HTTP/2 introduces support for stream prioritization, allowing clients to assign priority levels to individual resources. 

### Streaming

Streaming in gRPC refers to the capability to send a continuous flow of data between the client and server, rather than sending a single request and receiving a single response.

#### Server-Side Streaming RPC

The client sends a single request to the server and receives a stream of responses. The server can keep sending responses as long as it needs to, and the client reads from the returned stream until there are no more messages.

#### Client-Side Streaming RPC

The client sends a stream of requests to the server instead of a single request. The server processes the stream of requests and returns a single response.

#### Bidirectional Streaming RPC

Both the client and the server send a stream of messages to each other. The two streams operate independently, meaning the client and server  can read and write messages in any order they want.

## Reference

- [gRPC](https://grpc.io/)