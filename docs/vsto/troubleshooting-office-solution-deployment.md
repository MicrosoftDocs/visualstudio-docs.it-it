---
title: Risoluzione dei problemi di distribuzione di soluzioni Office | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 29c3cfdcf31609eb5b6aec0111fe2297ba8c01ef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-office-solution-deployment"></a>Risoluzione dei problemi relativi alla distribuzione di soluzioni Office
  Questo argomento contiene informazioni su come risolvere i problemi comuni che possono verificarsi durante la distribuzione di soluzioni Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="troubleshooting-office-solutions-by-using-the-event-viewer"></a>Risoluzione dei problemi relativi alle soluzioni Office mediante il Visualizzatore eventi  
 È possibile usare il Visualizzatore eventi di Windows per visualizzare i messaggi di errore acquisiti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] quando si installano o disinstallano soluzioni Office. Questi messaggi del registratore eventi possono essere usati per risolvere i problemi di installazione e di distribuzione. Per altre informazioni, vedere [Event Logging for Office Solutions](../vsto/event-logging-for-office-solutions.md).  
  
## <a name="changing-the-assembly-name-causes-conflicts"></a>La modifica del nome dell'assembly causa conflitti  
 Se si modifica il **nome Assembly** valore il **applicazione** pagina del **Progettazione progetti** dopo aver già distribuito una soluzione, gli strumenti di pubblicazione modificheranno il Pacchetto di installazione di un file Setup.exe e due manifesti di distribuzione. Se si distribuiscono due file manifesto, potrebbero verificarsi le condizioni seguenti:  
  
-   Se l'utente finale installa entrambe le versioni, l'applicazione caricherà entrambi i componenti aggiuntivi VSTO.  
  
-   Se il componente aggiuntivo VSTO è stato installato prima della modifica del nome dell'assembly, l'utente finale non riceverà mai aggiornamenti.  
  
 Per evitare queste situazioni, non modificare la soluzione **nome Assembly** valore dopo aver distribuito la soluzione.  
  
## <a name="checking-for-updates-takes-a-long-time"></a>Il controllo della disponibilità di aggiornamenti richiede molto tempo  
 Visual Studio 2010 Tools per Office Runtime fornisce una voce del Registro di sistema che gli amministratori possono usare per impostare il valore di timeout per il download dei manifesti e della soluzione.  
  
#### <a name="to-set-the-time-out-value"></a>Per impostare il valore di timeout  
  
1.  Nel Registro di sistema passare alla chiave seguente:  
  
     HKEY_CURRENT_USER\Software\Microsoft\VSTA  
  
2.  Nella sottochiave **AddInTimeout** impostare il valore di timeout in millisecondi.  
  
     Se la sottochiave **AddInTimeout** non esiste, crearla come DWORD.  
  
## <a name="cant-update-or-publish-to-a-network-file-share"></a>Non è possibile aggiornare o pubblicare in una condivisione file di rete  
 Le soluzioni Office che si trovano in una condivisione file di rete potrebbero visualizzare un messaggio fuorviante durante gli aggiornamenti se il file Setup.exe della soluzione è bloccato in un processo durante la pubblicazione dell'aggiornamento. Il messaggio può essere analogo al seguente: "Impossibile aggiungere 'setup.exe' al sito Web. Il file 'setup.exe' esiste già nel sito Web".  
  
 Per evitare il blocco del file, si può impostare la condivisione come di sola lettura per gli utenti finali. Se però nella condivisione sono presenti documenti, anche questi diventeranno di sola lettura per gli utenti finali.  
  
