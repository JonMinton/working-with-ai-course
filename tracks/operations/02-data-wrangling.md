# O2. Data Wrangling

## Data Work Without Code

You have a spreadsheet. You need to:
- Clean up messy entries
- Extract specific information
- Transform formats
- Combine from multiple sources
- Analyse patterns

Traditionally this required formulas, scripts, or data tools. AI can do much of this conversationally.

## Cleaning Patterns

### Inconsistent Formatting

> "Here's a list of phone numbers in various formats:
> (555) 123-4567
> 555.123.4567
> 555-123-4567
> 5551234567
>
> Convert all to the format: +1-555-123-4567"

AI can handle messy input and standardise it.

### Data Entry Errors

> "Here's a list of company names with likely typos and inconsistencies:
> Mircosoft
> Apple Inc.
> Apple Inc
> APPLE
> Gooogle
> Google LLC
>
> Identify likely duplicates and standardise to one correct version each."

Good for deduplication and standardisation.

### Missing Data

> "This CSV has missing values marked as 'N/A', 'null', '-', and empty cells. List all rows with missing data and which fields are missing."

Identifying gaps before you decide how to handle them.

```
QUIZ:
You have a spreadsheet with 200 addresses in inconsistent formats. What's the most efficient approach?

* Clean them manually — AI will make mistakes
* Have AI clean all 200 and trust the output
*! Have AI clean a sample of 20, verify the results, then clean the rest with adjustments if needed
* Export to a data cleaning tool

FEEDBACK: Testing on a sample first catches systematic errors before they propagate to all 200 entries. Always verify AI's data transformation approach.
```

## Extraction Patterns

### Structured Data from Text

> "Extract from each of these email signatures:
> - Name
> - Title
> - Company
> - Phone (if present)
> - Email (if present)
>
> Return as a table."

AI can pull structure from unstructured text.

### Specific Fields

> "From this list of product descriptions, extract:
> - Product name
> - Price (in GBP)
> - Key features (up to 3)
>
> If any field is unclear or missing, mark as 'N/A'."

Explicit instructions about handling ambiguity prevent guessing.

### Pattern Recognition

> "These transaction descriptions are from bank statements:
> - AMAZON.CO.UK 123456 SEATTLE
> - TESCO STORES 2847 LONDON
> - UBER *TRIP BHXDE
>
> Extract the merchant name (without location codes or reference numbers)."

AI can identify patterns humans would find tedious to parse.

```
EXERCISE:
Take a messy data source you work with regularly (email list, transaction log, contact database).

1. Paste a sample to AI
2. Ask it to identify what fields could be extracted
3. Have it extract those fields into a clean table
4. Verify accuracy against the original
```

## Transformation Patterns

### Format Conversion

> "Convert this data from vertical format (one row per attribute) to horizontal format (one row per entity, attributes as columns)."

> "Convert these dates from DD/MM/YYYY to YYYY-MM-DD format."

> "Convert these amounts from GBP to USD using rate 1.27."

### Categorisation

> "Categorise these expenses into: Travel, Software, Equipment, Services, Other. If unclear, suggest the most likely category."

AI can apply judgment where rules would be complex.

### Enrichment

> "For each company name in this list, add:
> - Likely industry
> - Company size (if well-known)
> - Note if it's a government, nonprofit, or education institution"

Be careful: AI may guess incorrectly. Verify important enrichments.

## Combining Data

### Matching Across Sources

> "Here are two lists of customers — one from our CRM, one from our billing system. They use different formats and some names are slightly different. Identify likely matches and flag uncertain ones."

Fuzzy matching that would require specialised tools.

### Reconciliation

> "Here's our inventory count and here's what the system shows. Identify discrepancies over 5% difference."

Comparison tasks that would require formulas.

## Analysis Patterns

### Quick Statistics

> "For this sales data:
> - What's the total, average, min, max?
> - Which product sold most?
> - Which month was highest?
> - Any obvious outliers?"

Overview before deeper analysis.

### Trend Identification

> "Look at these monthly figures for 2023. What patterns do you see? Any concerning trends? Any anomalies?"

AI can spot patterns and flag things worth investigating.

### Segmentation

> "Group these customers by:
> 1. Total spend (high/medium/low)
> 2. Frequency (regular/occasional/one-time)
> 3. Recency (active/lapsed)
>
> How many in each group?"

RFM-style analysis without building the model.

```
QUIZ:
AI identifies that sales dropped 40% in March. What should you do next?

* Report the finding to leadership
* Ask AI why sales dropped
*! Verify the 40% figure against the source data, then investigate causes
* Assume it's a data error

FEEDBACK: Always verify AI's analytical findings against source data before acting on them or reporting them. Then investigate causes (AI may not have the context to explain why).
```

## Working with Tables and Spreadsheets

### Describing Your Data

When asking AI to work with tabular data, describe clearly:

> "I have a spreadsheet with columns: Date, Customer, Product, Quantity, Unit Price, Total. 500 rows of sales transactions. I'll paste the first 20 rows as a sample."

Context helps AI understand what you're working with.

### Copy-Paste Workflow

For small datasets:
1. Copy data from spreadsheet
2. Paste into AI chat
3. Get transformed output
4. Paste back into spreadsheet

For large datasets:
- Work on samples
- Build formulas based on AI suggestions
- Consider actual data tools if AI approach doesn't scale

### When to Move to Real Tools

AI is good for:
- One-off transformations
- Exploring what's possible
- Small to medium datasets
- Tasks that don't need to repeat exactly

Real data tools (Excel, Python, SQL) are better for:
- Large datasets (thousands of rows)
- Repeated processing
- Auditable, reproducible workflows
- Complex calculations

## The Verification Imperative

Data work requires extra verification:

**Why AI data errors are dangerous:**
- Errors can be systematic (wrong on all 200 rows)
- Numbers look authoritative
- Errors cascade into decisions
- Hard to spot without checking

**How to verify:**
1. Check a random sample (not just the first few)
2. Verify edge cases (unusual values, missing data)
3. Cross-check totals and counts
4. Question surprising results

## Key Takeaways

- AI can clean, extract, transform, combine, and analyse data conversationally
- Cleaning: standardise formats, fix errors, identify gaps
- Extraction: pull structured data from unstructured text
- Transformation: convert formats, categorise, enrich
- Analysis: quick stats, trends, segmentation
- Always verify AI's data work — errors can be systematic
- Test on samples before processing large datasets
- Know when to move to real data tools (scale, repeatability, auditability)

---

Next: **O3. Process Documentation** →
