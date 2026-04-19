
# 🧾 Nigerian Personal Income Tax Calculator — Excel Tool

> An interactive, formula-driven Microsoft Excel tool for computing Nigerian Personal Income Tax (PIT) in compliance with the PAYE progressive tax bracket system — with built-in allowable deduction support.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [How It Works](#how-it-works)
- [Tax Band Structure](#tax-band-structure)
- [Allowable Deductions](#allowable-deductions)
- [How to Use](#how-to-use)
- [Formula Logic](#formula-logic)
- [Assumptions & Compliance Notes](#assumptions--compliance-notes)
- [Tools Used](#tools-used)
- [Files in This Repository](#files-in-this-repository)
- [Conclusion](#conclusion)

---

## Project Overview

### Title: Nigerian Personal Income Tax (PIT) Calculator — Excel-Based Tool

This project is a practical, ready-to-use Excel tool that automates the calculation of Nigerian Personal Income Tax under the **Pay-As-You-Earn (PAYE)** system. It applies the **progressive tax bracket structure** as defined by Nigeria's Personal Income Tax Act (PITA), while accommodating all standard **allowable deductions** — including pension (PFA), NHIS, NHF, rent relief, life insurance, and mortgage interest.

The tool is designed for employees, HR professionals, accountants, and individuals who want a clear, transparent breakdown of how their tax liability is computed — moving beyond guesswork to a structured, formula-based calculation.

---

## Features

- ✅ **Dual income input** — enter either monthly or annual income; the calculator auto-converts
- ✅ **Smart input detection** — dynamically detects which income field has been filled and confirms it to the user
- ✅ **Progressive tax computation** — applies Nigeria's 6-band PAYE structure accurately, taxing each income slice at the correct rate
- ✅ **Allowable deductions panel** — enter deductions (rent, pension, NHIS, NHF, life insurance, mortgage) and the tool auto-calculates applicable relief
- ✅ **Capped and percentage-based deduction logic** — e.g. Rent Relief is automatically capped at ₦500,000 (20% of annual rent); Pension auto-calculates at 8% of gross income
- ✅ **Monthly and annual output** — results displayed in both timeframes for easy payslip reconciliation
- ✅ **Estimated effective tax rate** — shows the blended tax rate as a percentage of gross income
- ✅ **Full tax breakdown table** — shows exactly how much is taxed in each income band and the corresponding tax due per band

---

## How It Works

The calculator follows a 4-step computation flow:

```
Step 1 → Income Input (Monthly or Annual)
Step 2 → Gross Annual Income Derived
Step 3 → Allowable Deductions Applied → Taxable Income Computed
Step 4 → Progressive Tax Bands Applied → Total Tax Due & Net Income Output
```

All calculations are powered entirely by **Excel formulas** — no macros, no VBA. The workbook is fully transparent; every formula is visible and auditable in the cells.

---

## Tax Band Structure

The calculator applies Nigeria's PAYE progressive tax bands as follows:

| Income Range (₦) | Tax Rate | Logic |
|---|---|---|
| ₦0 – ₦800,000 | 0% | First ₦800,000 is tax-free |
| ₦800,001 – ₦3,000,000 | 15% | Applied only to income within this band |
| ₦3,000,001 – ₦12,000,000 | 18% | Applied only to income within this band |
| ₦12,000,001 – ₦25,000,000 | 21% | Applied only to income within this band |
| ₦25,000,001 – ₦50,000,000 | 23% | Applied only to income within this band |
| Above ₦50,000,000 | 25% | Applied to all income above ₦50M |

> **Important:** Tax is calculated **progressively** — each band is taxed at its own rate, not the whole income at one rate. This is a common source of misunderstanding that this tool resolves transparently.

---

## Allowable Deductions

The tool supports all standard PITA-recognised deductions, applied **before** tax is computed to arrive at **Taxable Income**:

| Deduction | Basis | Cap / Rule |
|---|---|---|
| **Rent Relief** | 20% of annual rent paid | Capped at ₦500,000 |
| **Pension (PFA)** | 8% of gross income | Auto-calculated |
| **Health (NHIS)** | 2.5% of gross income | Auto-calculated |
| **Housing (NHF)** | National Housing Fund contributions | Fully deductible |
| **Life Insurance** | Life insurance premiums paid | Fully deductible |
| **Mortgage Interest** | Interest on residential mortgage | Fully deductible |

> **Note:** Pension, NHIS deductions are automatically calculated from the gross income entered. Rent, NHF, Life Insurance, and Mortgage Interest require manual input of the actual amounts paid.

---

## How to Use

1. **Open** `Tax_Calculator.xlsx` in Microsoft Excel (2016 or later recommended)
2. **Enter your income** in one of two cells:
   - `Monthly Income (₦)` — if you know your monthly gross pay
   - `Annual Income (₦)` — if you know your annual gross pay
   - *(Enter only one — the other should remain 0)*
3. **Check the status prompt** — it confirms which income type was detected
4. **Enter applicable deductions** in the Allowable Deductions panel:
   - Input your **annual rent** (tool auto-calculates the capped 20% relief)
   - NHF, Life Insurance, and Mortgage Interest inputs if applicable
   - Pension and NHIS are auto-filled from your gross income
5. **Read your results** from the output summary:
   - Gross Income (Monthly & Annual)
   - Taxable Income (Monthly & Annual)
   - Total Tax Due (Monthly & Annual)
   - Income After Tax (Monthly & Annual)
   - Estimated Effective Tax Rate (%)
6. **Review the tax band breakdown table** to see exactly how your tax is sliced across each band

---

## Formula Logic

Key formulas powering the calculator (for transparency and auditability):

| Output | Formula Logic |
|---|---|
| Gross Annual Income | `=IF(Annual>0, Annual, Monthly × 12)` |
| Gross Monthly Income | `=IF(Monthly>0, Monthly, Annual ÷ 12)` |
| Total Deductions | `=SUM(Rent Relief + Pension + NHIS + NHF + Life Insurance + Mortgage)` |
| Taxable Income | `=MAX(0, Gross Annual – Total Deductions)` |
| Tax per Band | `=MAX(0, MIN(Taxable Income, Band Ceiling) – Band Floor) × Band Rate` |
| Total Tax | `=SUM(Tax across all 6 bands)` |
| Income After Tax | `=Taxable Income – Total Tax + Rent Relief applied` |
| Effective Tax Rate | `=Total Tax ÷ Gross Annual Income` |
| Rent Relief | `=MIN(20% × Annual Rent, 500,000)` |
| Pension (PFA) | `=8% × Gross Annual Income` |
| NHIS | `=2.5% × Gross Annual Income` |

---

## Assumptions & Compliance Notes

- The tax bands used are based on the **Personal Income Tax Act (PITA) as amended**, reflecting current FIRS PAYE guidelines
- The **first ₦800,000** of annual income attracts a **0% tax rate** (Consolidated Relief Allowance provision)
- This tool computes **employee-side tax only** — employer contributions (e.g. employer pension match) are not included
- Pension is computed as **8% of gross income** as a standard estimate; actual pension basis (basic + housing + transport) may vary by employer — users may override the auto-calculated pension value where the actual figure is known
- This tool is intended for **planning and estimation purposes** — for formal tax filings, consult a certified tax professional or FIRS-registered tax consultant

---

## Tools Used

| Tool | Purpose |
|---|---|
| Microsoft Excel | Full tool development — formulas, layout, UX design |
| Excel Formula Engine | Progressive tax logic, deduction caps, conditional input detection |

---

## Files in This Repository

| File | Description |
|---|---|
| `Tax_Calculator.xlsx` | The fully functional Excel-based tax calculator |
| `README.md` | Project documentation (this file) |

---

## Conclusion

This tool strips away the complexity of Nigerian PAYE tax computation and puts a clear, auditable, and reusable calculator in the hands of anyone who needs it. Whether you are an employee reconciling your payslip, an HR officer verifying payroll deductions, or an accountant doing quick client estimates — this calculator delivers accurate, band-by-band results with full transparency into the underlying logic.

Built entirely in Excel with zero macros, it is lightweight, portable, and immediately usable by anyone with a basic understanding of spreadsheets.

---

## Connect With Me

Want to know more?  
> Feel free to reach out: [ajagunalliyu@gmail.com](mailto:ajagunalliyu@gmail.com)  
> Connect with me on [LinkedIn](https://www.linkedin.com/in/alliyuajagun)  
> Follow on [Twitter/X](https://x.com/Sayyid_Alliyu)  
> Read more on [Medium](https://medium.com/@ajagunalliyu)  
> 💻 Explore more projects on [GitHub](https://github.com/ajagunalliyu)
---

**Prepared by:**  
**Alliyu Ajagun Aremu**

