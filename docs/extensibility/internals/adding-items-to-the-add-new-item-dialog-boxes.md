---
title: Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a24a6d531812a170768f8c100f14ad64ab1e68c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo
Il processo di aggiunta di elementi di **Aggiungi nuovo elemento** viene avviata la finestra di dialogo con le chiavi del Registro di sistema. Come illustrato nelle voci del Registro di sistema seguenti, la sezione AddItemTemplates contiene il percorso e nome della directory degli elementi disponibili nel **Aggiungi nuovo elemento** la finestra di dialogo vengono inseriti.  
  
> [!NOTE]
>  Nella tabella immediatamente dopo il segmento di codice contiene informazioni aggiuntive sulla voce del Registro di sistema.  
  
 In questa sezione si trova in [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects].  
  
 Il primo GUID è il CLSID per i progetti di questo tipo. il secondo GUID indica il tipo di progetto registrati per i modelli di aggiungere elementi.  
  
 \\\1 \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} {C061DB26-5833-11D2-96F5-000000000000}  
  
 @="#6"  
  
 "TemplatesDir"="\<il percorso di installazione di Visual Studio SDK\\\VSIntegration\\\SomeFolder\\\SomePackage\\\SomeProject\\\SomeProjectItems"  
  
 "SortPriority" = dword:00000064  
  
|nome|Tipo|Dati (dal file con estensione RGS)|Descrizione|  
|----------|----------|-----------------------------|-----------------|  
|@ (Impostazione predefinita)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY %|ID di risorsa per **Aggiungi elemento** modelli.|  
|Val TemplatesDir|REG_SZ|%TEMPLATE_PATH%\ SomeProjectItems|Percorso degli elementi di progetto visualizzati nella finestra di dialogo per la **Aggiungi nuovo elemento** procedura guidata.|  
|Val SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)])|Nel nodo della struttura dei file visualizzati nell'ordine determina il **Aggiungi nuovo elemento** la finestra di dialogo.|  
  
