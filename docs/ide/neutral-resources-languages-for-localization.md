---
title: Lingue di risorse non associate ad alcun paese per la localizzazione | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0bbddac532d242ce42330c955a797603b2d7e4a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="neutral-resources-languages-for-localization"></a>Linguaggi di risorse non associate ad alcun paese per la localizzazione
La classe <xref:System.Resources.NeutralResourcesLanguageAttribute> specifica le impostazioni cultura delle risorse incluse nell'assembly principale. Questo attributo viene usato per migliorare le prestazioni facendo in modo che l'oggetto <xref:System.Resources.ResourceManager> non cerchi le risorse incluse nell'assembly principale.  
  
 Il codice seguente illustra come impostare la lingua di risorse neutra. Il codice può essere inserito in uno script di compilazione o nel file AssemblyInfo.vb o AssemblyInfo.cs.  
  
```vb  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```csharp  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Resources.ResourceManager>   
 [Introduzione alle applicazioni internazionali basate su .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Organizzazione gerarchica di risorse per la localizzazione](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Applicazioni localizzate](../ide/localizing-applications.md)   
 [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)