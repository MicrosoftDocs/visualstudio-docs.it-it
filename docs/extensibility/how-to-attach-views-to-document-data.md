---
title: 'Procedura: collegare viste per documentare i dati | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3dfe0163bc4a47ec51e5c2dea832f6adda42ff7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128461"
---
# <a name="how-to-attach-views-to-document-data"></a>Procedura: collegare viste per documentare i dati
Se si dispone di una nuova visualizzazione del documento, è possibile associarlo a un oggetto dati del documento esistente.  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Per determinare se è possibile collegare una visualizzazione a un oggetto dati del documento esistente  
  
1.  Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2.  Nell'implementazione di `IVsEditorFactory::CreateEditorInstance`, chiamare `QueryInterface` nell'oggetto dati di documento esistente quando si chiama l'IDE il `CreateEditorInstance` implementazione.  
  
     La chiamata `QueryInterface` consente di esaminare l'oggetto dati esistente del documento, specificata nel `punkDocDataExisting` parametro.  
  
     Le interfacce esatte è necessario eseguire una query, tuttavia, dipende l'editor di apertura del documento, come descritto nel passaggio 4.  
  
3.  Se non si trovano le interfacce appropriate sull'oggetto dati di documento esistente, quindi restituire un codice di errore dell'editor che indica che l'oggetto dati del documento non è compatibile con l'editor.  
  
     Nell'implementazione dell'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, una finestra di messaggio che informa che il documento è aperto in un altro editor e viene chiesto se si desidera per chiuderla.  
  
4.  Se si chiude il documento, Visual Studio chiama il factory editor per la seconda volta. In questa chiamata, il `DocDataExisting` parametro è uguale a NULL. Quindi è stato possibile aprire l'oggetto dati del documento in un editor con l'implementazione della factory dell'editor.  
  
    > [!NOTE]
    >  Per determinare se è possibile utilizzare un oggetto dati del documento esistente, è possibile utilizzare anche informazioni private dell'implementazione dell'interfaccia eseguendo il cast di un puntatore a effettivi [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] classe dell'implementazione privata. Ad esempio, tutti gli editor standard implementano `IVsPersistFileFormat`, che eredita da <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Di conseguenza, è possibile chiamare `QueryInterface` per <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, e se l'ID classe di oggetto dati del documento esistente corrisponde l'implementazione di ID di classe, quindi è possibile utilizzare l'oggetto dati del documento.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Quando Visual Studio chiama l'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo passa nuovamente un puntatore per l'oggetto dati del documento esistente nel `punkDocDataExisting` parametro, se presente. Esaminare l'oggetto dati del documento restituito in `punkDocDataExisting` per determinare se l'oggetto dati del documento è appropriata per l'editor come descritto nella nota nel passaggio 4 della procedura in questo argomento. Se è appropriato, quindi il factory editor deve fornire una seconda vista per i dati come descritto [di supporto di più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md). In caso contrario, viene quindi visualizzato un messaggio di errore appropriato.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporta più viste di documento](../extensibility/supporting-multiple-document-views.md)   
 [Dati documento e visualizzazione documento negli editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md)