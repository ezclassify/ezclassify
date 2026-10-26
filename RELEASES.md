# Releases and packages

Install the public client libraries and schemes from the registries below.
This repository hosts the [product releases](https://github.com/ezclassify/ezclassify/releases).
Each release contains coordinated product release notes. Package registry
pages list available package versions; component repositories carry
the corresponding version tags and changelogs.

## Public package registries

| Package | Registry | Repository |
| --- | --- | --- |
| `@ezclassify/rest-client` | npm | [ezclassify/client-js](https://github.com/ezclassify/client-js) |
| `@ezclassify/ui`, `@ezclassify/react`, `@ezclassify/vue`, `@ezclassify/angular` | npm | [ezclassify/web](https://github.com/ezclassify/web) |
| `@ezclassify/tsconfig`, `@ezclassify/types`, `@ezclassify/schemas`, `@ezclassify/openapi`, `@ezclassify/conformance`, `@ezclassify/validator`, `@ezclassify/conformance-server` | npm | [ezclassify/contracts](https://github.com/ezclassify/contracts) |
| `com.ezclassify.rest:client` and `:contract`, over the `com.ezclassify.rest:sdk-parent` parent POM | Maven Central | [ezclassify/client-java](https://github.com/ezclassify/client-java) |
| `EzClassify.Rest.Client` and `EzClassify.Rest.Contract` | NuGet | [ezclassify/client-dotnet](https://github.com/ezclassify/client-dotnet) |
| `ezclassify-rest-client` and `ezclassify-rest-contract` | PyPI | [ezclassify/client-python](https://github.com/ezclassify/client-python) |
| `github.com/ezclassify/client-go` | Go modules | [ezclassify/client-go](https://github.com/ezclassify/client-go) |
| `@ezclassify/schemes` | npm | [ezclassify/community-content](https://github.com/ezclassify/community-content) |

## The applications

The REST API, the MCP server, the CLI, and Studio are commercial applications,
not libraries. They are distributed as container images and archives under their
own license terms, obtained through EzClassify rather than from a public package
registry. The engine is never published as a consumable library.

## Versioning

Versions are coordinated so the applications and the clients that talk to them
move together. The [product release notes](https://github.com/ezclassify/ezclassify/releases)
describe each coordinated version. Component tags and changelogs provide
package-specific details.
