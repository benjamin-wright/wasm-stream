# wasm-stream
trying out wasm-based workloads with an event-based interface for responding to HTTP requests

## System Design

```mermaid
graph LR;
  internet["Internet"]
  api["API Gateway"]
  redis["Redis Store"]
  worker["WASM Workloads"]
  keda["KEDA"]

  internet-->api
  api-->redis
  api-->worker
  keda-->api
  keda-->worker
```
