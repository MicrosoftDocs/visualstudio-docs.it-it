---
title: '&lt;Firma&gt; elemento (distribuzione di ClickOnce) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: ffcc04808916d8ef31fb77cab72f54c1e22e924c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Firma&gt; elemento (distribuzione di ClickOnce)
Contiene le informazioni necessarie per apporre una firma digitale al manifesto della distribuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Note  
 Firma un manifesto di distribuzione utilizzando una firma protetta è facoltativa ma consigliato. Per ulteriori informazioni sulla firma XML file il World Wide Web Consortium, vedere raccomandazione "Firma XML Syntax and Processing," descritto in [http://www.w3.org/TR/xmldsig-core/](http://www.w3.org/TR/xmldsig-core/).  
  
 Se si desidera firmare il manifesto, è necessario specificare l'hash per tutti i file. Impossibile firmare un manifesto con i file che non è stato eseguito l'hashing, perché gli utenti non è possibile verificare il contenuto del file senza hash.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato un `Signature` elemento in un manifesto di distribuzione utilizzato in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione.  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)