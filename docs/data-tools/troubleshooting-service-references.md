---
title: Riferimenti al servizio di risoluzione dei problemi | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: b57547aa9a5fa3c036a534c85cb55bb1749a421b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-service-references"></a>Risoluzione dei problemi relativi ai riferimenti al servizio
In questo argomento vengono elencati i problemi che possono verificarsi quando si lavora con [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] o [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] fa riferimento [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="error-returning-data-from-a-service"></a>Errore di restituzione di dati da un servizio  
 Quando viene restituito un `DataSet` o `DataTable` da un servizio, è possibile ricevere un'eccezione "è stata superata la quota della dimensione massima dei messaggi in arrivo". Per impostazione predefinita, il `MaxReceivedMessageSize` di alcune associazioni è impostata su un valore relativamente basso per limitare l'esposizione agli attacchi di tipo denial of service. È possibile aumentare questo valore per evitare l'eccezione. Per altre informazioni, vedere <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.  
  
 Per correggere l'errore:  
  
1.  In **Esplora**, doppio clic sul file app. config per aprirlo.  
  
2.  Individuare il `MaxReceivedMessageSize` proprietà e impostarla su un valore maggiore.  
  
## <a name="cannot-find-a-service-in-my-solution"></a>Impossibile trovare un servizio nella soluzione  
 Quando si fa clic il **Discover** pulsante il **aggiungere riferimenti al servizio** la finestra di dialogo, uno o più progetti di libreria di servizi WCF nella soluzione non vengono visualizzati nell'elenco dei servizi. Ciò può verificarsi se una libreria di servizi è stato aggiunto alla soluzione, ma non è ancora stata compilata.  
  
 Per correggere l'errore:  
  
-   In **Esplora**, fare clic sul progetto libreria di servizi WCF e fare clic su **compilare**.  
  
## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Errore durante l'accesso di un servizio su un Desktop remoto  
 Quando un utente accede a un servizio WCF ospitato sul Web su una connessione desktop remoto e l'utente non dispone di autorizzazioni amministrative, viene utilizzata l'autenticazione NTLM. Se l'utente non dispone di autorizzazioni amministrative, l'utente potrebbe ricevere il messaggio di errore seguente: "la richiesta HTTP non è autorizzata con lo schema di autenticazione client 'Anonymous'. L'intestazione di autenticazione ricevuto dal server: 'NTLM' ".  
  
 Per correggere l'errore:  
  
1.  Nel progetto di sito Web, aprire il **proprietà** pagine.  
  
2.  Nel **opzioni di avvio** scheda, deseleziona il **l'autenticazione NTLM** casella di controllo.  
  
    > [!NOTE]
    >  È consigliabile disattivare l'autenticazione NTLM solo per i siti Web che contengono esclusivamente servizi WCF. Sicurezza per i servizi WCF è gestita tramite la configurazione nel file Web. config. In questo modo l'autenticazione NTLM non necessari.  
  
## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Livello di accesso per classi generate impostazione non ha alcun effetto  
 Impostazione di **livello di accesso per classi generate** opzione il **Configura riferimento a servizio** finestra di dialogo per **interno** o **Friend** potrebbe non funzionare. Anche se l'opzione viene visualizzata da impostare nella finestra di dialogo, verranno generate con un livello di accesso delle classi di supporto risultante `Public`.  
  
 Si tratta di una limitazione nota di determinati tipi, ad esempio quelli serializzati utilizzando il <xref:System.Xml.Serialization.XmlSerializer>.  
  
## <a name="error-debugging-service-code"></a>Codice di errore debug del servizio  
 Quando si esegue il codice per un servizio WCF dal codice client, si potrebbe ricevere un errore correlato ai simboli mancanti. Ciò può verificarsi quando un servizio che faceva parte della soluzione è stato spostato o rimosso dalla soluzione.  
  
 Quando si aggiunge un riferimento a un servizio WCF che fa parte della soluzione corrente, una dipendenza di compilazione esplicita viene aggiunto tra il progetto di servizio e il progetto client del servizio. Ciò garantisce che il client accede sempre file binari del servizio aggiornata, a cui è particolarmente importante per gli scenari, ad esempio l'esecuzione di istruzioni dal codice client del codice del servizio di debug.  
  
 Se il progetto di servizio viene rimosso dalla soluzione, viene invalidata la dipendenza di compilazione esplicita. Visual Studio non può più garantire che che viene ricompilato il progetto di servizio in base alle esigenze.  
  
 Per correggere l'errore, è necessario ricreare manualmente il progetto di servizio:  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nel **opzioni** finestra di dialogo espandere **progetti e soluzioni**, quindi selezionare **generale**.  
  
3.  Assicurarsi che il **avanzata Mostra configurazioni della build** casella di controllo è selezionata e quindi fare clic su **OK**.  
  
4.  Caricare il progetto di servizio WCF.  
  
5.  Nel **Configuration Manager** la finestra di dialogo, impostare il **configurazione soluzione attiva** a **Debug**. Per altre informazioni, vedere [How to: Create and Edit Configurations](../ide/how-to-create-and-edit-configurations.md) (Procedura: Creare e modificare le configurazioni).  
  
6.  In **Esplora**, selezionare il progetto di servizio WCF.  
  
7.  Nel **compilare** menu, fare clic su **ricompilare** per ricompilare il progetto di servizio WCF.  
  
## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services non è disponibile nel Browser  
 Quando si tenta di visualizzare una rappresentazione XML dei dati in un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], Internet Explorer che potrebbero essere erroneamente i dati come un feed RSS. È necessario assicurarsi che l'opzione per visualizzare feed RSS sia disabilitata.  
  
 Per correggere l'errore, disabilitare i feed RSS:  
  
1.  In Internet Explorer nel **strumenti** menu, fare clic su **Opzioni Internet**.  
  
2.  Nel **contenuto** nella scheda il **feed** fare clic su **impostazioni**.  
  
3.  Nel **impostazioni Feed** la finestra di dialogo, deseleziona il **attivare la visualizzazione di lettura feed** casella di controllo e quindi fare clic su **OK**.  
  
4.  Fare clic su **OK** per chiudere la **Opzioni Internet** la finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)