## Amount Estimator

This folder contains a single-page HTML tool located at `index.html` that helps quickly estimate the deposit amount for a bill issuance. The page is purely static and can be opened directly in any modern browser.

### Structure

- **Core Calculation (Section ①)** – Enter company name, either the target bill amount (in 10,000 CNY units) or the deposit amount, the interest rate and date range. The page automatically computes the 360/365 day deposit requirements, recommended rounding and displays an internal summary.
- **Materials & Invoice Info (Section ②)** – Record whether a discount occurred within a week, the planned number of bills, counterparty, and whether invoices will be supplied later. The checklist (e.g. purchasing contract, electronic invoices, invoice list, inbound funds screenshot, discount flows) feeds directly into the generated scripts.
- **Outputs (Section ③)** – Two text areas are produced:
  - *Customer Manager Script* includes internal measurement results, OA wording and reminders (including the detailed invoice-supplement template when required).
  - *Customer Communication Script* summarizes what to send to clients via WeChat (amount, rate/tenor, deposit requirement, materials to provide and confirmations).

Each output has a “复制…” button that copies the generated text to the clipboard.

### Usage

1. Open `index.html` in a browser.
2. Fill in the required fields in Section ① (at least one of “拟开票金额” or “拟存定期”). The dates will auto-adjust to a +6 month tenor and calculate the day count.
3. Enter invoice/recipient information plus select/check the materials required.
4. Click **“立即测算并生成话术”**. Both the customer manager and customer scripts populate automatically using the latest templates (including the detailed invoice-supplement wording you provided).
5. Use the copy buttons under each text area to paste the script into OA, email, or WeChat as needed.

### Customization Tips

- All calculations use 10,000 CNY units for inputs. The script converts to yuan internally and presents both numeric and uppercase amounts when referencing contracts.
- The invoice-supplement template lives inside the `buildInvoiceSupplement` function in the `<script>` block; editing that function updates the generated paragraph globally.
- Materials checkboxes drive the wording in the outputs. To add/remove options, edit the checklist within Section ② and ensure the `data-label` text matches the phrase you want in the script.

Feel free to duplicate `index.html` for variations of the tool or to adjust styles (colors, fonts, spacing) directly within the `<style>` block near the top of the file.
