# Graph-Based Multi-Agent System for Alzheimer's Disease

An agentic AI system that **discovers candidate biological pathways for Alzheimer's disease**.
Several specialised agents collect knowledge from biomedical databases and the literature,
merge it into a single knowledge graph, and rank new candidate pathways (genes, proteins,
mechanisms) using graph mining. The result is an explained report that cites the evidence
behind each hypothesis.

> Group project for the **Graph Mining** course, M2 SIA, Université de Bourgogne.
> Project 3: *Agentic system that discovers new pathways for a disease*.

---

## How it works

```
                 "Alzheimer's disease"
                          │
                ┌─────────▼─────────┐
                │    Orchestrator   │
                └─────────┬─────────┘
     ┌──────────────┬─────┴───────┬──────────────┐
     ▼              ▼             ▼              ▼
 Disease–gene    Protein       Pathway       Literature
    agent      interaction      agent          agent
(Open Targets)  agent (STRING) (Reactome/KEGG)  (PubMed)
     └──────────────┴─────┬───────┴──────────────┘
                          ▼
              Merged knowledge graph (NetworkX)
                          ▼
   Ranking: shortest paths · random walks · link prediction
                          ▼
          Explained report with cited evidence
```

1. **Collect.** Each agent has its own tool and data source.
2. **Merge.** Results are combined into one heterogeneous graph
   (disease, gene/protein, pathway, publication nodes).
3. **Rank.** Graph algorithms score candidate disease–pathway links that are not yet known.
4. **Explain.** An LLM writes a report for each hypothesis, citing the supporting
   graph paths and papers.
5. **Evaluate.** Known Alzheimer's–pathway links are hidden, and we measure whether the
   system finds them again (e.g. Hits@k, MRR, AUC).

## Data sources

| Source | What we use it for | Access |
|---|---|---|
| [Open Targets Platform](https://platform.opentargets.org) | Disease–target associations | GraphQL API |
| [STRING](https://string-db.org) | Protein–protein interactions | REST API |
| [Reactome](https://reactome.org) | Curated biological pathways | REST API |
| [KEGG](https://www.kegg.jp) | Pathway maps | REST API |
| [PubMed](https://pubmed.ncbi.nlm.nih.gov) | Biomedical literature | NCBI E-utilities |

## Tech stack

- **Language:** Python
- **Graph:** NetworkX
- **Agents:** LangGraph, CrewAI or smolagents *(to be decided)*
- **LLM provider:** *to be decided*
- **Interface:** Streamlit (planned), hosted on Streamlit Community Cloud or Hugging Face Spaces

## Deliverables

- [ ] Online platform reachable from a public URL
- [ ] Demo video showing the full pipeline: data → graph → analysis → results
- [ ] Submission PDF (names, project number and title, platform link, video link)

## Project status

🚧 **Early setup.** The code structure, setup instructions and how to run the app will be
added once the tech choices above are made.

## Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md) before your first commit. It explains the branch
workflow, commit messages and how pull requests are reviewed.

## Team

| Name | Role |
|---|---|
| Daffa Kautsar | |
| | |
| | |

## Disclaimer

This is an academic project. The pathways it proposes are **computational hypotheses**,
not validated findings, and must not be used for medical decisions.
