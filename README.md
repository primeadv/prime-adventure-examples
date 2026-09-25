# Prime Adventure examples

Practice files for original Prime Adventure videos.

## A price lookup can miss duplicate quotes

The lookup returns **$8.00**, but another row contains the same product code and **$9.00**. This two-row lesson shows how to count the matching rows and hold a conflicting update.

[Download the practice ZIP](https://github.com/primeadv/prime-adventure-examples/releases/download/duplicate-quotes-v1/duplicate-quote-practice.zip)

The ZIP contains the editable `.xlsx` workbook, a fictional CSV, instructions and file hashes. No sign-in is intended to be required for the public download.

## Try the workbook

1. Open `duplicate-quote-practice.xlsx`. The worksheet is named `Duplicate quote`.
2. A6 and A7 contain the product codes. B6 and B7 contain the prices.
3. D6 is the code to find. E6 shows the first price; F6 counts matching rows.
4. With DUP-S in both source rows, F6 is 2 and G6 says `Hold: duplicate`.
5. Change A7 to OTHER. F6 becomes 1. `Compare price` does not mean approve the price.
6. Change D6 to ABSENT. The count becomes 0 and the result says `Missing`.
7. Clear D6. The count stays blank and the action says `Enter code`.

The formula in F6 is:

```
=IF(D6="","",COUNTIFS($A$6:$A$7,D6))
```

COUNTIFS ignores letter case. This lesson uses the same uppercase code in both rows. It also treats `*` and `?` as wildcards; adapt and test the criteria for codes containing these characters.
The source range covers only two rows. Extend it for a longer list. Keep product codes as text when leading zeros matter.

The lookup is deliberately separate from the duplicate check. Returning a price does not establish that the match is unique or that the price is correct.

## What was verified

The workbook was recalculated with LibreOffice and checked by changing the inputs in Excel for Mac 16.70 for duplicate, unique, missing, blank and lowercase search cases. This does not establish compatibility with every spreadsheet application or import setting.

This file is a lesson, not a store importer or a complete price-validation system. Keep both conflicting source quotes until the supplier clarifies which is valid. No account connection, macros or real customer data is required.

## What still takes time?

After trying the check, [tell us which step you still repeat](https://github.com/primeadv/prime-adventure-examples/issues/new?template=practice-feedback.yml). For example: matching a fresh supplier file to the same catalog each week, or resolving two different prices for one code.

The feedback form requires a GitHub account; the download does not. Describe your workflow using invented examples, without private supplier files or customer details. Feedback helps us choose what to demonstrate next and does not create a support or feature-delivery commitment.

Channel: https://www.youtube.com/@WatchPrimeAdventure
