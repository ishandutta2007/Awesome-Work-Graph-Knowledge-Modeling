# Awesome-Work-Graph-Knowledge-Modeling

# Top Work Graph & Knowledge Modeling Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Enterprise Knowledge Graphs, Work Context Modeling & Self-Hosted Graph Infrastructure*  
**Last updated: October 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Work Graph & Knowledge Modeling**. These tools enable organizations to connect people, content, projects, and activity into a unified, queryable graph—surfacing relationships that siloed tools hide and providing the contextual foundation for AI assistants, search, and workforce intelligence.

**Examples** include Atlassian Teamwork Graph, Microsoft Graph, Glean Knowledge Graph, Viva Insights, Salesforce Data Cloud, Palantir Foundry, Neo4j, Diffbot, OrgVue, and Workday Prism (the category leaders).

**Open-source emphasis**: Work Graph & Knowledge Modeling is a domain where open-source tooling is **emerging but genuinely promising for developer-led graph construction**, though it remains far from replicating the turnkey enterprise graphs of Atlassian, Microsoft, or Glean. **trikedb** stands out as the most focused open-source tool for *work* graphs specifically—a YAML-based, MCP-native graph engine designed for pipeline and data-lineage modeling with hybrid semantic + SPARQL retrieval for AI agents . **ontograph** provides LLM-powered entity extraction with ontological schemas tailored for workplace concepts (people, projects, teams) and orbit-based proximity scoring . **Neo4j Community Edition** remains the foundational graph database, now with vector search for GraphRAG workflows . The critical gap: **no open-source project provides the pre-built connectors, identity unification, and permission-aware traversal** that make Glean's Knowledge Graph or Microsoft Graph immediately useful out of the box—those require crawling 100+ enterprise sources and reconciling identities across them .

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-products)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Atlassian Teamwork Graph](https://developer.atlassian.com/platform/teamwork-graph/)**  
  Atlassian's relationship-first graph connecting Jira work items, Confluence content, Loom videos, Goals, and Teams via a unified GraphQL API; as of October 2026 the Consumption API is in **Preview**, offering curated typed queries (`atlassianUserAssignedJiraWorkItems`, `confluencePageContributors`) and persisted Cypher queries with granular object-level scopes (`read:graph:issue:jira`) . Designed to provide context for AI agents and cross-product search within the Atlassian ecosystem.

- **[Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview)**  
  The gateway to data and intelligence across Microsoft 365, Windows, and Enterprise Mobility + Security; a single endpoint (`graph.microsoft.com`) exposing REST APIs and SDKs for users, mail, calendars, Teams, SharePoint, OneDrive, and more . Includes **connectors** for external sources (Box, Google Drive, Jira, Salesforce) and **Data Connect** for bulk export to Azure data stores. The most mature enterprise work graph, but tightly bound to the Microsoft ecosystem.

- **[Glean Knowledge Graph](https://docs.glean.com/security/knowledge-graph)**  
  Enterprise knowledge graph built on three pillars: **Content** (documents, messages, tickets), **People** (identities, roles, teams, relationships), and **Activity** (interactions, engagement patterns) . Uses 100+ connectors for source-specific crawling, unified identity resolution across applications, and permission-aware search. Activity data is used for personalization with strict isolation—individual data remains per-user, and collective insights apply privacy thresholds . The benchmark for enterprise search context.

- **[Microsoft Viva Insights](https://learn.microsoft.com/en-us/viva/insights/)**  
  Workplace analytics platform providing behavioral insights into how work gets done—collaboration patterns, wellbeing, and hybrid work impact . Advanced analysis tools allow custom queries and Power BI reports over organizational data, with Copilot integration for query setup. Focused on **aggregate patterns** rather than individual relationship traversal.

- **[Salesforce Data 360 (formerly Data Cloud)](https://www.salesforce.com/data/)**  
  Salesforce's native data engine with **Zero Copy** integration for bringing warehouse and lake data into Salesforce without pipelines; includes a vector database for unstructured content, unified customer profiles, and activation across Agentforce, Sales, Service, and Marketing . Positioned as a CDP but extends to any business function fueled by data. Not a work graph per se, but provides the customer context layer for Salesforce AI.

- **[Palantir Foundry](https://www.palantir.com/platforms/foundry/)**  
  Enterprise data platform built around an **Ontology**—a set of entities (nouns) and actions (verbs) representing the business view of the world, grounded in enterprise data sources and writable back to transactional systems . Breaks down the IT/business wall by allowing business users to build applications on the ontology while IT maintains data integration and governance. Deployed in critical industries for operational decision-making.

- **[Neo4j](https://neo4j.com/)**  
  The leading graph database (listed here for its AuraDB managed cloud offering); Community Edition now includes **vector search** for AI workflows, enabling GraphRAG patterns that combine relationship traversal with semantic similarity in a single query . The standard backend for custom knowledge graph applications.

- **[Diffbot](https://www.diffbot.com/)**  
  Knowledge graph and web data extraction platform; provides a **Knowledge Graph** of public web entities queried via DQL (Diffbot Query Language), plus extraction APIs for turning web pages into structured data . Useful for enriching internal graphs with external entity context (organizations, people, products).

- **[OrgVue](https://www.orgvue.com/)**  
  Workforce transformation and organizational design platform; models the organization as a graph of positions, people, skills, and activities for scenario planning and strategic workforce planning . **Henshaw AI** (early access) automates role clustering and provides a conversational interface for workforce data queries . Focused on org design rather than general work context.

- **[Workday Prism Analytics](https://www.workday.com/en-us/products/analytics-reporting/data-hub.html)**  
  Enterprise data hub for HR and finance; ingests high-volume external data via API, SFTP, or browser upload, transforms it with low-code/no-code pipelines (joins, unions, group-by, filters), and publishes insights into Workday reports and dashboards . Blends Workday transactional data with external operational data for unified workforce and financial analytics. Not a relationship graph—an analytics data hub.

## Open-Source GitHub Projects

### Work Graph & Pipeline Modeling

- **[trikedb](https://pypi.org/project/trikedb/)**  
  The most focused open-source **work graph engine** for pipeline and data-lineage modeling (YAML-based, MCP-native) . Stores facts as subject-predicate-object triples in human-readable YAML, with support for **edge attributes** (provenance, schedules, deprecation flags) and node properties without schema migration. Features **hybrid retrieval** combining semantic search with SPARQL filtering in a single `find()` call—"cast a wide net by meaning, then keep only what precisely matches" . Includes built-in **MCP server** for AI agent access via OAuth 2.1, SPARQL 1.1 queries, SHACL validation, RDFS/OWL inference, and HTML graph export. **The best open-source starting point for modeling work relationships (pipelines, dependencies, data flows) with AI agent accessibility**—but it is a library/CLI, not a turnkey enterprise graph platform.

- **[ontograph](https://pypi.org/project/ontograph/0.2.0/)**  
  LLM-powered **knowledge graph engine** with ontological entity resolution for workplace concepts . Define schemas for entity types (person, project, team, meeting, topic) and relationship types (works_on, manages, colleague, discussed, member_of); ingest unstructured text (transcripts, documents) and the LLM extracts entities and relationships constrained by the schema. Features **orbit-based proximity scoring** (entities you interact with frequently score higher for resolution) and hybrid semantic-graph search. **Best for extracting work relationships from unstructured text**—but requires OpenAI API key and is early-stage (v0.2.0).

### Graph Databases & Infrastructure

- **[Neo4j Community Edition](https://github.com/neo4j/neo4j)**  
  The foundational open-source graph database (GPLv3); Community Edition now includes **vector search** for GraphRAG, Cypher 25 with GQL alignment, and connection to Aura Console for visual exploration via Neo4j Bloom . **The standard backend for building custom knowledge graphs**—requires modeling and application development on top, but provides production-grade graph storage and traversal.

### Additional Strong Open-Source Options

- **code-hq** — Local-first knowledge graph CLI for project context, tasks, notes, and relationships using semantic JSON-LD; AI-agent friendly with SPARQL-like query language (TQL) . **Developer-focused**—for managing software project knowledge, not enterprise-wide work graphs.
- **mdgraph-ai** — Converts Markdown documents into interconnected concept files with cross-links, BM25 search, multi-hop traversal, and MCP server for agent access . **Documentation-focused**—useful for building a knowledge base from docs, not a work activity graph.
- **BioCypher project-planning** — Demo pipeline that builds a Neo4j knowledge graph from GitHub Projects issues, team members, and annotations, with LLM assistance for task summarization and planning . **Research demo**—demonstrates the pattern of extracting work graphs from project management data, but not production-ready.

**Frameworks for building custom systems**: For **pipeline and data-lineage work graphs**, trikedb provides the most focused foundation with YAML storage, MCP access, and hybrid retrieval . For **extracting work relationships from text**, ontograph offers schema-constrained LLM extraction with entity resolution . For **custom graph applications**, Neo4j CE provides the database layer with vector search . No open-source project provides the **pre-built enterprise connectors, identity unification, and permission-aware traversal** of Glean or Microsoft Graph—building those requires significant integration work across source systems.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Work graph platforms handling employee activity and organizational data must comply with applicable privacy regulations (GDPR, CCPA) and implement strict permission models; **activity data is particularly sensitive**—Glean isolates individual activity while aggregating for collective insights with privacy thresholds .
- **Open-source work graph tooling is emerging but requires assembly**—trikedb provides a focused engine for pipeline graphs , ontograph extracts relationships from text , and Neo4j provides the database layer . However, **no open-source project replicates the 100+ connectors, unified identity resolution, and permission-aware enterprise search** of Glean or Microsoft Graph. Organizations requiring a turnkey enterprise work graph should evaluate commercial platforms.
- Verify license terms for commercial use; trikedb and ontograph are PyPI packages (check licenses), and Neo4j Community Edition uses GPLv3 .

---

**Made for knowledge engineers, enterprise architects, AI platform teams, and workforce analytics practitioners.**  
Let's make work graph and knowledge modeling more open, but with clear eyes about the connector and identity-resolution infrastructure that commercial platforms still own.
