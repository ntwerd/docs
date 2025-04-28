<!--
Copy this file into your repository’s `doc/adr/` folder.
Name the file using the pattern: NNN-title-with-dashes.md
Where NNN is a monotonically increasing integer.
-->

#### **000: Title here**
<!--  
*A short, human-readable summary of the architectural decision.*  
☑ Keep it under ~50 chars.  
☑ Use imperative mood (“Adopt PostgreSQL for…”, “Introduce CQRS for…”).  
☑ Avoid jargon an outsider wouldn’t understand.  
-->

**Status: 📝 **RFC****
<!--  
- 📝**RFC** – under discussion, not binding.
- 🚧**Proposed** – under discussion, not binding.  
- ✅**Accepted** – agreed and in effect.  
- 🔄**Superseded** – replaced by a newer ADR (link it).  
- ❌**Rejected** – considered but not adopted.  
- 🗑️**Deprecated** – was accepted but no longer recommended.  
Include the decision date (YYYY-MM-DD).  
-->

#### **Context**
We need to simplify how we store customer survey responses. The data
currently resides in a relational store, and its rigid schema requirements
have become challenging as we evolve the surveys (for example, introducing
different or extended surveys for our premium customers).

There are various options available to us, like the JSONB data type in
PostgreSQL or document stores such as MongoDB.
<!--  
☑ Describe the business/technical forces, constraints, and goals.  
☑ Summarize relevant background and “problem statement”.  
☑ List key stakeholders and drivers.  
☑ Reference any prior ADRs, tickets, research, benchmarks, or PoCs.  
☑ Keep to facts; avoid proposing a solution here.  
-->

#### **Decision**
We will use a document database for the customer survey.
The marketing department requires a faster, more flexible way to make changes
to the customer surveys.

Moving to a document database will provide better flexibility and speed, and will
etter facilitate changes by simplifying the customer survey user interface.
<!--  
☑ State the selected option unambiguously.  
☑ Explain the rationale—why this option beats the reasonable alternatives.  
☑ Mention rejected alternatives with a one-line reason each.  
☑ Include diagrams, tables, or links if they clarify the choice.  
☑ Reference principles/policies that influenced the decision (e.g. “12-Factor”, “Secure by Design”).  
-->

#### **Consequences**
Since we will be using a single representation for all surveys, multiple documents
will need to be changed when a common survey question is updated, added, or
removed.

The IT team will need to shut down survey functionality during the data migration
rom the relational database to the document datahase
. causine downtime
<!--  
☑ Positive outcomes (benefits gained).  
☑ Negative trade-offs (costs, risks, limitations).  
☑ Impact on performance, scalability, security, operability, UX, budget, timeline, team skillset.  
☑ Migration or deprecation strategy if applicable.  
-->

#### **Governance**

Decisions in this document are reviewed periodically to ensure alignment with business goals and technical needs. The governance process includes:

- Accountability: The Platform Tech Lead oversees implementation and impact.
- Review Cadence: Re-evaluate decisions every six months or upon major releases.
- Cross-Functional Input: A review board evaluates outcomes and suggests improvements.
- Change Control: Updates require formal review and approval to ensure transparency.
- Monitoring: Regular audits and stakeholder check-ins track metrics and adjust strategies.

Key elements:
- [x] Accountable role (e.g., “Platform Tech Lead”).
- [x] Review cadence (e.g., “every 6 months or major release”).
- [x] Success metrics/KPIs.
- [x] Change-control process.
- [x] Link to RFC or change-request template.


#### **Notes**
- Original author
- Approval date
- Approved by
- Superseded date
- Last modified date
- Modified by
- Last modification
<!--  
☑ Meeting minutes, whiteboard photos, slack threads.  
☑ Open questions or follow-ups.  
☑ Pointers to implementation PRs once work begins.  
☑ Anything useful that doesn’t fit other sections.  
-->