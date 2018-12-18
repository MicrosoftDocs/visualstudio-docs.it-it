---
title: Managed Extensibility Framework nell'Editor | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c13b1a4e1b183b3a6f4b54f58cca3593ce5c7bb2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework nell'Editor
L'editor è integrato con i componenti di Managed Extensibility Framework (MEF). È possibile compilare i componenti MEF per estendere l'editor e il codice può utilizzare anche i componenti dell'editor.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Panoramica di Managed Extensibility Framework  
 La libreria MEF è una libreria .NET che consente di aggiungere e modificare le funzionalità di un'applicazione o un componente che segue il modello di programmazione di MEF. Editor di Visual Studio sia consentono e utilizzare parti componente MEF.  
  
 La libreria MEF è contenuta nell'assembly .NET Framework versione 4 System.ComponentModel.Composition.dll.  
  
 Per ulteriori informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
### <a name="component-parts-and-composition-containers"></a>Componenti e i contenitori di composizione  
 Un componente è una classe o un membro di una classe che è possibile eseguire una (o entrambe) delle operazioni seguenti:  
  
-   Utilizzare un altro componente  
  
-   Essere utilizzati da un altro componente  
  
 Si consideri ad esempio un'applicazione di acquisto che dispone di un componente di voce dell'ordine che dipende dai dati di disponibilità del prodotto forniti da un componente di inventario del magazzino. In termini MEF, è possibile la parte di inventario *esportare* dati disponibilità del prodotto e ordine voce parte può *importare* i dati. La parte di voce di ordine e la parte di magazzino non è necessario conoscere a vicenda. il *contenitore di composizione* (fornito dall'applicazione host) è responsabile per mantenendo l'insieme di esportazioni e la risoluzione di esportazioni e importazioni.  
  
 Il contenitore di composizione, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, in genere è di proprietà dell'host. Il contenitore di composizione mantiene un *catalogo* le parti componenti esportato.  
  
### <a name="exporting-and-importing-component-parts"></a>Esportazione e importazione di componenti  
 È possibile esportare qualsiasi funzionalità, come viene implementato come classe pubblica o un membro pubblico di una classe (proprietà o metodo). Non è necessario derivare da parte dell'utente componente <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. In alternativa, è necessario aggiungere un <xref:System.ComponentModel.Composition.ExportAttribute> attributo alla classe o membro di classe che si desidera esportare. Questo attributo specifica il *contratto* dal componente che un'altra parte è possibile importare la funzionalità.  
  
### <a name="the-export-contract"></a>Il contratto di esportazione  
 Il <xref:System.ComponentModel.Composition.ExportAttribute> definisce l'entità (classe, interfaccia o struttura) da esportare. In genere, l'attributo di esportazione accetta un parametro che specifica il tipo dell'esportazione.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Per impostazione predefinita, il <xref:System.ComponentModel.Composition.ExportAttribute> attributo definisce un contratto che è il tipo della classe di esportazione.  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 Nell'esempio, il valore predefinito `[Export]` attributo equivale a `[Export(typeof(TestAdornmentLayerDefinition))]`.  
  
 È inoltre possibile esportare una proprietà o metodo, come illustrato nell'esempio seguente.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>L'importazione di un'esportazione MEF  
 Quando si desidera utilizzare un'esportazione MEF, è necessario conoscere il contratto (in genere il tipo) mediante il quale è stato esportato e aggiungere un <xref:System.ComponentModel.Composition.ImportAttribute> attributo con tale valore. Per impostazione predefinita, l'attributo di importazione accetta un parametro, ovvero il tipo della classe che modifica. Le righe di importazione di codice seguente il <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> tipo.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Recupero di funzionalità dell'Editor da un componente MEF  
 Se il codice esistente è un componente MEF, è possibile utilizzare i metadati MEF per utilizzare l'editor di componenti.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Per utilizzare le funzionalità di editor da un componente MEF  
  
1.  Aggiungere riferimenti a System.Composition.ComponentModel.dll, che si trova nella global assembly cache (GAC), e per gli assembly dell'editor.  
  
2.  Aggiungere rilevanti utilizzando le istruzioni.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Aggiungere il `[Import]` attributo all'interfaccia di servizio, come indicato di seguito.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  Dopo aver ottenuto il servizio, è possibile utilizzare uno qualsiasi dei relativi componenti.  
  
5.  Quando è stato compilato l'assembly, inserirlo nel... \Common7\IDE\Components\ cartella di installazione di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)