---
title: 'Procedura: gestire una raccolta privata usando le impostazioni del Registro di sistema | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8d88c4b440f61e87792210e8a0844b6b622e8f05
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Procedura: gestire una raccolta privata usando le impostazioni del Registro di sistema
Se si è un amministratore o lo sviluppatore di un'estensione della Shell isolata, è possibile controllare l'accesso ai controlli, modelli e strumenti in Visual Studio Gallery, la raccolta di esempi o raccolte private. Per rendere una raccolta disponibile o non disponibile, è possibile creare un file. pkgdef che descrive le chiavi del Registro di sistema modificate e i relativi valori.  
  
## <a name="managing-private-galleries"></a>La gestione di raccolte Private  
 È possibile creare un file. pkgdef per controllare l'accesso alle raccolte in più computer. Questo file deve avere il formato seguente.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Il `Repositories` chiave fa riferimento alla raccolta di essere abilitato o disabilitato. Visual Studio Gallery e la raccolta di esempi utilizzano il repository seguente GUID:  
  
-   Visual Studio Gallery: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
-   Raccolta di esempi: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
 Il `Disabled` valore è facoltativo. Per impostazione predefinita, una raccolta è abilitata.  
  
 Il `Priority` valore determina l'ordine in cui le raccolte sono elencate nella finestra di dialogo Opzioni. Visual Studio Gallery ha priorità 10 e la raccolta di esempi ha priorità 20. Raccolte private iniziano con una priorità di 100. Se più raccolte hanno lo stesso valore di priorità, l'ordine in cui vengono visualizzati è determinato dai valori dei relativi localizzata `DisplayName` attributi.  
  
 Il `Protocol` valore è obbligatorio per le raccolte di SharePoint o basata su Atom.  
  
 Sia `DisplayName`, o entrambi `DisplayNameResourceID` e `DisplayNamePackageGuid`, deve essere specificato. Se vengono specificati tutti, il `DisplayNameResourceID` e `DisplayNamePackageGuid` coppia viene utilizzata.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>La disabilitazione di un File. pkgdef utilizzando Visual Studio Gallery  
 È possibile disabilitare una raccolta in un file. pkgdef. La voce seguente disabilita la raccolta di Visual Studio:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 La voce seguente disabilita la raccolta di esempi:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolte private](../extensibility/private-galleries.md)