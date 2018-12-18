---
title: Informazioni sulle estensioni di nome File | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8f504a70950ea9e808d50bd8b9bc7ef5dd92d699
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="about-file-name-extensions"></a>Sulle estensioni di File
Quando si registra un'estensione di file di un VSPackage, è associarlo a una versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Questo è importante se più di una versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è installato in un computer.  
  
 Estensioni di file per i pacchetti VSPackage sono registrate nella chiave HKEY_CLASSES_ROOT con un valore predefinito che punta a associati identificatore programmatico (ProgID).  
  
 Di seguito è riportato un esempio delle informazioni di registrazione per l'estensione di file vcproj:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 I file associati [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve essere un ProgID con controllo delle versioni, ad esempio `VisualStudio.vcproj.8.0`per consentire le installazioni side-by-side del prodotto per mantenere le associazioni di estensione di file tra versioni del prodotto. Un ProgID specifico della versione consente anche di usare i verbi standard, ad esempio modifica aperto e così via, senza preoccuparsi della sovrascrittura o sovrascritto da altre applicazioni o le versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 In alcuni casi, il ProgID associato a un'estensione di file non deve essere modificato. Ad esempio, il ProgID per l'estensione del file con estensione htm (progid = htmlfile) sono hard-coded in un numero di posizioni nel sistema operativo ed è ampiamente noto e utilizzata in associazione con i file htm e HTML.  
  
## <a name="see-also"></a>Vedere anche  
 [Registrazione di estensioni di File per le distribuzioni Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Definizione dei gestori di file per le estensioni di file](../extensibility/specifying-file-handlers-for-file-name-extensions.md)