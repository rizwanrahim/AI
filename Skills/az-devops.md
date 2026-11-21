---
name: az-devops
description: Fetch Azure DevOps work item details (User Stories, Bugs, Tasks) by URL or ID using the AZDO_PAT environment variable and save the extracted ID, title, description, and acceptance criteria or repro steps into a Markdown (.md) file. Use whenever the user provides an Azure DevOps work item URL or ID (e.g., #12345) or asks to fetch, extract, or export Azure DevOps story or bug details.
---

# az-devops

Fetch Azure DevOps work items via the REST API using `AZDO_PAT` and save their details into a Markdown file.

## When to Use

- The user provides an Azure DevOps work item URL or ID (e.g., `#12345`).
- The user asks to fetch, extract, or save a User Story or Bug into a `.md` file.

## Workflow

- Extract the work item `id` (and `org` / `project` from the URL, or check `.git/config` if omitted).
- Verify `AZDO_PAT` is set; if missing, ask the user to configure it before retrying.
- Query `GET https://dev.azure.com/{org}/{project}/_apis/wit/workitems/{id}?$expand=all&api-version=7.1` with header `Authorization: Basic <base64(:$AZDO_PAT)>`.
- Extract `id`, `System.WorkItemType`, `System.Title`, and `System.Description`.
- Extract `Microsoft.VSTS.TCM.ReproSteps` if `System.WorkItemType` is `Bug`, or `Microsoft.VSTS.Common.AcceptanceCriteria` otherwise.
- Convert HTML fields into clean Markdown (use `_None provided._` if empty).
- Save the `.md` file inside `<workspace-root>/Project file/DevOps/` (for example, `Project file/DevOps/work-item-{id}.md`, creating the directories if they do not exist) with sections for Metadata, Description, and Acceptance Criteria or Repro Steps.

## Gotchas

- Prepend a colon (`:$AZDO_PAT`) before Base64-encoding the Basic auth token.
- Convert raw HTML markup from Azure DevOps fields to clean Markdown before writing the `.md` file.
