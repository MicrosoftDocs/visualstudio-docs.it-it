---
title: Scelta di una strategia di aggiornamento ClickOnce | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0013b9f7ae004b709a1651af0e32e36dd45f909c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="choosing-a-clickonce-update-strategy"></a>Scelta di una strategia di aggiornamento ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] può fornire il supporto per gli aggiornamenti automatici delle applicazioni. Oggetto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] legge periodicamente il file manifesto di distribuzione per vedere se sono disponibili aggiornamenti per l'applicazione. In caso affermativo, la nuova versione dell'applicazione viene scaricata ed eseguita. Per maggiore efficienza, vengono scaricati solo i file che risultano modificati.  
  
 Quando si progetta un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], è necessario determinare la strategia da adottare per controllare la disponibilità di aggiornamenti. È possibile utilizzare tre strategie di base: l'impostazione del controllo della disponibilità di aggiornamenti all'avvio dell'applicazione, l'impostazione del controllo dopo l'avvio dell'applicazione (esecuzione in un thread in background) o la creazione di una specifica interfaccia utente per gli aggiornamenti.  
  
 È inoltre possibile determinare la frequenza con cui verrà eseguito il controllo, nonché contrassegnare gli aggiornamenti come obbligatori.  
  
> [!NOTE]
>  Per gli aggiornamenti dell'applicazione è necessario disporre della connettività di rete. In assenza di una connessione di rete, l'applicazione verrà eseguita senza il controllo della disponibilità di aggiornamenti, indipendentemente dalla strategia di aggiornamento prescelta.  
  
