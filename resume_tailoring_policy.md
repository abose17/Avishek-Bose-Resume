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
- **Quantitative measures (metrics and numbers) are always encouraged** — assign reasonable estimates and mark them with `$\sim$` where exact figures are unknown; Avishek reviews and corrects all numbers in Overleaf before submitting
- Use domain-specific terminology only when matched to the JD **and** grounded in Avishek's actual background
- **Avishek always does a final edit in Overleaf before submitting** — the goal is to produce a strong first draft that makes his editing job easier, not a perfect final product

## Experience Bullets
- Write simple, coherent, easy-to-read bullets — one idea per bullet
- Split compound bullets joined by semicolons into separate bullets
- Only include skills and experience relevant to the specific role
- Do not surface domain-specific work (e.g. drug toxicology, infrastructure resilience) unless directly relevant to the role
- Do not use content from commented-out sections in `main_original.tex` as active bullets
- Tailor for the seniority level: mid-level roles require domain-specific technical facts and concrete metrics, not just high-level outcomes
- **Never pattern-match or copy bullets from previous tailored resumes.** Every resume is written fresh from `main_original.tex` and the JD alone
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
- Claude commits each tailored `.tex` file via a temp clone (workspace repo has lock files held by Windsurf)
- Avishek pushes from his terminal using the full sequence every time:
  ```bash
  git stash
  git pull github main --rebase
  git stash pop
  git add <filename>.tex
  git commit -m "<message>"
  git push github master:main
  ```
- Avishek syncs to Overleaf manually via Menu → Sync → Pull from GitHub
