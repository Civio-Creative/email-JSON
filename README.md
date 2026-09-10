# Structured Extraction from Sales Emails: An Eval Case Study

An LLM pipeline that pulls CRM-ready fields (sender, company, dates, dollar amounts, questions, requested actions) out of inbound sales email, plus the evaluation I built to decide which fields can be trusted.

**[Open the notebook in Colab](https://colab.research.google.com/github/Civio-Creative/sample_outputs/blob/main/AI_Bootcamp.ipynb)**

## Key finding

The first version passed a consistency check on most emails and still got fields wrong. It also invented a year (`2023-12-15`) for "get back to me by 12/15," even though its prompt said to skip ambiguous dates. Most failures turned out to be spec gaps, not randomness: the prompt never decided how to handle dates without a year, requests phrased as questions, or quoted text.

## What's in the notebook

1. The problem and the schema decisions
2. A four-email test set, each email built to stress a different failure mode
3. Hand-labeled ground truth, with per-field scoring
4. v1 baseline: consistency and accuracy
5. Failure analysis with root causes
6. v2 fixes: temperature 0, the received date passed in, explicit rules, tightened schema
7. Before/after comparison and cost per email
8. Product implications: which fields go straight to the CRM and which need a person to review them

## Files

| File | Description |
|---|---|
| `AI_Bootcamp.ipynb` | Full case study: code, results, and analysis |
| `email_extractions.json` | Final v2 extraction output for the test set |

## Stack

Python · OpenAI Responses API (`gpt-4o-2024-08-06`, structured outputs) · Pydantic · pandas · Google Colab

*Part of AI Bootcamp 2026, Testing track.*
