# LeakageLens

### Find money your business is silently losing.

LeakageLens is an explainable financial leakage detection platform that analyzes invoices, purchase orders, payments, and credit notes to identify potential duplicate payments, overbilling, missed credits, and suspicious financial discrepancies.

Built for **ExaThon India 2026 — Money, Risk & Regulation**.

## Problem

Businesses process thousands of financial transactions across disconnected records. Duplicate payments, incorrect charges, missed supplier credits, and reconciliation errors can go undetected.

Manual audits are time-consuming, and simple matching rules can miss discrepancies when invoice identifiers, descriptions, or dates differ.

## Solution

LeakageLens combines SQL-based reconciliation, rule-based anomaly detection, and fuzzy matching to identify suspicious transactions.

Key capabilities:

- Duplicate invoice and payment detection
- Invoice-to-purchase-order reconciliation
- Credit note and payment mismatch detection
- Fuzzy matching for similar invoice records
- Confidence-ranked findings with supporting evidence
- Estimated potential financial exposure
- Auditor-friendly investigation reports

## Architecture

1. Generate or import synthetic financial transaction data.
2. Load invoice, purchase order, payment, and credit note tables into Exasol Personal.
3. Execute SQL joins, aggregations, and reconciliation checks.
4. Apply duplicate detection and fuzzy matching.
5. Calculate finding confidence and potential financial exposure.
6. Display findings and supporting evidence in the application.

## Technology Stack

- **Database:** Exasol Personal
- **Analytics:** SQL
- **Application:** Python with Streamlit
- **Data processing:** pandas
- **Similarity matching:** RapidFuzz or an equivalent library
- **Testing:** pytest
- **Version control:** Git and GitHub

Adjust this list to match the libraries and tools actually used in the project.

## Data

The project uses synthetic financial records. No proprietary employer or customer data is required.

Expected datasets:

- Invoices
- Purchase orders
- Payments
- Credit notes

All demo results and financial exposure figures should be calculated from the supplied dataset.

## Getting Started

### Prerequisites

- Python 3.11 or another supported project version
- Git
- An accessible Exasol Personal instance
- Database connection details

### Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/LeakageLens.git
cd LeakageLens
```

Create and activate a virtual environment:

```bash
python -m venv .venv
```

Windows:

```bash
.venv\Scripts\activate
```

macOS/Linux:

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

### Configure the database

Create a local `.env` file using `.env.example` as a reference.

Configure the connection parameters required by the selected Exasol Python driver. Never commit real passwords or credentials.

### Run the application

After configuring the database and implementing the setup scripts:

1. Create the database tables using the SQL scripts in `sql/`.
2. Load the synthetic datasets into Exasol Personal.
3. Run the reconciliation and detection queries.
4. Start the application:

```bash
streamlit run app.py
```

## Validation

Test the system against synthetic cases with known expected outcomes, including:

- An invoice paid twice
- An invoice exceeding its purchase order
- A credit note omitted from reconciliation
- An invoice with a modified identifier
- A valid transaction that should not be flagged

Report actual detection results and false-positive counts from the test dataset.

## Explainability

Each finding should include:

- Detection category and rule
- Related transaction identifiers
- Expected and observed amounts
- Evidence supporting the discrepancy
- Confidence score and calculation method
- Estimated potential exposure
- Recommended next investigation step

Flagged transactions require human verification before being treated as confirmed losses or recoveries.

## Project Structure

- `sql/` — database schema, reconciliation, and detection queries
- `src/` — database connectivity and analytical logic
- `data/` — synthetic data generation and instructions
- `tests/` — validation and regression tests
- `docs/` — architecture and demonstration documentation
- `presentation/` — hackathon pitch deck

## Responsible Use

LeakageLens is a decision-support and audit investigation tool. Its findings are indicators for human review, not definitive proof of fraud or wrongdoing.

## Future Scope

- Recurring financial audits
- Accounting system integrations
- Supplier-level risk analysis
- Investigation workflow and reviewer feedback
- Historical trend analysis

## License

Licensed under the Apache License, Version 2.0. See [LICENSE](LICENSE).

## Team

Nissi Fedora X 
team name:

## Acknowledgments

Built for ExaThon India 2026 using Exasol Personal as the analytical data platform.
