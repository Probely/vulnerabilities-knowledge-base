---
name: Certificate with insufficient key size or usage, or insecure signature algorithm
severity: low
cvss-score: 4.8
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:L/I:L/A:N
cwe-id: CWE-310
cwe-name: Cryptographic Issues
compliance:
  owasp10: A2
  pci: 4.1, 6.5.4

---            

We identified one or more issues with your X509 server certificate, which are detailed further below.

This finding usually means that the certificate was emitted with insecure attributes. Common examples include:

  * Using 1024-bit RSA keys;
  * Using the MD5 hashing algorithm for digital signatures;
  * Having an invalid `keyUsage` attribute. For example, using a certificate whose purpose does not allow it to be used for Digital Signature or Key Agreement.

## How to fix

{% tabs certificate-with-insufficient-key-size-or-usage-or-insecure-signature-algorithm %}
{% tab certificate-with-insufficient-key-size-or-usage-or-insecure-signature-algorithm generic %}
Please replace your X509 certificate as soon as possible. Use a certificate from a Certification Authority trusted by modern browsers, which should guarantee it fulfills all security requirements. If you are unsure about choosing a Certificate Authority, we recommend [Let's Encrypt](https://letsencrypt.org/). Let's Encrypt provides modern X509 certificates at no cost.

If you are using an internal Certificate Authority, or are using self-signed certificates, please ensure that the following requirements are met:

  * Use RSA certificates with, at least, 2048-bit key size, or EC certificates with, at least, 256-bit key size;
  * Ensure that a strong hash function is used in the certificate digital signature, such as SHA-256;
  * Ensure that the `keyUsage` attribute has the required flags: Digital Signature and Key Agreement.
{% endtab %}

{% endtabs %}
