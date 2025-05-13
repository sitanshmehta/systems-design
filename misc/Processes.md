# Processes

A process is an independent, running program that forms a building block of a system. It operates concurrently with other processes and often on different machines where commmunication happens via messages over a network

Processes have their own memory, state, and resources.

| Location Transparency  | You often interact with a process without knowing its physical location |
| --- | --- |
| Failure Independance | a process can crash independantly without bring the entire system down |
| Concurrency | Many processes can run simultaneosly on the same system or different nodes |

*Why processes matter in distributed systems?*

1. Modularity: Systems can be broken down in to microservices — each a process with a focused job
2. Concurrency: Systems can handle many tasks at once through multiple processes running at the same time
3. Scale: with each process running on a separate machine, scaling horizonatlly becomes easier

## Remote Procedure Calls

*What is an RPC?*

Remote procedure calls lets a program call a function on another computer just like it would call a local function while hiding all the network communication under the hood

Basic Terms:

- Stub | Auto generated wrapper that hides network code
- Serialization | data must be converted into a format that can be sent over the network (Json, protobuf)
- Transport | uses protocols like TCP, HTTP/2
- Blocking vs Async | some RPCs wait for a repsone, others are fire and forget

How it works:

- Client Stub: acts like the real function but just packages up the call (function name and args)
- Network: the call is sent to a server process over a network
- Server stub: unpacks the call and invokes the real function on the server
- Return val : result is sent back and unpacked by the client stub

Common RPC Frameworks:

| gRPC | C++, Go, Python | Fast, uses protocol buffers, supports HTTP/2 and streaming |
| --- | --- | --- |
| Thrif |  |  |
| JSON-RPC |  |  |

Examples

- Microservices communicating with each other, mobile apps sending request to backends, distributed databases syncing state

Challenges

| Challenge | Importance |
| --- | --- |
| Network Failures | remote system may be down or slow |
| partial failures | client works but sevrer crashes or vice versa |
| latency | network adds delay compared to local calls |
| versioning | both client and server must agree on data formats |