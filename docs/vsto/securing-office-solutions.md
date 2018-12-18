---
title: Sicurezza delle soluzioni Office | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a587534406d128655f9c24c9195902afb8e8817b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="securing-office-solutions"></a>Sicurezza delle soluzioni Office
  Il modello di sicurezza per le soluzioni Office comprende diverse tecnologie: il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)], il Centro protezione di Microsoft Office e l'area siti con restrizioni di Internet Explorer. Le sezioni seguenti descrivono il funzionamento delle diverse funzionalità di sicurezza:  
  
-   [Concessione dell'attendibilità alle soluzioni Office](#GrantingTrustToSolutions)  
  
-   [Concessione dell'attendibilità ai documenti](#GrantingTrustToDocuments)  
  
-   [Concessione dell'attendibilità quando si usa Windows Installer](#GrantingTrustWindowsInstaller)  
  
-   [Considerazioni specifiche sulla sicurezza per le soluzioni Office](#Security)  
  
-   [Sicurezza durante lo sviluppo](#SecurityDuringDeployment)  
  
-   [Visual Studio Tools per Office Runtime](#VisualStudioToolsForOfficeRuntime)  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="GrantingTrustToSolutions"></a> Concessione dell'attendibilità alle soluzioni Office  
 La concessione dell'attendibilità alle soluzioni Office prevede la modifica dei criteri di sicurezza di tutti gli utenti finali in modo che la soluzione Office venga considerata attendibile in base alla seguente evidenza:  
  
-   Il certificato usato per firmare il manifesto della distribuzione.  
  
-   L'URL del manifesto della distribuzione.  
  
 Per ulteriori informazioni, vedere [concessione dell'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md).  
  
##  <a name="GrantingTrustToDocuments"></a> Concessione dell'attendibilità ai documenti  
 Una personalizzazione a livello di documento richiede che il documento si trovi in una directory progettata come percorso attendibile. Per altre informazioni, vedere [Granting Trust to Documents](../vsto/granting-trust-to-documents.md).  
  
##  <a name="GrantingTrustWindowsInstaller"></a> Concessione dell'attendibilità quando si usa Windows Installer  
 È possibile usare Windows Installer per creare un file MSI per installare le soluzioni Office nella directory Programmi, che richiede diritti di amministratore. Per le soluzioni Office nella directory Programmi, Visual Studio 2010 Tools per Office Runtime considera le soluzioni di Office siano attendibili e non visualizza la richiesta di attendibilità di ClickOnce.  
  
##  <a name="Security"></a> Considerazioni specifiche sulla sicurezza per le soluzioni Office  
 Le funzionalità di sicurezza fornite da [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] e Microsoft Office possono contribuire alla protezione contro diverse possibili minacce alla sicurezza nelle soluzioni Office. Per altre informazioni, vedere [Specific Security Considerations for Office Solutions](../vsto/specific-security-considerations-for-office-solutions.md).  
  
##  <a name="SecurityDuringDeployment"></a> Sicurezza durante lo sviluppo  
 Per semplificare il processo di sviluppo, Visual Studio imposta i criteri di sicurezza necessari per eseguire ed eseguire il debug della soluzione nel computer ogni volta che si compila un progetto. In alcuni scenari, è necessario aggiungere altri passaggi di sicurezza per sviluppare il progetto.  
  
### <a name="document-level-solutions"></a>Soluzioni a livello di documento  
 Il percorso completo di un documento deve essere aggiunto all'elenco di percorsi attendibili nell'applicazione Microsoft Office se si stanno sviluppando i tipi di progetti seguenti:  
  
-   Le soluzioni presenti in una condivisione di file di rete, ad esempio a livello di documento  *\\\servername\sharename*.  
  
-   Soluzioni a livello di documento per Word che usano file doc o docm.  
  
 Includere le sottodirectory quando si aggiunge il percorso del documento all'elenco di percorsi attendibili oppure includere le cartelle di debug e di compilazione specifiche. Per ulteriori informazioni, vedere l'articolo della Guida Online di Microsoft Office [creazione, rimozione o modifica di un percorso attendibile per i file](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
### <a name="temporary-certificates"></a>Certificati temporanei  
 Se non è disponibile un certificato di firma, Visual Studio crea un certificato temporaneo. Usare questo certificato temporaneo solo durante lo sviluppo e acquistare un certificato ufficiale per la distribuzione.  
  
 Il certificato temporaneo viene generato dopo la prima compilazione di un progetto Office. Quando si preme di nuovo F5, il progetto viene ricompilato perché viene contrassegnato come modificato durante l'aggiunta del certificato.  
  
 Cancellare regolarmente i certificati temporanei poiché potrebbero accumularsi nel tempo.  
  
##  <a name="VisualStudioToolsForOfficeRuntime"></a> Visual Studio Tools per Office Runtime  
 Il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dispone di funzionalità per verificare l'identità del server di pubblicazione e le autorizzazioni concesse a una personalizzazione. Verifica le autorizzazioni mediante una sequenza di controlli di sicurezza.  
  
### <a name="security-during-customization-loading"></a>Sicurezza durante il caricamento della personalizzazione  
 Quando viene caricata una personalizzazione a livello di documento, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sempre controlla se il documento è nell'elenco di percorsi attendibili. Inoltre, il runtime controlla se la soluzione richiede FullTrust nel manifesto dell'applicazione. Non esegue controlli di sicurezza aggiuntivi durante il caricamento della personalizzazione.  
  
### <a name="sequence-of-security-checks-during-installation"></a>Sequenza di controlli di sicurezza durante l'installazione  
 Quando una soluzione Office viene installata o aggiornata, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] esegue un set di controlli di sicurezza in una sequenza specifica per prendere una decisione di attendibilità. Una soluzione viene installata o aggiornata solo se il runtime ne determina l'attendibilità.  
  
 È possibile avviare il processo di installazione in uno dei seguenti quattro modi: eseguendo il programma di installazione, aprendo il manifesto della distribuzione, aprendo l'host applicazioni di Microsoft Office o eseguendo VSTOInstaller.exe.  
  
 Il primo controllo di sicurezza si applica solo alle soluzioni a livello di documento. Il documento di una soluzione a livello di documento deve trovarsi in un percorso attendibile. Se il documento si trova in una condivisione file di rete remota oppure ha un'estensione di file doc o docm, il percorso del documento deve essere aggiunto all'elenco di percorsi attendibili. Per altre informazioni, vedere [Granting Trust to Documents](../vsto/granting-trust-to-documents.md).  
  
 ![Sicurezza VSTO: installazione da Microsoft Office](../vsto/media/host-install.png "sicurezza VSTO: installazione da Microsoft Office")  
  
 Il set di controlli di sicurezza successivo è quello di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] e ClickOnce. Per superare questi controlli, soluzioni Office devono richiedere le autorizzazioni FullTrust, essere firmate con un certificato che non è elencato nell'elenco di server di pubblicazione non attendibili e trovarsi in una posizione che non è presente in tale area Internet Explorer. Se il certificato nell'elenco di server di pubblicazione Trusted, la soluzione viene installata immediatamente. In caso contrario, se ha superato i controlli, la soluzione continua con l'ultimo set di controlli.  
  
 ![Sicurezza VSTO per l'installazione di soluzioni](../vsto/media/installing.png "sicurezza VSTO per l'installazione di soluzioni")  
  
 Se il [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] richiesta di attendibilità è consentito e la soluzione non è ancora concessa l'attendibilità, il runtime consente all'utente finale di prendere la decisione di attendibilità. Se l'utente concede l'attendibilità alla soluzione, viene aggiunta una voce all'elenco di inclusione dell'utente. Tutte le soluzioni nell'elenco di inclusione dell'utente hanno l'attendibilità totale e possono essere installate ed eseguite.  
  
 A partire da Visual Studio 2010, l'elenco di inclusione viene ignorato se la soluzione Office viene installata usando Windows Installer (MSI) nella directory Programmi. Per ulteriori informazioni, vedere [Trusting soluzioni di Office per gli elenchi di inclusione](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 ![Sicurezza VSTO: tramite il programma di installazione per installare](../vsto/media/setup-vstoinstaller.png "sicurezza VSTO: tramite il programma di installazione per installare")  
  
## <a name="see-also"></a>Vedere anche  
 [Concessione dell'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)   
 [Concessione dell'attendibilità ai documenti](../vsto/granting-trust-to-documents.md)   
 [Concessione dell'attendibilità alle soluzioni Office mediante gli elenchi di inclusione](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Procedura: configurare la protezione di elenco di inclusione](../vsto/how-to-configure-inclusion-list-security.md)   
 [Procedura: firmare soluzioni Office](../vsto/how-to-sign-office-solutions.md)   
 [Risoluzione dei problemi di sicurezza delle soluzioni Office](../vsto/troubleshooting-office-solution-security.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Riferimenti di ClickOnce](/visualstudio/deployment/clickonce-reference)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
  