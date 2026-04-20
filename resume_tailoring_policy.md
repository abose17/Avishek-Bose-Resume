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

## Experience Bullets
- Write simple, coherent, easy-to-read bullets — one idea per bullet
- Split compound bullets joined by semicolons into separate bullets
- Only include skills and experience relevant to the specific role
- Do not surface domain-specific work (e.g. drug toxicology, infrastructure resilience) unless directly relevant to the role
- Do not use content from commented-out sections in `main_original.tex` as active bullets
- Use domain-specific terminology only when a match or relevant information is found in the job description — do not introduce technical terms that are absent from the JD
- Always include quantitative measures (e.g. data volume, model accuracy, latency, throughput, number of models, time saved); if the exact figure is unknown, assign a reasonable estimate — Avishek will correct in Overleaf
- Tailor for the seniority level: mid-level roles require domain-specific technical facts and concrete metrics, not just high-level outcomes

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
- Co-designed a graduate-level AI/ML course during PhD at Kansas State — surface for roles that emphasize knowledge sharing, communication, or technical leadership

---

## Git Workflow
- Claude commits each tailored `.tex` file to the local repo
- Avishek pushes from his terminal:
  ```bash
  git push github master:main
  ```
- Avishek syncs to Overleaf manually via Menu → Sync → Pull from GitHub
