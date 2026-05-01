# Resume Tailoring Policy
> Do not modify this file unless explicitly instructed by Avishek.

---

## Inputs Required
1. Company name
2. Role title
3. Full job description

---

## File Management
- **Master resume:** `main_original.tex` — never edit this file
- **New file per application:** `{Company}_{Role}_{YYYY-MM-DD}.tex` (spaces replaced with underscores)
- Always start fresh from `main_original.tex` for each new tailored resume

---

## Title
- Change the subtitle to match the exact role title from the job description

---

## Summary
- Reframe to match the role's framing:
  - Product/engineering roles → emphasize shipping features, production systems, speed
  - Research roles → emphasize publications, model development, scientific rigor
  - Consulting roles → emphasize client delivery, stakeholder communication, breadth

---

## Factual Accuracy — Hard Rule
- **Never attach a tool or technology to an experience where it was not actually used** (e.g. do not add PySpark to Tegna bullets if PySpark was not used at Tegna)
- **Never add a skill to the skills section that Avishek has not confirmed** he knows or uses
- **Never invent context** such as organizational details or project outcomes that have not been stated
- Use domain-specific terminology only when matched to the JD **and** grounded in Avishek's actual background
- **Avishek always does a final edit in Overleaf before submitting** — the goal is to produce a strong first draft that makes his editing job easier, not a perfect final product

## No Keyword Stuffing — Hard Rule
**Never write a sentence whose sole purpose is to place a JD keyword in the resume.** This applies even if the sentence is grammatically correct and sounds plausible.

A bullet is only acceptable if every technical claim in it traces directly back to `main_original.tex` or the confirmed Key Facts table. The test is:

> *Can I point to a specific line in `main_original.tex` or the Key Facts that justifies each tool, action, and outcome named in this bullet?*

If the answer is no for any part of the bullet, remove or rewrite that part — do not soften it into vague language to make it fit.

**Specific patterns to reject:**
- Copying JD requirement language and recasting it as an accomplishment (e.g. JD says "secrets management and least-privilege access" → bullet says "applied secrets management and least-privilege access" without any confirmation that Avishek did this)
- Adding a tool or concept from the JD that has no grounding in the master resume (e.g. "LLM gateways", "model routing", "co-instructed" when only "co-designed" is confirmed)
- Paraphrasing the JD's own value statements into the summary as if they describe Avishek's work (e.g. "scoping solutions, prototyping rapidly, and transferring skills for independent operation")

**If a JD keyword has no real match, record it as a gap in the Skills Match table — do not insert it into the resume to create the appearance of a match.**

---

## Quantitative Measures — Mandatory

**Every bullet should contain at least one number, scale, or precision metric.** This is not optional. Vague bullets like "improved retrieval quality" or "built scalable systems" are unacceptable — they must be quantified.

- Use `$\sim$` in LaTeX for estimated figures (e.g. `$\sim$35\%`) — Avishek reviews and corrects all numbers in Overleaf before submitting
- Numbers must be **technically grounded and defensible**, not arbitrary. Use the reference table below as the canonical source
- Do NOT copy numbers from one tailored resume to another — each resume is written fresh and numbers should be chosen to fit the framing of the specific role

### Reference Table of Grounded Estimates

| Experience | Metric | Value | Technical Basis |
|---|---|---|---|
| Tegna | Daily production requests | 100K+ | Confirmed fact |
| Tegna | Retrieval precision improvement (semantic vs. keyword) | $\sim$35\% | Dense retrieval over BM25 on news-domain corpora; consistent with BEIR benchmark ranges |
| Tegna | Number of production models monitored via RAGAs/DeepEval | 5+ | Reasonable for a multi-model RAG platform with retrieval, reranking, and generation components |
| ORNL | Training corpus for MatGPT | 2M+ materials science documents | Consistent with Materials Project, ICSD, PubChem, and arXiv extractions at Exascale compute scale |
| ORNL | DOE/ORNL incident report corpus | 50K+ reports | Realistic for DOE's operational incident logging across facilities over decades |
| ORNL | Classification accuracy improvement from LoRA fine-tuning | $\sim$15\% | Typical domain-adaptation gain reported in BERT/LLaMA fine-tuning literature (10–20% range) |
| ORNL | Inference response time (Azure, warm instance) | <100ms | Standard SLA achievable for Azure Functions with pre-loaded embeddings |
| ORNL | 24×7 availability SLA | 99.9\%+ | Standard cloud SLA target for containerized services with autoscaling |
| KDD Lab | Social media posts processed (cyber threat) | 10M+ | Twitter Streaming API volume over multi-year research is consistent with this scale |
| KDD Lab | GNN accuracy for HPC job prediction | $\sim$89\% | High accuracy is achievable for structured log data with clear categorical labels |
| KDD Lab | Disaster reports processed per batch (summarization) | 1K+ | Consistent with batch inference throughput for T5/BART-class models |
| Dutch Bangla Bank | Daily banking transactions processed | 100K+ | Consistent with a mid-tier commercial bank's daily transaction volume |

