---
title: 'Procedura: fornire contesto per gli editor | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d9b89c4e45f8268df55386d321816325fb50174c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-context-for-editors"></a>Procedura: fornire contesto per gli editor
Per un editor, il contesto è attivo solo quando l'editor ha lo stato attivo o lo stato attivo immediatamente prima che lo stato attivo è stato spostato in una finestra degli strumenti. È possibile fornire contesto per un editor effettuando le seguenti operazioni:  
  
1.  Creare un elenco di contesti.  
  
2.  Pubblicare l'elenco di contesti all'identificatore di elemento di selezione (SEID).  
  
3.  Mantenere il contesto nel contenitore.  
  
 Queste attività rientrano nelle procedure riportate di seguito. Per ulteriori informazioni su come fornire contesto, vedere **programmazione efficiente** più avanti in questo argomento.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Per creare un contenitore di contesto per un editor o una finestra di progettazione  
  
1.  Chiamare `QueryService` sul <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaccia per il <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> servizio.  
  
     Un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> interfaccia viene restituita.  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> metodo per creare un nuovo contenitore di contesto o sottocontesto.  
  
     Un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> interfaccia viene restituita.  
  
3.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> per aggiungere gli attributi, le parole chiave di ricerca o le parole chiave F1 all'elenco di contesto o sottocontesto.  
  
4.  Se si sta creando un contenitore sottocontesto, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> metodo a cui collegarsi contenitore sottocontesto contesti padre.  
  
5.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> per ricevere notifiche quando il **Guida dinamica** finestra sta per aggiornare.  
  
     Con il **Guida dinamica** finestra chiamare editor quando è pronto per l'aggiornamento consente di ritardare la modifica del contesto fino a quando non si verifica l'aggiornamento. In questo modo è possibile migliorare le prestazioni poiché consente di ritardare l'esecuzione richiede molto tempo algoritmi fino a quando non è disponibile tempo di inattività del sistema.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Per pubblicare l'elenco di contesti di SEID  
  
1.  Chiamare `QueryService` sul <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> servizio di restituire un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfaccia.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, specificando un identificatore di elemento (`elementid` parametro) valore di SEID_UserContext per indicare che si sta passando contesto a livello globale.  
  
3.  Quando l'editor o la finestra di progettazione diventa attivo, i valori dei relativi <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> oggetto vengono propagati alla selezione globale. È sufficiente completare questo processo una volta per sessione e quindi archiviare il puntatore al contesto globale creato durante la chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.  
  
### <a name="to-maintain-the-context-bag"></a>Per mantenere i contesti  
  
1.  Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> per garantire che il **Guida dinamica** chiamate nella finestra editor o nella finestra di progettazione prima l'aggiornamento.  
  
     Per ogni contenitore di contesto che ha chiamato <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> dopo contesti, viene creato e ha implementato <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, le chiamate IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> per notificare al provider di contesto che saranno aggiornati contesti. È possibile utilizzare questa chiamata per modificare gli attributi e le parole chiave in contesti e in qualsiasi bagagli sottocontesto, prima di **Guida dinamica** si verifica di Windows update.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> in contesti per indicare che l'editor o la finestra di progettazione ha nuovo contesto.  
  
     Quando il **Guida dinamica** chiamate finestra <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> per indicare che effettua l'aggiornamento, l'editor o la finestra di progettazione può aggiornare il contesto in modo appropriato per contesti padre e qualsiasi sacchetti sottocontesto in quel momento.  
  
    > [!NOTE]
    >  Il `SetDirty` flag viene impostato automaticamente su `true` ogni volta che cui contesto viene aggiunto o rimosso dall'elenco di contesto. Il **Guida dinamica** finestra chiama solo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> in contesti se il `SetDirty` flag è impostato su `true`. Viene reimpostato su `false` dopo l'aggiornamento.  
  
3.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> per aggiungere contesto per la raccolta di contesto attivo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> rimuovere contesto.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Se si sta scrivendo un editor personalizzato, è necessario completare tutte e tre le procedure descritte in questo argomento per fornire il contesto per l'editor.  
  
> [!NOTE]
>  Per attivare correttamente una finestra dell'editor o finestra di progettazione e verificare che il routing di comandi è stato aggiornato correttamente, è necessario chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> sul componente per rendere tale finestra lo stato attivo.  
  
 Il SEID è una raccolta di proprietà che cambiano in base alla selezione. SEID informazioni sono disponibili tramite la selezione globale. Gli eventi attivati dai è connessa alla selezione globale di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfaccia, e ha un elenco di tutti gli elementi che è selezionato (editor corrente, finestra degli strumenti corrente, la gerarchia corrente e così via).  
  
 Per gli editor e finestre di progettazione, nel cui contesto può essere modificato ogni volta che il cursore si sposta all'interno di una parola, non è opportuno aggiornare costantemente i contesti. Per facilitare l'aggiornamento più efficiente ogni volta che si rileva il cursore all'interno di editor o nella finestra di progettazione, è possibile chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. Questa operazione consente di mantenere le modifiche di contesto, fino a quando non è il tempo di inattività e il servizio di contesto dell'IDE invia notifica a editor o nella finestra di progettazione che di **Guida dinamica** finestra sta aggiornando. Questo approccio viene utilizzato nella procedura "per mantenere i contesti" in questo argomento.  
  
 Dopo l'inserimento di contesto per le attività all'interno dell'editor o finestra di progettazione, è necessario fornire una parola chiave F1 specifica per consentire agli utenti di visualizzare la Guida di editor o nella finestra di progettazione stessa.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>