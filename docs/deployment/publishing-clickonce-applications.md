---
title: Pubblicazione di applicazioni ClickOnce | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Options
- Microsoft.VisualStudio.Publish.ClickOnceProvider.PublishWizard.Help
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- ClickOnce applications, publishing
- applications [Visual Studio], ClickOnce deployment
- deploying applications [ClickOnce], publishing ClickOnce applications
ms.assetid: eb6dfe79-f54c-4331-8e36-073688e70973
caps.latest.revision: "22"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 02b5f2477a18f3432bc255b9bd17a2ac11fbc030
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="publishing-clickonce-applications"></a>Pubblicazione di applicazioni ClickOnce
Quando si pubblica un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per la prima volta, è possibile impostare le proprietà di pubblicazione con la pubblicazione guidata. Solo alcune delle proprietà sono disponibili nella procedura guidata; tutte le altre proprietà vengono impostate sui valori predefiniti.  
  
 Vengono apportate modifiche successive alle proprietà di pubblicazione sul **pubblica** nella pagina di **Progettazione progetti**.  
  
## <a name="publish-wizard"></a>Pubblicazione guidata  
 È possibile usare la pubblicazione guidata per configurare le impostazioni di base per la pubblicazione dell'applicazione. Ciò include le seguenti proprietà di pubblicazione:  
  
-   Posizione cartella di pubblicazione: percorso in cui Visual Studio copierà i file (computer locale, condivisione file di rete, server FTP o sito Web)  
  
-   Percorso cartella di installazione: percorso dal quale gli utenti finali eseguiranno l'installazione (condivisione file di rete, server FTP, sito Web, CD/DVD)  
  
-   Disponibilità in linea o non in line: se gli utenti finali possono accedere all'applicazione con o senza una connessione di rete  
  
