# Architecture

EzClassify has one engine. Public clients use its REST wire contract. The engine
knows how to parse, validate, correct, render, roll up, translate, and
access-check a marking. It runs inside the licensed REST API, MCP server, and
CLI, and Studio uses the same engine while you author content. Public REST
client libraries connect to the API over HTTP.

## The map

```
            community schemes, your own content,
                 licensed EzClassify content
                              |
       authored and signed in Studio, or with the CLI
                              |
                              v
                     signed .ezb bundles
                              |
                     verified on install
                              |
                              v
  +-------------------------------------------------------+
  |    EzClassify runtime: the engine runs in each one    |
  |                                                       |
  |    MCP server         REST API             CLI        |
  +-------------------------------------------------------+
            |                 |                 |
           MCP       HTTP wire contract  terminal, local
            |            /v1/ctx/...     or --remote-url
            v                 |
        AI agents             |
                +-------------+-------------+
                |             |             |
                v             v             v
            browser,     Java, .NET     your own
              Node       Python, Go    HTTP calls
           rest-client     clients
             and ui
                |             |             |
                +-------------+-------------+
                              |
                              v
                      your application
```

## One boundary, five clients

The REST API is the public client contract. The Java, .NET, Python, Go, and
JavaScript clients are thin: wire types, an HTTP client, and the ergonomics that
make the calls pleasant in that language. They hold no marking logic, so there
is no second implementation to drift out of step with the engine.

| Client | Wire models | HTTP transport |
| --- | --- | --- |
| JavaScript | Imports canonical TypeScript contracts | Handwritten `fetch` client |
| Java | Generated from OpenAPI and JSON Schemas | Handwritten `java.net.http` client |
| .NET | Generated from OpenAPI and JSON Schemas | Handwritten `System.Net.Http` client |
| Python | Pydantic models generated from OpenAPI and JSON Schemas | Handwritten `httpx` client |
| Go | Generated from OpenAPI | `oapi-codegen` client with a handwritten public facade |

The shared conformance corpus checks the clients against the same recorded
exchanges. Acceptance against a live deployment is a separate verification lane.

Nothing prevents an application from calling the contract directly. The clients
exist because most teams would rather not hand-roll HTTP and model code.

## Contexts

A Context composes a scheme with its layers, any guides, an optional access
policy, and any crosswalks it uses. Each reference can pin an exact version or
follow `latest`. Pin every component and a Context version always means the
same composition. Follow `latest` and the composition behind that same Context
version changes when a newer component is installed. Access results also depend
on the subject attributes supplied with the request.

A client connects by Context id and version. Requesting `latest` is allowed, and
the response reports the concrete Context version it resolved to. Record that
version for your audit trail. If the Context follows `latest` for any
component, also record the concrete component versions that
`GET /v1/ctx/{ctxId}/{version}` reports: the schemes and their layers, guides,
access policy, and crosswalks. Pin those references when a Context version
must retain the same composition as newer components become available.

## The surfaces that run the engine

- **REST API.** The HTTP wire contract the clients speak, under `/v1/ctx/...`.
- **MCP server.** The core marking operations, exposed as tools over the Model
  Context Protocol for AI agents: validate, process, explain, roll up and
  translate markings, audit the markings in a document, check access to a
  marking or a document, describe what access a marking requires, and list the
  available Contexts.
- **CLI.** Marking and document operations from a terminal, plus scheme
  authoring and testing, bundle signing, and local runtime administration. It
  runs the engine locally, or calls a REST deployment with `--remote-url`.

A result is the same whichever surface produced it. They are doors onto one
engine, not separate implementations.

## Studio and content delivery

**Studio.** Optional authoring and lifecycle management for content artifacts.
Studio signs content into bundles a runtime can load, including in a
disconnected environment. Runtime customers can also sign and install their own
content with the CLI. Studio's `/api/v1` is its own management API; it is not
the wire contract clients call.

The runtime does not need Studio to operate. Production content arrives as
signed `.ezb` bundles, and the runtime authenticates each one when it is
installed. A bundle that fails verification is refused, and the content already
installed keeps serving.

## Disconnected and air-gapped sites

A running deployment keeps serving from verified local state when Studio, the
network, or the licensing service is unavailable. Installed content is
immutable, and an alias such as `latest` keeps its last-known-good resolution
until a newer verified version is installed. The license is read locally from
`EZCLASSIFY_LICENSE_LOCATION`. An expired license raises warnings and audit
records. It does not stop the service.

A new replica with no usable local state stays unready until it can establish
one. Air-gapped sites receive a release kit with image archives and chart
packages, and need no connection back to EzClassify.

## Deployment

The REST API, MCP server, and Studio run as containers. Their Helm charts are
published at `oci://ghcr.io/ezclassify/charts`: `ezclassify-api`,
`ezclassify-mcp`, `ezclassify-studio`, `ezclassify-studio-api`, and
`ezclassify-studio-web`. The three Studio charts matter only if you run Studio.

## Schemes are data

A scheme defines the vocabulary: the concepts, their categories, how they parse,
which combinations are legal, how a set of markings rolls up into one, and how
each form renders. A guide adds guide rules that connect subject matter to a
marking. An access policy evaluates a subject's attributes against access rules
and returns a decision with reasons. A crosswalk translates a marking from one
scheme to another, and can refuse a translation outright.

All four are versioned data the runtime loads and validates. Public schemes
live in the [community-content](https://github.com/ezclassify/community-content)
repository. Organizations author their own the same way. EzClassify also
maintains licensed content for IC Classification and Control Markings (CAPCO)
and Controlled Unclassified Information (CUI).

## The web layer

`@ezclassify/ui` runs in the browser and provides marking fields, suggestions,
tooltips and display of rendered markings, with React, Vue, and Angular bindings
over one shared core. The components call an engine-compatible adapter. The
supported adapter is `@ezclassify/rest-client`, connected to a licensed REST
deployment.

You can start before you have a runtime. The Cedar Valley replay server answers
over real HTTP with recorded responses, so the same client and components work
against it:

```bash
npx @ezclassify/conformance-server --scenario cedar-valley --port 4010
```

Moving to a real runtime means pointing `baseUrl` at it and supplying real
credentials. The
[conformance server guide](https://github.com/ezclassify/contracts/tree/main/packages/conformance-server#testing-an-application-integration)
lists the requests the scenario covers.

The EzClassify website separately embeds the engine for its interactive
demonstrations, which run in the browser.
