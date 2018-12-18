---
title: Estensione del nodo Connessioni di SharePoint in Esplora Server | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0eabca43f604d92ecab78dccae281a450f7c0400
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-sharepoint-connections-node-in-server-explorer"></a>Estensione del nodo Connessioni di SharePoint in Esplora server
  In Visual Studio, è possibile connettersi ai siti SharePoint locali nel computer di sviluppo utilizzando la **connessioni di SharePoint** nodo il**Esplora Server** finestra. Questo nodo vengono visualizzati molti componenti dei siti di SharePoint locale in una visualizzazione struttura ad albero gerarchica. Ad esempio, è possibile visualizzare elenchi, raccolte e tipi di contenuto nei siti locali. Per ulteriori informazioni sull'utilizzo **Esplora Server** per connettersi ai siti di SharePoint locali, vedere [esplorazione SharePoint connessioni tramite Esplora Server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).  
  
 È possibile estendere il **connessioni di SharePoint** nodo mediante la creazione di estensioni per i nodi esistenti o creando un tipo di nodo personalizzato e aggiungerlo alla gerarchia di nodi.  
  
## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Attività per l'estensione del nodo Connessioni di SharePoint  
 Per estendere un nodo esistente, creare un'estensione di Visual Studio che implementa il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaccia. Quando si estende un nodo, è possibile aggiungere funzionalità al nodo, ad esempio la propria voci di menu di scelta rapida o le proprietà personalizzate. Per ulteriori informazioni, vedere [procedura: estendere un nodo SharePoint in Esplora Server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
 Per creare un tipo di nodo personalizzati, creare un'estensione di Visual Studio che implementa il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfaccia. Creare un nodo personalizzato se si desidera visualizzare i componenti dei siti di SharePoint che non vengono visualizzati in **Esplora Server** per impostazione predefinita. Ad esempio, **Esplora Server** non visualizzare la raccolta di Web Part di un sito di SharePoint per impostazione predefinita, ma è possibile aggiungere un nodo personalizzato che esegue questa operazione. Per ulteriori informazioni, vedere [procedura: aggiungere un nodo SharePoint personalizzata a Esplora Server](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) e [procedura dettagliata: estensione di Esplora Server per visualizzare Web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="adding-custom-properties-to-nodes"></a>Aggiunta di proprietà personalizzate ai nodi  
 Quando si estende un nodo o creare un tipo di nodo personalizzati, è possibile aggiungere proprietà personalizzate al nodo. Cui vengono visualizzate le proprietà di **proprietà** finestra quando è selezionato il nodo.  
  
 Esistono due tipi di proprietà personalizzate, che è possibile aggiungere a un nodo:  
  
-   Proprietà che consentono di visualizzare un set di dati di sola lettura dal sito di SharePoint. I dati descrivono il componente di SharePoint che rappresenta il nodo. Per una procedura dettagliata che illustra come eseguire questa operazione, vedere [procedura dettagliata: estensione di Esplora Server per visualizzare Web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Proprietà di visualizzazione dei dati di lettura/scrittura personalizzato. Per un esempio di codice che illustra come eseguire questa operazione, vedere [procedura: estendere un nodo SharePoint in Esplora Server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="getting-data-for-built-in-nodes"></a>Recupero dei dati per nodi incorporati  
 Tutti i nodi incorporati forniti da Visual Studio includono alcuni dati relativi al componente di SharePoint che rappresentano. Ad esempio, un nodo che rappresenta un elenco nel sito di SharePoint fornisce alcuni dati sull'elenco, ad esempio il titolo e l'URL della visualizzazione predefinita per l'elenco.  
  
 Per accedere a questi dati, recuperare un oggetto dati di <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> oggetto che rappresenta il nodo in questione. Il tipo dell'oggetto dati dipende dal tipo di nodo.  
  
 Esempio di codice riportato di seguito viene illustrato come ottenere l'oggetto dati per un nodo di elenco. Per questo esempio nel contesto di un esempio più esaustivo, vedere [procedura: ottenere dati per un nodo SharePoint incorporato in Esplora Server](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]  
  
 Nella tabella seguente elenca i tipi di oggetto dati per ogni tipo di nodo predefiniti.  
  
|Tipo di nodo|Tipo di oggetto dati|  
|---------------|----------------------|  
|Nodo di sito di SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|Tipo di contenuto|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|Funzionalità|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Campo|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|List|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|Modello di elenco|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|Visualizzazione elenco (Microsoft.SharePoint.SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|Associazione del flusso di lavoro|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|Modello di flusso di lavoro|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 Per ulteriori informazioni sull'utilizzo di <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà, vedere [associare dati personalizzati alle estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Estensione di Esplora Server per visualizzare le Web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Procedura: estendere un nodo SharePoint in Esplora Server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Procedura: aggiungere un nodo personalizzato di SharePoint a Esplora Server](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Procedura: recuperare dati per un nodo SharePoint incorporato in Esplora Server](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Associazione di dati personalizzati con le estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Esplorazione di connessioni di SharePoint tramite Esplora Server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Estensione degli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  