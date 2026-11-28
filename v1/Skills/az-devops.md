---
name: az-devops
description: Fetches an Azure DevOps work item by URL or ID using AZDO_PAT and saves it to a Markdown file. Use when the user gives a work item URL or ID (e.g., #12345) or asks to export a story or bug.
---

# az-devops

1. Get `id`, `org`, and `project` from the URL (or `.git/config`).
2. If `AZDO_PAT` is unset, ask the user to set it.
3. `GET https://dev.azure.com/{org}/{project}/_apis/wit/workitems/{id}?$expand=all&api-version=7.1`
   Header: `Authorization: Basic base64(":" + AZDO_PAT)`
4. Read `System.WorkItemType`, `System.Title`, `System.Description`, plus:
   - Bug: `Microsoft.VSTS.TCM.ReproSteps`
   - Other: `Microsoft.VSTS.Common.AcceptanceCriteria`
5. Convert HTML to Markdown. Use `_None provided._` for empty fields.
6. Save to `<workspace-root>/Project file/DevOps/work-item-{id}.md` with sections: Metadata, Description, Acceptance Criteria or Repro Steps.

Gotchas:
- The colon comes before the PAT when encoding.
- No raw HTML in the output file.
