## Development Guidelines

This document intends to establish guidelines which build a transparent, open mechanism for deciding how to evolve the OpenAPI Specification. The OpenAPI Technical Steering Committee (TSC) will initially follow these processes when merging changes from external contributors or from the TSC itself. This guideline document will be adjusted as practicality dictates.

### Essential Policies

If in doubt about a policy, please [ask on our Slack](https://communityinviter.com/apps/open-api/openapi) before opening a PR.

#### No changes to published specifications

No changes, ***no matter how trivial***, are ever made to the contents of published specifications.  The only potential changes to those documents are updates to link URLs _if and only if_ the targeted document is moved by a 3rd party.  Other changes to link URLs are not allowed.

#### Current branches and documents open to change

The first PR for a change should be against the oldest release line to which it applies.  Changes can then be forward-ported as appropriate.

The current (February 2024) active releases are:

| Version | Branch | File |
| ------- | ------ | ---- |
| 3.0.4 | `v3.0.4-dev` | `versions/3.0.4.md` |
| 3.1.1 | `v3.1.1-dev` | `versions/3.1.1.md` |
| 3.2.0 | `v3.2.0-dev` | `versions/3.2.0.md` |
| 4.0.0 | [OAI/sig-moonwalk](https://github.com/OAI/sig-moonwalk) | [discussions only](https://github.com/OAI/sig-moonwalk/discussions) |

#### Changing the schemas

Schemas are only changed _after_ the specification is changed.  Changes are made on the `main` branch, and should be made to the YAML version _only_.  The JSON version will be generated automatically.

## OAI Specification Driving factors

The OpenAPI Specification should be use-case driven. We can specify support for hypothetical use cases as we see fit, but specifications should be backed by realistic scenarios.

## Specification Change Criteria

The specification *will evolve over time*. Changes  may be made when any of the following criteria are met:

* Clarity. The current "way" something is done doesn't make sense, is complicated, or not clear.

* Consistency. A portion of the specification is not consistent with the rest, or with the industry standard terminology.

* Necessary functionality. We are missing functionality because of a certain design of the specification.

* Forward-looking designs. As usage of APIs evolves to new protocols, formats, and patterns, we should always consider what the next important functionality should be.

* Impact. A change will provide impact on a large number of use cases. We should not be forced to accommodate every use case. We should strive to make the *common* and *important* use cases both well supported and common in the definition of the OAI Spec. We cannot be edge-case driven.

## Specification Change Process

For each change in the specification we should *always* consider the following:

* Migration. Is this a construct that has a path from the [existing specification](https://github.com/OAI/OpenAPI-Specification/releases)? If so, how complicated is it to migrate to the proposed change?

* Tooling. Strive to support code generation, software interfaces, spec generation techniques, as well as other utilities. Some features may be impossible to support in different frameworks/languages. These should be documented and considered during the change approval process.

* Visualization. Can the specification change be graphically visualized somehow in a UI or other interface?

Spec changes should be approved by a majority of the committers. Approval can be given by commenting on the issue itself, for example, "Approved by @webron" however at least one formal GitHub-based  flow approval must be given. After voting criteria is met, any committer can merge the PR. No change should be approved until there is documentation for it, supplied in an accompanying PR. 

### Proposals for Specification Changes

As an organisation, we're open to changes, and these can be proposed by anyone.
The specification is very widely adopted, and there is an appropriately high bar for wide appeal and due scrutiny as a result.
We do not accept changes lightly (but we will consider any that we can).

Small changes are welcome as pull requests.

Bigger changes require a more formal process.

1. Start a [discussion](https://github.com/OAI/OpenAPI-Specification/discussions) of type "Enhancements".
   The discussion entry must include some use cases, your proposed solution and the alternatives you have considered.
   If there is engagement and support for the proposal over time, then it can be considered as a candidate to move to the next stage.

2. It really helps to see the proposed change in action.
   Start using it as a `x-*` extension if that's appropriate, or try to bring other evidence of your proposed solution being adopted.

3. If you are adding support for something from another specification (such as OAuth), please point to implementations of that
   specification so that we can understand how, and to what degree, it is being used.

4. If the suggested change has good support, you will be asked to create a formal proposal.
   Use the [template in the proposals directory](https://github.com/OAI/OpenAPI-Specification/tree/main/proposals), copy it to a new file, and complete it.
   Once you the document is ready, open a pull request.

5. The proposal will be more closely reviewed and commented on or amended until it is either rejected or accepted.
   At that point, the proposal is merged to the `main` branch and a final pull request is opened to add the feature to the appropriate version of the specification.

Questions are welcome on the process and at any time. Use the discussions feature or find us in Slack.

## Tracking Process

* GitHub is the medium of record for all spec designs, use cases, and so on.

* The **human readable** document is the source of truth. If using a JSON Schema again to document the spec, it is secondary to the human documentation. The documentation should live in a *.md file, in parallel to the latest document (versions/3.0.0.md for example).

* At any given time, there would be *at most* 4 work branches. The branches would exist if work has started on them. Assuming a current version of 3.0.0:

    * main - Current stable version. No PRs would be accepted directly to modify the specification. PRs against supporting files can be accepted.

    * v3.0.1-dev - The next PATCH version of the specification. This would include non-breaking changes such as typo fixes, document fixes, wording clarifications.

    * v3.1.0 - The next MINOR version.

    * v4.0.0 - The next MAJOR version.

* The main branch shall remain the current, released OpenAPI Specification. We will describe and link the work branch(es) on the **default** README.md on main.

* Examples of how something is described *currently* vs. the proposed solution should accompany any change proposal.

* New features should be done in feature branches/forks which, upon approval, are merged into the proper work branch.

* Use labels for the workflow of specification changes. Examples of labels are proposed, housekeeping, migration-review, tooling-, needs documentation, review (candidate for upcoming TSC mtg), rejected, and needs approval. These labels must be assigned by project committers. Style is lowercase with dashes in place of spaces.

* An issue will be opened for each feature change. Embedded in the issue, or ideally linked in a file via pull-request (PR), a document about use cases should be supplied with the change.

* A PR will be used to describe the *proposed* solution and linked to the original issue.

* Not all committers will contribute to every single proposed change. There may be many open proposals at once, and multiple efforts may happen in parallel.

* When the work branch is ready and approved, the branch will be merged to main.

## Release Process

A release requires a vote on the release notes by TSC members within the voting period. Major or minor release voting periods will be announced by the Liaison in the Slack channel and noted on the calendar at least 6 days in advance. During this time, TSC members who have not yet voted must note their approval on the GitHub pull request for the release notes. Patch releases happen at the first TSC meeting of a calendar month. The Liaison is responsible for coordinating the actual merge to main with marketing support, if any.

* Patch-level releases require majority approval by TSC members. (Max voting period 3 days)

* Minor: requires approval by 66% of TSC members. (Max voting period 7 days)

* Major: requires approval by 66% of TSC members. (Max voting period 14 days)

## Transparency

The process should be as transparent as possible. Sometimes there will be discussions that use customer names, sensitive use cases, and so on. These must be anonymized, discussed in a private repository, or conducted offline. General discussions should happen on the GitHub issues for this project.

## Automated closure of issues Process

In an effort to keep the list of issues up to date and easier to navigate through, issues get closed automatically when they become inactive.

This process makes use of the following labels:

* Needs author feedback: the issue has been replied to by the triage team and is awaiting a follow up from the issue's author. This label needs to be added manually by people doing triage/experts whenever they reply. It's removed automatically by the workflow.
* No recent activity: the issue hasn't received a reply from its author within the last 10 days since `Needs author feedback` was added and will be closed within 28 days if the author doesn't follow up. This label is added/removed automatically by the workflow.
* Needs attention: The issue's author has replied since the `Needs author feedback` label was set and the triage team will reply as soon as possible. This label needs to be removed manually by people doing triage/experts whenever they reply. It's added automatically by the workflow.

## Automated TDC agenda issues Process

An issue is opened every week, 7 days in advance, for the Technical Direction Committee (TDC), it provides the information to connect the the meeting, and serves as a placeholder to build the agenda for the meeting. Anyone is welcome to attend the meeting, or to add items to the agenda as long as they plan on attending to present the item. These issues are also automatically pinned for visibility and labeled with "Housekeeping".

Ten (10) days after the meeting date is passed (date in the title of the issue), it gets closed and unpinned automatically.

## Participation

While governance of the specification is the role of the TSC, the evolution of the specification happens through the participation of members of the developer community at large. Any person willing to contribute to the effort is welcome, and contributions may include filing or participating in issues, creating pull requests, or helping others with such activities.

## Community Roles

While these developer community roles are informal, there are many ways to get involved with the OpenAPI community, such as:

* Contributor: Includes but is not limited to any [contributor to the specification](https://github.com/OAI/OpenAPI-Specification/graphs/contributors) via an accepted pull request or who participates in issues or TSC calls.

* Implementer: any person involved in the creation or maintenance of tooling that leverages the current OpenAPI Specification

* Ambassador: represents the OpenAPI Specification to the developer community. This could be through talks at conferences or meetups, blog posts, or answering questions in places like Twitter, Stack Overflow, or the GitHub repo.

* Supporter: uses the specification and appreciates its value. 
