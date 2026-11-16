# Freight Finance Controls Project

A hands-on learning project that simulates the day-to-day finance work of a freight forwarder in Nairobi: recording transactions, checking supplier invoices before payment, and reporting what the numbers mean.

> **Disclaimer:** This is an independent learning project. It is not affiliated with, endorsed by, or built from the internal data of DHL or any other company. All transaction data in this repository is **synthetic** (invented for training). Supplier names are fictional. Any public company figures added later will be clearly labelled with their source.

---

## Why I built it

I am an Economics and Statistics graduate (Kenyatta University, 2025) preparing for entry-level finance roles. A finance trainee in logistics is expected to:

- run finance processes such as **Record to Report (RTR)**, **Procure to Pay (PTP)** and **Controlling**,
- **produce and validate data and numbers**,
- spot and resolve issues,
- explain finance to colleagues and stakeholders.

Each module below practises one of those skills, using tools I already work with (Excel, Git/GitHub) and tools I am building up (MySQL, Power BI).

---

## Project map

| # | Module | Skill shown | Status | File |
|---|---|---|---|---|
| 01 | Shipment ledger: journal, trial balance, shipment P&L | RTR: double-entry, balancing, margins | Done | `01_shipment_ledger.xlsx` |
| 02 | Supplier invoice matching and ageing | PTP: three-way match, holds, ageing | Done | `02_ptp_matching.xlsx` |
| 03 | Budget vs actual and variance analysis | Controlling | Planned | |
| 04 | Reconciliation and validation checks | Data validation (Excel, MySQL) | Planned | |
| 05 | Public company results dashboard | Reporting and insight (Power BI) | Planned | |

*I update this table as each module is completed.*

---

## Module 01: Shipment ledger (RTR)

Follows one air freight shipment, Nairobi to Frankfurt, from invoice to profit.

- **Journal:** six lines, each debit matched by a credit.
- **Trial balance:** totals per account built with `SUMIFS`, with a balance check (debits minus credits = 0).
- **Shipment P&L:** revenue 10,000, freight cost 7,600, handling 700, gross profit 1,700 (17%), overheads 1,000, operating profit 700 (7%), all in USD and illustrative.

**What it shows:** every transaction is recorded in two places and the books must balance before anything is reported.

---

## Module 02: Supplier invoice matching and ageing (PTP)

A synthetic register of 20 freight supplier invoices (air, ocean and road; KES 5,690,500 in total), checked before payment.

**Controls built**

| Check | Rule |
|---|---|
| Price check | Invoice vs booked cost; **HOLD** if variance is above the tolerance (2%) |
| Service evidence | **Hold** if the receipt or proof of service is missing, or differs from the invoice by more than the tolerance |
| Final status | **READY FOR PAYMENT** only if both checks pass |
| Ageing | Days overdue against a fixed reporting date, grouped into buckets (not overdue, 1-30, 31-60, 61-90, over 90) |
| Action note | Tells the reader what to do next for each invoice |

A dashboard summarises invoices on hold, held value, missing evidence, ageing and control outcomes.

**What the data shows** (reporting date 16-Nov-2026)

- 6 invoices are on hold, worth **KES 2,265,500 (about 40% of the total value)**: four price variances, one missing receipt and one receipt shortfall.
- 6 invoices pass the checks but are **61 to 137 days overdue** (about KES 1.63 million). Passing the checks does not mean the invoice has been paid, which points to a payment-run problem rather than a matching problem. In practice this risks late fees and strained supplier relationships.

**What it shows:** the three-way match catches problems that price checks alone would miss, and a summary table is only trustworthy if it reconciles back to its source.

---

## Assumptions and limitations

- All data is synthetic. Currency is KES for module 02 and USD for module 01.
- The tolerance (2%) and the reporting date are set as assumptions, not hidden inside formulas.
- Simplified on purpose: no ERP system, no tax, no foreign exchange revaluation, no partial payments.
- This demonstrates process thinking and control logic, not experience with a specific accounting system.

---

## Tools

- **Excel:** `SUMIFS`, `COUNTIFS`, nested `IF`, charts
- **Git and GitHub:** version history across the build
- **Planned:** MySQL, Power BI

---

## How to use

1. Download or clone the repository.
2. Open the workbooks in Excel. Formulas are live, so you can change an invoice amount and watch the status and dashboard update.

---

## Author

**Emmanuel Onyiego Nyotumba**: Economics and Statistics graduate, Nairobi, Kenya
LinkedIn: linkedin.com/in/emmanuel-onyiego-1320b7403
