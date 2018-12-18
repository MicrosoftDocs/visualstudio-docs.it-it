---
title: '&lt;entryPointsCollection&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <entryPointsCollection> element
- application manifests [Office development in Visual Studio], <entryPointsCollection> element
- entryPointsCollection element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 357e2b4d7aedb82b63676055f1ad1215171a25cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ltentrypointscollectiongt-element-office-development-in-visual-studio"></a>&lt;entryPointsCollection&gt; elemento (sviluppo per Office in Visual Studio)
  L'elemento `entryPointsCollection` dello spazio dei nomi `vstav3` contiene tutti gli elementi `entryPoints` associati a soluzioni Office.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<entryPointsCollection>  
  <entryPoints>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
  </entryPoints>  
</entryPointsCollection>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `entryPointsCollection` è obbligatorio e si trova nello spazio dei nomi `vstav3` . Anche gli elementi figlio devono trovarsi in questo spazio dei nomi. Viene definito un solo elemento `entryPointsCollection` in un manifesto dell'applicazione.  
  
 L'elemento `entryPointsCollection` non ha attributi.  
  
 `entryPointsCollection` presenta gli elementi seguenti:  
  
### <a name="entrypoints"></a>entryPoints  
 Obbligatorio. Il ruolo del `entryPoints` elemento il `vstav3` dello spazio dei nomi è definito in [ &#60;entryPoints&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).  
  
## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra l'elemento `entryPointsCollection` in un manifesto dell'applicazione per una soluzione a livello di documento distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
<vstav3:entryPointsCollection>  
    <vstav3:entryPoints>  
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
    </vstav3:entryPoints>  
  </vstav3:entryPointsCollection>  
```  
  
## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra un elemento `entryPointsCollection` in un manifesto dell'applicazione per una soluzione a livello di applicazione distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
<vstav3:entryPointsCollection>  
    <vstav3:entryPoints>  
      <vstav3:entryPoint   
        class="ContosoOutlookAddIn.ThisAddIn">  
        <assemblyIdentity   
          name="ContosoOutlookAddIn"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
    </vstav3:entryPoints>  
  </vstav3:entryPointsCollection>  
```  
  
## <a name="multi-project-deployment-example"></a>Esempio di distribuzione di più progetti  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra un elemento `entryPointsCollection` in un manifesto dell'applicazione per una distribuzione di più progetti con due soluzioni Office. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
<vstav3:entryPointsCollection>  
      <vstav3:entryPoints   
        id="ContosoExcel">  
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
      </vstav3:entryPoints>  
      <vstav3:entryPoints   
        id="ContosoOutlook">  
        <vstav3:entryPoint   
          class="ContosoOutlookAddIn.ThisAddIn">  
          <assemblyIdentity   
            name="ContosoOutlookAddIn"   
            version="1.0.0.0"   
            language="neutral"   
            processorArchitecture="msil" />  
        </vstav3:entryPoint>  
      </vstav3:entryPoints>  
    </vstav3:entryPointsCollection>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  