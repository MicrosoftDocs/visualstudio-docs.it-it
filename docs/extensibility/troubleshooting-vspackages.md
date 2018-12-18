---
title: Risoluzione dei problemi di VSPackage | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73c754de72238671dd10235e792c43fb6d0a1b5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-vspackages"></a>Risoluzione dei problemi di VSPackage
Di seguito sono problemi comuni che potrebbero aver con il pacchetto VSPackage e suggerimenti per risolvere i problemi.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Per risolvere i problemi di un VSPackage che impedisce l'avvio di Visual Studio  
  
-   Avviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in modalità provvisoria.  
  
     Per avviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in modalità provvisoria, al prompt dei comandi, digitare **devenv.exe /safemode**.  
  
     Durante questo processo non VSPackage sono caricati, ad eccezione di VSPackage inclusi in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Per risolvere i problemi di un VSPackage che non viene caricato  
  
1.  Assicurarsi che si sta utilizzando la radice del Registro di sistema in cui il pacchetto VSPackage è registrato per l'esecuzione, in genere la radice del Registro di sistema sperimentale.  
  
     Per ulteriori informazioni, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
2.  Se il pacchetto VSPackage è la destinazione per l'esecuzione nella radice del Registro di sistema sperimentale, assicurarsi che si esegue la versione sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Per eseguire la versione sperimentale, digitare quanto segue nella finestra di comando: **devenv /rootsuffix exp**.  
  
3.  Controllare le voci del Registro di sistema di VSPackage.  
  
     Per ulteriori informazioni, vedere [registrazione VSPackage](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd) e [gestione VSPackage](../extensibility/managing-vspackages.md).  
  
4.  Aprire il **Output** finestra dell'istanza di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che non riesce a caricare il pacchetto VSPackage. Informazioni sui motivi caricare il pacchetto VSPackage verrà visualizzate nella finestra.  
  
    > [!NOTE]
    >  Se si sta avviando la versione sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE), controllare il **Output** finestra di entrambe le versioni.  
  
5.  Esaminare il registro attività.  
  
     Per ulteriori informazioni, vedere [procedura: utilizzare il registro attività](../extensibility/how-to-use-the-activity-log.md).  
  
6.  Per ulteriori informazioni sulle eccezioni generate dall'IDE, fare clic su **eccezioni** sul **Debug** menu per abilitare le eccezioni. Nel **eccezioni** la finestra di dialogo selezionare i tipi di eccezioni su cui si desiderano ulteriori informazioni.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Per risolvere i problemi di un VSPackage che non consente di registrare  
  
1.  Assicurarsi che l'assembly VSPackage si trova in una posizione attendibile. RegPkg non è possibile registrare gli assembly in una posizione non attendibile o parzialmente attendibile, ad esempio una condivisione di rete nella configurazione predefinita di sicurezza di .net. Anche se viene visualizzato un avviso ogni volta che un utente crea un progetto in un percorso non attendibile, la casella di controllo "non visualizzare più questo messaggio" può impedire l'avviso verifichi.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Per risolvere i problemi di un comando che non è visibile o che genera un errore quando si sceglie un comando  
  
1.  Unire i comandi di menu nuovi o modificati e quelli già nell'IDE digitando il comando seguente al [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prompt dei comandi: **/rootsuffix devenv /setup Exp**.  
  
2.  Assicurarsi che [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] reperibile UI.dll per il pacchetto VSPackage.  
  
    1.  Trovare il CLSID del pacchetto VSPackage nella sezione pacchetti del Registro di sistema:  
  
         Studio HKLM\Software\Microsoft\Visual\\*\<versione >*\Packages  
  
    2.  Verificare che il percorso specificato per la sottochiave SatelliteDll sia corretto.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Per risolvere i problemi di un VSPackage che si comporta in modo imprevisto  
  
1.  Impostare i punti di interruzione nel codice.  
  
     Punti di partenza ottimali per il debug sono il costruttore e il metodo di inizializzazione. È inoltre possibile impostare i punti di interruzione nell'area di cui che si desidera valutare, ad esempio un comando di menu. Per abilitare i punti di interruzione, è necessario eseguire il debugger.  
  
    1.  Scegliere **Proprietà** dal menu **Progetto**.  
  
    2.  Nel **pagine delle proprietà** la finestra di dialogo, seleziona il **Debug** scheda.  
  
    3.  Nel **argomenti della riga di comando** , digitare il suffisso della radice dell'ambiente di sviluppo che il pacchetto VSPackage è destinato. Ad esempio, per selezionare la build sperimentale, digitare: **RootSuffix Exp**.  
  
    4.  Nel **Debug** menu, fare clic su **Avvia debug** o premere F5.  
  
        > [!NOTE]
        >  Se si esegue il debug di un progetto, creare o caricare un'istanza esistente del progetto ora.  
  
2.  Utilizzare il registro attività.  
  
     Traccia VSPackage comportamento scrivendo informazioni nel log di attività in punti chiavi. Questa tecnica è particolarmente utile quando si esegue un pacchetto VSPackage in un ambiente di vendita al dettaglio. Per ulteriori informazioni, vedere [procedura: utilizzare il registro attività](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Utilizzare i simboli pubblici.  
  
     Per migliorare la leggibilità durante il debug, è possibile collegare i simboli del debugger.  
  
    1.  Dal **Strumenti/opzioni** menu, passare al **debug/simboli** la finestra di dialogo.  
  
    2.  Aggiungere questo **simboli (PDB) percorso**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Per migliorare le prestazioni, specificare una cartella della cache di simboli, ad esempio:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Per risolvere i problemi relativi a un VSPackage mancano o una delle relative dipendenze  
  
1.  Per codice gestito, assicurarsi che i percorsi di riferimento siano corretti.  
  
    1.  Scegliere **Proprietà** dal menu **Progetto**.  
  
    2.  Selezionare il **riferimenti** nella scheda il **pagine delle proprietà** la finestra di dialogo e assicurarsi che tutti i percorsi siano corretti. In alternativa, è possibile utilizzare il **Visualizzatore oggetti** per cercare gli oggetti di riferimento.  
  
         Per codice gestito, è possibile utilizzare il [Fuslogvw.exe (Visualizzatore Log associazione Assembly)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) per visualizzare i dettagli di caricamenti di assembly non riuscita.  
  
2.  Per codice non gestito, trovare il CLSID di VSPackage nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nodo del Registro di sistema CLSID:  
  
     Studio HKLM\Software\Microsoft\Visual\\*\<versione >*\CLSID  
  
 Assicurarsi che la voce InprocServer32 è il percorso corretto della dll VSPackage.  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)