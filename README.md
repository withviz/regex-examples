# regex-examples
 regex examples for google sheets, alteryx, and python

## setup

### [Google sheets](https://support.google.com/docs/answer/3098244?hl=en)

`REGEXEXTRACT(text, regular_expression)`

use `regexreplace()` to replace any `,` or currency symbols with `''` before extracting.

Convert the `result` into something that sheets can use by using `value()`

e.g.
`=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))`


### Alteryx

"In "Parse" mode, partial matches will be considered, however only the first match will be returned."

Option 1: 

Tool 1 - Use the formula tool and `REGEX_Replace([Field1], "£|$|,","")`
Tool 2 - Use the regex tool with `(-*\d+.\d+)` and Output method = Parse. Change the configuration in Output Columns to `Fixed Decimal`.

2 step `REGEX_Replace([Field1], "£|$|,","")` then `(-*\d+.\d+)` 
### Python

``` python
import re

text = " "
query = " "
x = re.findall(query,string)
print(x)

```

| text | do what? | google sheets | alteryx | python | result |
| :-- | :-- | :-- | :-- | :-- | :--|
| String with £12.99 | parse the positive number after £ | `=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))` |  2 step `REGEX_Replace([Field1], "£|$|,","")` then `(-*\d+.\d+)` | | 12.99
| String with -£12.99 | parse the negative number after £ |`=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))` | 2 step `REGEX_Replace([Field1], "£|$|,","")` then `(-*\d+.\d+)` | | 12.99
| String with 0.99 |  parse the positive number | `=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))` | 2 step `REGEX_Replace([Field1], "£|$|,","")` then `(-*\d+.\d+)` | | 0.99
| String with -0.99 | parse the negative number |`=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))` | 2 step `REGEX_Replace([Field1], "£|$|,","")` then `(-*\d+.\d+)`  | | -0.99
| String with £12,000 | parse the positive number after £ without including ',' | `=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))` | 2 step `REGEX_Replace([Field1], "£|$|,","")` then `(-*\d+.\d+)`  | | 12000
| String with -£12,000 | parse the negative number after £ without including ',' | `=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))` | 2 step `REGEX_Replace([Field1], "£|$|,","")` then `(-*\d+.\d+)` | | -12000
| String with £12,000.00 | parse the number and being mindful of the decimal | `=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))` | 2 step `REGEX_Replace([Field1], "£|$|,","")` then `(-*\d+.\d+)`  | | 12000.00
| String with -£12,000.00 | parse the number and be mindful of the decimal | `=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))` | 2 step `REGEX_Replace([Field1], "£|$|,","")` then `(-*\d+.\d+)`  | | -12000.00
