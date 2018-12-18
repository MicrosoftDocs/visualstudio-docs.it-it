---
title: '&lt;punto di ingresso&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f4bd7a9a119a5e604461f44bb166f19e063ab4af
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;punto di ingresso&gt; elemento (sviluppo per Office in Visual Studio)
  Ogni elemento `entryPoint` dello spazio dei nomi `vstav3` identifica un assembly di personalizzazione che deve essere eseguito quando l'applicazione [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] è installata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `entryPoint` è obbligatorio e si trova nello spazio dei nomi `vstav3` .  
  
 Ogni elemento `entryPoint` può contenere solo un assembly di personalizzazione. Possono essere definiti più elementi `entryPoint` in un manifesto dell'applicazione.  
  
 L'elemento `entryPoint` presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`class`|Obbligatorio. Identifica un assembly di personalizzazione da eseguire. La sintassi per questo attributo è *NamespaceName.ClassName*.|  
  
 `entryPoint` presenta l'elemento seguente:  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 Obbligatorio. L'elemento `assemblyIdentity` nello spazio dei nomi `vstav3` si riferisce a un elemento `assemblyIdentity` esistente nel manifesto dell'applicazione [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .  
  
 Il ruolo di `assemblyIdentity` e relativi attributi è definito in [ &#60;assemblyIdentity&#62; elemento &#40;dell'applicazione ClickOnce&#41;](/visualstudio/deployment/assemblyidentity-element-clickonce-application).  
  
## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra elementi `entryPoint` in un manifesto dell'applicazione per una soluzione Office a livello di documento distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.ThisWorkbook">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet1">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet2">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet3">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra un elemento `entryPoint` in un manifesto dell'applicazione per una soluzione Office a livello di applicazione distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
<vstav3:entryPoint   
  class="ContosoOutlookAddIn.ThisAddIn">  
  <assemblyIdentity   
    name="ContosoOutlookAddIn"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  