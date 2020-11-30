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

### Python

``` python
import re

text = " "
query = " "
x = re.findall(query,string)
print(x)

```

For all examples, the objective is to retrieve the integer or decimal number.

| text |  google sheets | alteryx | python | result |
| :-- |  :-- | :-- | :-- | :--|
| String with £12.99 | `=value(regexextract(REGEXREPLACE(A1,"£\|$|,",""),"-*\d+.\d+"))` |  see option 1 | tbc | 12.99 |
| String with -£12.99 | `=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))` | see option 1 | tbc| 12.99
| String with 0.99 |  `=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))` | see option 1 | tbc| 0.99
| String with -0.99 | `=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))` | see option 1  | tbc| -0.99
| String with £12,000 | `=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))` | see option 1  | tbc| 12000
| String with -£12,000 | `=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))` | see option 1 | tbc| -12000
| String with £12,000.00 | `=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))` | see option 1  |tbc | 12000.00
| String with -£12,000.00 | `=value(regexextract(REGEXREPLACE(A1,"£|$|,",""),"-*\d+.\d+"))` | see option 1  | tbc| -12000.00
