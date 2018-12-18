---
title: Manifesti di distribuzione per le soluzioni Office | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], deployment manifests
- deployment manifests [Office development in Visual Studio]
- manifests [Office development in Visual Studio], deployment
- Office development in Visual Studio, deployment manifests
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e1276650d38f16f8ccc36720f7e273472e609367
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="deployment-manifests-for-office-solutions"></a>Manifesti di distribuzione per le soluzioni Office
  Un manifesto di distribuzione è un file XML che descrive le impostazioni di distribuzione di una soluzione Office e identifica la versione dell'applicazione corrente.  
  
 Lo sviluppo di Office in Visual Studio utilizza il [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] schema del manifesto di distribuzione definito nel [manifesto della distribuzione ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest) riferimento.  
  
## <a name="remarks"></a>Note  
 Il file manifesto di distribuzione per le soluzioni Office identifica la versione corrente e altre impostazioni di distribuzione. Fa riferimento il manifesto dell'applicazione, che descrive la versione della soluzione e tutti i file contenuti nella soluzione corrente.  
  
## <a name="file-name-syntax"></a>Sintassi del nome file  
 Il nome di un file manifesto di distribuzione deve terminare con l'estensione vsto. Anche se è uno standard [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] manifesto della distribuzione, l'estensione differisce per abilitare gli strumenti Visual Studio per Office runtime di gestire il file.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato un manifesto di distribuzione per un Visual Studio Tools per la soluzione Office.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly   
  xsi:schemaLocation=  
    "urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"   
  xmlns:dsig="http://www.w3.org/2000/09/xmldsig#"   
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"   
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"   
  xmlns="urn:schemas-microsoft-com:asm.v2"   
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"   
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"   
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"   
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <assemblyIdentity   
    name="ContosoOfficeSolutions.vsto"   
    version="1.0.0.0"   
    publicKeyToken="25d0f3ca94156f1f"   
    language="neutral"   
    processorArchitecture="msil"   
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <description   
    asmv2:publisher="Microsoft"   
    asmv2:product="ContosoOfficeSolutions"   
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <deployment install="false" mapFileExtensions="true" />  
  <dependency>  
    <dependentAssembly   
      dependencyType="install"   
      codebase="ContosoOfficeSolutions.dll.manifest"   
      size="13545">  
      <assemblyIdentity   
        name="ContosoOfficeSolutions.dll"   
        version="1.0.0.0"   
        publicKeyToken="25d0f3ca94156f1f"   
        language="neutral"   
        processorArchitecture="msil"   
        type="win32" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm=  
            "urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm=  
          "http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>PoY</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
  <publisherIdentity name="name" issuerKeyHash="003" />  
<Signature   
  Id="StrongNameSignature"   
  xmlns="http://www.w3.org/2000/09/xmldsig#">    
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
      "http://www.w3.org/2001/10/xml-exc-c14n#" />  
  <SignatureMethod Algorithm=  
    "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
          "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
        <Transform Algorithm=  
          "http://www.w3.org/2001/10/xml-exc-c14n#" />  
      </Transforms>  
      <DigestMethod Algorithm=  
        "http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>5oz</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>nNG</SignatureValue>  
  <KeyInfo Id="StrongNameKeyInfo">  
    <KeyValue>  
      <RSAKeyValue>  
        <Modulus>ufI</Modulus>  
        <Exponent>AQAB</Exponent>  
      </RSAKeyValue>  
    </KeyValue>  
    <msrel:RelData   
      xmlns:msrel=  
        "http://schemas.microsoft.com/windows/rel/2005/reldata">  
      <r:license   
        xmlns:r="urn:mpeg:mpeg21:2003:01-REL-R-NS"   
        xmlns:as=  
          "http://schemas.microsoft.com/windows/pki/2005/Authenticode">  
        <r:grant>  
          <as:ManifestInformation   
            Hash="099"   
            Description=""   
            Url="">  
            <as:assemblyIdentity   
              name="ContosoOfficeSolutions.vsto"   
              version="1.0.0.0"   
              publicKeyToken="25d0f3ca94156f1f"   
              language="neutral"   
              processorArchitecture="msil"   
              xmlns="urn:schemas-microsoft-com:asm.v1" />  
          </as:ManifestInformation>  
          <as:SignedBy />  
          <as:AuthenticodePublisher>  
            <as:X509SubjectName>CN=DDNET\BAAdmin</as:X509SubjectName>  
          </as:AuthenticodePublisher>  
        </r:grant>  
        <r:issuer>  
          <Signature   
            Id="AuthenticodeSignature"   
            xmlns="http://www.w3.org/2000/09/xmldsig#">  
            <SignedInfo>  
              <CanonicalizationMethod   
                Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" />  
              <SignatureMethod   
                Algorithm=  
                  "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
              <Reference URI="">  
                <Transforms>  
                  <Transform Algorithm=  
                    "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
                  <Transform Algorithm=  
                    "http://www.w3.org/2001/10/xml-exc-c14n#" />  
                </Transforms>  
                <DigestMethod   
                  Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
                <DigestValue>iAd</DigestValue>  
              </Reference>  
            </SignedInfo>  
            <SignatureValue>HL9</SignatureValue>  
            <KeyInfo>  
              <KeyValue>  
                <RSAKeyValue>  
                  <Modulus>ufI</Modulus>  
                  <Exponent>AQAB</Exponent>  
                </RSAKeyValue>  
              </KeyValue>  
              <X509Data>  
                <X509Certificate>MII</X509Certificate>  
              </X509Data>  
            </KeyInfo>  
          </Signature>  
        </r:issuer>  
      </r:license>  
    </msrel:RelData>  
  </KeyInfo>  
</Signature>  
</asmv1:assembly>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesti di applicazione per soluzioni Office](../vsto/application-manifests-for-office-solutions.md)  
  
  