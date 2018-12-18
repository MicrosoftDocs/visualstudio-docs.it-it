---
title: Modello di Visual Studio Manifest Schema Reference | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 87f676ef30da7c667c4ce2b688520a49ed1931c3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Riferimenti dello Schema manifesto dei modelli di Visual Studio
Questo schema viene descritto il formato dei file manifesto (.vstman) modello Visual Studio generati per i modelli di progetto o un elemento di Visual Studio e descrive il percorso e altre informazioni rilevanti relative al modello.  
  
 : Poiché esistono elemento separato e le directory di progetto, un manifesto non debba mai in grado di contenere una combinazione dei modelli di elemento e progetto.  
  
> [!IMPORTANT]
>  Il manifesto è disponibile a partire da Visual Studio 2017.  
  
## <a name="vstemplatemanifest-element"></a>Elemento VSTemplateManifest  
 L'elemento radice del manifesto.  
  
### <a name="attributes"></a>Attributi  
  
-   **Versione**: una stringa che rappresenta la versione del manifesto del modello. Obbligatorio.  
  
-   **Impostazioni locali**: stringa che rappresenta le impostazioni locali o impostazioni locali del manifesto del modello. Il valore delle impostazioni locali si applica a tutti i modelli, è necessario utilizzare un manifesto distinto per ognuna delle impostazioni locali. Facoltativo.  
  
### <a name="child-elements"></a>Elementi figlio  
  
-   **VSTemplateContainer** facoltativo.  
  
-   **VSTemplateDir** facoltativo.  
  
### <a name="parent-element"></a>Elemento padre  
 Nessuno.  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 Il contenitore del modello di manifesto elementi. Un contenitore di modello per ogni modello che definisce un manifesto.  
  
### <a name="attributes"></a>Attributi  
 **VSTemplateType** : un valore stringa che specifica il tipo del modello (`"Project"`, `"Item"`, o `"ProjectGroup"`). Obbligatorio  
  
### <a name="child-elements"></a>Elementi figlio  
  
-   **RelativePathOnDisk**: il percorso relativo del file di modello su disco. Questo percorso definisce anche la posizione del modello nell'albero del modello nella **nuovo progetto** o **nuovo elemento** finestra di dialogo. Per i modelli distribuiti come singoli file e una directory, questo percorso fa riferimento alla directory contenente i file di modello. Per i modelli distribuiti come file con estensione zip, questo percorso deve essere il percorso del file con estensione zip.  
  
-   **VSTemplateHeader** : A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elemento che descrive l'intestazione.  
  
### <a name="parent-element"></a>Elemento padre  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Descrive la directory in cui si trova il modello. Un manifesto può contenere più **VSTemplateDir** voci per fornire il nome localizzato e ordinamento di ordinamento per le directory per controllare l'aspetto nell'albero delle categorie di modello.  
  
 A causa delle loro configurazione, **VSTemplateDir** voci devono essere visualizzato solo in manifesti specificati non delle impostazioni locali.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
-   **RelativePath**: il percorso del modello. Può esistere solo una voce per ogni percorso, il primo criterio avrà la precedenza per tutti i manifesti.  
  
-   **LocalizedName**: A **NameDescriptionIcon** elemento che specifica il nome localizzato. Facoltativo.  
  
-   **SortOrder** : una stringa che specifica il tipo di ordinamento. Facoltativo.  
  
-   **ParentFolderOverrideName**: il nome della cartella padre sottoposto a override. Facoltativo. L'elemento ha un **nome** attributo, ovvero un valore stringa che specifica il nome.  
  
### <a name="parent-element"></a>Elemento padre  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Specifica il nome e descrizione, probabilmente per i modelli localizzati. Vedere **LocalizedName** sopra.  
  
### <a name="attributes"></a>Attributi  
  
-   **Pacchetto**: un valore stringa che specifica il pacchetto. Facoltativo.  
  
-   **ID**: un valore stringa che specifica l'ID. Facoltativo.  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-element"></a>Elemento padre  
 **LocalizedName**  
  
## <a name="examples"></a>Esempi  
 Di seguito è riportato un esempio di un file di progetto modello .vstman.  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>  
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>TestProjectTemplate</Name>  
        <Description>TestProjectTemplate</Description>  
        <Icon>TestProjectTemplate.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>TestProjectTemplate</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Di seguito è riportato un esempio di file di un elemento modello .vstman.  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Item">  
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ItemTemplate1</Name>  
        <Description>ItemTemplate1</Description>  
        <Icon>ItemTemplate1.ico</Icon>  
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <DefaultName>Class.cs</DefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```