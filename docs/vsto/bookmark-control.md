---
title: Bookmark (controllo) | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 38e3286d24f0591ca4ced3339118b6d0d4bfe1d7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="bookmark-control"></a>Bookmark (controllo)
  Il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> è un segnalibro con un nome univoco che espone gli eventi e può essere associato ai dati. Può essere usato come segnaposto per contrassegnare un elemento o una posizione in un documento di Microsoft Office Word. Il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> è una combinazione degli oggetti <xref:Microsoft.Office.Interop.Word.Bookmark> e <xref:Microsoft.Office.Interop.Word.Range> .  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Nei progetti a livello di documento è possibile aggiungere i controlli <xref:Microsoft.Office.Tools.Word.Bookmark> al documento in fase di progettazione o di esecuzione. Nei progetti di componente aggiuntivo VSTO è possibile aggiungere i controlli <xref:Microsoft.Office.Tools.Word.Bookmark> a qualsiasi documento aperto in fase di esecuzione. Per altre informazioni, vedere [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
## <a name="binding-data-to-the-control"></a>Data binding al controllo  
 Un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> supporta un data binding semplice. Il segnalibro deve essere associato a un'origine dati usando la proprietà <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> . La proprietà di data binding predefinita del segnalibro è <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> .  
  
 Se i dati nel set di dati associato vengono aggiornati, il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> riflette tali modifiche.  
  
 Nei progetti a livello di documento è anche possibile associare i dati ai segnalibri usando la finestra **Origini dati** . Per altre informazioni, vedere [How to: Populate Documents with Data from Objects](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
## <a name="formatting"></a>Formattazione  
 La formattazione applicabile a <xref:Microsoft.Office.Interop.Word.Bookmark> può essere applicata anche a un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> . Sono inclusi tipi di carattere, rientri, spaziatura, numerazione e stili.  
  
## <a name="assigning-text-to-the-bookmark"></a>Assegnazione di testo al segnalibro  
 Un'altra differenza tra un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> e un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> riguarda il comportamento tenuto quando viene assegnato un testo al segnalibro. Se si assegna un testo a un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark>di lunghezza zero, il testo viene aggiunto alla destra del segnalibro e il segnalibro resta di lunghezza zero. Tuttavia, se si assegna un testo a un controllo <xref:Microsoft.Office.Tools.Word.Bookmark>di lunghezza zero, il testo viene inserito nel segnalibro e la lunghezza del segnalibro aumenta per il numero totale di caratteri inseriti.  
  
 Il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> ha anche la proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> , che è diversa dalla proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A> disponibile nella proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Range%2A> di un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> o nella proprietà <xref:Microsoft.Office.Interop.Word.Bookmark.Range%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> .  
  
|Proprietà Text|Descrizione|  
|-------------------|-----------------|  
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>|Usare questa proprietà per visualizzare un testo nel segnalibro e lasciare il segnalibro nel documento. L'assegnazione di un testo al segnalibro espande l'intervallo del segnalibro senza eliminarlo.<br /><br /> Ad esempio, `Bookmark1.Text = "Hello world"` inserisce il testo nel segnalibro e lascia intatto il segnalibro.|  
|<xref:Microsoft.Office.Interop.Word.Range.Text%2A>|Usare questa proprietà per visualizzare il testo in corrispondenza del segnalibro ed eliminare automaticamente il segnalibro. Ad esempio, `Bookmark1.Range.Text = "Hello world"` inserisce il testo nel segnalibro ed elimina il segnalibro.|  
  
## <a name="renaming-the-control-at-design-time"></a>Ridenominazione del controllo in fase di progettazione  
 Nei progetti a livello di documento, quando si trascina un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> dalla **casella degli strumenti** al documento, Visual Studio genera automaticamente un nome per il controllo, che può essere modificato nella finestra **Proprietà** .  
  
## <a name="overlapping-controls"></a>Sovrapposizione di controlli  
 I controlli Bookmark possono sovrapporsi, ossia lo stesso testo può essere condiviso da più segnalibri. Quando si assegna un nuovo testo a uno dei segnalibri sovrapposti, questo conterrà solo il nuovo testo e la sovrapposizione verrà eliminata. L'altro segnalibro conterrà solo il testo non condiviso tra i segnalibri precedentemente sovrapposti.  
  
 La tabella seguente mostra in che modo la frase "This is sample text." viene condivisa tra due segnalibri sovrapposti.  
  
|Segnalibro|Testo|  
|--------------|----------|  
|Segnalibri sovrapposti|[this is {sample] text.}|  
|Segnalibro1|This is sample|  
|Segnalibro2|sample text.|  
  
 Se si assegna il nuovo testo "This is replacement." al Segnalibro1, i segnalibri non saranno più sovrapposti e il Segnalibro2 visualizzerà solo il testo non contenuto in origine dal Segnalibro1.  
  
|Segnalibro|Testo|  
|--------------|----------|  
|Due segnalibri separati|[this is replacement]{ text.}|  
|Segnalibro1|This is replacement|  
|Segnalibro2|text.|  
  
 Se un segnalibro è contenuto completamente in un altro segnalibro e si modifica il testo del segnalibro esterno, quello interno non viene eliminato. Tuttavia, il segnalibro interno diventa un segnalibro vuoto e viene spostato alla fine del segnalibro esterno. La tabella seguente mostra in che modo la frase "This is sample text." viene condivisa da un segnalibro contenuto in un altro segnalibro.  
  
|Segnalibro|Testo|  
|--------------|----------|  
|Segnalibri sovrapposti|[this is {sample} text.]|  
|Segnalibro1|This is sample text.|  
|Segnalibro2|esempio|  
  
 Se si assegna il nuovo testo "This is replacement." al Segnalibro1, i segnalibri non sono più sovrapposti e il Segnalibro2 diventa un segnalibro vuoto posizionato alla fine del Segnalibro1.  
  
|Segnalibro|Testo|  
|--------------|----------|  
|Due segnalibri separati|[this is replacement.]{}|  
|Segnalibro1|This is replacement.|  
|Segnalibro2|*\<vuota >*|  
  
## <a name="events"></a>Eventi  
 Gli eventi seguenti sono disponibili per il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> :  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>  
  
## <a name="see-also"></a>Vedere anche  
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Procedura dettagliata: Creazione di menu di scelta rapida per segnalibri](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Associazione dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  