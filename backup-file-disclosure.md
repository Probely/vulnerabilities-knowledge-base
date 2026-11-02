---
name: Backup file disclosure
severity: low
cvss-score: 5.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N
cwe-id: CWE-200
cwe-name: Exposure of Sensitive Information to an Unauthorized Actor
compliance:
  HIPAA: "164.306(a)"
  PCI-DSS v4.0.1: "6.2.4"
---

A backup or temporary file is accessible through the web server. Such files can expose application source, configuration, credentials, or other information that was not intended to be public. A backup may also be served as plain text instead of passing through the interpreter or access controls used by the original file.

The impact depends on the exposed content. This is a deployment or configuration weakness rather than a vulnerability tied to one software version or CVE.

## How to fix

{% tabs backup-file-disclosure %}
{% tab backup-file-disclosure generic %}
Remove backup and temporary files from publicly served directories and store required backups outside the web root with appropriate access controls. Ensure deployment packages contain only the files needed to run the application.

Configure the web server to deny access to backup and editor-generated files, and verify that the affected URLs are no longer accessible. If sensitive data was exposed, investigate access and rotate affected credentials.
{% endtab %}

{% endtabs %}
