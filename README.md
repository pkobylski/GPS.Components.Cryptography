# GPS.Components.Cryptography

.NET Library for signature Xades-BES and PKCS#7. The library is used for signature by XADES-BES and PKCS # 7 method

## Methods

The EDeklaracja object in the namespace of GPS.Components.Cryptography.EDeklaracje provides static **main methods**:

```
public static XmlDocument PodpiszXades(XmlDocument doc, X509Certificate2 cert, CryptType cryptType)

public static XmlDocument PodpiszXades(string content, X509Certificate2 cert, CryptType cryptType)

public static byte[] PodpiszXadesByte(XmlDocument doc, X509Certificate2 cert, CryptType cryptType, ref XmlDocument signedXml)

public static byte[] PodpiszXadesByteZbiorczy(string base64String, X509Certificate2 cert, CryptType cryptType, ref XmlDocument signedXml)

Parameter @CryptType - SHA1, SHA256 (enum)
```
and helpers:

```
public static X509Certificate2 SelectCertificate (string title, string description)        
    
public static X509Certificate2 GetCertificate(object findValue, X509FindType findType)
    
public static byte[] PodpiszPKCS7(byt[] content, CmsSigner signer)

public static void PodpiszPKCS7(string fileName, string signedFileName, CmsSigner signer)

public static byte[] GetByte(object obj)

public static byte[] GetByte64(object obj)

public static byte[] GetByte64(object obj, ref string xml)

public static byte[] GetByte64(byte[] byteArray)
```

## Examples

```
X509Certificate certificate = EDeklaracja.GetCertificate("A600C49442FD00B77894F83E5CD0C37FA48FC45D", X509FindType.FindByThumbprint);
XmlDocument doc = XmlDocument.Load(@"c:\file.xml");
XmlDocument signed = new XmlDocument();

1) XmlDocument signedXml = EDeklaracja.PodpiszXades(doc, certificate, CryptType.SHA256);

2) XmlDocument signedXml = EDeklaracja.PodpiszXades(doc.OuterXml, certificate, CryptType.SHA256);

3) byte[] byte = EDeklaracja.PodpiszXadesByte(doc, certificate, CryptType.SHA256, ref signed);

4) byte[] byte = EDeklaracja.PodpiszXadesByteZbiorczy("UEsDBBQAAAAIAIR8LUbQEyrgdQQAALMeAAALAAAAUElULTExWi54bWztmc9u00AQxs/wFJZPcGjXdkIhKDGqmhaFQmIlRRW5oK29tI7/bGQ7GPsIQjwEr0Pfi5mNEzuZFglOIGy1+uL5zc6uP2edkdx/8SkKtY8iSX0ZD3Tz0NA1EbvS8+Prgf724uzgma6lGY89HspYDPRCpPoL+2F/KIKQJ9xdcA0qxOlAv8my5XPG3MQ7vJYfD5chy0uZMMswu8y0mGUxs9ftMX2d/zxOrbvGAGSpeyMinhXMK30B/7HMBYs+YCmTGUfMMpkYsqH44Me+uxAXxbJolO38QVm1QkOVdUYXU6bbDzU4+mN+HUJWsD5VoXPpnckkWsHVl1wLpDcr0kxEMi8GOow9ME3tkWU+1hE50uNZsFJA1xLplXwxl1cy93nJY58P9Lmu5WD+gs9wcVDCOjBOdXtdaN5nO7M1VnHJE5/HWYNZZp/VUTriRITzUJYCptWWsoQ1vT/SbRhUg2b6VAY2GtNn8Gn38t8mpfBWtgFHn23PK8fYrmV9sCDyZWbC1YccJr39zLPYD/RGSfgmPJ+k8oqPfbilZeGWcb2SOmU8cmxzc8C6NzGa6Ygw5mNe5tw+G03fHK9z6+gdQ6anLyfjqnw9RU3q1bK7l7tmm6vdXjxg2CFZsRzoL/W7bHTsjmV0Gz5uL6g2z9rcMNM41isjATWNpGae7Szt125aWzfvyR5FvnB8keRpKWw8AXP24/cMRcf9NJD25sN65ObsnlFDnvG3sGHWX0uzZ5gH6g8G79H9u8nud6Auf+wlIp1zWH1aBrgTq82p4rBfp8dDMPYBHHW6I0MIbWNww84TvljZzmucsw40ky7lQuRQOculfTk6fX0+cSavZ+ejUxiyi5ujHHxAZPb5dHIxmc3f3X6BETBgS5q5LyM/5tvUMaRtgs2scTKU0Qp3e33W5G98sUhdmcvUtd+MTl/NTiaXk9kJpO/CPQMc6ZYZPPngm3SgNsxevJmuYtx2JifzC9iRdajyme0YTe8pvWfNTbnZKVWs3nxiVrqluJb4TNqr6ry3umgJKkVPbEOhJxQdVeiIoqcVekrRswo9o6hXoR5BHQMRKkVmhUyKrApZFHUq1KGoW6EuRcoNVIqUG6gUKTdQKVJuoFLUqxB1o6vcQKVIuYFKkXIDlSLlBipFyg1UipQbqBQpN1ApUm6gUqTcQKWoVyHqxhPlBipFyg1UipQbqBQpN1ApUm6gUqTcQKVIuYFKkXIDlSLlBipFvQpRN46UG6gUKTdQKVJuoFKk3EClSLmBSpFyA5Ui5QYqRcoNVIqUG6gU9SpE3Xiq3EClSLmBSpGFz0PU3WcrfZA2Cf/Hup3Ob3c7VtvttN1O2+3sorbbaaK229kebbfTdjttt/O3dDvd3+52Om2303Y7bbezi9pup4nabmd7tN1O2+38D93OysVfZGHPubZyb4orH8809TLzx9cykJG2rN7tce06kaWvSW8JEN+08jCWt99/fNOW0AblPkZiruUa/JyIIIUyAU/iItJSUChYRIcw/3bGh31WvW1W6/kJUEsBAj8AFAAAAAgAhHwtRtATKuB1BAAAsx4AAAsAJAAAAAAAAAAgAAAAAAAAAFBJVC0xMVoueG1sCgAgAAAAAAABABgAydA7RD4v0AFeAf/rt+7PAV4B/+u37s8BUEsFBgAAAAABAAEAXQAAAJ4EAAAAAA==", certificate, CryptType.SHA256, ref signed);
```
## Example object with Signature

