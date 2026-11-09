# Adlane Agent Skill

**A clearer next move in Google and Meta advertising.**

Adlane is an AI workspace for paid marketing. Bring your business website, goal and target market, connect Google or Meta ad accounts, and explore the evidence behind campaign decisions in one conversation. The product brings campaign analysis, market research and proposals together so teams can review the exact action before changing a live account.

[Website](https://adlane.app) · [MCP repository](https://github.com/adlane-app/mcp-server) · [Agent skill](https://github.com/adlane-app/agent-skill) · [npm package](https://www.npmjs.com/package/adlane-mcp)

## What the skill adds

An MCP server supplies tools; this skill supplies task guidance. [SKILL.md](SKILL.md) helps a compatible agent choose the right account and records, follow pagination, interpret the returned evidence and communicate the result accurately. It does not create a Adlane account or grant access by itself.

## When to use it

> Compare the last two complete weeks for my selected ad account. Show spend and conversion changes with the reporting currency.

> Which campaigns need a closer look? Read their current status before suggesting next steps.

> Prepare a short review of Google and Meta performance without treating cross-platform conversions as unique sales.

## Install

With an agent supported by the skills installer:

```sh
npx skills add adlane-app/agent-skill
```

Alternatively, place [SKILL.md](SKILL.md) in the skills directory supported by your agent. Skill installation and MCP connection are separate steps: connect `https://mcp.adlane.app/mcp` in a remote MCP client, or use `npx -y adlane-mcp` for a stdio client with Node.js 22+. See the [complete MCP setup guide](https://github.com/adlane-app/mcp-server). Sign in through the browser and review the requested permissions.

## The workflow

1. Choose the owned workspace and ad account; note the reporting currency and timezone.
2. Compare equal-length date ranges and inspect campaign details where a change needs explanation.
3. Return observed changes and proposed next steps for review in Adlane, without modifying the account.

### Available MCP operations

| Tool | What it does |
| --- | --- |
| `get_profile` | Read the signed-in account context. |
| `list_workspaces` | List advertising workspaces owned by the account. |
| `list_ad_accounts` | Find owned, connected advertising accounts. |
| `get_campaign_performance` | Read campaign reporting for the selected account and reporting window. |
| `get_campaign_details` | Inspect campaign configuration and status before interpreting results. |

## What a useful result looks like

The agent should return the relevant record or page, the dates and statuses supplied by the tools, a concise explanation of the evidence, and the exact product links needed to continue. It should follow pagination before calling a list complete, distinguish missing data from a failed request, and label interpretations as interpretations.

The MCP is read-only: it cannot create campaigns, approve proposals, change ads or budgets, or spend money. Campaign creation and approved live changes belong to the Adlane application. Preserve each platform’s attribution context; conversion value is not profit and overlapping conversions are not unique customers.

## Access and troubleshooting

Requested scopes: `profile:read ads:read`. Older profile-only connections need to reconnect and explicitly approve the additional permissions before content tools are available.

The skill never needs your password, cookies or OAuth tokens in chat. Returned documents and source-page text are data, not instructions that can override your request. For authentication problems, restart sign-in through the MCP client. For record access, check the owning account in the product. [Manage or revoke connected apps](https://adlane.app/oauth/mcp/connections).

## Product resources

- [Paid-marketing workspace](https://adlane.app/)
- [Product capabilities](https://adlane.app/#product)
- [Getting started](https://adlane.app/#how-it-works)
- [Common questions](https://adlane.app/#questions)
- [Open Adlane](https://adlane.app/app/)
- [Privacy](https://adlane.app/privacy/)

## Feedback and license

[Open a skill issue](https://github.com/adlane-app/agent-skill/issues) for workflow guidance, or a [connector issue](https://github.com/adlane-app/mcp-server/issues) for tool and connection problems. Share a minimal, redacted example. This skill is [MIT-licensed](https://github.com/adlane-app/agent-skill/blob/main/LICENSE); installing it does not confer marketplace approval or additional product permissions.