> [!NOTE]
>  In .NET Framework 2.0 e .NET Framework 3.0, qualunque sia la strategia di aggiornamento adottata, prima dell'avvio, dopo l'avvio o mediante le API di <xref:System.Deployment.Application>, è necessario impostare `deploymentProvider` nel manifesto di distribuzione. Il `deploymentProvider` elemento corrispondente in Visual Studio per il **percorso di aggiornamento** nel campo di **aggiornamenti** la finestra di dialogo del **pubblica** scheda. Tale regola è relaxed in .NET Framework 3.5. Per ulteriori informazioni, vedere [la distribuzione di applicazioni ClickOnce per test e i server di produzione senza Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
## <a name="checking-for-updates-after-application-startup"></a>Controllo della disponibilità di aggiornamenti dopo l'avvio dell'applicazione  
 Se si utilizza questa strategia, l'applicazione tenterà di individuare e leggere il file manifesto di distribuzione in background, mentre è in esecuzione. Se è disponibile un aggiornamento, la volta successiva che l'utente eseguirà l'applicazione verrà chiesto di scaricarlo e installarlo.  
  
 Questa strategia risulta più adatta a connessioni di rete con larghezza di banda limitata o ad applicazioni di maggiori dimensioni che possono richiedere lunghi tempi di download.  
  
 Per attivare questa strategia di aggiornamento, fare clic su **dopo l'avvio dell'applicazione** nel **scegliere quando controllare la disponibilità di aggiornamenti** sezione la **gli aggiornamenti dell'applicazione** la finestra di dialogo. Quindi specificare un intervallo di aggiornamento nella sezione **specificare la frequenza con cui l'applicazione deve verificare gli aggiornamenti**.  
  
 Equivale a modificare il **aggiornamento** manifesto di elemento nella distribuzione come indicato di seguito:  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <expiration maximumAge="6" unit="hours" />  
   </update>  
</subscription>  
```  
  
## <a name="checking-for-updates-before-application-startup"></a>Controllo della disponibilità di aggiornamenti prima dell'avvio dell'applicazione  
 La strategia predefinita consiste nel tentare di individuare e leggere il file manifesto di distribuzione prima dell'avvio dell'applicazione. Se si utilizza questa strategia, l'applicazione tenterà di individuare e leggere il file manifesto di distribuzione ogni volta che verrà avviata. Se è disponibile un aggiornamento, questo verrà scaricato e avviato. In caso contrario, verrà avviata la versione esistente dell'applicazione.  
  
 Questa strategia risulta più adatta a connessioni di rete con larghezza di banda più ampia. Il ritardo nell'avvio dell'applicazione potrebbe essere eccessivamente lungo nel caso di connessioni con larghezza di banda limitata.  
  
 Per attivare questa strategia di aggiornamento, fare clic su **prima dell'avvio dell'applicazione** nel **scegliere quando controllare la disponibilità di aggiornamenti** sezione la **gli aggiornamenti dell'applicazione** la finestra di dialogo.  
  
 Equivale a modificare il **aggiornamento** manifesto di elemento nella distribuzione come indicato di seguito:  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <beforeApplicationStartup />  
   </update>  
</subscription>  
```  
  
## <a name="making-updates-required"></a>Impostazione degli aggiornamenti come obbligatori  
 In alcuni casi può essere necessario richiedere agli utenti di eseguire una versione aggiornata dell'applicazione. È ad esempio possibile che sia stata apportata una modifica a una risorsa esterna, quale un servizio Web, che impedisce il corretto funzionamento dell'applicazione. In tal caso, può essere opportuno contrassegnare l'aggiornamento come obbligatorio e impedire che gli utenti eseguano la versione precedente.  
  
> [!NOTE]
>  Anche se è possibile richiedere aggiornamenti mediante altre strategie, la selezione **prima dell'avvio dell'applicazione** è l'unico modo per garantire che non venga eseguita una versione precedente. Se all'avvio viene rilevato l'aggiornamento obbligatorio, è necessario accettare l'aggiornamento o chiudere l'applicazione.  
  
 Per contrassegnare un aggiornamento come obbligatorio, fare clic su **specificare una versione minima richiesta per questa applicazione** nel **aggiornamenti dell'applicazione** finestra di dialogo e quindi specificare la versione di pubblicazione (**principale**, **Secondaria**, **compilare**, **revisione**), che specifica il numero minimo di versione dell'applicazione che può essere installato.  
  
 Questa è la stessa impostazione di **minimumRequiredVersion** attributo del **distribuzione** elemento nel manifesto di distribuzione; ad esempio:  
  
```  
<deployment install="true" minimumRequiredVersion="1.0.0.0">  
```  
  
## <a name="specifying-update-intervals"></a>Impostazione degli intervalli di aggiornamento  
 È possibile specificare anche la frequenza con cui dovrà essere effettuato il controllo della disponibilità di aggiornamenti, A tale scopo, specificare che il controllo della disponibilità degli aggiornamenti deve essere eseguito dall'applicazione dopo l'avvio come descritto in "Controllo della disponibilità di aggiornamenti dopo l'avvio dell'applicazione", precedentemente in questo argomento.  
  
 Per specificare l'intervallo di aggiornamento, impostare il **specificare la frequenza con cui l'applicazione deve verificare gli aggiornamenti** le proprietà di **gli aggiornamenti dell'applicazione** la finestra di dialogo.  
  
 Questa è la stessa impostazione di **maximumAge** e **unità** gli attributi del **aggiornamento** elemento nel manifesto di distribuzione.  
  
 Ad esempio è possibile ripetere l'operazione ogni volta che viene eseguita l'applicazione, una volta alla settimana o una volta al mese. Se nel momento specificato non è disponibile una connessione di rete, la disponibilità di aggiornamenti verrà controllata alla successiva esecuzione dell'applicazione.  
  
## <a name="providing-a-user-interface-for-updates"></a>Creazione di un'interfaccia utente per gli aggiornamenti  
 Quando utilizza questa strategia, lo sviluppatore dell'applicazione fornisce un'interfaccia che consente all'utente di scegliere quando o con quale frequenza dovrà essere effettuato il controllo della disponibilità di aggiornamenti. È ad esempio possibile rendere disponibile un comando "Controlla aggiornamenti adesso" o una finestra di dialogo "Impostazioni di aggiornamento" con opzioni per la selezione di diversi intervalli di aggiornamento. Il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione API forniscono un framework di programmazione la propria interfaccia utente di aggiornamento. Per altre informazioni, vedere lo spazio dei nomi <xref:System.Deployment.Application>.  
  
 Se per controllare la disponibilità di aggiornamenti l'applicazione utilizza le API distribuzione, si consiglia di bloccare questo controllo come descritto nella sezione successiva "Blocco del controllo della disponibilità di aggiornamenti".  
  
 Questa strategia risulta più adatta quando sono necessarie strategie di aggiornamento differenti per utenti differenti.  
  
## <a name="blocking-update-checking"></a>Blocco del controllo della disponibilità di aggiornamenti  
 È anche possibile impedire all'applicazione di effettuare il controllo della disponibilità di aggiornamenti. Questo può essere utile, ad esempio, quando si dispone di un'applicazione semplice che non verrà mai aggiornata, ma si desidera trarre vantaggio dalla semplicità di installazione offerta dalla distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Si consiglia di bloccare il controllo della disponibilità di aggiornamenti anche quando nell'applicazione vengono utilizzate API di distribuzione per l'esecuzione di aggiornamenti specifici. Per informazioni, vedere la sezione precedente "Creazione di un'interfaccia utente per gli aggiornamenti".  
  
 Per bloccare il controllo degli aggiornamenti, deselezionare il **controllare la disponibilità di aggiornamenti** casella di controllo nella finestra di dialogo Aggiornamenti applicazione.  
  
 Per bloccare questo controllo, è anche possibile rimuovere il tag `<Subscription>` dal manifesto di distribuzione.  
  
## <a name="permission-elevation-and-updates"></a>Elevazione delle autorizzazioni e aggiornamenti  
 Se in una nuova versione di un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è richiesto un livello di attendibilità più alto rispetto alla versione precedente, verrà chiesto da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se si desidera che all'applicazione venga concesso un livello di attendibilità più alto. Se non si accetta di concedere un livello di attendibilità più alto, l'aggiornamento non verrà installato. In [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verrà chiesto di installare nuovamente l'applicazione al successivo riavvio. Se non si accetta di concedere un livello di attendibilità più alto in questa fase e l'aggiornamento non è contrassegnato come obbligatorio, verrà eseguita la versione obsoleta dell'applicazione. Se tuttavia l'aggiornamento è obbligatorio, l'applicazione non verrà eseguita finché non si accetterà il livello di attendibilità più alto.  
  
 Se si utilizza la distribuzione di applicazioni attendibili, non verrà visualizzato alcun prompt relativo ai livelli di attendibilità. Per altre informazioni, vedere [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Deployment.Application>   
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Modo in cui ClickOnce esegue gli aggiornamenti dell'applicazione](../deployment/how-clickonce-performs-application-updates.md)   
 [Procedura: Gestire gli aggiornamenti per un'applicazione ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md)