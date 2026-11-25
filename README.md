# <img src="assets/icon.svg" alt="" width="32"> EzClassify overview and issues

[![license: Apache-2.0](https://img.shields.io/badge/license-Apache_2.0-blue.svg)](LICENSE)

[Report a bug or request a feature](https://github.com/ezclassify/ezclassify/issues/new/choose)
for any EzClassify application or project, and pick the app on the form.
This repository is the central issue tracker and starting point for the
projects below. Report security vulnerabilities privately through
[Security](SECURITY.md).

EzClassify is software for security markings and sensitivity labels. It parses
and validates classification markings, suggests corrections, renders banner and
portion marks, rolls portion marks up into an overall marking, and checks
whether a person may access marked content. Rules ship as versioned data:
IC Classification and Control Markings (CAPCO), Controlled Unclassified
Information (CUI), Traffic Light Protocol (TLP) 2.0, Common Vulnerability
Scoring System (CVSS), or your own scheme.

Every client library and UI component here talks to an EzClassify runtime. The
free developer runtime carries TLP 2.0, CVSS, and demo subsets of CAPCO and CUI.
The full CAPCO and CUI schemes are licensed content.

Against the `capco-demo` Context on the developer runtime, `SECRET//NOFORN`
validates and renders as portion mark `S//NF`. The portion marks `S//NF`, `C`,
and `U` roll up to `SECRET//NOFORN`. `SECRET//NOFORN/REL TO USA, GBR` is
rejected, because NOFORN cannot be combined with REL TO.

[Website](https://ezclassify.com) · [Architecture](docs/architecture.md) ·
[Packages and releases](RELEASES.md) · [Report an issue](https://github.com/ezclassify/ezclassify/issues)

## Integrate with EzClassify

Connect your application to an EzClassify runtime over REST using a
client for JavaScript, Java, .NET, Python, or Go. For browser applications,
add marking fields and autocomplete through the shared UI components and
React, Vue, or Angular bindings.

Your runtime administrator supplies the endpoint and published Context, plus
credentials when the deployment requires authentication. A Context composes a
scheme with its layers, any guides, an optional access policy, and any
crosswalks. Each component can pin an exact version or follow `latest`. The
runtime evaluates the marking and returns canonical results, validation errors,
and access decisions with reasons.
See each client repository for its install instructions and quickstart.

### Open-source repositories

The public integration libraries, contracts, and community schemes use
Apache-2.0. The classification engine and maintained government scheme content
are commercially licensed.

[Packages and releases](RELEASES.md) lists the published packages and their
registries.

| Repository | Purpose |
| --- | --- |
| [JavaScript client](https://github.com/ezclassify/sdk-js) | `@ezclassify/rest-client` for browser and Node.js applications |
| [Web UI](https://github.com/ezclassify/web) | `@ezclassify/ui`, `@ezclassify/react`, `@ezclassify/vue`, and `@ezclassify/angular` |
| [Java client](https://github.com/ezclassify/sdk-java) | `com.ezclassify:ezclassify-rest-client`; Java 17+ |
| [.NET client](https://github.com/ezclassify/sdk-dotnet) | `EzClassify.Rest.Client`; netstandard2.0 and net8.0 |
| [Python client](https://github.com/ezclassify/sdk-python) | `ezclassify-rest-client`; Python 3.11+ |
| [Go client](https://github.com/ezclassify/sdk-go) | `github.com/ezclassify/sdk-go`; Go 1.26.10+ |
| [Contracts](https://github.com/ezclassify/contracts) | Shared types, JSON Schemas, OpenAPI, schema validation, and conformance data |
| [Community content](https://github.com/ezclassify/community-content) | `@ezclassify/schemes`: public schemes, crosswalks, and worked examples |

The clients use the same REST contract and are tested against a shared
conformance corpus. Policy evaluation stays in the licensed runtime.
Applications can also call the HTTP API directly.

## Commercial applications

| Application | Purpose |
| --- | --- |
| **REST API** | Marking and access operations for application integrations |
| **MCP server** | Runtime operations exposed to AI agents through the Model Context Protocol |
| **Studio** | Authoring and lifecycle management for schemes, guides, access policies, and Contexts; signed content delivery to runtimes |

Deploy on your infrastructure, in a cloud environment, or in a disconnected
network. EzClassify also maintains licensed CAPCO and CUI scheme content.
Production use is licensed per named production system.

For pricing, an evaluation, or deployment guidance, contact
[sales@ezclassify.com](mailto:sales@ezclassify.com). Customers who cannot post
on the public tracker, such as air-gapped sites, can reach support at
[support@ezclassify.com](mailto:support@ezclassify.com).

## Schemes are data

A scheme is a YAML document describing a marking vocabulary: its concepts and
categories, parsing and rendering formats, allowed combinations, and aggregation
behavior. Guides connect subject matter to markings; access policies evaluate
whether a subject may read marked content. The runtime validates these
artifacts when it loads them.

The [community content catalog](https://github.com/ezclassify/community-content)
provides public schemes and tested examples. Organizations can author their own
schemes using the same format.

## Contributing and support

- [Contributing](CONTRIBUTING.md): choose a repository and follow its contribution process.
- [Issue tracker](https://github.com/ezclassify/ezclassify/issues/new/choose): bug reports, feature requests, and documentation problems for every product.
- [Security policy](SECURITY.md): report vulnerabilities privately.
- [Code of Conduct](CODE_OF_CONDUCT.md): standards for project participation.

## License

This repository is licensed under Apache-2.0 ([LICENSE](LICENSE)). Each software
repository carries its own license. EzClassify names and logos remain trademarks
of EzClassify, LLC.
