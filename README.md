# wasm-stream
trying out wasm-based workloads with an event-based interface for responding to HTTP requests

## System Design

```mermaid
graph LR;
  internet["Internet"]
  api["API Gateway"]
  operator["Gateway Operator"]
  redis[(Redis Store)]
  worker["WASM Workloads"]
  keda["KEDA"]
  config["Workload Config"]

  internet-->api
  api-->redis
  api-->worker
  keda-->api
  keda--"scales to zero"-->worker
  operator--configures-->api
  operator--deploys-->worker
  operator--monitors-->config
```
