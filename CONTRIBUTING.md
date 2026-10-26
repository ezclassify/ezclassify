# Contributing to EzClassify

Contributions are welcome across the public integration surface: the client libraries, the UI components, and the public marking
schemes. The engine and the applications that run it are commercial software
and follow a separate internal contribution process.

This file is the project-wide overview. Some repositories also carry their own
CONTRIBUTING file covering the toolchain and the conventions for that language.
Read this first, then that one if the repository you are targeting has it.

## Pick the right repository

| You want to change | Repository |
| --- | --- |
| The browser and Node REST client | [ezclassify/client-js](https://github.com/ezclassify/client-js) |
| The UI components or the React, Vue, and Angular bindings | [ezclassify/web](https://github.com/ezclassify/web) |
| A REST client for Java, .NET, Python, or Go | [ezclassify/client-java](https://github.com/ezclassify/client-java), [ezclassify/client-dotnet](https://github.com/ezclassify/client-dotnet), [ezclassify/client-python](https://github.com/ezclassify/client-python), [ezclassify/client-go](https://github.com/ezclassify/client-go) |
| The wire types, the JSON Schemas, the OpenAPI document, or the conformance corpus | [ezclassify/contracts](https://github.com/ezclassify/contracts) |
| A public marking scheme | [ezclassify/community-content](https://github.com/ezclassify/community-content) |
| This documentation | [ezclassify/ezclassify](https://github.com/ezclassify/ezclassify) |

Each repository builds and tests on its own. Its CONTRIBUTING guide links the toolchain and development commands it
needs.

## Sign your commits

**Pending counsel review. This section records the intended contribution process
and is not a legal conclusion.**

Contributions are accepted under the Developer Certificate of Origin 1.1. There
is no separate agreement to sign and nothing to send us. You certify the
statement by adding a `Signed-off-by` line to each commit, and `git commit -s`
writes that line for you from your git configuration.

The full text is in [DCO.md](DCO.md). It is the single text for every public
EzClassify repository, and each of them follows the same process.

## The contribution loop

1. Fork the repository and create a branch.
2. Make your change. Match the code around it: its style, its naming, its test
   conventions.
3. Add tests. New behavior gets a test that fails without the change.
4. Build and test in that repository, as its contribution guide describes.
5. Sign off every commit with `git commit -s`.
6. Open a pull request against `main`. Keep the commits focused and the message
   honest about the whole diff.

## What a good change looks like

- Scoped. A docs change touches docs. A fix touches the thing it fixes.
  Reformatting does not ride along with a feature.
- Tested. The test would fail without your change.
- Consistent. It reads like the code already around it.

## Schemes

Marking schemes are data. A new public scheme goes in
[ezclassify/community-content](https://github.com/ezclassify/community-content). Its contribution guide describes schema
validation and behavior suites. Passing those checks verifies the submitted
cases; source review is also needed to establish domain accuracy.

## Third-party code

Keep third-party code and its license out of a contribution unless the license
is compatible with the repository you are contributing to and the attribution is
clear.

## Report a bug or request a feature

Every EzClassify product shares one issue tracker in this repository, including
the commercial applications whose source is private.
[Open an issue](https://github.com/ezclassify/ezclassify/issues/new/choose),
and choose a form. Use "Bug in a deployed app" for Studio, the REST API, the
MCP server, the CLI, EzClassify SSO, or an installation; it asks where you run
the app and what you have already tried. Use "Bug in a library, UI component or
the website" for a package, a UI component, a marking scheme, or the website.
Feature requests and documentation problems have their own forms. Pick the app
you are using under "What are you using?" so the report reaches the right
maintainers, or "Not sure" on the forms that offer it. For a REST client
library, also pick its language.

The tracker is public. Never post classified information, CUI, real marked
documents, credentials, tokens, or customer data; use synthetic examples
instead. If you cannot post publicly, for example from an air-gapped site,
email support@ezclassify.com.

Open an issue before starting a non-trivial change, so the approach is agreed
before you put in the work.

## Reporting security issues

Do not open a public issue for a security vulnerability. Email
security@ezclassify.com. That address covers every EzClassify repository and
application. The affected repository's SECURITY policy, or [the one in this
repository](SECURITY.md), describes what to include and what to expect.

## Code of Conduct

This project follows our [Code of Conduct](CODE_OF_CONDUCT.md). By
participating, you are expected to uphold it.
