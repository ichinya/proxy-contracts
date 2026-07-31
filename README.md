# Proxy Contracts

Shared data contracts and schemas for the proxy checking platform.

## Purpose

This repository contains stable contracts used between platform components:

- proxy-collector
- proxy-scheduler
- proxy-checker
- ip-judge
- proxy-site

The goal is to keep communication formats consistent between services written in different languages.

## Contracts

Planned schemas:

- `proxy.v1` — normalized proxy endpoint
- `check-job.v1` — proxy check task sent to workers
- `check-result.v1` — checker result
- `judge-response.v1` — IP judge response

## Example flow

```text
proxy-collector
      |
      v
 proxy.v1
      |
      v
proxy-scheduler
      |
      v
check-job.v1
      |
      v
proxy-checker
      |
      v
check-result.v1
```

## Versioning

Contracts are versioned independently from services.

Breaking changes require a new version:

```
check-job.v1
check-job.v2
```

## Related projects

- proxy-checker
- proxy-collector
- proxy-scheduler
- proxy-stack
- ip-judge
- proxy-site