> [!NOTE]
>  I GUID per i tipi di progetto Visual c# e Visual Basic sono i seguenti:[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 La directory elencata per TemplateDirs, ovvero % TEMPLATE_PATH%\SomeProjectItems è il nodo sul lato sinistro del **Aggiungi nuovo elemento** albero casella finestra di dialogo. Elementi aggiuntivi nell'albero sono basati sulla sottodirectory della directory radice. I file possono essere aggiunti al progetto sono gli elementi nel riquadro di destra la **Aggiungi nuovo elemento** la finestra di dialogo.  
  
 In genere, questa cartella conterrà i file di modello per il progetto, ad esempio un modello HTML o file con estensione cpp e tutti i file vsz per l'avvio di procedure guidate. Per controllare la modalità di visualizzazione di elementi, è inoltre possibile includere i file VSDIR per la localizzazione di icone e i nomi di directory. La stringa localizzata è la didascalia visualizzata nella finestra di dialogo che rappresenta questo nodo nell'albero della finestra di dialogo Aggiungi nuovo elemento.  
  
 Tuttavia, non si dispone di tutti gli elementi in un unico file VSDIR. È un file VSDIR per ogni elemento nella directory. Per ulteriori informazioni, vedere [guidata (. File vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) e [Directory descrizione del modello (. File VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
>  I file VSDIR nelle directory modello sono facoltativi. Se si desidera inserire un elemento di progetto nella directory e visualizzarli nel **Aggiungi nuovo elemento** nella finestra di dialogo è possibile inserire file nella directory di modelli specificate nell'istruzione TemplatesDir. Il file verrà quindi visualizzato nel riquadro destro del **Aggiungi nuovo elemento** la finestra di dialogo per il progetto. Tuttavia, se si desidera visualizzare un titolo per il file o un'icona localizzato, è necessario includere almeno un file VSDIR nella directory di modelli.  
  
## <a name="grouping-project-items"></a>Elementi di progetto di raggruppamento  
 Se si desidera includere gruppi di modelli nelle cartelle di **Aggiungi nuovo elemento** albero casella finestra di dialogo, è necessario disporre di una sottodirectory nella directory principale del modello con gli elementi in essi contenuti. Quando il **Aggiungi nuovo elemento** la finestra di dialogo viene visualizzata agli utenti, verrà inoltre visualizzare le sottocartelle e in grado di selezionare gli elementi del progetto.  
  
 La priorità di ordinamento nel segmento di codice determina in cui verrà creata questa directory modello nella struttura della relazione ad altri elementi del nodo dell'albero. Per il **Aggiungi nuovo elemento** la finestra di dialogo, la priorità di ordinamento è tutto ciò che è necessario includere in modo che gli elementi verranno visualizzati nella posizione corretta nella finestra di dialogo.  
  
 È anche possibile implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> filtrare quanto visualizzato nell'interfaccia di **Aggiungi nuovo elemento** la finestra di dialogo. Implementando questa interfaccia, è possibile impostare un modello di directory sul disco che contiene, ad esempio 50 file di modello e procedura guidata. In tal modo, è possibile disporre di diversi tipi di progetto con 20 file che appartengono a un tipo di progetto, gli altri 30 file che appartengono a un altro tipo di progetto e tutti i file disponibili in un tipo generale del progetto. In questo modo, a seconda di quale progetto modello è stato creato, è possibile visualizzare un set diverso di file di modello.  
  
 Ad esempio, in un progetto di Visual Basic, potrebbe essere progetti Web e client. Web Form non sono elementi utili per aggiungere un progetto di client e windows form non sono elementi utili per aggiungere a un progetto di server Web. Pertanto, è possibile creare una directory di modello che contiene tutti i file per entrambi i tipi di progetto. Quindi implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, è possibile nascondere gli elementi che non devono essere visualizzati in base al tipo di progetto o le impostazioni di progetto nel progetto.  
  
## <a name="filtering-project-items"></a>Filtraggio degli elementi di progetto  
 `IVsFilterAddProjectItemDlg2` sono disponibili per il filtro di elementi nella struttura ad albero (riquadro a sinistra) e i file di progetto (riquadro a destra) nei modi seguenti:  
  
-   Per i nomi localizzati (didascalie visualizzate nella finestra di dialogo che è contenuto nel file VSDIR) fornita dal `IVsFilterAddProjectItemDlg`.  
  
-   Per i nomi effettivi dei file e cartelle su disco (non localizzato: nessun file VSDIR) forniti da `IVsFilterAddProjectItemDlg`.  
  
-   Per categoria, fornito da `IVsFilterAddProjectItemDlg2`.  
  
 Per filtrare in base alla categoria, specificare una stringa di categoria a un elemento nel file VSDIR, ad esempio "Web form" o "Elemento Client" in Visual Basic. Il codice di finestra di dialogo quindi recupera la classificazione di categoria nel file VSDIR e lo passa all'utente. È quindi possibile passare tali informazioni per l'implementazione di `IVsFilterAddProjectItemDlg2` per filtrare il **Aggiungi nuovo elemento** la finestra di dialogo per le categorie. È inoltre possibile filtrare gli elementi per le pagine Web o come casi di applicazioni client Win32. Inoltre, è possibile identificare [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] contrassegnare gli elementi come Microsoft Foundation Classes (MFC) o gli elementi di modello attivo library (ATL). Quando si rileva questi elementi, il sistema di progetto può definire i proprio classificazioni in modo che il sistema può essere filtrato in base alle categorie e le classificazioni.  
  
 Se si implementa questa funzionalità di filtro, non è necessario eseguire il mapping di una tabella di ogni elemento che deve essere nascosto. È possibile semplicemente classificare gli elementi in tipi e le classificazioni nel file VSDIR o file. È quindi possibile nascondere tutti gli elementi che hanno una specifica classificazione implementando l'interfaccia. In questo modo, è possibile rendere gli elementi di **Aggiungi nuovo elemento** della finestra di dialogo dinamico in base allo stato all'interno del progetto.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATID per gli oggetti che vengono in genere utilizzati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Descrizione del modello Directory (. File VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)