---
title: Estensione di esempio per i test codificati dell'interfaccia utente per Excel | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: coded UI tests, extensions for Excel
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 4986d833807f5566b74d0879b13f74e3e9e68b07
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Estensione di esempio per i test codificati dell'interfaccia utente per Excel
Il componente dell'estensione dell'esempio viene eseguito nel processo del test codificato dell'interfaccia di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ed è organizzato in modo gerarchico, con la classe `ExtensionPackage` alla base. Al livello successivo si trovano le classi `TechnologyManager`, `ActionFilter` e `PropertyProvider`, con gli elementi di controllo al livello superiore.  
  
 ![Architettura di estensione di test di Excel](../test/media/excel_extarch.png "Excel_ExtArch")  
Architettura di estensione di Excel  
  
## <a name="extension-points"></a>Punti di estensione  
 Queste classi rappresentano i punti di estensione che sono implementati nell'esempio per abilitare i test codificati dell'interfaccia utente per [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
### <a name="extensionpackage"></a>ExtensionPackage  
 Ereditata dalla classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>, è il punto di ingresso per l'estensione dei test codificati dell'interfaccia utente. L'implementazione di questa classe astratta fornisce al framework dei test codificati dell'interfaccia utente l'accesso interno al gestore tecnologia di test dell'interfaccia utente personalizzata, al provider di proprietà dei test dell'interfaccia utente e al filtro delle azioni dei test dell'interfaccia utente per il test della nuova interfaccia utente. Per altre informazioni, vedere [Classe ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md).  
  
### <a name="technologymanager"></a>TechnologyManager  
 Ereditata dalla classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>, questa classe rappresenta un gestore di tecnologia per la registrazione e la riproduzione dei test. Per altre informazioni, vedere [Classe TechnologyManager](../test/sample-excel-extension-technologymanager-class.md).  
  
### <a name="actionfilter"></a>ActionFilter  
 Ereditata dalla classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, questa classe rappresenta una classe di base per l'aggregazione dei risultati delle azioni dei test simili in un unico risultato. Per altre informazioni, vedere [Classe ActionFilter](../test/sample-excel-extension-actionfilter-class.md).  
  
### <a name="technology-elements"></a>Elementi della tecnologia  
 Una classe di base ereditata dalla classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> fornisce le basi per gli elementi della tecnologia nei test dell'interfaccia utente che possono essere registrati e riprodotti. Per altre informazioni, vedere [Classi Element](../test/sample-excel-extension-element-classes.md).  
  
### <a name="propertyprovider"></a>PropertyProvider  
 Ereditata dalla classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>, questa classe costituisce una classe di base per il supporto delle proprietà degli elementi dell'interfaccia utente per la registrazione e la riproduzione dei test. Per altre informazioni, vedere [Classe PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Classe ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md)   
 [Classe TechnologyManager](../test/sample-excel-extension-technologymanager-class.md)   
 [Classe ActionFilter](../test/sample-excel-extension-actionfilter-class.md)   
 [Classi Element](../test/sample-excel-extension-element-classes.md)   
 [Classe PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md)
