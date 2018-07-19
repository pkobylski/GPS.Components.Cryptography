# GPS.Components.Cryptography
.NET Library for signature Xades-BES and PKCS#7

The library is used for signature by XADES-BES and PKCS # 7 method

The EDeklaracja object in the namespace of GPS.Components.Cryptography.EDeklaracje provides static **main methods**:

1) public static XmlDocument **PodpiszXades** (XmlDocument doc, X509Certificate2 cert, CryptType cryptType)

2) public static byte [] **PodpiszXadesByte** (XmlDocument doc, X509Certificate2 cert, CryptType cryptType, ref XmlDocument signedXml)

3) public static byte [] **PodpiszXadesByte** (XmlDocument doc, X509Certificate2 cert, CryptType cryptType, ref XmlDocument signedXml)

4) public static byte [] **PodpiszXadesByteZbiorczy** (string base64String, X509Certificate2 cert, CryptType cryptType, ref XmlDocument signedXml)

@CryptType - SHA1, SHA256

    and:

    1) public static X509Certificate2 SelectCertificate (string title, string description)
    
    2) public static X509Certificate2 GetCertificate(object findValue, X509FindType findType)

    3) public static byte [] PodpiszPKCS7 (byte [] content, CmsSigner signer)

    4) public static void PodpiszPKCS7 (string fileName, string signedFileName, CmsSigner signer)

    5) public static byte [] GetByte (object obj)

    6) public static byte [] GetByte64 (object obj)

    7) public static byte [] GetByte64 (object obj, ref string xml)

    8) public static byte [] GetByte64 (byte [] byteArray)

    Example:

    XmlDocument signed = new XmlDocument ();
    
    byte [] byte = EDeklaracja.PodpiszXadesByte (doc, this.X509Certificate, ref signed);

    In addition, the library also provides the Encryption object in namespace GPS.Components.Cryptography, which allows string encryption after providing a static Password.

The signature is compatible for the "e-deklaracje" system in Poland

**Library only for testing purposes**
