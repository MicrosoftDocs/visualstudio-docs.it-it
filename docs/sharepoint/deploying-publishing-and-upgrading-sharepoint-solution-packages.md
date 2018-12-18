---
title: La distribuzione, pubblicazione e aggiornamento dei pacchetti delle soluzioni SharePoint | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5990ab0f6ff6ec02131921f54197dd28e7f4e6ff
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="deploying-publishing-and-upgrading-sharepoint-solution-packages"></a>Distribuzione, pubblicazione e aggiornamento dei pacchetti delle soluzioni SharePoint
  Dopo aver sviluppato una soluzione di SharePoint in Visual Studio, è possibile distribuire il file di pacchetto (con estensione wsp) in un server SharePoint locale o pubblicarla in un server SharePoint locale o remoto. Se si distribuisce i file, è possibile personalizzare la modalità in cui vengono distribuiti i file del pacchetto (con estensione wsp).  
  
> [!NOTE]  
>  Attualmente, solo soluzioni create mediante sandbox possono essere pubblicate in server remoti di SharePoint. Per ulteriori informazioni, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="deploying-publishing-and-upgrading"></a>La distribuzione, pubblicazione e aggiornamento  
 *Distribuzione* fa riferimento alla copia di un file di soluzione SharePoint compilato da un progetto SharePoint in Visual Studio in un host locale. In una soluzione distribuita, è possibile configurare la procedura di distribuzione, quali il riciclo del pool di Internet Information Services (IIS), l'attivazione della soluzione dopo la distribuzione e così via. Per distribuire, utilizzare il **Distribuisci** comando il **compilare** menu. Per ulteriori informazioni, vedere [procedura: modificare una configurazione di distribuzione di SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) e [procedura: distribuire e pubblicare una soluzione di SharePoint in un sito di SharePoint locale](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 *Pubblicazione* si riferisce al caricamento di un file di soluzione creata mediante sandbox di SharePoint in una condivisione remota sito, ovvero un sito si trova in un altro sistema. È anche possibile pubblicare un file di soluzione creata mediante sandbox di SharePoint in un sito di SharePoint locale, ma indipendentemente dal fatto che il sito pubblicato in sia locale o remoto, non è possibile configurare i passaggi di distribuzione.  
  
 *L'aggiornamento* si riferisce all'aggiornamento di un esistente in modalità remota o una soluzione di SharePoint locale pubblicata. Dopo aver apportato le modifiche alla soluzione di SharePoint in Visual Studio, si modifica nome file del pacchetto della soluzione, ripubblicare la soluzione e quindi aggiornare la soluzione dopo Ripubblica correttamente. Se si pubblica nuovamente una soluzione pubblicata in locale, è possibile sovrascrivere il file di soluzione esistente.  
  
## <a name="deploying-packages"></a>Distribuzione di pacchetti  
 È possibile distribuire i file del pacchetto nel server SharePoint nel computer di sviluppo di test e debug. È anche possibile creare un file di pacchetto che è possibile installare in un altro computer scegliendo il **pubblica su File System** pulsante di opzione di **pubblica** la finestra di dialogo. Il pacchetto viene creato e copiato nel percorso file locale specificato. Per distribuire una soluzione di SharePoint al server locale, utilizzare il **Distribuisci** comando il **compilare** menu. Per ulteriori informazioni, vedere [procedura: distribuire e pubblicare una soluzione di SharePoint in un sito di SharePoint locale](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 Per informazioni su come distribuire una definizione di elenco, aggiungere un ricevitore di eventi e utilizzare le funzionalità di progettazione e del pacchetto, vedere [procedura dettagliata: distribuzione di una definizione di elenco attività di progetto](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).  
  
## <a name="customizing-the-deployment-process"></a>Personalizzazione del processo di distribuzione  
 Nella tabella seguente mostra le due configurazioni di distribuzione che è possibile utilizzare quando si eseguire il debug e distribuisce una soluzione di SharePoint.  
  
|Configurazione della distribuzione|Descrizione|  
|------------------------------|-----------------|  
|Impostazione predefinita|La configurazione di distribuzione predefinita. Vengono eseguiti i passaggi di distribuzione seguenti:<br /><br /> 1.  Eseguire il comando di pre-distribuzione.<br />2.  Riciclare il pool di applicazioni IIS.<br />3.  Ritira soluzione.<br />4.  Aggiungere una soluzione.<br />5.  Attivare le funzionalità.<br />6.  Eseguire il comando di post-distribuzione.<br /><br /> Quando si disinstalla un pacchetto, vengono eseguite le seguenti operazioni di ritiro.<br /><br /> 1.  Riciclare il pool di applicazioni IIS.<br />2.  Ritira soluzione.|  
|Nessuna attivazione|Questa configurazione di distribuzione esegue le stesse operazioni come la configurazione predefinita, ma ignora il passaggio di attivazione.|  
  
 È possibile creare le proprie configurazioni di distribuzione per completare un singolo passaggio o modificare l'ordine dei passaggi del processo di distribuzione. Per ulteriori informazioni, vedere [procedura: modificare una configurazione di distribuzione di SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
 È anche possibile aggiungere comandi da eseguire prima e dopo la distribuzione. Per ulteriori informazioni, vedere [procedura: impostare i comandi di distribuzione di SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).  
  
## <a name="publishing-packages-to-a-remote-or-local-server"></a>Pubblicazione di pacchetti in un Server locale o remoto  
 Per pubblicare una soluzione creata mediante sandbox di SharePoint a un server remoto, nella barra dei menu, scegliere **compilare**, **pubblica**, quindi il **pubblica** finestra di dialogo scegliere la **Pubblica sul sito di SharePoint** pulsante di opzione, fornendo l'URL del server remoto, ad esempio **https://someremoteserver.sharepoint.microsoftonline.com**.  
  
 Per pubblicare una soluzione di SharePoint a un server locale, nel **pubblica** finestra di dialogo scegliere la **pubblica su File System** pulsante di opzione, fornire un percorso di sistema locale.  
  
 Dopo che una soluzione pubblica correttamente in SharePoint, la soluzione è inclusa nel **raccolta soluzioni** in cui è possibile attivarla. Per ulteriori informazioni, vedere [procedura: distribuire, pubblicare e aggiornare le soluzioni SharePoint in un Server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
### <a name="upgrading-published-packages"></a>L'aggiornamento dei pacchetti pubblicati  
 Se si apportano modifiche a un progetto SharePoint in Visual Studio dopo la pubblicazione, è necessario aggiornare il pacchetto pubblicato per includere le modifiche. Per aggiornare correttamente, un pacchetto deve avere un nome univoco. Se un pacchetto con lo stesso nome viene trovato nel sito di SharePoint, che può verificarsi quando si aggiorna un'applicazione esistente - avvisi di un errore di nome file in conflitto e consente di rinominare il pacchetto. Dopo aver venga pubblicato nuovamente, il nuovo pacchetto viene visualizzato nel sito di SharePoint e può essere aggiornato. Un pacchetto aggiornato Aggiorna la soluzione utilizzando i dati dal pacchetto precedente e quindi attiva la soluzione in SharePoint. Per ulteriori informazioni, vedere [procedura: distribuire, pubblicare e aggiornare le soluzioni SharePoint in un Server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  