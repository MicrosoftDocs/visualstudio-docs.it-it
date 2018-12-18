---
title: Glossario di Visual Studio SDK | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a08985c4977896e35fa8cd94014385ac32dd8bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-sdk-glossary"></a>Glossario di Visual Studio SDK
Il glossario includono le definizioni dei termini utilizzati nel [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] documentazione.  
  
## <a name="terms"></a>Termini  
 componente aggiuntivo  
 Un'applicazione di utilità, driver o altro software aggiunti a un'applicazione principale. Nell'ambiente di sviluppo integrato (IDE) di Visual Studio, un componente aggiuntivo è un'applicazione basata su automazione che estende le funzionalità dell'IDE.  
  
 modello di automazione  
 Il modello di automazione, noto nelle versioni precedenti di Visual Studio come modello di estendibilità, è un'interfaccia di programmazione che consente di accedere alle routine sottostanti tale unità IDE. Componenti aggiuntivi, procedure guidate e le macro, utilizzano gli oggetti nel modello di automazione per controllare o estendono le funzionalità dell'IDE.  
  
 contesto del comando dell'interfaccia utente  
 Associazione di un GUID con la visibilità di un comando dell'interfaccia utente o un elemento, ad esempio una barra degli strumenti. Contesto del comando dell'interfaccia utente è a differenza di contesto della selezione, in quanto non è connesso a una finestra.  
  
 Contesto dell'interfaccia utente di comando può essere utilizzato per:  
  
-   Assegnare un GUID a una barra degli strumenti visualizzata quando viene attivata una particolare finestra.  
  
-   Assegnare un GUID per la disponibilità di un comando senza dover caricare o eseguire un pacchetto VSPackage.  
  
-   Assegnare un GUID per influire sull'associazione chiave attiva.  
  
-   Assegnare un GUID per attivare la registrazione di macro.  
  
