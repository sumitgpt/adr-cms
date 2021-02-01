---
permalink: /about/
title: "Architecture Decision Records (ADR)"
---

## Background - what is ADR?

Lightweight Architecture Decision Record (ADR) was popularised by [ThoughtWorks](https://www.thoughtworks.com/radar/techniques/lightweight-architecture-decision-records) in their Technology Radar in 2016

> Much documentation can be replaced with highly readable code and tests.
> In a world of evolutionary architecture, however, it's important to record
> certain design decisions for the benefit of future team members as well as
> for external oversight.
> Lightweight Architecture Decision Records is a technique for capturing important
> architectural decisions along with their context and consequences. We recommend
> storing these details in source control, instead of a wiki or website, as then
> they can provide a record that remains in sync with the code itself. For most
> projects, we see no reason why you wouldn't want to use this technique.

An architecture decision record is a short text file in a format similar to an Alexandrian pattern. (Though the decisions themselves are not necessarily patterns, they share the characteristic balancing of forces.)

Each record describes a set of forces and a single decision in response to those forces. Note that the decision is the central piece here, so specific forces may appear in multiple ADRs.

[Example](https://github.com/deshpandetanmay/lightweight-architecture-decision-records/blob/master/doc/adr/0001-use-elasticsearch-for-search-api.md)

## Why shall we use ADRs

We need a mechanism for capturing all architectural decisions where creating large amounts of documentation which nobody likes to read wouldn't help. This means that the process needs to be lightweight and easy-to-use, yet keeping a full track record of all decisions.

One of the hardest things to track during the life of a project is the motivation behind certain decisions. A new person coming on to a project may be perplexed, baffled, delighted, or infuriated by some past decision. Without understanding the rationale or consequences, this person has only two choices:

1. **Blindly accept the decision**<br>
   This response may be OK, if the decision is still valid. It may not be good, however, if the context has changed and the decision should really be revisited. If the project accumulates too many decisions accepted without understanding, then the development team becomes afraid to change anything and the project collapses under its own weight.

2. **Blindly change it**<br>
   Again, this may be OK if the decision needs to be reversed. On the other hand, changing the decision without understanding its motivation or consequences could mean damaging the project's overall value without realizing it. (E.g., the decision supported a non-functional requirement that hasn't been tested yet.)

## When to create an ADR

Create ADRs for **architecturally significant** decisions.
> Architecturally significant decisions are those that affect the structure, non-functional characteristics, dependencies, interfaces or construction techniques.

Some examples are:
* major architectural decisions introducing breaking changes that impact other squads
* complex technical design with multiple options where a peer-review is desirable

## Content of an ADR

An ADR should be simple to read, not more than 2 pages!<br>
An ADR can contain images/diagrams if it helps understanding the context/decision.<br><br>
The content of the ADR can have the following sections:<br>

* **Title** - Title of the decision record
* **Date** - Date of last update
* **Status** - Status can be `draft, proposed, accepted, rejected` or `superseded`
* **Context** - What is the context of this decision? It is important to capture
  the full context of the decision so that the reader knows the reasons behind
* **Decision** - The decision that was made
* **Consequences** - In this section, you can add what would happen if this decision
  is made. The idea here is to keep it light so people can read it.

ADR Template can be found at path ./_drafts/template.md

## Lifecycle of an ADR

**Prerequisite:** Problem at hand qualifies for an ADR (see [when to create an ADR](#when-to-create-an-adr))
1. Copy the ADR template from _drafts into _posts directory as `<date-title>.md`
2. Fill in the template, once ready to share, set the status to `proposed`
3. If your ADR contains images, create an `img` sub-directory in your ADR directory
4. Set up a meeting with your squad (invite anyone outside the squad where you see a need, eg. Stakeholders inside/outside tribe)
5. Meeting (**Outcome:** consent on the decision, share the ADR after update)
6. Update the `Decision` in the ADR based on the meeting
7. Change the `Status` based on the decision from the meeting
8. Update the `Review date` based on the agreement in the meeting
9. In case the ADR was rejected, it is desirable to add a section `Reason for rejection` below
   the `Status` section, giving a short explanation on the reason for rejection
10. Set a reminder for yourself based on the `Review date` (eg. calendar reminder/invite) [until we have a solution to automate it]
11. Once the review date has come, agree with team whether the previous ADR decision is still valid, or whether a new ADR is required to change direction (supersede previous decision)

**Note:** ADRs are immutable. If a decision is reversed, we create a new ADR and keep the old one around, but mark it as `superseded`.
