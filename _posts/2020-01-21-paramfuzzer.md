---
title: "Parameter Fuzzer"
date: "2020-01-21"
layout: single
tags:
- AI
categories:
- Projects
---

# Parameter Fuzzer ( ParamFuzzer )

Basically it gets parameters / inputs of the site
**explain code**:
```python
source_code = soup(respones.text, "html.parser")
inputs = source_code.find_all("input")
for i in inputs:
    if i['name'] == "":
      pass
    else:
      print i['name']
```
then it tries to edit it and see if XSS or IDOR is
available