-   Assegnare un GUID per attivare la modalità di debug o per passare dalla progettazione alla modalità di esecuzione in un editor.  
  
 component  
 Componente software che può essere eseguito parte delle funzionalità di un'applicazione senza tale applicazione con le informazioni sull'implementazione del software pre-esistente. La comunicazione tra un componente e un'applicazione è esclusivamente tramite interfacce OLE.  
  
 gestione dei componenti  
 Un servizio, `SOleComponentManager`, che fornisce servizi di coordinamento di interfaccia non utente per i componenti di livello superiore. Il `SOleComponentManager` servizio implementa il `IOleComponentManager` interfaccia.  
  
 gestione dei componenti dell'interfaccia utente  
 Un servizio, `SOleComponentUIManager`, che fornisce servizi di coordinamento dell'interfaccia utente. Il `SOleComponentUIManager` servizio implementa il `IOleComponentUIManager` e `IOleInPlaceComponentUIManager` interfacce.  
  
 contesti  
 Un `IVsUserContext` oggetto (COM) collegato a un componente di ambiente. Questo oggetto contiene parole chiave di ricerca, le parole chiave F1 e gli attributi relativi al componente. Contenitori di contesto è inoltre puntare a qualsiasi sacchetti sottocontesto collegate a tali.  
  
 provider di contesto  
 Un componente nell'IDE che dispone di un contenitore di contesto è associato. Tali componenti includono una finestra degli strumenti, editor o la gerarchia di progetto.  
  
 finestra di progettazione  
 Interfaccia di programmazione che consente agli utenti di modificare gli elementi dell'interfaccia utente (Form, pulsanti e altri controlli).  
  
 DocData  
 Un oggetto COM che incapsula i dati sottostanti di un documento in un mondo in cui è presente una separazione documento/visualizzazione (ad esempio, in caso di editor di testo, questo sarebbe il buffer di testo sottostante tutte le visualizzazioni di editor di testo). Se il EditorFactory non fornisce questo oggetto, l'IDE verrà produrre uno per suo conto. La responsabilità di questo oggetto consiste nel gestire la persistenza dei dati e la semantica di condivisione per più viste su questo stesso `DocData`. Se il `DocData` oggetto supporta la `IOleCommandTarget` interfaccia, verrà incluso nel routing dei comandi di UIShell il.  
  
 DocObject  
 Tecnologia usata per ospitare l'interfaccia utente in un intervallo fornito dall'host. In particolare, questo termine si riferisce a qualsiasi incorporamento che supporta il `IOleDocument` e le relative interfacce. Questa tecnologia ha molte applicazioni potenziali, ad esempio un dettaglio di implementazione di documenti di COM, le finestre degli strumenti in Visual Basic 5.0, finestre di progettazione ActiveX in Visual Basic 6.0 e così via.  
  
 documento  
 Utilizzato per fare riferimento in modo generico per il documento nel suo complesso, sia il `DocData` e `DocView`. Ad esempio, un DocumentFrame contiene un `DocView`, ma anche mantiene un riferimento al `DocData` per gestire la persistenza.  
  
 DocView  
 DocObject/incorporamento/WindowPane con cui l'utente interagisce per visualizzare e modificare sottostante `DocData`. Si noti che gli utenti non usufruiscono di separazione che fa parte del documento/visualizzazione di `DocObject` interfaccia di progettazione. Gli utenti di usare un'intera DocObject come una visualizzazione anziché una nozione più astratto (e meno formalizzato) di dati sottostante, noto come `DocData`. `DocView` gli oggetti sono sempre incorporati con gli oggetti di cornice di documento (finestre figlio MDI) dell'IDE.  
  
 DTE  
 Il `DTE` oggetto (estensibilità degli strumenti di sviluppo) è il punto di accesso di primo livello nel modello di automazione di Visual Studio, che consente di automatizzare a livello di codice ed estendere l'IDE.  
  
 Finestra Guida dinamica  
 Finestra dello strumento che viene implementato dall'IDE e visualizza un elenco di parole chiave di ricerca o gli argomenti della Guida F1.  
  
 editor  
 Codice (classe, CLSID) che implementa il `DocView`. Implementa inoltre `DocData` se la separazione di dati/visualizzazione è supportata.  
  
 estensione  
 Una funzionalità che consente di modificare, Personalizza o aggiunge un IDE. Si creano estensioni utilizzando il modello di automazione o di un VSPackage.  
  
 editor esterno  
 Un editor che non è specifico dell'IDE, ad esempio Microsoft Word. È stato registrato tramite i proprio meccanismi e può essere utilizzata all'esterno dell'IDE. Se questo editor può essere incorporato, viene visualizzato all'interno di una finestra dell'IDE. Se non può essere incorporato, viene creata una finestra di primo livello separata.  
  
 gerarchia  
 Struttura ad albero di nodi, ogni nodo associato a un set di proprietà.  
  
 componente di primo livello indipendente  
 Un componente che utilizza una finestra di primo livello non modale e può funzionare in modo efficace come una finestra dell'applicazione autonoma, ma viene implementato come un oggetto in-process. Pertanto, un componente di livello superiore indipendente deve coordinare modalità e i servizi di ciclo di messaggi con l'IDE. Gli oggetti in-process non dispone di proprio ciclo di messaggi.  
  
 provider di informazioni  
 Il provider di informazioni è un modulo che è possibile cercare parole chiave e restituire un elenco di argomenti, sotto forma di `IVsUserContextItem` oggetti. Per fornire elementi di parola chiave F1 e ricerca per il provider di informazioni, registrare il file della Guida compilato (. HxS) con il sistema. Gli argomenti della Guida in questi file vengono utilizzati per fornire l'elenco di argomenti visualizzati nella finestra Guida dinamica e visualizzate se si preme F1.  
  
 componente sul posto  
 Un oggetto VSPackage che implementa il `IOleInPlaceComponent` interfaccia per la gestione di una finestra visivamente contenuta all'interno di una finestra del documento dell'IDE di proprietà. I componenti sul posto non partecipano standard OLE unione dei menu; In alternativa i relativi elementi dell'interfaccia utente vengono integrate nell'IDE.  
  
 Esistono due tipi di componenti sul posto: cablata sul posto componenti e controlli dei componenti.  
  
 Cablata sul posto componenti dispone di menu, barre degli strumenti e i comandi che sono strettamente integrati nell'interfaccia utente dell'IDE, viene visualizzato come se sono state compilate direttamente nell'IDE.  
  
 Componente controlli non dispongono di uno qualsiasi dei propri elementi dell'interfaccia utente integrati nell'IDE; In alternativa utilizzare i menu, comandi e le barre degli strumenti dell'IDE. Ad esempio, il comando grassetto Impossibile utilizzabile da visualizzare in grassetto una parola selezionata all'interno di un controllo RTF incorporato in un form. Tuttavia, controlli di un componente possono richiedere che visualizzati elementi dell'interfaccia utente di specifici dei componenti installati in modo dinamico.  
  
 Servizio di linguaggio  
 Un set di oggetti che consente agli sviluppatori di VSPackage implementare le funzionalità dell'editor di codice lingua di computer, ad esempio testo contrassegnare e colorare.  
  
 Progetto di file esterni  
 Progetto utilizzato per memorizzare i file aperti che non sono presenti in qualsiasi progetto. L'elenco di elementi in questo progetto non è persistente.  
  
 progetto  
 I progetti sono costituiti da oggetti della gerarchia o che implementano oggetti COM di `IVsHierarchy` interfaccia.  
  
 progettazione specifici del progetto o nell'editor  
 Finestra di progettazione che non può essere utilizzato in modo indipendente da tipi di progetto. Tutte le finestre di progettazione specifici del progetto deve immettere le informazioni di Factory dell'Editor del Registro di sistema. L'IDE quindi possibile creare un'istanza alla finestra di progettazione ogni volta che un determinato tipo di file viene aperto in un particolare progetto.  
  
 finestra di tipo di progetto  
 Una finestra che tiene traccia costantemente la gerarchia del progetto attivo e l'elemento nel contesto di selezione globale. Tipo di progetto windows utilizza il `SVsTrackSelectionEx` servizio per indicare all'IDE di modifiche e visualizzare i commenti e suggerimenti per l'utente. Esplora soluzioni è un esempio di una finestra del tipo di progetto.  
  
 Finestra Proprietà  
 Visualizzatore di proprietà in precedenza.  
  
 progetti di tipo riferimento  
 Progetto che non richiedono i file per il progetto si trovi nella stessa directory. Invece i riferimenti ai file da altre directory non correlati vengono archiviati e gestiti dal progetto stesso.  
  
 tabella documenti in esecuzione  
 Struttura interna mediante il quale l'IDE gestisce l'elenco di tutti i documenti attualmente aperti. Questo elenco include tutti i documenti aperti in memoria indipendentemente dal fatto che i documenti sono in corso di modifica. Un documento è qualsiasi elemento che viene salvato, incluse le stored procedure aperte in un editor, i file in un progetto o file di progetto principale (ad esempio, il file vcproj).  
  
 Contesto della selezione  
 Dati che fa parte dei dettagli di ogni finestra dell'IDE e viene utilizzati per rilevare le selezioni attive. Contesto di selezione è costituito da:  
  
