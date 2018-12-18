---
title: 'Procedura: eseguire un comando di SharePoint | Documenti Microsoft'
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
helpviewer_keywords: SharePoint commands [SharePoint development in Visual Studio], executing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8cfbcf4b00e4551b568e9124e839423f58d922c9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-execute-a-sharepoint-command"></a>Procedura: eseguire un comando di SharePoint
  Se si desidera utilizzare il modello a oggetti server in un'estensione degli strumenti di SharePoint, è necessario creare un oggetto personalizzato *comando di SharePoint* per chiamare l'API. Dopo aver definito il comando e distribuirlo con l'estensione degli strumenti di SharePoint, l'estensione può eseguire il comando per effettuare chiamate nel modello a oggetti di SharePoint server. Per eseguire il comando, utilizzare uno dei metodi di ExecuteCommand un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto.  
  
 Per ulteriori informazioni sullo scopo dei comandi di SharePoint, vedere [chiamate ai modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-execute-a-sharepoint-command"></a>Per eseguire un comando di SharePoint  
  
1.  Nell'estensione di strumenti di SharePoint, ottenere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto. Il modo in cui ottenere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto dipende dal tipo di estensione che si sta creando:  
  
    -   In un'estensione del sistema del progetto SharePoint, utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> proprietà.  
  
         Per ulteriori informazioni sulle estensioni del sistema di progetto, vedere [estensione del sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   In un'estensione del **connessioni di SharePoint** nodo **Esplora Server**, utilizzare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> proprietà. Per ottenere un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> oggetto, usare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> proprietà.  
  
         Per ulteriori informazioni su **Esplora Server** estensioni, vedere [estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   Nel codice che non fa parte di un'estensione degli strumenti di SharePoint, ad esempio la creazione guidata modello di progetto, utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> proprietà.  
  
         Per ulteriori informazioni sul recupero del servizio di progetto, vedere [utilizza il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  Chiamare uno dei metodi di ExecuteCommand il <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto. Passare il nome del comando da eseguire per il primo argomento del metodo ExecuteCommand. Se il comando ha un parametro personalizzato, è possibile passare questo parametro per il secondo argomento del metodo ExecuteCommand.  
  
     È un overload del metodo ExecuteCommand diversi per ogni firma comandi supportati. La tabella seguente elenca le firme supportate e overload da utilizzare per ogni firma.  
  
    |Firma del comando|ExecuteCommand overload da utilizzare|  
    |-----------------------|------------------------------------|  
    |Il comando contiene solo il valore predefinito <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametro e nessun valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Il comando contiene solo il valore predefinito <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametro e un valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Il comando ha due parametri (il valore predefinito <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametro e un parametro personalizzato) e nessun valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Il comando ha due parametri e un valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente viene illustrato come utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> overload da chiamare il `Contoso.Commands.UpgradeSolution` comando descritto in [procedura: creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]  
  
 Il `Execute` metodo illustrato in questo esempio è un'implementazione del <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> metodo il <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfaccia in un passaggio di distribuzione personalizzati. Per visualizzare questo codice nel contesto di un esempio più esaustivo, vedere [procedura dettagliata: creazione di un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
 Notare i seguenti dettagli relativi alla chiamata per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> metodo:  
  
-   Il primo parametro identifica il comando che si desidera chiamare. Questa stringa corrisponde al valore passato al <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> sulla definizione dei comandi.  
  
-   Il secondo parametro è il valore che si desidera passare al secondo parametro del comando personalizzato. In questo caso, è il percorso completo del file con estensione wsp che viene aggiornato al sito di SharePoint.  
  
-   Il codice non supera il flag implicito <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametro al comando. Questo parametro viene passato al comando automaticamente quando si chiama il comando da un'estensione del sistema del progetto SharePoint o un'estensione del **connessioni di SharePoint** nodo **Esplora Server**. In altri tipi di soluzioni, ad esempio la creazione guidata modello di progetto che implementa il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia, questo parametro è **null**.  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 In questo esempio richiede un riferimento all'assembly Microsoft.VisualStudio.SharePoint.  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamate ai modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Procedura: creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Procedura dettagliata: estensione di Esplora server per visualizzare web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  