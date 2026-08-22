---
title: "SCAP -- Defense Against RAG Knowledge Poisoning"
excerpt: >-
  A RAG security prototype that clusters retrieval similarity scores to flag
  suspiciously high-relevance documents and uses cluster-aware prompting to
  cross-check claims without discarding useful context.
collection: portfolio
permalink: /portfolio/scap-rag-poisoning/
order: 5
---

SCAP (Suspicious-Cluster-Aware Prompting) is a RAG security research prototype
co-developed with Pratyush Singh to mitigate knowledge-poisoning attacks such as
PoisonedRAG. Instead of removing retrieved documents outright, SCAP identifies
unusually high-relevance groups, labels them as suspicious, and asks the LLM to
cross-check claims against the normal-relevance group.

## Problem

Knowledge poisoning attacks can insert malicious documents into a RAG knowledge
base. If a poisoned document is engineered to closely match a query, it can be
retrieved ahead of correct evidence and steer the LLM toward an attacker-chosen
answer. Simple post-retrieval filtering can remove the wrong document or discard
the correct answer along with the malicious one.

## SCAP Approach

1. Retrieve a larger context set (10 documents in the evaluation).
2. Compute query-to-document cosine-similarity scores.
3. Use K-Means with two clusters to distinguish suspiciously high-relevance
   documents from the normal-relevance baseline.
4. Keep both document groups rather than hard-filtering the suspicious cluster.
5. Construct a verification-focused prompt that labels the groups, asks the LLM
   to identify conflicts, and prioritizes claims supported by normal-relevance
   evidence.

This reframes an attacker’s artificially high retrieval score as a signal for
verification, avoiding the high false-positive risk of simply deleting top-ranked
context.

## Architecture

![SCAP architecture showing query retrieval, score-cluster labeling, and LLM cross-verification against a poisoned RAG knowledge base.](/images/projects/scap-architecture.png)

The pipeline retrieves documents from the knowledge base, calculates their
similarity to the query, separates suspicious and normal score clusters, and
passes both labeled groups to the LLM. The response is generated only after the
model cross-checks potentially conflicting evidence.

## Project Work

- Configured the experiment environment on Clemson's Palmetto cluster with
  Python 3.10.
- Reproduced PoisonedRAG-style attacks with Vicuna-7B and Llama-7B models across
  Natural Questions, HotpotQA, and MS MARCO.
- Evaluated semantic-content clustering, score clustering, and an LLM-based
  gatekeeper before developing the final cluster-aware prompting approach.
- Implemented score-based K-Means clustering and the robust prompting workflow
  that labels, rather than removes, retrieved evidence.

## Results

- Reproduced the baseline poisoning attack with an average attack-success rate
  above 95%.
- Reported 90% defense effectiveness on Natural Questions and HotpotQA.
- Reported 80% defense effectiveness on MS MARCO.
- Preserved relevant evidence that score-cluster filtering would otherwise
  discard, reducing the risk of false positives during answer generation.

## Technical Highlights

- RAG security and knowledge-poisoning defense
- Query-to-document cosine similarity
- K-Means score clustering
- Cluster-aware prompt design and evidence cross-verification
- Vicuna-7B and Llama-7B evaluation
- Natural Questions, HotpotQA, and MS MARCO benchmarks
- Python 3.10 and Clemson Palmetto HPC

## Limitations and Next Steps

SCAP relies on poisoning attempts producing unusually high retrieval scores. An
adaptive attacker could deliberately lower a malicious document’s score to blend
into the normal cluster. Future work includes evaluating that threat model and
extending the defense to multimodal RAG systems.
