# 1099Policy MCP server

Connect an AI assistant to your 1099Policy account and ask about contractor insurance in plain language: who has active coverage, whether a contractor meets a client's requirements, why a certificate was flagged, and what it would cost to cover someone on a job.

This is a hosted server. This repository holds its registry listing and documentation, not its source code.

- **Endpoint:** `https://mcp.1099policy.com/mcp` (Streamable HTTP)
- **Authentication:** OAuth 2.1. You approve the connection in your 1099Policy dashboard and choose which organizations it can reach, live data or sandbox, and read-only or read-and-write.
- **Documentation:** https://www.1099policy.com/docs/mcp
- **Tool reference:** https://www.1099policy.com/docs/mcp-tools

## Configure

You need a 1099Policy account. Point your MCP client at the endpoint and approve the connection when your browser opens.

VS Code and GitHub Copilot (`.vscode/mcp.json`):

```json
{
  "servers": {
    "1099policy": {
      "type": "http",
      "url": "https://mcp.1099policy.com/mcp"
    }
  }
}
```

Other clients: add a remote MCP server with the same URL.

## Use

Ask your assistant things like:

- "Who on our account has no active insurance coverage right now?"
- "Show our coverage as a chart."
- "Across all our organizations, how many contractors are uncovered?"
- "Why was the certificate our videographer sent flagged?"
- "Who was sent an insurance application and hasn't finished it?"
- "What would it cost to cover a freelance set designer on the Denver install?"

## What it can do

| Area | Tools |
|---|---|
| Coverage | `checkCoverage`, `findCoverageGaps`, `getPortfolioCoverage`, `showCoverageChart`, `listActivePolicies` |
| Certificates | `reviewCertificate`, `submitCertificate`, `openCertificateUpload`, `getUploadedCertificate`, `listUploadedCertificates`, `getIssuedCertificate`, `listInsuranceRequirements` |
| Contractors | `listContractors`, `createContractor`, `createLoginLink` |
| Jobs | `listJobs`, `createJob`, `listCategoryCodes` |
| Premium estimates | `estimatePremium`, `listPremiumEstimates` |
| Assignments | `listAssignments`, `bindAssignment`, `extendAssignment`, `cancelAssignment` |
| Insurance applications | `getInsuranceApplication`, `listInsuranceApplications`, `createInsuranceApplicationLink` |
| Billing | `listInvoices` |
| Organization and team | `listEntities`, `listTeamMembers`, `inviteTeamMember`, `removeTeamMember`, `getAuditTrail`, `listOrganizations`, `switchOrganization` |
| Classification | `analyzeContract`, `listClassificationStates` |

Tools that change records are offered only on connections approved to make changes, and your assistant asks before running them. Contract analysis is an automated heuristic, not legal advice.

## Support

Email integration@1099policy.com. Privacy policy: https://www.1099policy.com/legal/privacy

Insurance services are provided by 1099Policy Insurance Agency, LLC.