-   Frequenza di aggiornamento: la frequenza con cui l'applicazione verifica la presenza di nuovi aggiornamenti.  
  
 Per ulteriori informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## <a name="publish-page"></a>Pagina Pubblica  
 La pagina **Pubblica** della **Creazione progetti** consente di configurare le proprietà relative alla distribuzione ClickOnce. Gli argomenti sono elencati nella tabella seguente.  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura: Specificare il percorso in cui vengono copiati i file in Visual Studio](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Viene descritto come impostare il percorso in cui Visual Studio inserisce i file di applicazione e i manifesti.|  
|[Procedura: Specificare il percorso da cui gli utenti finali eseguiranno l'installazione](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Viene descritto come impostare il percorso in cui gli utenti potranno scaricare e installare l'applicazione.|  
|[Procedura: Specificare la modalità di installazione online o offline di ClickOnce](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|Viene descritto come specificare se l'applicazione sarà disponibile online o offline.|  
|[Procedura: Impostare la versione pubblicazione per un'applicazione ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)|Viene descritto come impostare ClickOnce **versione pubblicazione** proprietà che determina se l'applicazione che si sta pubblicando verrà considerata un aggiornamento.|  
|[Procedura: Incrementare automaticamente il numero di versione pubblicazione dell'applicazione ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Viene descritto come incrementare automaticamente il numero di revisione di **PublishVersion** ogni volta che si pubblica l'applicazione.|  
  
 Per ulteriori informazioni, vedere [pagina pubblica, Progettazione progetti](../ide/reference/publish-page-project-designer.md)  
  
### <a name="application-files-dialog-box"></a>Finestra di dialogo File applicazione  
 Questa finestra di dialogo consente di specificare come sono suddivisi in categorie i file del progetto per la pubblicazione, il download dinamico e l'aggiornamento. Contiene una griglia in cui sono elencati i file di progetto non esclusi per impostazione predefinita, o che hanno un gruppo di download.  
  
 Per escludere i file, contrassegnare come file di dati o i prerequisiti, i file e creare gruppi di file per l'installazione condizionale nell'interfaccia utente Visual Studio, vedere [procedura: specificare che i file da pubblicare mediante ClickOnce](../deployment/how-to-specify-which-files-are-published-by-clickonce.md). È anche possibile contrassegnare i file di dati con il file Mage.exe. Per altre informazioni, vedere [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
### <a name="prerequisites-dialog-box"></a>Prerequisiti (finestra di dialogo)  
 Questa finestra di dialogo consente di specificare quali componenti prerequisiti sono installati, nonché le relative modalità di installazione. Per ulteriori informazioni, vedere [procedura: installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) e [la finestra di dialogo Prerequisiti](../ide/reference/prerequisites-dialog-box.md).  
  
### <a name="application-updates-dialog-box"></a>Finestra di dialogo Aggiornamenti applicazione  
 Questa finestra di dialogo consente di specificare in che modo l'installazione dell'applicazione deve controllare gli aggiornamenti. Per ulteriori informazioni, vedere [procedura: gestire gli aggiornamenti per un'applicazione ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md).  
  
### <a name="publish-options-dialog-box"></a>Finestra di dialogo Opzioni di pubblicazione  
 La finestra di dialogo Opzioni di pubblicazione consente di specificare le opzioni di distribuzione di un'applicazione.  
  
|||  
|-|-|  
|[Procedura: Cambiare la lingua di pubblicazione di un'applicazione ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Viene descritto come specificare le impostazioni della lingua corrispondente alla versione localizzata.|  
|[Procedura: Specificare il nome di un'applicazione ClickOnce per il menu Start](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|Viene descritto come modificare il nome visualizzato per un'applicazione ClickOnce.|  
|[Procedura: Specificare un collegamento per il supporto tecnico](../deployment/how-to-specify-a-link-for-technical-support.md)|Viene descritto come impostare il **URL di supporto** proprietà che identifica una pagina Web o una condivisione file in cui gli utenti possono accedere per ottenere informazioni sull'applicazione.|  
|[Procedura: Specificare un URL di supporto per i singoli prerequisiti in una distribuzione ClickOnce](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|È stato illustrato come modificare manualmente un manifesto dell'applicazione in modo da includere singoli URL di supporto per ogni prerequisito.|  
|[Procedura: Specificare una pagina di pubblicazione per un'applicazione ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|Viene descritto come generare e pubblicare una pagina di Web predefinita (publish.htm) insieme all'applicazione|  
|[Procedura: personalizzare la pagina Web predefinita ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Viene descritto come personalizzare la pagina Web che viene automaticamente generata e pubblicata insieme all'applicazione.|  
|[Procedura: Attivare l'avvio automatico per le installazioni da CD](../deployment/how-to-enable-autostart-for-cd-installations.md)|Viene descritto come attivare AutoStart per avviare automaticamente l'applicazione ClickOnce dopo l'inserimento del supporto.|  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura: Creare associazioni di file per un'applicazione ClickOnce](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|Viene descritto come aggiungere il supporto delle estensioni di file a un'applicazione ClickOnce.|  
|[Procedura: Recuperare informazioni sulle stringhe di query in un'applicazione ClickOnce online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|Viene illustrato come recuperare i parametri passati nell'URL usato per eseguire un'applicazione ClickOnce.|  
|[Procedura: Disabilitare gli URL di applicazioni ClickOnce tramite la finestra di progettazione](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Viene descritto come forzare l'avvio dell'applicazione dal **avviare** menu utilizzando la finestra di progettazione.|  
|[Procedura: Disabilitare l'attivazione dell'URL delle applicazioni ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Viene descritto come forzare l'avvio dell'applicazione dal **avviare** menu.|  
|[Procedura dettagliata: download di assembly su richiesta con l'API della distribuzione ClickOnce tramite la finestra di progettazione](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Viene spiegato come scaricare gli assembly dell'applicazione solo quando vengono innanzitutto usati dall'applicazione con la finestra di progettazione.|  
|[Procedura dettagliata: download di assembly su richiesta con l'API della distribuzione ClickOnce](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Viene spiegato come scaricare gli assembly dell'applicazione solo quando vengono innanzitutto usati dall'applicazione.|  
|[Procedura dettagliata: download di assembly satellite su richiesta con l'API della distribuzione ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Viene descritto come contrassegnare gli assembly satellite come facoltativi e scaricare solo l'assembly di cui un computer client ha bisogno per le impostazioni cultura correnti.|  
|[Procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|Viene illustrato come usare le utilità di.NET Framework per distribuire l'applicazione ClickOnce.|  
|[Procedura dettagliata: distribuzione manuale di una applicazione ClickOnce che non richiede una nuova firma e mantiene le informazioni di personalizzazione](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)|Viene illustrato come usare le utilità di.NET Framework per distribuire l'applicazione ClickOnce senza firmare nuovamente i manifesti.|  
|[Procedura: Configurare progetti per le piattaforme di destinazione](../ide/how-to-configure-projects-to-target-platforms.md)|Viene illustrato come pubblicare per un processore a 64 bit modificando la **CPU destinazione** o **piattaforma di destinazione** proprietà del progetto.|  
|[Procedura dettagliata: Abilitazione di un'applicazione ClickOnce per l'esecuzione in più versioni di .NET Framework](http://msdn.microsoft.com/en-us/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|Viene spiegato come abilitare l'installazione e l'esecuzione di un'applicazione ClickOnce in più versioni di .NET Framework.|  
|[Procedura dettagliata: creazione di un programma di installazione personalizzato per un'applicazione ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|Viene spiegato come creare un programma di installazione personalizzato per installare un'applicazione ClickOnce.|  
|[Procedura: Pubblicare un'applicazione WPF per la quale sono attivati gli stili di visualizzazione](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Vengono fornite istruzioni dettagliate per risolvere un errore che viene visualizzato quando si tenta di pubblicare un'applicazione WPF con gli stili visuali abilitati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Riferimenti di ClickOnce](../deployment/clickonce-reference.md)