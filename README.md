# Engineering README Framework

> A reusable documentation framework for producing consistent, evidence-based GitHub documentation for cloud infrastructure, platform engineering, Kubernetes, observability, security, and data engineering projects using authoritative Google Cloud documentation and standardized engineering practices.

---

## Overview

As my cloud engineering portfolio expanded across Google Cloud infrastructure, Kubernetes, observability, security, and data engineering, I found that maintaining consistent, technically accurate documentation became increasingly difficult.

Traditional AI-generated READMEs often suffer from the same problems:

- Generic descriptions copied from vendor documentation
- Hallucinated implementation details
- Missing architectural reasoning
- Broken documentation links
- Inconsistent formatting
- Little emphasis on engineering trade-offs

I wanted a documentation workflow that reflected how platform engineering teams document systems internally—not marketing material or tutorial-style writeups.

This repository contains the documentation standards I use to generate consistent technical documentation for every cloud engineering project in my portfolio.

Rather than relying on one massive prompt, the documentation rules are version-controlled, reusable, and continuously improved as the portfolio grows.

---

# Philosophy

> Good documentation explains **why** a system was built the way it was—not just **what** technologies it uses.

The goal of this framework is simple:

- Explain engineering decisions.
- Document architectural trade-offs.
- Reference only authoritative documentation.
- Never invent technical information.
- Produce documentation that can be defended during technical interviews.

---

# Documentation Principles

## Engineering Decisions Over Product Descriptions

This framework intentionally avoids copying vendor documentation.

Instead of writing:

> BigQuery is Google's serverless enterprise data warehouse...

the documentation explains:

> BigQuery was selected over Cloud SQL because analytical workloads required serverless execution, SQL analytics, and native BigLake integration while eliminating database administration overhead.

Every service included in a README should answer one question:

> **Why was this chosen?**

---

## Evidence First

Implementation is always the source of truth.

Documentation is generated from:

- implementation steps
- infrastructure configuration
- CLI commands
- deployment workflow
- validation outputs
- architecture
- screenshots

If information cannot be verified, it is not documented.

---

## Official Documentation Only

Whenever cloud services are referenced, documentation is validated using official Google Cloud documentation.

Community blogs and unofficial tutorials are intentionally avoided whenever authoritative documentation is available.

---

## Never Invent Engineering Details

The framework never fabricates:

- latency
- throughput
- performance metrics
- infrastructure scale
- production characteristics
- cost estimates
- limitations
- architectural decisions

If implementation details are unavailable, placeholders are used instead.

---

## Consistency

Every repository should feel like it belongs to the same engineering portfolio.

Regardless of whether the project covers:

- Kubernetes
- BigQuery
- BigLake
- Compute Engine
- Cloud Run
- IAM
- Observability
- Data Engineering

the documentation should maintain a consistent structure and writing style.

---

# Repository Structure

```
.
├── SKILL.md
├── references/
│   └── link-registry.md
└── README.md
```

## SKILL.md

Defines the documentation standards used when generating project documentation.

The framework includes:

- documentation blueprint
- formatting standards
- architecture layout
- design decision templates
- validation sections
- troubleshooting guidelines
- writing conventions
- anti-patterns
- documentation quality rules

---

## references/link-registry.md

Maintains curated references to official product documentation.

These references ensure generated documentation links to authoritative sources rather than community articles or vendor marketing material.

---

# Documentation Workflow

Instead of embedding documentation rules inside every request, the framework stores them in version-controlled files.

When documenting a project, the request instructs the model to:

1. Read the documentation standards from this repository.
2. Load the official documentation reference registry.
3. Retrieve authoritative Google Cloud product knowledge using the Google Developer Knowledge MCP server.
4. Use the supplied project implementation as the only implementation source.
5. Generate documentation according to the engineering standards defined by this framework.

This separation allows documentation standards to evolve independently without rewriting prompts for every project.

---

# Example Documentation Request

```
Act as an experienced Google Cloud Platform Architect.

Before generating documentation:

• Read the documentation rules from:

  - SKILL.md
  - references/link-registry.md

• Use Google Developer Knowledge MCP to retrieve official Google Cloud documentation.

• Never assume implementation details.

• Never invent metrics, limitations, or architectural decisions.

• Use the provided implementation as the source of truth.

Generate documentation according to the framework.

Project implementation:

<implementation>
```

---

# Why Google Developer Knowledge MCP?

Cloud products evolve rapidly.

Rather than relying solely on an LLM's pretrained knowledge, this workflow retrieves authoritative Google Cloud documentation during documentation generation.

Benefits include:

- current product terminology
- official implementation guidance
- validated product capabilities
- official documentation references
- reduced documentation drift

---

# Design Goals

This framework is designed to produce documentation that is:

- technically accurate
- evidence-based
- interview defensible
- recruiter friendly
- architect readable
- consistent across repositories
- maintainable over time

---

# Documentation Standards

Every generated README should communicate:

- Business problem
- Solution overview
- Architecture
- Engineering decisions
- Design trade-offs
- Validation
- Troubleshooting
- Cleanup
- Production considerations

The objective is to explain engineering intent rather than simply listing implementation steps.

---

# What This Framework Does Not Do

This framework intentionally avoids:

- vendor marketing language
- generic service descriptions
- unsupported performance claims
- fabricated production metrics
- unofficial documentation references
- assumptions about implementation

Accuracy is always preferred over completeness.

---

# Target Audience

This framework is intended for documenting projects involving:

- Google Cloud Platform
- Platform Engineering
- Cloud Infrastructure
- Kubernetes
- Site Reliability Engineering
- DevOps
- Infrastructure Automation
- Data Engineering
- Observability
- Cloud Security
- Distributed Systems

---

# Future Roadmap

Planned improvements include:

- Architecture Decision Record (ADR) generation
- Architecture diagram templates
- Mermaid diagram generation
- Documentation quality validation
- Multi-cloud documentation support
- Infrastructure-as-Code documentation templates
- Automated documentation consistency checks

---

# Acknowledgements

This documentation workflow combines:

- repository-defined documentation standards
- curated official documentation references
- Google Developer Knowledge MCP for authoritative product knowledge
- implementation evidence provided by the project author

Together, these components help produce technical documentation that emphasizes engineering reasoning, architectural decisions, and implementation accuracy over generic feature descriptions.

---

# License

This repository is provided as an open reference for engineers interested in building consistent, evidence-based documentation workflows for cloud and platform engineering projects.
