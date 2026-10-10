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

