# Camden_Council_Expenditure_Audit

What is this project?

I took a massive list of 408,317 spending records from Camden Council and cleaned it up. When data is this big, it often has mistakes or confusing labels. I used Python to fix those issues so we can see where the money actually goes.

What did I fix?

Cleaning Names: The council used different ways to write "Redacted" (e.g., "REDACTED", "xxxRedactedxxx"). I grouped them all into one category so we could see the true total of hidden spending.

Removed NaNs: There were over 7,000 null values. I replaced these all but one of these with '0' as this was consistent with the context. The remaining null value was for a company name. In this case I dropped the row as it was statistically insignificant.

Outliers: I identified a few massive payments (like a £31.5m levy) that were making the rest of the data hard to read, and handled them separately.

Key Findings

Processed over 400,000 rows of data.

The cleaning revealed that 'Redacted' spending is one of the largest categories in the dataset.

The top spending area, once cleaned, was clearly identified as the GLA Statutory Levy.
