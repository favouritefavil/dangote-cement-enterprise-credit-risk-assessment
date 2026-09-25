# Data Dictionary

This dictionary is reproduced from the final Power BI analysis workbook. It defines the fields used in the analytical dataset and records the intended reporting basis and source mapping.

| Table | ColumnName | Meaning | Unit | ReportingBasisNote | SourceEvidenceReference |
| --- | --- | --- | --- | --- | --- |
| Fact_Financials | Year | Fiscal year (calendar year ended 31 December) | Year |  | Dim_Year |
| Fact_Financials | ReportingBasis | Group (consolidated) or Company (standalone) | Text |  | Dim_Basis |
| Fact_Financials | Revenue | Total revenue as disclosed on the face of the income statement | NGN bn | Group & Company | Batch 1 — Income Statement, Note 5 |
| Fact_Financials | CostOfSales | Production cost of sales (negative = cost) | NGN bn | Group & Company | Batch 1, Note 7 |
| Fact_Financials | GrossProfit | Revenue less cost of sales, as disclosed | NGN bn | Group & Company | Batch 1 |
| Fact_Financials | OperatingProfit | Profit from operating activities, as disclosed | NGN bn | Group & Company | Batch 1 |
| Fact_Financials | FinanceCosts | Finance costs, as disclosed (negative = expense) | NGN bn | Group & Company | Batch 1, Note 10.2 |
| Fact_Financials | ProfitBeforeTax | Profit before tax, as disclosed | NGN bn | Group & Company | Batch 1 |
| Fact_Financials | IncomeTax | Income tax expense (negative = expense) | NGN bn | Group & Company | Batch 1, Note 14.1 |
| Fact_Financials | NetProfit | Profit for the year (PAT), as disclosed | NGN bn | Group & Company | Batch 1 |
| Fact_Financials | EBITDA | Company-reported EBITDA ("Earnings before interest, taxes, depreciation and amortisation"), as disclosed in the Finance Review — Group basis only, not calculated | NGN bn | Group only — not disclosed at Company level | Phase2B_DR003_EBITDA_Raw/Standardized |
| Fact_Financials | InterestExpense | Interest expense used in the Phase 3 signed-off Interest Coverage calculation. FY2023: traced to Batch 1 Finance Costs (Note 10.2) as no more granular interest-only figure is available — same treatment as FY2024. FY2024: equals FinanceCosts (no separate interest-only figure used). FY2025: a distinct, more granular figure (346.2bn) net of other finance-cost components, per Phase 3 analysis — not independently re-verified against a specific annual-report note reference. Blank for 2022 and all Company-basis years (no validated figure available/applicable). | NGN bn | Group only — no Company-basis figure available | FY2023/FY2024: Batch 1, Note 10.2 (Finance Costs) used directly. FY2025: Phase 3 signed-off analysis. |
| Fact_Financials | Cash | Cash and cash equivalents, as disclosed on the balance sheet | NGN bn | Group & Company | Batch 2, Note 32.1 |
| Fact_Financials | TradeReceivables | Trade and other receivables total, as disclosed | NGN bn | Group & Company | Batch 2, Note 21 |
| Fact_Financials | Inventory | Inventories total, as disclosed | NGN bn | Group & Company | Batch 2, Note 20 |
| Fact_Financials | CurrentAssets | Total current assets, as disclosed | NGN bn | Group & Company | Batch 2 |
| Fact_Financials | CurrentLiabilities | Total current liabilities, as disclosed | NGN bn | Group & Company | Batch 2 |
| Fact_Financials | TradeOtherPayables | Total trade and other payables, as disclosed | NGN bn | Group & Company | Batch 5, Note 25 |
| Fact_Financials | DataQualityFlag | Notes any confirmed disclosure limitation affecting this row | Text |  |  |
| Fact_CashFlow | OperatingCashFlow | Net cash generated from/(used in) operating activities, as disclosed | NGN bn | Group & Company | Batch 4 |
| Fact_CashFlow | InvestingCashFlow | Net cash generated from/(used in) investing activities, as disclosed | NGN bn | Group & Company | Batch 4 |
| Fact_CashFlow | FinancingCashFlow | Net cash used in financing activities, as disclosed | NGN bn | Group & Company | Batch 4 |
| Fact_CashFlow | CapitalExpenditure | Additions to property, plant and equipment (Note 15), as disclosed — confirmed as the correct source-mapped Capex variable; the parallel "Acquisition of PP&E" cash-flow line is a separate, not-fully-reconciled figure and is NOT used here (see Batch 4 QA / Project Lead disposition) | NGN bn | Group & Company | Batch 4, Note 15 |
| Fact_CashFlow | DividendsPaid | Dividends paid, as disclosed on the cash flow statement | NGN bn | Group & Company | Batch 4 |
| Fact_CashFlow | DataQualityFlag | Notes the FY2024 Operating/Investing CF reclassification (accepted public-source limitation, both values traceable in Batch 4 QA) | Text |  | Batch 4 QA Report |
| Fact_Debt | ShortTermBorrowings | Financial liabilities (current), per the Statement of Financial Position — the authoritative "total current debt" figure per Project Lead disposition | NGN bn | Group & Company | Batch 3; DR023 addendum |
| Fact_Debt | LongTermBorrowings | Financial liabilities (non-current), per the Statement of Financial Position — reconciles exactly to Note 26.6's long-term maturity schedule in every year | NGN bn | Group & Company | Batch 3 |
| Fact_Debt | TotalBorrowings_Note26 | Note 26's own instrument-schedule "Total borrowings" figure — a cross-reference/supporting figure, NOT identical to ShortTerm+LongTerm in every year (see DataQualityFlag) | NGN bn | Group & Company | Batch 3, Note 26 |
| Fact_Debt | SecuredBorrowings | Secured borrowings at amortised cost (Note 26 category-level split) — entirely within the "Bank loans" category; individual loan-level assignment is NOT disclosed | NGN bn | Group & Company | Phase2B_DR009; DR023 addendum |
| Fact_Debt | UnsecuredBorrowings | Unsecured borrowings at amortised cost (Note 26 category-level split) | NGN bn | Group & Company | Phase2B_DR009; DR023 addendum |
| Fact_Debt | LeaseLiabilities_Current | Lease liabilities, current portion, as disclosed | NGN bn | Group & Company | Batch 3, Note 33 |
| Fact_Debt | LeaseLiabilities_NonCurrent | Lease liabilities, non-current portion, as disclosed | NGN bn | Group & Company | Batch 3, Note 33 |
| Fact_Debt | Equity | Total equity, as disclosed on the Statement of Financial Position | NGN bn | Group & Company | Batch 3 |
| Fact_Debt | ParentGuarantees_DR027 | Parent-company (Dangote Industries Limited) guarantees over subsidiary loans — aggregate figure, not itemised by subsidiary | NGN bn | Company only — no Group equivalent disclosed | Batch 3, Note 30.7.1/30.7.2 (DR027) |
| Fact_Debt | DataQualityFlag | Notes the SFP-vs-Note 26 current-portion reconciliation gap (accepted public-source limitation) and the Company-only nature of DR027 | Text |  | Batch 3 QA / DR023 addendum |
| Fact_Risk | RiskCategory | One of five distinct risk categories — see Dim_RiskCategory for definitions; categories are never combined into a single "total FX/risk exposure" figure | Text |  | Dim_RiskCategory |
| Fact_Risk | Metric | The specific disclosed metric within the risk category | Text |  | See SourceEvidenceNote per row |
| Fact_Risk | Currency | Currency of denomination, where relevant (FX Monetary Exposure only); "N/A" for categories not currency-specific | Text |  |  |
| Fact_Risk | Value | The disclosed figure; blank/null where confirmed not disclosed (never zero-filled) | NGN bn (see Unit) | Group & Company, varies by row | See SourceEvidenceNote per row |
| Fact_Risk | SourceEvidenceNote | Batch/note reference for this specific observation | Text |  |  |
| Dim_Year | Year / FiscalYearLabel / PeriodStart / PeriodEnd / AnnualReportSource | Calendar-year dimension for all fact tables |  |  |  |
| Dim_Basis | ReportingBasis / Definition | Group vs Company definition dimension |  |  |  |
| Dim_RiskCategory | RiskCategory / Description | Definitions of the five distinct risk categories used in Fact_Risk |  |  |  |
