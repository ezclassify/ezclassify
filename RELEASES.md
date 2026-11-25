# Releases and packages

Install the public client libraries and schemes from the registries below.
This repository hosts the [product releases](https://github.com/ezclassify/ezclassify/releases).
Each release contains coordinated product release notes. Package registry
pages list available package versions; component repositories carry
the corresponding version tags and changelogs.

## Public package registries

| Package | Registry | Repository |
| --- | --- | --- |
| `@ezclassify/rest-client` | npm | [ezclassify/sdk-js](https://github.com/ezclassify/sdk-js) |
| `@ezclassify/ui`, `@ezclassify/react`, `@ezclassify/vue`, `@ezclassify/angular` | npm | [ezclassify/web](https://github.com/ezclassify/web) |
| `@ezclassify/tsconfig`, `@ezclassify/types`, `@ezclassify/schemas`, `@ezclassify/openapi`, `@ezclassify/conformance`, `@ezclassify/validator`, `@ezclassify/conformance-server` | npm | [ezclassify/contracts](https://github.com/ezclassify/contracts) |
| `com.ezclassify:ezclassify-rest-client` | Maven Central | [ezclassify/sdk-java](https://github.com/ezclassify/sdk-java) |
| `EzClassify.Rest.Client` | NuGet | [ezclassify/sdk-dotnet](https://github.com/ezclassify/sdk-dotnet) |
| `ezclassify-rest-client` | PyPI | [ezclassify/sdk-python](https://github.com/ezclassify/sdk-python) |
| `github.com/ezclassify/sdk-go` | Go modules | [ezclassify/sdk-go](https://github.com/ezclassify/sdk-go) |
| `@ezclassify/schemes` | npm | [ezclassify/community-content](https://github.com/ezclassify/community-content) |

## The applications

The REST API, the MCP server, and Studio are commercial applications,
not libraries. They are distributed as container images and archives under their
own license terms, obtained through EzClassify rather than from a public package
registry. The engine is never published as a consumable library.

## Versioning

Versions are coordinated so the applications and the clients that talk to them
move together. The [product release notes](https://github.com/ezclassify/ezclassify/releases)
describe each coordinated version. Component tags and changelogs provide
package-specific details.
