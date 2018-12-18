---
title: Risoluzione dei problemi di distribuzione e creazione di pacchetti di SharePoint | Documenti Microsoft
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a2c9cbb7b0b9e7f0536fb393bcea3d0873e0d90a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="troubleshooting-sharepoint-packaging-and-deployment"></a>Risoluzione dei problemi relativi alla creazione di pacchetti e alla distribuzione di SharePoint
  In questo argomento vengono analizzati vari problemi che possono verificarsi durante la creazione di pacchetti e la distribuzione di soluzioni SharePoint.  
  
## <a name="enabling-enhanced-debugging"></a>Abilitazione del debug avanzato  
 Per effettuare una diagnosi dei problemi relativi a Visual Studio, SharePoint e ad altri livelli, è possibile utilizzare la chiave del Registro di sistema EnableDiagnostics per visualizzare la traccia dello stack. Per ulteriori informazioni, vedere [debug delle soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="adding-project-output-to-the-solution-package"></a>Aggiunta dell'output del progetto al pacchetto della soluzione  
 È possibile aggiungere l'output del progetto a un pacchetto mediante Progettazione pacchetti. Quando tuttavia si aggiunge l'output del progetto, verificare che la piattaforma del progetto corrisponda alla piattaforma della soluzione SharePoint. È consigliabile utilizzare il **qualsiasi CPU** piattaforma di destinazione per gli assembly che si desidera distribuire in un server SharePoint. Per ulteriori informazioni, vedere [pagina compilazione, Progettazione progetti &#40; Visual Basic &#41; ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) e [avanzata di dialogo Impostazioni del compilatore &#40; Visual Basic &#41; ](/visualstudio/ide/reference/advanced-compiler-settings-dialog-box-visual-basic).  
  
## <a name="validation-warnings-and-errors"></a>Avvisi ed errori di convalida  
 Gli strumenti di sviluppo di SharePoint in Visual Studio consentono di eseguire passaggi di convalida per verificare che il pacchetto della soluzione venga creato correttamente. È inoltre possibile creare passi di convalida personalizzati per le funzionalità e i pacchetti. Per ulteriori informazioni, vedere [procedura: creare funzionalità personalizzate e regole di convalida del pacchetto per le soluzioni SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## <a name="deployment-conflict-resolution"></a>Risoluzione dei conflitti di distribuzione  
 Quando si distribuisce una soluzione SharePoint, possono verificarsi conflitti se un elemento sul server ha lo stesso nome, URL o ID di un elemento presente nel pacchetto della soluzione. È possibile modificare il **risoluzione conflitti di distribuzione** proprietà da risolvere, segnalare o ignorare i conflitti per i moduli, Web parti, le istanze di elenco e tipi di contenuto.  
  
 Nella tabella seguente illustra le impostazioni per il **risoluzione conflitti di distribuzione** proprietà.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|Automatic|I conflitti vengono rilevati e risolti automaticamente.|  
|Prompt|I conflitti vengono rilevati e segnalati allo sviluppatore prima di essere risolti.|  
|nessuno|I conflitti non vengono rilevati.|  
  
## <a name="differences-between-f5-deployment"></a>Differenze rispetto alla distribuzione tramite il tasto F5  
 Quando si utilizza [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per distribuire il progetto SharePoint nel server SharePoint locale per il test e l'esecuzione del debug, in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vengono eseguiti alcuni passaggi aggiuntivi.  
  
1.  Reimpostazione di Internet Information Service (IIS) durante il passaggio di distribuzione.  
  
2.  Associazione automatica dei flussi di lavoro.  
  
3.  Impostazione dell'ordine di attivazione delle funzionalità in base alla gerarchia di Progettazione pacchetti.  
  
 È possibile aggiungere passaggi di distribuzione personalizzati per modificare ulteriormente il comportamento del tasto F5. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="delay-displaying-sharepoint-page-when-deploying-visual-web-part"></a>Ritardo della visualizzazione della pagina di SharePoint durante la distribuzione di una Web part visiva  
 La visualizzazione della pagina di SharePoint richiede molto tempo quando si distribuisce una Web part visiva nella cartella Bin di [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] o [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]. Se si modificano i file di una directory di livello superiore di [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], ad esempio la directory Bin, viene ricompilata l'intera applicazione Web. Questo può determinare fino a 25 secondi di ritardo nel rendering della pagina di SharePoint.  
  
### <a name="error-message"></a>Messaggio di errore  
 Nessuno.  
  
### <a name="resolution"></a>Risoluzione  
 Per risolvere il problema, effettuare i passaggi seguenti:  
  
1.  Installare l'aggiornamento KB967535 come descritto nell'articolo del supporto Microsoft [FIX: è disponibile un hotfix per risolvere due problemi in ASP.NET in IIS 7.0 per Windows Vista e Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=179055).  
  
2.  Aggiungere la riga di codice seguente al file Web.config:  
  
    ```  
    <compilation batch="false" optimizeCompilations="true">  
    ```  
  
## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>Distribuzione del progetto SharePoint non riuscita con generazione dell'errore "Impossibile estrarre il file cab nella soluzione"  
 Se il nome di un qualsiasi elemento di progetto SharePoint contiene parentesi, la distribuzione della soluzione non riesce generando un errore.  
  
### <a name="error-message"></a>Messaggio di errore  
 Si è verificato un errore nel passaggio di distribuzione 'Aggiungi Soluzione': Impossibile estrarre il file cab nella soluzione.  
  
### <a name="resolution"></a>Risoluzione  
 Per risolvere il problema, rimuovere le parentesi nei nomi degli elementi di progetto SharePoint.  
  
## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Errore visualizzato durante la distribuzione di una web part visiva in un sito in un'applicazione Web diversa  
 La prima volta che viene distribuita una Web part visiva a un sito su un'applicazione Web diversa da quella sulla quale è correntemente distribuita (modificando la proprietà SiteUrl della Web part visiva), si ottiene un errore.  
  
### <a name="error-message"></a>Messaggio di errore  
 Si è verificato un errore nel passaggio di distribuzione 'Aggiungi Soluzione': Una funzionalità con ID [#] è già stata installata in questa farm. Utilizzare l'attributo force per installare nuovamente in modo esplicito la funzionalità.  
  
### <a name="resolution"></a>Risoluzione  
 Questo errore si verifica a causa della modalità con cui le funzionalità della Web part visiva vengono ritratte in SharePoint. Per distribuire correttamente la Web part visiva, distribuire di nuovo la soluzione premendo F5.  
  
## <a name="warning-appears-when-deploying-nested-user-controls"></a>Avviso visualizzato durante la distribuzione di controlli utente annidati  
 Questo avviso viene visualizzato quando si distribuisce una soluzione SharePoint in cui sono annidati controlli utente, quale una web part visiva contenente un controllo utente o un controllo utente contenente una web part visiva o un altro controllo utente. Questo avviso viene generato se aggiungere un controllo a una finestra di progettazione trascinandolo dalla casella degli strumenti o utilizzando il @Register direttiva nella visualizzazione origine.  
  
### <a name="error-message"></a>Messaggio di errore  
 Avviso 1: l'elemento ' [*nome controllo*]' non è un elemento noto. Il problema potrebbe essere dovuto a un errore di compilazione del sito Web oppure il file web.config risulta mancante.  
  
### <a name="resolution"></a>Risoluzione  
 Se il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sistema del progetto non è compatibile con un controllo utente annidato, non può fornire Intellisense e genera l'avviso. Il sistema del progetto è a conoscenza di un controllo utente annidato se il progetto non è stato compilato e la finestra di progettazione non viene chiuso e riaperto, o se la ritrazione automatica è attivata, che comporta il controllo utente ritirare dall'hive SharePoint dopo il debug.  
  
 Per rimuovere questo avviso, compilare il progetto, quindi chiudere e riaprire la finestra di progettazione oppure disabilitare l'opzione di ritrazione automatica per il progetto. A tale scopo, deselezionare il **ritrazione automatica dopo il debug** casella di controllo di **SharePoint** scheda della finestra di dialogo delle proprietà del progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