The signature is compatible for the "e-deklaracje" system in Poland

```
<?xml version="1.0" encoding="UTF-8"?><Signature Id="Signature-265e4f81-bdf4-402d-9753-fb977edba826" xmlns="http://www.w3.org/2000/09/xmldsig#"><SignedInfo Id="SignedInfo-265e4f81-bdf4-402d-9753-fb977edba826"><CanonicalizationMethod Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315" /><SignatureMethod Algorithm="http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" /><Reference Id="Signature-265e4f81-bdf4-402d-9753-fb977edba826-KeyInfo-Ref" URI="#Object_265e4f81-bdf4-402d-9753-fb977edba82"><DigestMethod Algorithm="http://www.w3.org/2001/04/xmlenc#sha256" /><DigestValue>EKH/3WArnsDRO2dg8oIPHKRj1ag7A1nBvCBYb7ClJU8=</DigestValue></Reference><Reference Id="Signature-265e4f81-bdf4-402d-9753-fb977edba826-XADES-Properties-Ref" URI="#SignatureProperties-265e4f81-bdf4-402d-9753-fb977edba826" Type="http://uri.etsi.org/01903#SignedProperties"><DigestMethod Algorithm="http://www.w3.org/2001/04/xmlenc#sha256" /><DigestValue>d7mXqSZZj5lQ3plQYBnriqUfNrMsAK+cD8F32EQcDjI=</DigestValue></Reference></SignedInfo><SignatureValue>FaUe59CE6F0it4Hi6Af8WQoXyEhJSSS0ZcLbOMVaRfPO/2CFvV27vD99ExqPWCm4ZONwzuobIw4UbcFXlcV3JYuIRDf/0QfcNS0Tl/pR64ecRVdL7DEyIHpyXfVFKsOo+oTYJUamqu5288QJDSRqNyTuSY15zzSllfK4Sh0U7M0=</SignatureValue><KeyInfo Id="KeyInfo-265e4f81-bdf4-402d-9753-fb977edba826"><X509Data><X509Certificate>MIIDXTCCAsqgAwIBAgIQZQxrqU2tfo9CUDmHzYjJXzAJBgUrDgMCHQUAMIGLMSswKQYDVQQLEyJDcmVhdGVkIGJ5IGh0dHA6Ly93d3cuZmlkZGxlcjIuY29tMSEwHwYDVQQKHhgARABPAF8ATgBPAFQAXwBUAFIAVQBTAFQxOTA3BgNVBAMeMABEAE8AXwBOAE8AVABfAFQAUgBVAFMAVABfAEYAaQBkAGQAbABlAHIAUgBvAG8AdDAeFw0xNDExMjIyMzAwMDBaFw0yNTExMjIyMjU5NTlaMGoxKzApBgNVBAsTIkNyZWF0ZWQgYnkgaHR0cDovL3d3dy5maWRkbGVyMi5jb20xITAfBgNVBAoeGABEAE8AXwBOAE8AVABfAFQAUgBVAFMAVDEYMBYGA1UEAxMPbS53ZWJ0cmVuZHMuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQC45Qi6iN/Bj3z+6RlihR2sGLYWzu6LxGVoTbIrSN1vIuuSRiqSnQsANYY9MZLFseadINFatcKPg/XX/T35YQWJC9T8P0a4XnP8f1wmsiPBTHLerstiEobpo7j2oTSKqnIueJpc0QO8qn2ZRVZ36jsfTtLi4eF0y8IsNNz3IPzJlwIDAQABo4HpMIHmMAwGA1UdEwEB/wQCMAAwEwYDVR0lBAwwCgYIKwYBBQUHAwEwgcAGA1UdAQSBuDCBtYAQQ5WclIgg5B6frIMajNqV/aGBjjCBizErMCkGA1UECxMiQ3JlYXRlZCBieSBodHRwOi8vd3d3LmZpZGRsZXIyLmNvbTEhMB8GA1UECh4YAEQATwBfAE4ATwBUAF8AVABSAFUAUwBUMTkwNwYDVQQDHjAARABPAF8ATgBPAFQAXwBUAFIAVQBTAFQAXwBGAGkAZABkAGwAZQByAFIAbwBvAHSCEPCYdYjH+KShRhpiTabMfYMwCQYFKw4DAh0FAAOBgQCS5n3b8kPViASj6SxMFJ3R2vtfn3j8wRU1UepQsRWp4qd7YcKNZNiDz04oGDyzWRHQz36MX0ZRPkYJY1jGxrV90lxa8tsiDV4ypggw/Ol4I7t/uIKJalSluPyr3KKeCdcpLcoUIO7goJ4fG5oZC9sviPYwVNwpeRCUNz3i13zeWQ==</X509Certificate></X509Data></KeyInfo><Object><xades:QualifyingProperties Id="QualifyingProperties-265e4f81-bdf4-402d-9753-fb977edba826" Target="#Signature-265e4f81-bdf4-402d-9753-fb977edba826" xmlns:xades="http://uri.etsi.org/01903/v1.3.2#"><xades:SignedProperties Id="SignatureProperties-265e4f81-bdf4-402d-9753-fb977edba826"><xades:SignedSignatureProperties><xades:SigningTime>2018-07-24T11:37:28Z</xades:SigningTime><xades:SigningCertificate><xades:Cert><xades:CertDigest><DigestMethod Algorithm="http://www.w3.org/2001/04/xmlenc#sha256" /><DigestValue>/yupUf2AIbo8/Ypg9EOpp/501nrX8BZGLPGc8Kuux7A=</DigestValue></xades:CertDigest><xades:IssuerSerial><X509IssuerName>CN=TEST, O=DO_NOT_TRUST, OU=Created by http://www.test.com</X509IssuerName><X509SerialNumber>134316518768006064318111822423947528543</X509SerialNumber></xades:IssuerSerial></xades:Cert></xades:SigningCertificate></xades:SignedSignatureProperties><xades:SignedDataObjectProperties><xades:DataObjectFormat ObjectReference="#Signature-265e4f81-bdf4-402d-9753-fb977edba826-KeyInfo-Ref"><xades:Description>BINARY_FORMAT []</xades:Description><xades:MimeType>text/xml</xades:MimeType><xades:Encoding>http://www.w3.org/2000/09/xmldsig#base64</xades:Encoding></xades:DataObjectFormat></xades:SignedDataObjectProperties></xades:SignedProperties></xades:QualifyingProperties></Object><Object Id="Object_265e4f81-bdf4-402d-9753-fb977edba826" MimeType="text/xml"><YOUROBJECT></YOUROBJECT></Object></Signature>
```

## Licence

Library only for testing purposes
