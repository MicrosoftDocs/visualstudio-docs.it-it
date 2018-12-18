---
title: Rendere persistenti i dati nel File di progetto MSBuild | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b2bb73602a6cba07fe9cbde4ddae4219f5a2b350
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Rendere persistenti i dati nel File di progetto MSBuild
Un sottotipo di progetto potrebbe essere necessario rendere persistenti i dati specifici del sottotipo nel file di progetto per un uso successivo. Un sottotipo di progetto usa la persistenza del file di progetto per soddisfare i requisiti seguenti:  
  
1.  Mantenere i dati utilizzati come parte della compilazione del progetto. (Per ulteriori informazioni su Microsoft Build Engine, vedere [MSBuild](../../msbuild/msbuild.md).) Informazioni relative alla compilazione possono:  
  
    1.  Dati indipendenti dalla configurazione. Vale a dire i dati archiviati negli elementi di MSBuild con condizioni vuote o mancante.  
  
    2.  Dati dipendenti dalla configurazione. Vale a dire i dati archiviati negli elementi di MSBuild che sono condizionati per una configurazione di progetto. Ad esempio:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Rendere persistenti i dati che non sono pertinenti compilare. Questi dati possono essere espressi in XML in formato libero che non viene convalidato rispetto a XML schema.  
  
    1.  Dati indipendenti dalla configurazione.  
  
    2.  Dati dipendenti dalla configurazione.  
  
## <a name="persisting-build-related-information"></a>Mantenimento delle informazioni relative alla compilazione  
 Persistenza dei dati utili per la creazione di un progetto viene gestita tramite MSBuild. Il sistema MSBuild mantiene una tabella master di informazioni relative alla compilazione. Sottotipi di progetto sono responsabili per l'accesso a questi dati per ottenere e impostare i valori delle proprietà. Sottotipi di progetto è possono potenziare anche la tabella di dati correlati alla compilazione aggiungendo proprietà aggiuntive da rendere persistenti e rimozione di proprietà in modo che non sono persistenti.  
  
 Per modificare i dati di MSBuild, è responsabile per recuperare l'oggetto di proprietà MSBuild dal sistema di progetto di base tramite un sottotipo di progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>è un'interfaccia implementata nel sistema del progetto principale e l'aggregazione query sottotipo di progetto per tale eseguendo `QueryInterface`.  
  
 La procedura seguente vengono delineati i passaggi per la rimozione di una proprietà utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Per rimuovere una proprietà da un file di progetto MSBuild  
  
1.  Chiamare `QueryInterface` in <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> del sottotipo di progetto.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> con `pszPropName` impostato sulla proprietà che si desidera rimuovere.  
  
### <a name="persisting-non-build-related-information"></a>Informazioni relative alla compilazione Non persistenti  
 Persistenza dei dati nei file di progetto che non è rilevante per compilare viene gestita tramite <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.  
  
 È possibile implementare <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> su principale `project subtype aggregator` oggetto, il `project subtype project configuration` oggetto, o entrambi.  
  
 Di seguito sono indicate i principali concetti riguardanti la persistenza di informazioni correlate non compilazione.  
  
-   Chiama il progetto di base sull'oggetto progetto principale aggregator sottotipo (vale a dire il sottotipo del progetto più esterno) per caricare e salvare i dati di configurazione indipendente e chiama gli oggetti di configurazione di progetto sottotipo di progetto per caricare o salvare dipendenti dalla configurazione dati.  
  
-   Il progetto di base chiama i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> più volte per ogni livello di aggregazione sottotipo di progetto e passa il GUID per ogni livello.  
  
-   Il progetto di base passa o riceve un frammento XML è dedicato a un sottotipo di progetto specifico e che utilizza questo meccanismo in modo persistente lo stato tra i livelli di aggregazione.  
  
-   Il progetto di base chiama il sottotipo di progetto più esterno <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementazione passando un GUID. Se il GUID appartiene il sottotipo del progetto più esterno, gestisce la chiamata. in caso contrario delega la chiamata a un sottotipo di progetto interna e così via, fino a quando non viene trovato il sottotipo del progetto corrispondente al GUID.  
  
-   Un sottotipo di progetto è possibile modificare anche il frammento XML prima o dopo la delega la chiamata a un sottotipo di progetto interna. Nell'esempio seguente viene illustrato un estratto da un file di progetto, in cui un nome di un file che contiene le proprietà specifiche di un sottotipo di progetto, viene passato a tale sottotipo di progetto.  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)