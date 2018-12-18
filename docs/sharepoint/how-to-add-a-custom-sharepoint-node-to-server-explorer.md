---
title: 'Procedura: aggiungere un nodo personalizzato di SharePoint a Esplora Server | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5b5cc829451a4227625ae1ad8da9e5da8bd0d9d4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Procedura: aggiungere un nodo personalizzato di SharePoint a Esplora server
  È possibile aggiungere nodi personalizzati sotto il **connessioni di SharePoint** nodo **Esplora Server**. Ciò è utile quando si desidera visualizzare i componenti aggiuntivi di SharePoint che non vengono visualizzati in **Esplora Server** per impostazione predefinita. Per ulteriori informazioni, vedere [estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
 Per aggiungere un nodo personalizzato, creare innanzitutto una classe che definisce il nuovo nodo. Quindi creare un'estensione che aggiunge il nodo come figlio di un nodo esistente.  
  
### <a name="to-define-the-new-node"></a>Per definire il nuovo nodo  
  
1.  Creare un progetto Libreria di classi.  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  
  
4.  Alla classe, aggiungere gli attributi seguenti:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Questo attributo consente a Visual Studio di individuare e caricare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> tipo al costruttore dell'attributo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. Nella definizione di un nodo, questo attributo specifica l'identificatore di stringa per il nuovo nodo. È consigliabile utilizzare il formato *nome società*. *nome del nodo* per assicurarsi che tutti i nodi di abbiano un identificatore univoco.  
  
5.  Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> metodo, utilizzare i membri del *typeDefinition* parametro per configurare il comportamento del nuovo nodo. Questo parametro è un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> oggetto che fornisce accesso agli eventi definiti nel <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interfaccia.  
  
     Esempio di codice riportato di seguito viene illustrato come definire un nuovo nodo. Questo esempio si presuppone che il progetto contiene un'icona denominata CustomChildNodeIcon come risorsa incorporata.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]  
  
### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Per aggiungere il nuovo nodo come figlio di un nodo esistente  
  
1.  Nello stesso progetto della definizione del nodo, creare una classe che implementa il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaccia.  
  
2.  Aggiungere il <xref:System.ComponentModel.Composition.ExportAttribute> attributo alla classe. Questo attributo consente a Visual Studio di individuare e caricare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> tipo al costruttore dell'attributo.  
  
3.  Aggiungere il <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> attributo alla classe. In un'estensione del nodo, questo attributo specifica l'identificatore di stringa per il tipo di nodo che si desidera estendere.  
  
     Per specificare i tipi di nodo predefiniti forniti da Visual Studio, passare uno dei seguenti valori di enumerazione al costruttore dell'attributo:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Utilizzare questi valori per specificare i nodi di connessione del sito (i nodi che consentono di visualizzare gli URL dei siti), i nodi dei siti o tutti gli altri nodi padre **Esplora Server**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Utilizzare questi valori per specificare uno dei nodi incorporati che rappresentano un singolo componente in un sito di SharePoint, ad esempio un nodo che rappresenta un elenco, un campo o un tipo di contenuto.  
  
4.  Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> (metodo), l'handle di <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> evento del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> parametro.  
  
5.  Nel <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> gestore dell'evento, aggiungere il nuovo nodo alla raccolta di nodi figlio di <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> oggetto esposto dal parametro di argomenti dell'evento.  
  
     Esempio di codice riportato di seguito viene illustrato come aggiungere il nuovo nodo come figlio del nodo di sito di SharePoint in **Esplora Server**.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]  
  
## <a name="complete-example"></a>Esempio completo  
 Esempio di codice seguente fornisce il codice completo per definire un nodo semplice e aggiungerlo come elemento figlio del nodo di sito di SharePoint in **Esplora Server**.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio si presuppone che il progetto contiene un'icona denominata CustomChildNodeIcon come risorsa incorporata. In questo esempio richiede riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## <a name="deploying-the-extension"></a>Distribuzione dell'estensione  
 Per distribuire il **Esplora Server** estensione, creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) per l'assembly e altri file che si desiderano distribuire con l'estensione del pacchetto. Per ulteriori informazioni, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Procedura: estendere un nodo SharePoint in Esplora Server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Procedura dettagliata: estensione di Esplora server per visualizzare web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  