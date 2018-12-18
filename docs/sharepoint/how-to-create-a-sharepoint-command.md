---
title: 'Procedura: creare un comando di SharePoint | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fbfaeba966a2608f67ff63b0de39f13669a7169f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-sharepoint-command"></a>Procedura: creare un comando di SharePoint
  Se si desidera utilizzare il modello a oggetti server in un'estensione degli strumenti di SharePoint, è necessario creare un oggetto personalizzato *comando di SharePoint* per chiamare l'API. Definire il comando di SharePoint in un assembly che è possibile chiamare direttamente nel modello a oggetti server.  
  
 Per ulteriori informazioni sullo scopo dei comandi di SharePoint, vedere [chiamate ai modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-create-a-sharepoint-command"></a>Per creare un comando di SharePoint  
  
1.  Creare un progetto libreria di classi con la configurazione seguente:  
  
    -   Destinata a .NET Framework 3.5. Per ulteriori informazioni sulla selezione del framework di destinazione, vedere [procedura: destinare una versione di .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
    -   È destinato il AnyCPU o x64 piattaforma. Per impostazione predefinita, la piattaforma di destinazione per i progetti libreria di classi è AnyCPU. Per ulteriori informazioni sulla scelta della piattaforma di destinazione, vedere [procedura: configurare progetti per piattaforme di destinazione](../ide/how-to-configure-projects-to-target-platforms.md).  
  
    > [!NOTE]  
    >  Non è possibile implementare un comando di SharePoint nello stesso progetto che definisce un'estensione degli strumenti di SharePoint, perché i comandi di SharePoint come destinazione la destinazione di estensioni di strumenti .NET Framework 3.5 e SharePoint il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. È necessario definire i comandi di SharePoint che vengono utilizzati per l'estensione in un progetto separato. Per ulteriori informazioni, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft. SharePoint  
  
3.  In una classe nel progetto, creare un metodo che definisce il comando di SharePoint. Il metodo deve essere conforme alle linee guida seguenti:  
  
    -   Può avere uno o due parametri.  
  
         Il primo parametro deve essere un <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> oggetto. Questo oggetto fornisce il Microsoft.SharePoint.SPSite o Microsoft.SharePoint.SPWeb in cui viene eseguito il comando. Fornisce inoltre un <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> oggetto che può essere utilizzato per scrivere messaggi di **Output** finestra o **elenco errori** finestra in Visual Studio.  
  
         Il secondo parametro può essere un tipo di propria scelta, ma questo parametro è facoltativo. Se è necessario passare dati dall'estensione degli strumenti di SharePoint per il comando, è possibile aggiungere questo parametro al comando di SharePoint.  
  
    -   Può avere un valore restituito, ma questa operazione è facoltativa.  
  
    -   Il secondo parametro e il valore restituito deve essere un tipo che può essere serializzato da Windows Communication Foundation (WCF). Per ulteriori informazioni, vedere [tipi supportati dal serializzatore dei contratti dati](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) e [utilizzando la classe XmlSerializer](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).  
  
    -   Il metodo può avere qualsiasi visibilità (**pubblica**, **interno**, o **privata**), e può essere statico o non statici.  
  
4.  Applicare il <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> al metodo. Questo attributo specifica un identificatore univoco per il comando. Questo identificatore non deve corrispondere al nome di metodo.  
  
     Quando si chiama il comando di estensione degli strumenti di SharePoint, è necessario specificare lo stesso identificatore univoco. Per ulteriori informazioni, vedere [procedura: eseguire un comando di SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md).  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra un comando di SharePoint che include l'identificatore `Contoso.Commands.UpgradeSolution`. Questo comando Usa le API nel modello a oggetti server, eseguire l'aggiornamento a una soluzione distribuita.  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]  
  
 Oltre il primo implicito <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametro, questo comando ha anche un parametro di stringa personalizzata che contiene il percorso completo del file con estensione wsp che viene aggiornato al sito di SharePoint. Per visualizzare questo codice nel contesto di un esempio più esaustivo, vedere [procedura dettagliata: creazione di un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio richiede riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft. SharePoint  
  
## <a name="deploying-the-command"></a>Il comando di distribuzione  
 Per distribuire il comando, includere l'assembly del comando nello stesso [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) del pacchetto con l'assembly dell'estensione che usa il comando. È inoltre necessario aggiungere una voce per l'assembly di comandi nel file Extension. vsixmanifest. Per ulteriori informazioni, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamate ai modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Procedura: eseguire un comando di SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Procedura dettagliata: estensione di Esplora server per visualizzare web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  