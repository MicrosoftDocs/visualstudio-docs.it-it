---
title: Supporta più viste documento | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 78ddc7ed811086622454e31d12ca5f1324d00da5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="supporting-multiple-document-views"></a>Supporta più viste di documento
È possibile fornire più di una visualizzazione di un documento mediante la creazione di dati del documento separata e gli oggetti di visualizzazione di documento per l'editor. Alcuni casi in cui sarebbe utile una visualizzazione di documenti aggiuntive sono:  
  
-   Nuovo supporto di finestre: desiderato nell'editor per fornire due o più viste dello stesso tipo, in modo che un utente che dispone già di una finestra aprire nell'editor è possibile aprire una nuova finestra selezionando il **nuova finestra** comando il **finestra** menu.  
  
-   Modulo e il codice consente di visualizzare il supporto: si desidera l'editor per fornire visualizzazioni di tipi diversi. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], ad esempio, fornisce una visualizzazione form e una visualizzazione di codice.  
  
 Per ulteriori informazioni, vedere la procedura CreateEditorInstance nel file EditorFactory.cs nel progetto editor personalizzato creato per il modello di pacchetto di Visual Studio. Per ulteriori informazioni su questo progetto, vedere [procedura dettagliata: creazione di un Editor personalizzato](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## <a name="synchronizing-views"></a>La sincronizzazione delle visualizzazioni  
 Quando si implementano più viste, l'oggetto dati del documento è responsabile di mantenere tutte le visualizzazioni sincronizzate con i dati. È possibile utilizzare le interfacce in di gestione degli eventi <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> per sincronizzare più viste con i dati.  
  
 Se non si utilizza il <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> per sincronizzare più viste, è necessario implementare proprio sistema di eventi per gestire le modifiche apportate all'oggetto dati di documento. È possibile utilizzare diversi livelli di granularità per mantenere aggiornati più viste. Con un'impostazione di granularità massima, durante la digitazione in una vista altre visualizzazioni vengono aggiornati immediatamente. Con una granularità di minima, altre visualizzazioni non vengono aggiornati finché non vengono attivati.  
  
## <a name="determining-whether-document-data-is-already-open"></a>Determinare se i dati di documento è già aperta  
 La tabella document (RDT) in esecuzione nell'ambiente di sviluppo integrato (IDE) consente di verificare se i dati per un documento sono già aperti, come illustrato nel diagramma seguente.  
  
 ![Immagine di DocDataView](../extensibility/media/docdataview.gif "Docdataview")  
Visualizzazioni multiple  
  
 Per impostazione predefinita, ogni vista (oggetto visualizzazione del documento) è contenuta nella cornice di finestra (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>). Come già indicato, tuttavia, i dati di documento possono essere visualizzati in visualizzazioni multiple. A tale scopo, Visual Studio controlla il RDT per determinare se il documento in questione è già aperto in un editor. Quando l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> per creare l'editor, un valore non NULL restituito nel `punkDocDataExisting` parametro indica che il documento è già aperto in un altro editor. Per altre informazioni su come le funzioni RDT, vedere [tabella documenti in esecuzione](../extensibility/internals/running-document-table.md).  
  
 Nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> implementazione, esaminare l'oggetto dati del documento restituito in `punkDocDataExisting` per determinare se i dati del documento sono appropriati per l'editor. (Ad esempio, solo i dati HTML devono essere visualizzati da un editor HTML.) Se appropriato, il factory editor deve fornire una seconda vista per i dati. Se il `punkDocDataExisting` parametro non è `NULL`, è possibile che l'oggetto dati del documento è aperto in un altro editor, o, più probabile, che i dati del documento sono già aperti in una vista diversa con lo stesso, l'editor. Se i dati del documento sono aperti in un altro editor che non supporta il factory editor, Visual Studio non riesce aprire il factory editor. Per ulteriori informazioni, vedere [procedura: collegare le visualizzazioni di dati del documento](../extensibility/how-to-attach-views-to-document-data.md).