-   Puntatore al `IVsHierarchy` interfaccia della gerarchia del progetto  
  
-   Identificatore dell'elemento dell'elemento del progetto.  
  
-   Puntatore al `ISelectionContainer` interfaccia fornendo l'accesso alle proprietà per gli oggetti attivi.  
  
-   Matrice di valori di elemento.  
  
 servizio  
 Un contratto per un set di interfacce COM che si trovano in un singolo oggetto COM. Quando si crea un servizio, il quale è identificato da un GUID, definire il set di interfacce COM che esegue il servizio. Oggetti COM di utilizzare servizi per comunicare tra loro.  
  
 Soluzione  
 Gruppo di progetti correlati con cui un utente utilizza.  
  
 finestra di progettazione standard  
 Finestra di progettazione che può essere utilizzato indipendentemente dal tipo di progetto. Tutte le finestre di progettazione standard è necessario immettere le informazioni di Factory dell'Editor del Registro di sistema. L'IDE quindi possibile creare un'istanza alla finestra di progettazione ogni volta che viene aperto un file con un'estensione specifica. I dati devono essere definitive in un file.  
  
 editor standard  
 Editor che può essere utilizzato indipendentemente da qualsiasi tipo di progetto specifico. Tali editor dispongono EditorFactories registrato nel Registro di sistema. In questo modo l'IDE individuare e richiamare l'editor.  
  
 editor del sistema operativo standard  
 Incorporamento di un che non è Visual Studio specifico. È registrato utilizzando le chiavi di Win32 note (ad esempio, Esplora risorse Win32 sa come richiamare). Se è possibile incorporare tali editor, editor verrà visualizzata al suo posto nell'IDE. In caso contrario, viene creata una finestra di primo livello separata per tali editor.  
  
 contenitore sottocontesto  
 Un `IVsUserContext` oggetto collegato a un elenco di contesti. Questo oggetto contiene parole chiave di ricerca, le parole chiave F1 e gli attributi per una selezione all'interno di un componente IDE. Esempi di sottocontesto includono un comando in una finestra degli strumenti o una parola chiave in un editor.  
  
 Elenco attività  
 Finestra dello strumento che viene implementato dall'IDE e visualizza un elenco di attività attive.  
  
 Buffer del testo  
 Nome comune per l'oggetto `VSTextBuffer`.  
  
 Visualizzazione di testo  
 Nome comune per l'oggetto `VSTextView`.  
  
 componente di primo livello dello strumento  
 Un componente che funziona come una finestra popup modale, strettamente coordinamento con l'interfaccia utente dell'IDE. Ad esempio i componenti indipendenti di primo livello, componenti di livello principale dello strumento necessario coordinare anche modalità e i servizi di ciclo di messaggi con l'IDE.  
  
 componente di primo livello  
 Un oggetto VSPackage che gestisce una finestra di primo livello non modale anziché l'area client di una finestra dell'IDE. Componenti di livello superiore di implementare il `IOleComponent` interfaccia possa sfruttare i vantaggi di servizi di ciclo di messaggi ad esempio l'accesso a tempo di inattività.  
  
 Attivo dell'interfaccia utente  
 Un oggetto VSPackage che è visibile e attivo.  
  
 Gerarchia dell'interfaccia utente  
 Un oggetto COM che implementa il `IVsUIHierarchy` interfaccia per consentire la visualizzazione di una gerarchia. Implementa la finestra gerarchia dell'interfaccia utente di `ISelectionContainer` interfaccia per aggiornare la finestra Proprietà; le altre finestre del tipo di progetto è possono utilizzare questa implementazione, se lo si desidera.  
  
 VSCT  
 Tabella comandi di Visual Studio. Il file con estensione vsct contiene informazioni sul posizionamento e comportamenti dei menu, barre degli strumenti e comandi in formato XML.  
  
 VSPackage  
 Un componente installabile software che consente di estendere l'IDE di Visual Studio aggiungendo uno o più dei seguenti: interfaccia utente, servizi, i tipi di progetto o dell'editor di progettazione. Un VSPackage è costituito da un oggetto COM che implementa il `IVsPackage` interfaccia e uno o più altri oggetti COM che implementano le altre interfacce per supportare la selezione e altre funzionalità. Inoltre, un pacchetto VSPackage ha i requisiti di registrazione specifiche.