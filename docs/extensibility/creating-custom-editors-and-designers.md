---
title: Creazione di editor personalizzati e finestre di progettazione | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
caps.latest.revision: "31"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d8d354333545a6ec2b637e160818d506fa049c29
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="creating-custom-editors-and-designers"></a>Creazione di finestre di progettazione ed editor personalizzati
Ambiente di sviluppo integrato (IDE) di Visual Studio può ospitare diversi tipi di editor:  
  
-   Editor di componenti di base di Visual Studio  
  
-   Editor personalizzati  
  
-   Editor esterni  
  
-   Finestre di progettazione  
  
 Le informazioni seguenti consentono di scegliere il tipo di editor, che è necessario.  
  
## <a name="types-of-editor"></a>Tipi di Editor  
 Per informazioni sull'editor di componenti di base di Visual Studio, vedere [estensione dell'Editor e i servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md).  
  
##### <a name="custom-editors"></a>Editor personalizzati  
 Un editor personalizzato è quello che è progettato per funzionare in circostanze speciali. Ad esempio, è possibile creare un editor la cui funzione consiste nel leggere e scrivere dati in un repository specifico, ad esempio un server di Microsoft Exchange. Se si desidera un editor che funziona con solo il tipo di progetto o se si desidera un editor con alcuni comandi specifici, scegliere un editor personalizzato. Si noti tuttavia che gli utenti non saranno in grado di utilizzare un editor personalizzato per modificare standard [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetti.  
  
 Un editor personalizzato è possibile utilizzare una factory dell'editor e aggiungere informazioni sull'editor del Registro di sistema. Tuttavia, il tipo di progetto associato all'editor personalizzato può creare un'istanza all'editor personalizzato in altri modi.  
  
 Un editor personalizzato è possibile utilizzare l'attivazione sul posto o incorporamento semplificato per implementare una vista.  
  
##### <a name="external-editors"></a>Editor esterni  
 Editor esterni sono editor che non sono integrati in Visual Studio, ad esempio Microsoft Word, il blocco note o Microsoft FrontPage. Se, ad esempio, si passa il testo a esso dal VSPackage, è possibile chiamare un editor di questo tipo. Editor esterni effettuano la registrazione e può essere utilizzato all'esterno di Visual Studio. Quando si chiama un editor esterno, e possono essere incorporato in una finestra host, viene visualizzato in una finestra nell'IDE. In caso contrario, verrà creata una finestra separata per tale.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> metodo imposta la priorità usando il <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumerazione. Se il `DP_External` è specificato il valore, il file può essere aperto da un editor esterno.  
  
## <a name="editor-design-decisions"></a>Decisioni di progettazione di editor  
 Le domande di progettazione seguenti consentono di scegliere il tipo di editor migliore adattato alla propria applicazione:  
  
-   L'applicazione salverà i dati nei file o non? Se i dati verrà salvato nel file, saranno in un formato standard o personalizzato?  
  
     Se si utilizza un formato di file standard, sarà in grado di aprire e leggere e scrivere dati ad essi altri tipi di progetto oltre il progetto. Se si utilizza un formato di file personalizzati, tuttavia, solo il tipo di progetto sarà in grado di aprire e leggere e scrivere dati in essi.  
  
     Se il progetto usa i file, è necessario personalizzare l'editor standard. Se il progetto non usa i file, ma piuttosto utilizza gli elementi in un database o altri repository, è necessario creare un editor personalizzato.  
  
-   L'editor necessita ospitare controlli ActiveX?  
  
     Se l'editor ospita controlli ActiveX, quindi implementare un editor di attivazione sul posto, come descritto [attivazione sul posto](../extensibility/in-place-activation.md). Se non contiene controlli ActiveX, quindi utilizzare un editor di incorporamento semplificato oppure personalizzare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor predefinito.  
  
-   L'editor supporterà più visualizzazioni? Se si desidera che le visualizzazioni di editor sia visibile allo stesso tempo, come l'editor predefinito, è necessario supportare più visualizzazioni.  
  
     Se l'editor deve supportare più viste, i dati del documento e gli oggetti di visualizzazione di documento per l'editor devono essere oggetti separati. Per ulteriori informazioni, vedere [di supporto di più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md).  
  
     Se l'editor supporta più viste, si intende utilizzare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implementazione del buffer di testo dell'editor di base (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto) per l'oggetto dati del documento? Vale a dire, con cui si desidera supportare l'editor visualizza side-by-side con la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale? La possibilità di eseguire questa operazione è la base della finestra di progettazione form...  
  
-   Se è necessario ospitare un editor esterno, l'editor incorporabili in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?  
  
     Se può essere incorporato, è necessario creare una finestra host per l'editor esterno e quindi chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> metodo e impostare il <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> valore di enumerazione `DP_External`. Se l'editor non può essere incorporato, l'IDE crea automaticamente una finestra separata per tale.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Procedura dettagliata: Creazione di un editor personalizzato](../extensibility/walkthrough-creating-a-custom-editor.md)  
 Viene illustrato come creare un editor personalizzato.  
  
 [Procedura dettagliata: Aggiunta di funzionalità in un editor personalizzato](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 Viene illustrato come aggiungere funzionalità a un editor personalizzato.  
  
 [Inizializzazione della finestra di progettazione e configurazione dei metadati](../extensibility/designer-initialization-and-metadata-configuration.md)  
 Viene illustrato come inizializzare una finestra di progettazione.  
  
 [Aggiunta del supporto dell'annullamento alle finestre di progettazione](../extensibility/supplying-undo-support-to-designers.md)  
 Viene illustrato come fornire il supporto di annullamento per le finestre di progettazione.  
  
 [Colorazione della sintassi negli editor personalizzati](../extensibility/syntax-coloring-in-custom-editors.md)  
 Viene illustrata la differenza tra nell'editor di componenti di base e negli editor personalizzato di colorazione della sintassi.  
  
 [Dati documento e visualizzazione documento negli editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 Viene illustrato come implementare i dati del documento e visualizzazione del documento nell'editor personalizzati.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Interfacce legacy nell'Editor](../extensibility/legacy-interfaces-in-the-editor.md)  
 Viene illustrato come accedere all'editor di componenti di base tramite l'API legacy.  
  
 [Sviluppo di un servizio di linguaggio legacy](../extensibility/internals/developing-a-legacy-language-service.md)  
 Viene illustrato come implementare un servizio di linguaggio.  
  
 [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Viene illustrato come creare elementi dell'interfaccia utente che corrispondano al resto del [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>