# Task: Complete a Quarto Blog Post on Frequentist Statistics

## Context
You are completing a pre-populated Quarto (`.qmd`) template for a blog post on your public website. The post walks readers through key ideas in **classical frequentist statistics** using a series of simulations, framed around an **A/B test** for the "call to action" language on a website homepage.

## Deliverable
A rendered Quarto blog post that reads like a **semi-professional online article** — not a raw homework submission.

## Template Structure
The `.qmd` file already contains:
- Title
- Section headers
- Callouts describing what each section should cover

Your job is to **replace each callout with the actual content** it describes.

## Content Requirements

1. **Remove all callout prompts** from the template.
2. **Write explanatory prose**, not just code. Add paragraphs that:
   - Explain what you are doing in each section
   - Interpret what the results demonstrate
3. **Format charts professionally**:
   - Clear axis labels and titles
   - Thoughtful visual aesthetics (not default ggplot/matplotlib output)
4. **Format statistical output cleanly**:
   - Use the `gt` package (R) for tables — or an equivalent in Python
   - **Do not** dump raw R/Python console output (e.g., full `lm()` summaries with omnibus F-stats, residual quantiles, etc.)
   - Show only what's relevant to the reader

## Code Visibility Guidelines

Use Quarto code chunk options strategically:

| Situation | Recommendation |
|---|---|
| Demonstrating a core concept (e.g., Law of Large Numbers, bootstrap) | **Show the code** — it's part of the lesson |
| Chart-generation code that adds no pedagogical value | **Hide it** with `#| echo: false` |
| Verbose intermediate output | Hide with `#| output: false` or `#| include: false` |

Ask yourself for each chunk: *Does seeing this code help the reader understand the statistics?* If no, hide it.

## Final Step
Publish the rendered post to your **public website** as a blog entry.

---

**Tone target:** A data-literate reader landing on your blog should find a polished, self-contained article — one that teaches frequentist intuition through simulation, not a submitted assignment with scaffolding still visible.
