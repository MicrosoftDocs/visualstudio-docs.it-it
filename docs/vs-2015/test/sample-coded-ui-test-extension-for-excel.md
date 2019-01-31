---
title: Estensione di esempio per i test codificati dell'interfaccia utente per Excel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 15
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e8e3bebc82ffc2f714a6418afdb73de9092aab55
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54757232"
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Estensione di esempio per i test codificati dell'interfaccia utente per Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il componente dell'estensione dell'esempio viene eseguito nel processo del test codificato dell'interfaccia di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ed è organizzato in modo gerarchico, con la classe `ExtensionPackage` alla base. Al livello successivo si trovano le classi `TechnologyManager`, `ActionFilter` e `PropertyProvider`, con gli elementi di controllo al livello superiore.  
  
 ![Architettura di estensione di test di Excel](../test/media/excel-extarch.png "Excel_ExtArch")  
Architettura di estensione di Excel  
  
## <a name="extension-points"></a>Punti di estensione  
 Queste classi rappresentano i punti di estensione che sono implementati nell'esempio per abilitare i test codificati dell'interfaccia utente per [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
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
