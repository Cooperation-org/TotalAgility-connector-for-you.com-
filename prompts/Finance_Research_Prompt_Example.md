# Finance Research Prompt Example

## Example Prompt for You.com Finance Research API

**Use Case:** Earnings Analysis
**Research Effort:** `deep` (default)

---

**Prompt:**
```
Summarize Microsoft's Q2 FY2025 earnings results — revenue, segment performance, guidance, and analyst reaction.
```

**Expected Response Shape:**
```json
{
  "output": {
    "content": "**Microsoft Q2 FY2025 Earnings Summary**\n\n**Revenue:** $78.4B, up 14% year over year [[1]]\n\n**Key Drivers:**\n- **Intelligent Cloud** — Azure and cloud services up 31%, driven by AI demand for Copilot and Azure OpenAI Service\n- **Productivity** — Microsoft 365 commercial seats grew 10%, Copilot for Microsoft 365 reaching 1M+ seats\n- **More Personal Computing** — Windows OEM growth stabilizing, Xbox content/services up 61%\n\n**Guidance:** Full-year revenue guidance raised to $236-239B.\n\n**Analyst Reaction:** Maintained Buy ratings from Goldman Sachs and Morgan Stanley, price targets $500+ [[2]]",
    "content_type": "text",
    "sources": [
      {
        "url": "https://www.microsoft.com/en-us/Investor/earnings/earnings-press-release",
        "title": "Microsoft Q2 FY2025 Earnings Press Release"
      },
      {
        "url": "https://www.msn.com/en-us/money/companies/microsoft-q2-earnings-beat-estimates",
        "title": "Microsoft beats Q2 estimates, raises guidance"
      }
    ]
  }
}
```

---

## Alternative Prompt Styles

### Competitive Benchmarking
```
Compare the gross margins of Apple, Microsoft, and Google over the past three fiscal years.
```
*Best for: multi-company financial comparison, market analysis*

### Due Diligence
```
What are the key risk factors disclosed in Palantir's most recent 10-K filing?
```
*Best for: investment analysis, compliance review*

### Macroeconomic Research
```
How has the Federal Reserve's rate path affected commercial real estate valuations since 2022?
```
*Best for: sector analysis, macro research*

### Regulatory / Filing Analysis
```
What changes did Boeing make to its revenue recognition policies in its most recent annual report?
```
*Best for: accounting analysis, regulatory compliance*

---

## Research Effort Levels

The Finance Research API accepts five effort levels (verified live 2026-05-18 against `api.you.com/v1/finance_research`):

| Level | When to Use |
|-------|-------------|
| `ulow` | Fastest, cheapest — single-fact lookups, definitional queries |
| `lite` | Light synthesis — single-company quick summaries |
| `standard` | **Recommended default** — most earnings summaries, single-company analysis |
| `deep` | Multi-company comparisons, sector research, detailed metric breakdowns |
| `exhaustive` | Complex cross-market research, full 10-K analysis, highest quality needed |

Sending any other value returns HTTP 422 with message: *"Input should be 'ulow', 'lite', 'standard', 'deep' or 'exhaustive'"*.

---

## Tips for Effective Prompts

1. **Be specific about the company and time period** — "NVDA FY2025 revenue" not just "NVDA revenue"
2. **Include the metric or event** — "Azure growth" not just "Azure"
3. **Mention the use context** — helps the API tailor the response depth
4. **For comparisons, name all companies** — "Apple, Microsoft, Google" not "these three companies"

## Integration with TotalAgility

In TotalAgility, the Finance Research service maps:
- `INPUT` → the research question (multiline, max 40,000 chars)
- `RESEARCH_EFFORT` → one of `ulow` / `lite` / `standard` / `deep` / `exhaustive` (dropdown; default `deep`)
- `FINANCE_RESPONSE_DATA` → the full `output.content` markdown response
- `STATUS_CODE` → HTTP response code for error handling
