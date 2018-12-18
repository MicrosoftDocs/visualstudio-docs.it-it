---
title: 'Estensione Excel di esempio: classe ExtensionPackage | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 3603746325be5feff231d5e2538282f7bf6d6893
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Estensione Excel di esempio: classe ExtensionPackage
Questa classe estende la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> e offre il punto di ingresso per un test codificato dell'interfaccia utente per un foglio di lavoro di [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
## <a name="assembly-attribute"></a>Attributo Assembly  
 Il file inizia con un attributo Assembly che identifica l'assembly come un'estensione di test dell'interfaccia utente.  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 Questo attributo dichiara il nome della classe di base, il nome della classe del pacchetto e il nome completo della classe per la classe del pacchetto di estensione personalizzato.  
  
## <a name="simple-properties"></a>Proprietà semplici  
 Questa classe dispone di proprietà che forniscono i valori usati dal framework dei test codificati dell'interfaccia utente per identificare e descrivere l'estensione e l'assembly. Per altre informazioni, vedere i commenti del codice.  
  
## <a name="getservice-method"></a>Metodo GetService  
 Il metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> è il singolo punto di ingresso usato dal framework dei test codificati dell'interfaccia utente per accedere al gestore della tecnologia, al provider di proprietà e al filtro delle azioni, come identificato dalla classe di base per ogni oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
