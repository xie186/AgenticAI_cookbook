## What Is a Large Language Model?

At its core, a large language model (LLM) does one thing: it takes in a sequence of text — the prompt — and predicts, one token at a time, the sequence of text most likely to follow it — the response. Everything an LLM appears to "know" or "do" is a consequence of patterns learned from the enormous volume of text it was trained on, not a lookup against a live database.

This has one important practical consequence: the knowledge cutoff. An LLM's training data has a fixed end date, so it has no inherent awareness of anything that happened after that point — a new paper, an updated database record, or a newly characterized variant. For an AI agent built on top of an LLM, this is not a minor footnote; it is the reason such agents are almost always paired with retrieval tools (APIs, search, or direct database queries) rather than left to answer from memory alone.

One model, many tasks. A single LLM, without retraining, can be steered toward very different jobs simply by changing the prompt and the surrounding scaffolding:

* Translation — converting text from one language to another
* Summarization — compressing long text into its key points
* Chat — sustaining multi-turn, context-aware conversation
* Named Entity Recognition (NER) — identifying and labeling entities (people, places, organizations — or, in our domain, genes, proteins, diseases, drugs) within text
* Image generation — producing visuals from a text description (typically via a paired diffusion model rather than the LLM itself)



Why this matters for bioinformatics. Each of these generic capabilities has a direct analog in a bioinformatics AI agent:

| General capability |                                    Bioinformatics application                                   |
|:------------------:|:-----------------------------------------------------------------------------------------------:|
| Translation        | Converting between DNA/RNA and protein sequences; translating non-English literature            |
| Summarization      | Condensing research papers, clinical notes, or pipeline/variant-call logs into readable digests |
| Chat               | Natural-language querying of resources like UniProt, PubMed, or GEO                             |
| NER                | Extracting gene, protein, disease, and drug mentions from biomedical text at scale              |
| Image generation   | Producing pathway diagrams, structure previews, or annotated plots on request                   |

The knowledge-cutoff limitation is especially relevant here: biological databases update constantly, so a bioinformatics agent cannot rely on the LLM's internal memory for current sequence records, annotations, or literature. Instead, the LLM acts as the reasoning and language layer, while live retrieval tools supply the up-to-date biological data it reasons over.



## Retrieval-Augmented Generation (RAG)

In the previous section, we saw that an LLM's knowledge is frozen at the moment training ends. RAG — Retrieval-Augmented Generation — is the most widely used technique for working around that limitation. Rather than relying solely on what the model learned during training, RAG connects the LLM to an external knowledge base, commonly a vector database, that can be searched at the moment a query is made. The model's response is then generated using both the prompt and the relevant information retrieved from that external source.


### Why RAG matters

Overcoming outdated knowledge. Because an LLM's knowledge cutoff means it has no awareness of anything after its training period, RAG lets the model draw on current, continuously updated information — without the cost and delay of retraining the model itself.

Accessing private data. Most proprietary or domain-specific material — internal research papers, lab notebooks, unpublished datasets — was never part of a base model's training data. RAG allows the model to reason over exactly this kind of private or specialized content, retrieving it on demand rather than requiring it to have been "known" in advance.

Reducing hallucinations. When an LLM is asked something it doesn't actually know, it can generate a plausible-sounding but incorrect answer — a hallucination. By grounding the model's response in retrieved passages from verified sources, RAG substantially lowers the likelihood of this kind of fabrication, since the model is working from real supporting text rather than relying purely on internal pattern completion.

### Why this matters for bioinformatics

RAG is especially well suited to bioinformatics applications, where the underlying data changes constantly and much of the most relevant material is domain-specific or private. An agent built with RAG can, for example, retrieve the latest entries from UniProt or PubMed before answering a question about a protein, pull facts from a lab's internal sequencing reports, or ground its answer in a specific paper a researcher has uploaded — rather than relying on what the base model happened to have seen during training, which may be outdated, incomplete, or entirely absent for a niche organism or pathway.