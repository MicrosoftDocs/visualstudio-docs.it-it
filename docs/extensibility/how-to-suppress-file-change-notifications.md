---
title: 'Procedura: esclusione di notifiche di cambiamento File | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 95821baec7f2f46a65e2ab0f0b0b78b0e397f2ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-suppress-file-change-notifications"></a>Procedura: eliminare le notifiche di modifica File
Quando è stato modificato il file fisico che rappresenta il buffer di testo, una finestra di dialogo viene visualizzato con il messaggio **si desidera salvare le modifiche apportate ai seguenti elementi?** Questo è noto come notifica di modifica di file. Se prevede molte modifiche a file, tuttavia, questa finestra di dialogo visualizzazione più volte può risultare fastidiosa.  
  
 A livello di codice, è possibile eliminare questa finestra di dialogo mediante la procedura seguente. In questo modo, sarà possibile ricaricare un file immediatamente senza dover richiedere all'utente di salvare le modifiche ogni volta.  
  
### <a name="to-suppress-file-change-notification"></a>Esclusione di notifica di modifica file  
  
1.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodo per determinare quale oggetto buffer di testo è associato il file aperto.  
  
2.  Diretto di <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto monitorato in memoria per ignorare le modifiche ai file ottenendo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> interfaccia dal <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto (dati del documento) e quindi implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metodo con il `fIgnore` parametro Impostare su `true`.  
  
3.  Chiamare i metodi sul <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfacce per aggiornare la memoria in <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto con le modifiche al file (ad esempio, quando si aggiunge un campo per il componente).  
  
4.  Aggiornare il file su disco con le modifiche senza considerare le modifiche, che l'utente potrebbe essere in corso in sospeso.  
  
     In questo modo, quando si indirizzano il <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> notifiche di modifica oggetto per riprendere il monitoraggio per il file, il buffer di testo in memoria riflette le modifiche che è stato generato, nonché tutte le altre modifiche in sospeso. Il file su disco riflette il codice più recente generato dall'utente e salvare le modifiche apportate dall'utente in precedenza nel codice utente ha modificato.  
  
5.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metodo per notificare il <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto per riprendere il monitoraggio per le notifiche di modifica file impostando la `fIgnore` parametro `false`.  
  
6.  Se si intende apportare alcune modifiche al file, come nel caso di controllo del codice sorgente (SCC), è necessario indicare al servizio di modifica file globale di sospendere temporaneamente le notifiche di modifica di file.  
  
     Ad esempio, se si riscrittura il file e quindi modificarla il timestamp, è necessario sospendere le notifiche di modifica di file, come le operazioni di riscrittura e timestample ogni contare come evento di modifica di un file separato. Per abilitare la notifica di cambiamento file globale è necessario chiamare invece il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> metodo.  
  
## <a name="example"></a>Esempio  
 Di seguito viene illustrato come eliminare una notifica di modifica di file.  
  
```cpp  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Se il case comporta più modifiche al file, come nel caso di controllo del codice sorgente, è importante riprendere le notifiche di modifica file globale prima i dati del documento per riprendere il monitoraggio delle modifiche al file di avvisi.