### How to apply
- Pick the metrics most relevant to the role framing — do not include all of them in every resume
- Where the JD implies a different framing (e.g. research rigor vs. engineering scale), choose metrics that fit: precision/recall numbers for research, throughput/latency for engineering, cost/time savings for consulting
- If a bullet does not naturally accommodate any metric from the table, write the bullet differently so that a count, scale, or performance figure fits organically

## Experience Bullets
- Write simple, coherent, easy-to-read bullets — one idea per bullet
- Split compound bullets joined by semicolons into separate bullets
- Only include skills and experience relevant to the specific role
- Do not surface domain-specific work (e.g. drug toxicology, infrastructure resilience) unless directly relevant to the role
- Do not use content from commented-out sections in `main_original.tex` as active bullets
- Tailor for the seniority level: mid-level roles require domain-specific technical facts and concrete metrics, not just high-level outcomes
- **Never pattern-match or copy bullets from previous tailored resumes.** Every resume is an independent document written fresh from `main_original.tex` and the JD alone — do not look at or reuse phrasing from any previously generated `.tex` file in this folder
- **Every bullet must be technically precise.** Before writing a bullet, verify that the tools named actually perform the function described (e.g. Docker and Terraform are not CI/CD tools; they are containerization and IaC tools respectively). Never group unrelated tools under an inaccurate umbrella term

---

## Publications
- **Engineering roles** → omit publications entirely
- **Research roles** → uncomment the `\section{Publications}` block as its own standalone section; do not embed it inside any experience entry

---

## Skills Section
- Reorder to front-load tools and frameworks explicitly mentioned in the job description
- Add tools from the JD that Avishek genuinely uses (PyTorch, TensorFlow, Azure OpenAI, LangChain, LlamaIndex, Scikit-learn, Docker, Terraform, MLflow, SQL, C#, etc.)

---

## Page Length
- Resume must fit exactly one page
- Target: no more than ~55-60 lines of body text across all sections
- If over one page, trim the least relevant bullets first

---

## Key Facts (always factual, never fabricate)
- 100K+ daily production requests at Tegna
- 3 journal articles and 22 peer-reviewed conference papers (IPDPS, IEEE BigData, ICMLA, ISI)
- MatGPT trained on Frontier (world's first Exascale supercomputer)
- 8+ years of AI/ML experience (from 2018 KDD Lab); 10+ years total (from 2015 Dutch Bangla Bank)
- Proficient in PySpark — surface for roles involving big data, distributed computing, or data engineering
- Proficient in Elasticsearch — surface for roles involving search systems, information retrieval, or search infrastructure
- Co-designed a graduate-level AI/ML course during PhD at Kansas State — surface for roles that emphasize knowledge sharing, communication, or technical leadership

---

## Git Workflow

**Writing a file and committing it are a single atomic step. Claude must `git add` and `git commit` immediately after writing or modifying any `.tex`, `.md`, or policy file — never end a task without a commit.**

```bash
git add <filename(s)>
git commit -m "<description>"
```

After committing, tell Avishek to push from his terminal:
```bash
cd /Users/abose1/69df216bc598c596402998e7
rm -f .git/HEAD.lock .git/REBASE_HEAD.lock
git push github master:main
git push origin master
```

Avishek syncs to Overleaf manually via Menu → Sync → Pull from GitHub.
