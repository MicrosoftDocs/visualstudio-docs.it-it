---
title: All'interno di Visual Studio SDK | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e8b1374b6934e09bbf3ce1012d551dab2831292c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="inside-the-visual-studio-sdk"></a>All'interno di Visual Studio SDK
In questa sezione fornisce informazioni approfondite sulle estensioni di Visual Studio, tra cui architettura di Visual Studio, componenti, servizi, schemi, utilità e così via.  
  
## <a name="extensibility-architecture"></a>Architettura di estendibilità  
 Nella figura seguente viene illustrata l'architettura di estendibilità di Visual Studio. Pacchetti VSPackage forniscono funzionalità di applicazione, che viene condiviso nell'IDE come servizi. L'IDE standard offre una vasta gamma di servizi, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, che consentono di accedere alla funzionalità di windowing IDE.  
  
 ![Rappresentazione grafica dell'architettura ambiente](../../extensibility/internals/media/environment.gif "ambiente")  
Generalizzato di vista dell'architettura di Visual Studio  
  
## <a name="vspackages"></a>VSPackages  
 I VSPackage sono moduli software che compongono ed estendono Visual Studio con elementi dell'interfaccia utente, servizi, progetti, editor e finestre di progettazione. I VSPackage rappresentano l'unità centrale dell'architettura di Visual Studio. Per ulteriori informazioni, vedere [VSPackage](../../extensibility/internals/vspackages.md).  
  
## <a name="visual-studio-shell"></a>Visual Studio Shell  
 La shell di Visual Studio fornisce funzionalità di base e supportare la comunicazione tra tra i componente VSPackage ed estensioni MEF. Per ulteriori informazioni, vedere [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).  
  
## <a name="user-experience-guidelines"></a>Linee guida sull'esperienza utente  
 Se si intende progettare nuove funzionalità per Visual Studio, si deve dare un'occhiata a queste linee guida per i suggerimenti di progettazione e l'usabilità: [linee guida esperienza utente di Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="commands"></a>Comandi:  
 I comandi sono funzioni che eseguono attività, ad esempio la stampa di un documento, l'aggiornamento di una visualizzazione o la creazione di un nuovo file.  
  
 Quando si estende Visual Studio, è possibile creare comandi e registrarlo con la shell di Visual Studio. È possibile specificare come questi comandi verranno visualizzati nell'IDE, ad esempio, un menu o una barra degli strumenti. In genere è presente un comando personalizzato il **strumenti** menu e un comando per la visualizzazione di una finestra degli strumenti vengono visualizzate nel **altre finestre** sottomenu del **vista** menu.  
  
 Quando si crea un comando, è necessario creare anche un gestore eventi per tale. Il gestore eventi determina quando il comando è visibile o abilitato, è possibile modificare il testo e garantisce che il comando risponda in modo appropriato quando è abilitato. Nella maggior parte dei casi, l'IDE gestisce i comandi utilizzando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. I comandi in Visual Studio vengono gestiti a partire dal contesto del comando più interno, in base alla selezione locale e procedendo verso il contesto più esterno, in base alla selezione globale. I comandi aggiunti al menu principale sono immediatamente disponibili per lo scripting.  
  
 Per ulteriori informazioni, vedere [comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="menus-and-toolbars"></a>Menu e barre degli strumenti  
 Menu e barre degli strumenti consentono agli utenti di richiamare i comandi. I menu sono righe o colonne di comandi che in genere vengono visualizzate come singoli elementi di testo nella parte superiore di una finestra degli strumenti. Sottomenu sono menu secondari che appaiono quando un utente sceglie i comandi che includono una piccola freccia. Menu di scelta rapida visualizzato quando l'utente fa clic alcuni elementi dell'interfaccia utente. Alcuni nomi di menu comuni sono **File**, **modifica**, **vista**, e **finestra**. Per ulteriori informazioni, vedere [estensione menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
 Barre degli strumenti sono righe o colonne di pulsanti e altri controlli, ad esempio caselle combinate, caselle di riepilogo e caselle di testo. Pulsanti della barra degli strumenti sono in genere le immagini icona, ad esempio un'icona di cartella per un **Apri File** comando o una stampante per una **stampa** comando. Tutti gli elementi della barra degli strumenti sono associati a comandi. Quando si fa clic su un pulsante della barra degli strumenti, viene eseguito il comando associato. Nel caso di un controllo elenco a discesa, ogni elemento nell'elenco a discesa è associata a un comando diverso. Alcuni controlli della barra degli strumenti, ad esempio un controllo barra di divisione, sono ibridi. Un lato del controllo è un pulsante della barra degli strumenti e l'altro lato è una freccia rivolta verso il basso che visualizza comandi diversi quando viene selezionato.  
  
## <a name="tool-windows"></a>Finestre degli strumenti  
 Le finestre degli strumenti vengono usate nell'IDE per visualizzare le informazioni. **Casella degli strumenti**, **Esplora**, **proprietà** finestra e **Web Browser** sono esempi di finestre degli strumenti.  
  
 Le finestre degli strumenti in genere offrono vari controlli con cui l'utente può interagire. Ad esempio, il **proprietà** finestra consente all'utente di impostare le proprietà di oggetti che fungono a uno scopo specifico. Il **proprietà** finestra è specializzato in questo senso, ma anche generale perché può essere utilizzato in molte situazioni diverse. Analogamente, il **Output** finestra è specializzata in quanto fornisce output basato su testo, ma generale perché molti sottosistemi in Visual Studio possono usare per fornire output all'utente di Visual Studio.  
  
 Prendere in considerazione l'immagine di Visual Studio, che contiene diverse finestre degli strumenti seguente.  
  
 ![Cattura di schermata](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 Alcune delle finestre degli strumenti sono ancorate insieme in un unico riquadro che consente di visualizzare la finestra degli strumenti di Esplora soluzioni e nasconde le altre finestre degli strumenti, ma li rende disponibili facendo clic sulle schede. Nella figura sono illustrate due altre finestre degli strumenti, la **elenco errori** e **Output** ancorata in un unico riquadro della finestra.  
  
 Viene inoltre illustrato il riquadro principale del documento, che mostra diverse finestre dell'editor. Anche se le finestre degli strumenti hanno in genere una sola istanza (ad esempio, è possibile aprire un solo **Esplora**), finestre dell'editor possono avere più istanze, ognuno dei quali è possibile modificare un documento separato, ma ognuno dei quali vengono ancorati in il riquadro stesso. Nella figura è illustrato un riquadro del documento che dispone di due finestre dell'editor, una finestra di progettazione di form e una finestra del browser che mostra la pagina iniziale. Tutte le finestre nel riquadro del documento sono disponibili facendo clic sulle schede, ma la finestra dell'editor che contiene file EditorPane.cs è visibile e attivo.  
  
 Quando si estende Visual Studio, è possibile creare lo strumento windows che consentono agli utenti di Visual Studio di interagire con l'estensione. È inoltre possibile creare il propria editor che consentono agli utenti di Visual Studio di modificare i documenti. Poiché le finestre degli strumenti ed editor verranno integrate in Visual Studio, non si dispone di programmazione per ancorare o vengono visualizzati correttamente in una scheda. Quando sono registrati correttamente in Visual Studio, avranno automaticamente le funzionalità tipiche di finestre degli strumenti e finestre di documento in Visual Studio. Per ulteriori informazioni, vedere [estensione e le finestre degli strumenti personalizzazione](../../extensibility/extending-and-customizing-tool-windows.md).  
  
## <a name="document-windows"></a>Finestre dei documenti  
 Una finestra del documento è una finestra cornice figlio di una finestra di interfaccia a documenti multipli (MDI). Finestre di documento in genere usate per ospitare gli editor di testo, editor di form (noto anche come finestre di progettazione) o controlli di modifica, ma può ospitare anche altri tipi di funzionalità. Il **nuovo File** la finestra di dialogo sono inclusi esempi di finestre dei documenti fornite da Visual Studio.  
  
 La maggior parte degli editor sono specifiche per un linguaggio di programmazione o a un tipo di file, ad esempio pagine HTML, pagine con frame, i file di C++ o file di intestazione. Selezionando un modello di **nuovo File** nella finestra di dialogo in modo dinamico un utente crea una finestra del documento per l'editor per il tipo di file associata con il modello. Quando un utente apre un file esistente, viene creata anche una finestra di documento.  
  
 Finestre di documento sono limitate all'area client MDI. Ogni finestra del documento è disponibile una scheda nella parte superiore e l'ordine di tabulazione è collegato ad altre finestre che possono essere aperti nell'area MDI. Facendo clic sulla scheda di una finestra del documento, viene visualizzato un menu di scelta rapida che include opzioni per dividere l'area MDI in più gruppi di schede di orizzontale o verticale. Suddivisione area MDI consente di visualizzare contemporaneamente più file. Per ulteriori informazioni, vedere [finestre dei documenti](../../extensibility/internals/document-windows.md).  
  
## <a name="editors"></a>Editor  
 Editor di Visual Studio consente di personalizzare il report e utilizzarlo per un tipo di contenuto personalizzato mediante Managed Extensibility Framework (MEF). In molti casi non è necessario creare un pacchetto VSPackage per estendere l'editor, anche se se si desidera includere le funzionalità da shell (ad esempio, un comando di menu o un tasto di scelta rapida), è possibile combinare un'estensione MEF con un pacchetto VSPackage.  
  
 È anche possibile creare un editor personalizzato, ad esempio, se si desidera leggere e scrivere in un database o se si desidera utilizzare una finestra di progettazione. È inoltre possibile utilizzare un editor esterno, ad esempio Blocco note o WordPad Microsoft. Per ulteriori informazioni, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
## <a name="language-services"></a>Servizi di linguaggio  
 Se si desidera l'editor di Visual Studio per supportare nuove parole chiave di programmazione o anche un nuovo linguaggio di programmazione, si crea un servizio di linguaggio. Ogni servizio di linguaggio può implementare alcune funzionalità dell'editor completamente, parzialmente o non è affatto. A seconda di come è configurato, il servizio di linguaggio possa fornire evidenziazione della sintassi, corrispondenza parentesi graffe, il supporto IntelliSense e altre funzionalità dell'editor.  
  
 Il fulcro di un servizio di linguaggio sono un parser e uno scanner. Uno scanner (o lexer) divide un file di origine in elementi che sono note come token e un parser stabilisce le relazioni tra tali token. Quando si crea un servizio di linguaggio, è necessario implementare il parser e lo scanner in modo che Visual Studio è possibile comprendere i token e grammatica del linguaggio. È possibile creare servizi di linguaggio gestito o non gestito. Per ulteriori informazioni, vedere [estensibilità di servizio del linguaggio Legacy](../../extensibility/internals/legacy-language-service-extensibility.md).  
  
## <a name="projects"></a>Progetti  
 In Visual Studio, i progetti sono contenitori utilizzati dagli sviluppatori per organizzare e compilare il codice sorgente e altre risorse. Progetti consentono di organizzare, compilare, eseguire il debug e distribuire il codice sorgente, i riferimenti a servizi Web e database e altre risorse. VSPackage possono estendere il sistema del progetto di Visual Studio fornisce tipi di progetto, sottotipi di progetto e strumenti personalizzati.  
  
 I progetti possono anche essere acquisiti in una soluzione, ovvero un raggruppamento di uno o più progetti che funzionano insieme per creare un'applicazione. Informazioni di progetto e lo stato relativo alla soluzione viene archiviate in due file di soluzione, il file della soluzione basata su testo (con estensione sln) e il file di soluzione binario utente opzione (suo Solution). Questi file sono simili per i file di gruppo (VBG) che sono stati usati nelle versioni precedenti di [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], e l'area di lavoro (con estensione DSW) e le opzioni utente file (. OPT) utilizzati nelle versioni precedenti di [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 Per ulteriori informazioni, vedere [progetti](../../extensibility/internals/projects.md) e [soluzioni](../../extensibility/internals/solutions.md).  
  
## <a name="project-and-item-templates"></a>Project and Item Templates  
 Visual Studio include modelli di progetto predefiniti e i modelli di progetto. È possibile apportare anche modelli personalizzati o acquisire modelli dalla community e quindi integrarli in Visual Studio. Il [MSDN Code Gallery](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) consente di passare per i modelli e le estensioni.  
  
 I modelli contengono la struttura di progetto e i file necessari per compilare un particolare tipo di applicazione, controllo, una libreria o classe di base. Quando si desidera sviluppare software che è simile a uno dei modelli, creare un progetto basato sul modello e quindi modificare i file nel progetto.  
  
> [!NOTE]
>  Questa architettura di modello non è supportata per [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetti. Per informazioni su come creare [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] modelli di progetto, vedere [la progettazione di una procedura guidata](/cpp/ide/designing-a-wizard).  
  
 Per ulteriori informazioni, vedere [aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="properties-and-options"></a>Proprietà e le opzioni  
 Il **proprietà** finestra vengono visualizzate le proprietà di uno o più elementi selezionati: [estensione di proprietà](../../extensibility/internals/extending-properties.md) pagine Opzioni del menu contengono set di opzioni che riguardano un determinato componente, ad esempio un linguaggio di programmazione o un pacchetto VSPackage: [opzioni e le pagine di opzioni](../../extensibility/internals/options-and-options-pages.md). Le impostazioni sono le funzionalità in genere correlate all'interfaccia utente che possono essere importate ed esportate: [il supporto per le impostazioni utente](../../extensibility/internals/support-for-user-settings.md).  
  
## <a name="visual-studio-services"></a>Servizi di Visual Studio  
 Un servizio fornisce un set specifico di interfacce per i componenti da utilizzare. Visual Studio fornisce un set di servizi che può essere utilizzato da tutti i componenti, incluse le estensioni. Ad esempio, i servizi di Visual Studio consentono le finestre degli strumenti essere visualizzato o nascosto in modo dinamico, abilitare l'accesso a eventi di interfaccia utente, barra di stato o della Guida. Editor di Visual Studio fornisce anche i servizi che possono essere importati dalle estensioni di editor. Per ulteriori informazioni, vedere [sull'utilizzo e la fornitura di servizi](../../extensibility/using-and-providing-services.md).  
  
## <a name="debugger"></a>Debugger  
 Il debugger è l'interfaccia utente per i componenti di debug specifiche della lingua. Se è stato creato un nuovo servizio di linguaggio, è necessario creare un motore di debug specifiche per associare il debugger. Per ulteriori informazioni, vedere [estensibilità di Visual Studio Debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="source-control"></a>Controllo del codice sorgente  
 Per informazioni sull'implementazione di un plug-in controllo del codice sorgente o un VSPackage, vedere [controllo del codice sorgente](../../extensibility/internals/source-control.md).  
  
## <a name="wizards"></a>Procedure guidate  
 È possibile creare una procedura guidata in combinazione con un nuovo tipo di progetto, in modo che la procedura guidata può aiutare gli utenti prendere le decisioni destra durante la creazione di un nuovo progetto di quel tipo. Per ulteriori informazioni, vedere [procedure guidate](../../extensibility/internals/wizards.md).  
  
## <a name="custom-tools"></a>Strumenti personalizzati  
 Gli strumenti personalizzati consentono di associare uno strumento con un elemento in un progetto ed eseguire tale strumento ogni volta che il file viene salvato. Per ulteriori informazioni, vedere [strumenti personalizzati](../../extensibility/internals/custom-tools.md).  
  
## <a name="vssdk-utilities"></a>Utilità VSSDK  
 Visual Studio SDK include un set di utilità che potrebbe essere necessario per poter funzionare con diversi aspetti di VSPackage. Per ulteriori informazioni, vedere [VSSDK utilità](../../extensibility/internals/vssdk-utilities.md).  
  
## <a name="using-windows-installer"></a>Utilizzo di Windows Installer  
 In alcuni casi potrebbe essere necessario utilizzare il programma di installazione di Windows anziché il programma di installazione VSIX: ad esempio, potrebbe essere necessario scrivere nel Registro di sistema. Per informazioni sull'utilizzo di Windows Installer con le estensioni, vedere [l'installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
## <a name="help-viewer"></a>Help Viewer  
 Consente di integrare la propria Guida in linea e pagine F1 Help Viewer. Per ulteriori informazioni, vedere [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).