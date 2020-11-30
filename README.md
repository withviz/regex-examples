# regex-examples
 regex examples for google sheets, alteryx, and python


| String | Do What? | Google Sheets | Alteryx | Python | Result |
| :-- | :-- | :-- | :-- | :-- | :--|
| "String with £12.99" | parse the positive number after £
| "String with -£12.99" | parse the negative number after £
| "String with 0.99" |  parse the positive number
| "String with -0.99" | parse the negative number
| "String with £12,000" | parse the positive number after £ without including ','
| "String with -£12,000" | parse the negative number after £ without including ','
| "String with £12,000.00" | parse the number and being mindful of the decimal
| "String with -£12,000.00" | parse the number and be mindful of the decimal
| "String with  |