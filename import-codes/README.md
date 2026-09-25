# Keep product-code characters when importing a CSV

This is a fictional, three-row practice example tested in Excel for Mac 16.70. It follows the duplicate-quote lesson. It is not a store updater.

[Download the original CSV](https://raw.githubusercontent.com/primeadv/prime-adventure-examples/main/import-codes/supplier-codes.csv). Save it unchanged before opening it in a spreadsheet.

| Original code | Opening the CSV normally in this test | Importing the code column as Text |
|---|---|---|
| `00123` | numeric `123` | text `00123` |
| `123` | numeric `123` | text `123` |
| `0012A` | text `0012A` | text `0012A` |

The first two different identifiers became the same number when opened normally. Formatting that number afterward does not tell you which original identifier it represented. Return to the unchanged source file.

## Reproduce the text import

1. Create a blank workbook. Choose **Data > Get External Data > From Text**.
2. Select the original `supplier-codes.csv`.
3. In step 1, choose **Delimited**.
4. In step 2, select **Comma** and clear **Tab**. Check that the preview has two columns.
5. In step 3, select the **product_code** column and choose **Text**. Leave the price column as General.
6. Finish, then import at A1. Select A2 and check that the formula bar shows `00123`, not `123`.

Menu names and conversion defaults differ across Excel versions and settings. This is the actual flow tested on the version above, not a claim that every CSV always loses its zeros.

## Preserving text is not the same as matching it exactly

In the imported test, A2 contains text `00123`, A3 text `123`, and A4 text `0012A`.

| Formula | Actual result in this test |
|---|---|
| `=COUNTIFS(A2:A4,A2)` | `2` |
| `=EXACT(A2,A3)` | `FALSE` |
| `=SUMPRODUCT(--EXACT(A2:A4,A2))` | `1` |

COUNTIFS can treat numeric-looking codes as equivalent even when their text has different leading zeros. Use and test a comparison that fits your identifiers. The EXACT example compares characters **and letter case**; that may or may not match your business rules. It also does not restore characters already lost on import.

The original video uses the alphanumeric code `DUP-S` and counts its two matching rows correctly. This extra example explains a boundary to check before adapting that lesson to other identifiers.

Official background: [Microsoft on leading zeros](https://support.microsoft.com/en-US/Excel/keeping-leading-zeros-and-large-numbers) and [text/CSV import options](https://support.microsoft.com/en-us/excel/get-started/import-or-export-text-txt-or-csv-files). The three-row comparison and formula results above were run locally, rather than inferred from those pages.

[Share what still takes time](https://github.com/primeadv/prime-adventure-examples/issues/new?template=practice-feedback.yml) using invented examples. A GitHub account is needed for feedback, not for downloading the file.
