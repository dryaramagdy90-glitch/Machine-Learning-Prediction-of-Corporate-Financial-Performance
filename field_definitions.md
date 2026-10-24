# Variable and field definitions

All variables are constructed from a single LSEG/Refinitiv extract (Datastream accounting and
market fundamentals combined with Refinitiv ESG, formerly ASSET4, scores), extracted on
**20 June 2025**. Firms are identified by Reuters Instrument Code (RIC). The repeated fields are
organized by fiscal year; the outcome is one-period-ahead ROA. ROA is stored by the vendor as a
decimal fraction (a value of 0.060 denotes a 6.0% return), not in percentage points.

| Variable in paper | Block | LSEG/Refinitiv source field | Construction | Scale |
|---|---|---|---|---|
| One-period-ahead ROA (outcome) | Outcome | ROA Total Assets, Percent | Vendor ROA at year t+1 (net income scaled by total assets) | Decimal fraction |
| Current ROA | Financial | ROA Total Assets, Percent | Vendor ROA at year t | Decimal fraction |
| Firm size | Financial | Total Assets, Reported (USD) | Natural log of 1 + total assets | Log USD |
| Leverage | Financial | Total Debt (USD); Total Assets, Reported (USD) | Total debt divided by total assets | Ratio |
| Market capitalization | Financial | Company Market Capitalization (USD) | Natural log of 1 + market capitalization | Log USD |
| Environmental pillar | ESG pillar | Environmental Pillar Score | Vendor pillar score | 0–100 |
| Social pillar | ESG pillar | Social Pillar Score | Vendor pillar score | 0–100 |
| Governance pillar | ESG pillar | Governance Pillar Score | Vendor pillar score | 0–100 |
| Board gender diversity | Governance | Board Gender Diversity, Percent Score | Vendor standardized score | Percentile score |
| Executive gender diversity | Governance | Executive Members Gender Diversity, Percent Score | Vendor standardized score | Percentile score |
| Board size | Governance | Board Size | Raw count of directors | Count |
| Audit-committee independence | Audit/governance | Audit Committee Independence Score | Vendor standardized score | Percentile score |
| Audit-committee expertise | Audit/governance | Audit Committee Expertise Score | Vendor percentile for the share of audit-committee members with financial or accounting expertise | Percentile score |
| Auditor tenure | Audit/governance | Auditor Tenure Score | Vendor standardized score | Percentile score |
| CEO–chairman separation | Governance | CEO-Chairman Separation Score | Vendor standardized score | Percentile score |
| Sustainability committee | Governance | CSR Sustainability Committee Score | Vendor standardized score | Percentile score |
| Country | Control | Country of Headquarters | Categorical (one-hot encoded) | Category |
| Industry | Control | ICB Industry name | Categorical (one-hot encoded) | Category |

## Notes

- Several governance and audit scores sit on provider-specific scales that do not span exactly
  0–100, so levels are comparable within a variable but should not be read as universally
  calibrated percentages.
- Board size is a raw count; the other governance and audit items are vendor-standardized
  percentile scores. Raw counts and standardized scores are distinguished throughout.
- Preprocessing (median imputation with missingness indicators, standardization, one-hot encoding
  of country and industry) is performed inside each model-fitting pipeline to limit leakage.
