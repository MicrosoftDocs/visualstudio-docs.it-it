---
title: 'Procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un Server remoto | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 108474e725c95f495bf6eec0f9a2224ca971b3d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto
  Oltre a distribuire le soluzioni di SharePoint al sistema locale, è possibile pubblicare soluzioni create mediante sandbox di SharePoint a siti remoti o siti di SharePoint locali. Il processo di pubblicazione remoto copia il file con estensione wsp nel server SharePoint, installa la soluzione e quindi consente di attivare la soluzione. È inoltre possibile aggiornare un'installazione di soluzioni SharePoint remota dopo aver apportate le modifiche.  
  
## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Per pubblicare una soluzione creata mediante sandbox di SharePoint in un server SharePoint remoto  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il progetto in modalità sandbox di SharePoint che si desidera pubblicare, quindi fare clic **pubblica**.  
  
2.  Nel **pubblica** finestra di dialogo, scegliere il **pubblica sul sito di SharePoint** pulsante di opzione e quindi immettere un URL per un sito di pubblicazione online, come nell'esempio seguente: **https://mytestsite.sharepoint.microsoftonline.com** .  
  
3.  Scegliere il **aprire la pagina Raccolta soluzioni nel browser dopo la pubblicazione** pulsante di opzione per visualizzare l'elenco delle soluzioni di **raccolta soluzioni** pagina dopo la pubblicazione.  
  
4.  Scegliere il **pubblica** pulsante.  
  
5.  Accedere al server remoto se è necessaria l'autenticazione utente.  
  
     Viene visualizzato lo stato di pubblicazione in Visual Studio **Output** finestra. Al termine del processo, il file di soluzione (con estensione wsp) è installato nel server SharePoint remoto. Tuttavia, deve comunque essere attivata prima di poter essere utilizzato in SharePoint.  
  
6.  Nel **raccolta soluzioni** pagina, selezionare l'applicazione di SharePoint e sulla barra multifunzione, quindi scegliere il **attiva** pulsante.  
  
7.  Nel **attivare soluzione** della finestra di dialogo della barra multifunzione scegliere la **attiva** nuovamente clic sul pulsante.  
  
     Il **stato** colonna il **raccolta soluzioni** pagina indica che l'applicazione è attiva.  
  
## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Per eseguire l'aggiornamento di una soluzione creata mediante sandbox di SharePoint in un server SharePoint remoto  
 Se una soluzione creata mediante sandbox di SharePoint è già pubblicata in un server remoto, il processo seguente consente di eseguire l'aggiornamento dopo aver apportato modifiche all'applicazione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
1.  Rinominare il pacchetto di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. A tale scopo, in **Esplora** aprire il pacchetto. Viene visualizzato nel **Esplora pacchetti**.  
  
2.  In **Esplora pacchetti**nella **nome** , modificare il nome del pacchetto con un nome univoco.  
  
3.  Salvare il progetto.  
  
4.  In **Esplora**, aprire il menu di scelta rapida per il progetto e quindi scegliere **pubblica**.  
  
5.  Nel **pubblica** finestra di dialogo scegliere la **pubblica sul sito di SharePoint** pulsante di opzione e quindi, se l'URL per il server remoto in cui è stata salvata la soluzione è manca, l'immissione.  
  
6.  Scegliere il **aprire la pagina Raccolta soluzioni nel browser dopo la pubblicazione** pulsante di opzione per visualizzare l'elenco delle soluzioni di **raccolta soluzioni** pagina dopo la pubblicazione.  
  
7.  Scegliere il **pubblica** pulsante.  
  
8.  Accedere al server remoto se è necessaria l'autenticazione utente.  
  
     Se connesso al server remoto di recente, potrebbe non essere richiesta l'autenticazione.  
  
     Se la versione precedente dell'applicazione che ha lo stesso nome esiste ancora nel server SharePoint, si verificherà un errore che un pacchetto con lo stesso nome esiste già nel server SharePoint. È necessario rinominare il pacchetto con un nome univoco prima della pubblicazione.  
  
9. Scegliere la nuova applicazione in SharePoint, quindi, sulla barra multifunzione, il **aggiornamento** pulsante.  
  
10. Nel **aggiornare la soluzione** della finestra di dialogo della barra multifunzione scegliere la **aggiornamento** nuovamente clic sul pulsante. Il **stato** colonna il **raccolta soluzioni** pagina ora dovrebbe indicare che l'applicazione è attiva.  
  
     La versione precedente della soluzione è disattivata, la nuova versione della soluzione viene aggiornata con i dati gestiti dalla soluzione precedente e viene attivata la nuova soluzione in SharePoint.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: distribuire e pubblicare una soluzione di SharePoint in un sito di SharePoint locale](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [Creazione di pacchetti delle soluzioni SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Procedura: Aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  