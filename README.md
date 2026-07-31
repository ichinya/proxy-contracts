# Proxy Contracts

Versioned JSON Schemas and compatibility rules shared by Proxy Platform v2.

## Overview

Proxy Contracts is the source of truth for data exchanged by collectors, schedulers, checkers, judge services, deployment tooling, and the SaaS API.
Status: foundation planning. Initial v1 schemas and examples will land before services depend on them.

## Architecture

~~~text
schemas/proxy.v1.json
schemas/check-job.v1.json
schemas/check-result.v1.json
schemas/judge-response.v1.json
        |
        v
Generated validation tests and examples for every consumer
~~~

A typical contract flow is:

~~~text
proxy-collector -> proxy.v1 -> proxy-scheduler -> check-job.v1
                                              |
                                              v
                                      proxy-checker -> check-result.v1
~~~

This repository is the source of truth for the shared message and API shapes.

## Features

Planned capabilities:

- Versioned JSON Schemas
- Canonical proxy endpoint representation
- Check job and result envelopes
- Judge response schema
- Backward-compatibility policy
- Valid and invalid example fixtures

## Installation

No package is published yet. Clone the repository and consume schemas directly only after the first tagged release.

~~~shell
git clone https://github.com/ichinya/proxy-contracts.git
cd proxy-contracts
~~~

## Docker

A production container image is planned for v0.1 where applicable. Until an image and digest are published, there is no supported container invocation.

## Configuration

This repository has no runtime configuration. Schema identifiers, versioning rules, and release tags are part of the public contract.

## Environment variables

No environment variables are required. Schema validation tooling may expose command-line options as it is added.

## Development

The repository is language-neutral; validation tooling must remain reproducible.

1. Choose an open roadmap issue and confirm its acceptance criteria.
2. Keep contracts and examples versioned; coordinate cross-repository changes explicitly.
3. Add tests for behavior changes and update documentation in the same pull request.
4. Run the repository-specific checks documented by the implementation once they exist.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the common workflow and [SECURITY.md](SECURITY.md) for private vulnerability reporting.

## Roadmap

- **v0.1 Foundation:** repository structure, documentation, Docker/CI foundations, and base contracts.
- **v0.2 MVP:** collector -> scheduler -> MQ -> checker -> judge -> database -> site working cycle.
- **v1.0 Production:** multi-region judges, scoring, API, billing, monitoring, and high availability.

Track delivery in the [repository milestones](https://github.com/ichinya/proxy-contracts/milestones) and [issues](https://github.com/ichinya/proxy-contracts/issues).

## Related projects

- [ip-judge](https://github.com/ichinya/ip-judge)
- [proxy-checker](https://github.com/ichinya/proxy-checker)
- [proxy-collector](https://github.com/ichinya/proxy-collector)
- [proxy-scheduler](https://github.com/ichinya/proxy-scheduler)
- [proxy-stack](https://github.com/ichinya/proxy-stack)
- [proxy-site](https://github.com/ichinya/proxy-site)

## License

MIT License