## <a name="prerequisites-for-microsoft-office-arent-installed"></a>I prerequisiti per Microsoft Office non sono installati  
 È possibile aggiungere .NET Framework, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]e gli assembly di interoperabilità primari di Microsoft Office al pacchetto di installazione come prerequisiti distribuiti con la soluzione Office. Per informazioni su come installare gli assembly di interoperabilità primari, vedere [configurazione di un Computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) e [procedura: installare assembly di interoperabilità primari di Office](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
## <a name="publishing-using-localhost-can-cause-installation-problems"></a>La pubblicazione mediante 'Localhost' può causare problemi di installazione  
 Quando si utilizza "http://localhost" come percorso di pubblicazione o di installazione per le soluzioni a livello di documento, il **pubblicazione guidata** non converte la stringa per il nome effettivo del computer. In questo caso, è necessario installare la soluzione nel computer di sviluppo. Per fare in modo che le soluzioni distribuite usino IIS nel computer di sviluppo, usare il nome completo per tutti i percorsi HTTP/HTTPS/FTP anziché localhost.  
  
## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Vengono caricati gli assembly memorizzati nella cache anziché gli assembly aggiornati  
 Fusion, il caricatore di assembly di .NET Framework, carica la copia degli assembly memorizzata nella cache quando il percorso di output del progetto è in una condivisione file di rete, l'assembly è firmato con un nome sicuro e la versione dell'assembly della personalizzazione non cambia. Se si aggiorna un assembly che soddisfa queste condizioni, l'aggiornamento non verrà visualizzato la volta successiva che si esegue il progetto perché viene caricata la copia memorizzata nella cache.  
  
 È possibile configurare Visual Studio in modo che Fusion scarichi gli assembly ogni volta che si esegue il progetto.  
  
#### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Per scaricare gli assembly anziché caricare le copie memorizzate nella cache  
  
1.  Nella barra dei menu, scegliere **Project**, * ProjectName ***proprietà**.  
  
2.  Nella pagina **Applicazione** scegliere **Informazioni assembly**.  
  
3.  Nel primo **versione dell'Assembly** , immettere un asterisco (\*), quindi scegliere il **OK** pulsante.  
  
 Dopo aver modificato la versione dell'assembly, è possibile continuare a firmare l'assembly con nome sicuro e Fusion caricherà la versione più recente della personalizzazione.  
  
## <a name="installation-fails-when-the-uri-has-characters-that-aret-us-ascii"></a>L'installazione non riesce se l'URI contiene caratteri non US-ASCII  
 Quando si pubblica una soluzione Office in un percorso HTTP/HTTPS/FTP, il percorso non può contenere caratteri Unicode non US-ASCII. Questi caratteri possono causare un comportamento incoerente nel programma di installazione. Usare caratteri US-ASCII per il percorso di installazione.  
  
## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Viene visualizzata una richiesta di disinstallazione manuale quando si pubblica e si installa una soluzione nel computer di sviluppo  
 Quando si compila una soluzione Office, la versione compilata viene registrata automaticamente. Se la stessa soluzione è stata precedentemente pubblicata e installata nel computer di sviluppo, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rileva che i percorsi di installazione per la versione pubblicata e la versione compilata sono diversi dopo la successiva compilazione, ricompilazione o pubblicazione della soluzione. Il messaggio di errore è: "Impossibile installare la personalizzazione perché ne è installata un'altra versione che non può essere aggiornata da questo percorso". Le chiavi del Registro di sistema vengono aggiornate ogni volta che una soluzione viene ricompilata. Pertanto, prima della pubblicazione, del debug o dell'esecuzione della nuova versione, occorre disinstallare la versione precedente.  
  
 Per evitare la comparsa del messaggio, creare un altro account utente nel computer di sviluppo per testare la distribuzione. In alternativa, si può disinstallare la versione dall'elenco dei programmi installati nel computer prima di procedere alla pubblicazione, al debug o alla ricompilazione della soluzione.  
  
## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Errore relativo a un'eccezione non rilevata o un metodo non trovato durante l'installazione di una soluzione  
 Quando si installano soluzioni Office aprendo il manifesto della distribuzione (file con estensione vsto), l'applicazione di Office, il documento o la cartella di lavoro, è possibile che vengano visualizzati messaggi di errore per le condizioni seguenti:  
  
-   Impossibile trovare il metodo.  
  
-   MissingMethodException.  
  
-   Eccezione non rilevata.  
  
 Per evitare questi messaggi di errore, installare la soluzione eseguendo il programma di installazione.  
  
 Quando si installa la soluzione senza eseguire il programma di installazione, non vengono cercati o installati i prerequisiti. Il programma di installazione verifica la versione corretta dei prerequisiti e li installa, se necessario.  
  
## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Le chiavi del Registro di sistema del manifesto per i componenti aggiuntivi cambiano dopo la compilazione di un progetto InstallShield Limited Edition  
 La chiave del Registro di sistema del manifesto che fa parte del programma di installazione di un componente aggiuntivo VSTO talvolta cambia da .vsto a .dll.manifest quando si compila un progetto InstallShield Limited Edition.  
  
 Per risolvere questo problema, creare il progetto InstallShield Limited Edition in una soluzione diversa oppure usare CompanyName.AddinName come valore della chiave del Registro di sistema che contiene il nome del componente aggiuntivo VSTO.  
  
## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Il programma di installazione ClickOnce per la soluzione Office non installa gli assembly di interoperabilità primari  
 Quando si esegue il programma di installazione creato da ClickOnce per la soluzione Office, il programma di installazione per gli assembly di interoperabilità primari di Office viene eseguito solo se non sono già installati assembly di interoperabilità primari.  
  
 Se gli assembly di interoperabilità primari non vengono installati correttamente, installarli manualmente eseguendo il file del programma di installazione denominato o2007pia.msi dalla directory di installazione.  
  
## <a name="reinstalling-office-solutions-causes-an-argument-out-of-range-exception"></a>La reinstallazione delle soluzioni Office genera un'eccezione di tipo argomento non compreso nell'intervallo  
 Quando si reinstalla una soluzione Office, è possibile che venga visualizzata un'eccezione <xref:System.ArgumentOutOfRangeException> con il messaggio di errore seguente: Argomento specificato non compreso nell'intervallo.  
  
 Questa situazione si verifica se la combinazione di maiuscole e minuscole per l'URL del percorso di installazione è diversa. Ad esempio, questo errore può essere visualizzato se è stata installata una soluzione Office da [ http://fabrikam.com/ExcelSolution.vsto ](http://fabrikam.com/ExcelSolution.vsto) la prima volta e quindi utilizzato [ http://fabrikam.com/excelsolution.vsto ](http://fabrikam.com/excelsolution.vsto) la seconda volta.  
  
 Per evitare che venga visualizzato il messaggio, usare la stessa combinazione di maiuscole e minuscole quando si installano soluzioni Office.  
  
## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Non è possibile installare una soluzione ClickOnce aprendo il manifesto della distribuzione dal Web  
 Gli utenti possono installare soluzioni Office aprendo il manifesto della distribuzione dal Web. Alcune installazioni di Internet Information Services (IIS), tuttavia, bloccano l'estensione vsto. È necessario definire il tipo MIME in IIS prima di usarlo per distribuire una soluzione Office.  
  
 Per informazioni su come definire il tipo MIME in IIS 6, vedere l'articolo relativo alla [configurazione dei tipi MIME in IIS 6.0](http://www.microsoft.com/technet/prodtechnol/WindowsServer2003/Library/IIS/cd72c0dc-c5b8-42e4-96c2-b3c656f99ead.mspx?mfr=true).  
  
 Per informazioni su come definire il tipo MIME in IIS 7, vedere [Aggiungere un tipo MIME (IIS 7)](http://technet.microsoft.com/library/cc725608(WS.10).aspx).  
  
 Impostare l'estensione **.vsto** e il tipo MIME su **application/x-ms-vsto**.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi delle distribuzioni ClickOnce](/visualstudio/deployment/troubleshooting-clickonce-deployments)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
  