# Vulnerability Knowledge Base

This knowledge base is being used at https://probely.com/vulnerabilities/ and by Probely App.

You're free to use the information from this knowledge base. For more details check the LICENSE file.

The main difference between this and other vulnerability knowledge bases is that this one includes specific instructions on how to fix the vulnerabilities based on the tech stack used (Python, Java, PHP, nginx, Apache, etc.). 
This is a working in progress and we appreciate contributions.

You can also contribute back to this knowledge base, following the instructions below. 


## Contributing to this knowledge base
1. Clone this repo
2. Edit a vulnerability markdown file
3. Edit the text keeping in mind the file schema (see below)
4. Create a PR

## Vulnerability file schema

The header of the file is in YAML and the body in Markdown.

### Header format
```
name: <vuln name>
severity: <low|medium|high>
cvss-score: <n.n>
cvss-vector: <cvss v3 vector string>
cwe-id: <CWE-nnn>
cwe-name: <CWE name>
compliance:
  owasp10: <A1, A3, ...>
  pci: <6.5.3, 6.5.4, ...>
  ```
  
###  Body format

```
Vulnerability description text

## How to fix 

{% tabs <filename> %}

{% tab <filename> generic %}
generic how-to-fix instructions text
{% endtab %}

{% tab <filename> <tech> %}
how-to-fix instructions text for tech
{% endtab %}

{% endtabs %}
```



