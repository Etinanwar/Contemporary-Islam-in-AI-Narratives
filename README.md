# Contemporary Islam in AI Narratives

Quantitative text analysis of 100 AI-generated articles on contemporary Islam, archived on March 14, 2026 (analysis ID `019cec92`). Two models, Google's `gemini-3-pro-preview` and OpenAI's `gpt-5.2`, each wrote 50 long-form articles spread over ten topics, under identical prompting rules and generation parameters. The combined corpus was then run through twelve text analytics features to compare how each model narrates the same subject matter.

The core result is structural convergence with stylistic divergence. Both models cover the same thematic ground, produce statistically identical co-occurrence networks, and skew heavily positive. They part ways on vocabulary, rhetorical register, entity specificity, and topic granularity: Gemini writes longer, more assertive, identity-anchored prose grounded in named people, places, and legal traditions, while GPT-5.2 writes tighter text framed around law, community, and public life.

## Repository contents

| Path | Contents |
|---|---|
| [Data/Analyzed Data Contemporary Islam.pdf](Data/Analyzed%20Data%20Contemporary%20Islam.pdf) | 1,320-page data export with one record per article: provider, model, language, audience, tone, length, temperature, system and user prompts, executive summary, full article text, and per-segment word and character counts. |
| [Report/Analysis Report Contemporary Islam.pdf](Report/Analysis%20Report%20Contemporary%20Islam.pdf) | 13-page analysis report: composite cross-group comparison, per-model executive summaries, conclusion, and prioritized recommendations. |

There is no code in this repository. Both files are archival documents produced by the analysis pipeline.

## Corpus design

Ten topics, ten articles each, split evenly between the two models (five per model per topic). The export lists 100 articles and 179 segments in total.

| Topic |
|---|
| Islamic environmentalism |
| Islamic fashion |
| Islamic radicalism |
| Islam and the halal industry |
| Islam and human rights |
| Islamic banking and the circular economy |
| Islam and feminism |
| Islam and democracy |
| Islam and technology |
| Islamic modernity |

Generation parameters were held constant across all 100 articles:

- Models: `gemini-3-pro-preview` (50 articles) and `gpt-5.2` (50 articles)
- English, general audience, neutral tone, long length, temperature 0.7
- Output format: GitHub-Flavored Markdown blog post, 6,000 to 12,000 characters
- No external sources attached; each prompt forbids fabricated citations and requires a References section ending with "No external sources used"

Each model received its own set of article titles within the shared topic list, for example "Adopting sustainable habits through the lens of Muslim faith" (Gemini, environmentalism) and "How online networks accelerate Islamic radicalization" (GPT-5.2, radicalism).

## What was measured

The report runs twelve analytics over both groups: word frequency, TF-IDF, sentiment analysis, LDA topic modeling, n-gram collocations, co-occurrence networks, named entity recognition, text classification, network analysis, chunking, document similarity, and framing and bias detection. Report-level totals: 100 documents, 179 chunks, 146.5K words, average sentiment polarity 0.73, 19 LDA topics across the two models (6 dominant for Gemini, 13 for GPT-5.2).

## Findings

### Where the models converge

- Same thematic terrain: Islamic finance and the circular economy, human rights under Islamic law, feminism and gender, modest fashion, environmental stewardship, radicalism, democracy, technology, and modernity.
- Identical co-occurrence network topology in both groups: 50 nodes, 728 edges, density 0.5943, clustering coefficient 0.7080, one connected component. The shared prompt corpus drives the same structural relationships.
- Matching top co-occurrence pairs (ijarah-leasing, artificial-intelligence, street-style) and matching similarity clusters: halal (7 to 8 documents), circular economy (7 to 8), human rights (7), fashion (5 to 6), with internal similarity scores of roughly 0.20 to 0.30.
- Nearly identical sentiment: 86.9% positive for Gemini, 88.8% for GPT-5.2.
- The leading n-grams in both groups are meta-textual boilerplate ("references external sources", "external sources used") rather than content phrases.

### Where the models diverge

| Measure | gemini-3-pro-preview | gpt-5.2 |
|---|---|---|
| Corpus size | 50 documents, 99 chunks, ~79,100 words | 50 documents, 80 chunks, ~67,400 words |
| Signature vocabulary | "islamic" 627, "muslim" 161 | "religious" 251, "legal" 134, "community" 100, "public" 78 |
| Distinctive TF-IDF terms | fashion (2.60), economy (2.09), shura (1.77), green (1.64) | circular (3.78), modernity (2.50), human rights (2.21), community (1.37) |
| Largest text classification | Economy & Business, 29.3% | Law & Security, 32.5% |
| Classification categories used | 10 | 13, adding Education, Health, and Quran & Revelation |
| LDA topic structure | 6 dominant topics; one macro-topic ("Islam, Modernity, and Social Reform") at 37.4% | 13 topics; largest ("Islamic Governance and Political Modernity") at 26.7% |
| Named entities found | 4,316, including PERSON 426 and GPE 292 | 2,173, including PERSON 32 and GPE 25 |
| Passive voice constructions | 199 | 79 |
| Intensifiers | 31 | 5 |
| Loaded terms | 269 | 210 |
| Hedging instances | 15 | 17 |

Read together: Gemini anchors its writing in specifics (Muhammad 26 mentions, Maqasid al-Sharia 14, Indonesia 31, Turkey 15) and clusters content into broad narrative arcs. GPT-5.2 abstracts toward principles and frameworks, leans on legal and community vocabulary, and separates feminism from human rights into distinct topics where Gemini merges them.

### Artifacts the analysis flagged

- The "No external sources used" reference block creates near-duplicate chunks: three pairs in GPT-5.2 output, including one exact 1.0 similarity match, and one pair in Gemini output. The report recommends stripping this boilerplate before similarity analysis.
- GPT-5.2's markdown heading markers (`### 1`, `### 2`) were misclassified as MONEY entities (523 MONEY entities versus Gemini's 423), inflating its entity counts.
- Highest bias scores concentrate in security-related content: "Distinguishing mainstream theology from extremist ideology" (Gemini, 5.55) and "How online networks accelerate Islamic radicalization" (GPT-5.2, 5.87).

### Shared blind spots

Both corpora construct a largely monolithic "Islam":

- No meaningful Sunni, Shia, or Sufi differentiation.
- Worship and ritual practice is minimal: 1.0% of Gemini's classification, 3.8% of GPT-5.2's.
- Dissenting, progressive, and ex-Muslim voices are absent.
- Colonial and postcolonial framing does not surface in any topic or n-gram cluster (noted in the GPT-5.2 analysis).

## Caveats

- The corpus is entirely machine-written. This repository documents how two models narrate contemporary Islam, not contemporary Islam itself; frequency patterns reflect model priors and alignment tuning.
- The overwhelming positive sentiment (87 to 89%) is attributed in the report to alignment tuning rather than to the subject matter, and the total absence of neutral text is treated as a model artifact.
- Three sections of the report (Executive Summary, Composite Cross-Group Comparison, Conclusion and Recommendations) were generated by `anthropic/claude-opus-4.6` via OpenRouter, as disclosed in the report itself. All statistics were computed deterministically from the corpus.
- The archive notice applies to both files: AI output may contain inaccuracies, fabricated references, or unintended bias, and should be independently verified before reliance.

## Provenance

| Field | Value |
|---|---|
| Project | Contemporary Islam |
| Analysis ID | 019cec92 |
| Analysis date | March 14, 2026, 1:39 PM |
| Groups compared | gemini-3-pro-preview, gpt-5.2 |
