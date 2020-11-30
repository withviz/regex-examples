# regex-examples
 regex examples for google sheets, alteryx, and python

## setup

[Google sheets](https://support.google.com/docs/answer/3098244?hl=en)
`REGEXEXTRACT(text, regular_expression)`

Alteryx
Uses 'RegEx' tool with Output method 'Parse'

"In "Parse" mode, partial matches will be considered, however only the first match will be returned."

Python

``` python
import re

text = " "
query = " "
x = re.findall(query,string)
print(x)

```

| text | Do What? | Google Sheets | Alteryx | Python | Result |
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