# Issue labels

These labels must exist in [ezclassify/ezclassify](https://github.com/ezclassify/ezclassify). The issue forms apply a
type label and `triage` when an issue is opened, and GitHub skips any form
label that does not exist. The issue labeler adds one app label from the
form's "What are you using?" answer, and one language label from its optional
"Client library language" answer. The two bug forms, "Bug in a deployed app" and
"Bug in a library, UI component or the website", each offer the apps that fit
them, and an app maps to the same label on either form.

## Type and triage

| Label | Color | Description | Applied by |
| --- | --- | --- | --- |
| `bug` | `d73a4a` | Something isn't working | Both bug forms |
| `enhancement` | `a2eeef` | New feature or request | Feature request form |
| `documentation` | `0075ca` | Improvements or additions to documentation | Documentation form |
| `triage` | `fbca04` | Waiting for a maintainer to review | Every form |

Remove `triage` once a maintainer has confirmed the report and its app.

## Apps

| Label | Color | Description | Form answer |
| --- | --- | --- | --- |
| `app: studio` | `c5def5` | EzClassify Studio | Studio |
| `app: rest-api` | `c5def5` | REST API | REST API |
| `app: mcp-server` | `c5def5` | MCP server | MCP server |
| `app: cli` | `c5def5` | CLI | CLI |
| `app: sso` | `c5def5` | EzClassify SSO | EzClassify SSO |
| `app: ui` | `c5def5` | UI components (vanilla, React, Angular, Vue) | UI components (vanilla, React, Angular, Vue) |
| `app: rest-client` | `c5def5` | REST client library | REST client library |
| `app: schemes` | `c5def5` | Marking schemes and content | Marking schemes and content (community and licensed schemes, crosswalks) |
| `app: deployment` | `c5def5` | Installation and deployment | Installation and deployment (Helm charts, container images, air-gapped install) |
| `app: website-docs` | `c5def5` | Website and documentation | Website and documentation |

"Not sure" has no app label. To assign one, edit the issue's "What are you
using?" answer. The labeler keeps the app label in step with that answer, so an
app label added by hand that does not match the answer is removed the next time
the issue is edited.

## Client library language

| Label | Color | Description | Form answer |
| --- | --- | --- | --- |
| `lang: javascript` | `d4c5f9` | JavaScript REST client library | JavaScript |
| `lang: java` | `d4c5f9` | Java REST client library | Java |
| `lang: dotnet` | `d4c5f9` | .NET REST client library | .NET |
| `lang: python` | `d4c5f9` | Python REST client library | Python |
| `lang: go` | `d4c5f9` | Go REST client library | Go |

The language answer is optional and applies only to the REST client library
app. It is labeled on its own, so an issue can carry `app: rest-client` and a
language label, or an app label alone.

A new app needs three edits together: an option in each form under
[`ISSUE_TEMPLATE/`](ISSUE_TEMPLATE/) that applies to it, a pattern in [`issue-labeler.yml`](issue-labeler.yml), and a row here. A new
client library language works the same way.

## Dependency updates

| Label | Color | Description | Applied by |
| --- | --- | --- | --- |
| `dependencies` | `0366d6` | Dependency update | Dependabot |
| `ci` | `ededed` | Continuous integration | Dependabot (GitHub Actions updates) |
