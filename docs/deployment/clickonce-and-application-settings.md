---
title: Impostazioni applicazione e ClickOnce | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e325ed1d66729eaed18c577c27f09a3db45d98f6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="clickonce-and-application-settings"></a>Impostazioni dell'applicazione e ClickOnce
Le impostazioni dell'applicazione per Windows Form semplifica creare, archiviare e gestire applicazioni personalizzate e le preferenze dell'utente nel client. Il documento seguente vengono descritti il funzionamento dei file di impostazioni in un'applicazione ClickOnce, e come ClickOnce viene eseguita la migrazione delle impostazioni quando l'utente effettua l'aggiornamento alla versione successiva.  
  
 Le informazioni seguenti si applicano solo ai provider di impostazioni dell'applicazione predefinito, la <xref:System.Configuration.LocalFileSettingsProvider> classe. Se si fornisce un provider personalizzato, tale provider determinerà come archivia i dati e le relative impostazioni tra le versioni di aggiornamento. Per ulteriori informazioni sui provider di impostazioni dell'applicazione, vedere [architettura Impostazioni applicazione](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="application-settings-files"></a>File di impostazioni applicazione  
 Le impostazioni dell'applicazione vengono utilizzati due file: *app*. exe. config e User. config, dove *app* è il nome dell'applicazione Windows Form. User. config viene creato nel client la prima volta che l'applicazione archivia le impostazioni con ambito di utente. *app*. exe. config, al contrario, sarà presente prima della distribuzione se si definiscono i valori predefiniti per le impostazioni. Visual Studio includerà automaticamente questo file quando si utilizza il **pubblica** comando. Se si crea un'applicazione ClickOnce mediante Mage.exe o MageUI.exe, è necessario assicurarsi che questo file è incluso con l'applicazione di altri file quando si popola il manifesto dell'applicazione.  
  
 Nelle applicazioni Windows Form non distribuita tramite ClickOnce, un'applicazione *app*. exe. config viene archiviato nella directory dell'applicazione, mentre l'utente è archiviato il file di User. config **Documents and Settings**  cartella. In un'applicazione ClickOnce, *app*. exe. config si trova nella directory dell'applicazione all'interno della cache di ClickOnce, mentre User. config si trova nella directory di dati di ClickOnce per l'applicazione.  
  
 Indipendentemente dalla modalità di distribuzione dell'applicazione, le impostazioni dell'applicazione garantiscono un accesso di lettura per *app*. exe. config e l'accesso sicuro di lettura/scrittura a User. config.  
  
 In un'applicazione ClickOnce, le dimensioni dei file di configurazione utilizzato dalle impostazioni dell'applicazione sono vincolata dalla dimensione della cache di ClickOnce. Per ulteriori informazioni, vedere [Cenni preliminari sulla Cache di ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Aggiornamenti di versione  
 Come ogni versione di un'applicazione ClickOnce è isolata da tutte le altre versioni, le impostazioni dell'applicazione per un'applicazione ClickOnce sono isolate dalle impostazioni per anche le altre versioni. Quando l'utente viene aggiornato a una versione successiva dell'applicazione, le impostazioni dell'applicazione confronta impostazioni più recenti (numero più alto) della versione con quelle fornite con la versione aggiornata e unisce le impostazioni in un nuovo set di file di impostazioni.  
  
 La tabella seguente descrive come le impostazioni dell'applicazione decide le impostazioni da copiare.  
  
|Tipo di modifica|Azione di aggiornamento|  
|--------------------|--------------------|  
|Impostazione aggiunta a *app*. exe. config|La nuova impostazione viene unita nella versione corrente *app*. exe. config|  
|Impostazione rimossa da *app*. exe. config|L'impostazione precedente viene rimossa dalla versione corrente *app*. exe. config|  
|Valore predefinito dell'impostazione modificato. impostazioni locali è ancora impostata sul valore predefinito originale in User. config|L'impostazione viene unita User. config con il nuovo valore predefinito della versione corrente come valore|  
|Valore predefinito dell'impostazione modificato. impostazione non predefinita in User. config|L'impostazione viene unita di User. config della versione corrente con il valore non predefinito mantenuto|  
  
 Se si hanno creato le proprie impostazioni applicazione classe wrapper e si desidera personalizzare la logica di aggiornamento, è possibile eseguire l'override di <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> metodo.  
  
## <a name="clickonce-and-roaming-settings"></a>Impostazioni di Roaming e ClickOnce  
 ClickOnce non funziona con le impostazioni di roaming, che consente il file di impostazioni è tra più computer in una rete. Se è necessario che le impostazioni di roaming, è necessario implementare un provider di impostazioni dell'applicazione che archivia le impostazioni di rete o sviluppare le proprie classi di impostazioni personalizzate per la memorizzazione delle impostazioni in un computer remoto. Per ulteriori informazioni sui provider di impostazioni, vedere [architettura Impostazioni applicazione](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Cenni preliminari sulle impostazioni delle applicazioni](/dotnet/framework/winforms/advanced/application-settings-overview)   
 [Informazioni generali sulla Cache di ClickOnce](../deployment/clickonce-cache-overview.md)   
 [Accesso a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)