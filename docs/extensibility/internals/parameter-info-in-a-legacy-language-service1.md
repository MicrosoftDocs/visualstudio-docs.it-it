---
title: Informazioni sul parametro in un Service1 Language Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50450d1968c626e0a5b32dee4c6f03d005d6ede9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informazioni sul parametro in un servizio di linguaggio Legacy
La descrizione comando informazioni sul parametro IntelliSense fornisce agli utenti suggerimenti su dove si trovano in un costrutto di linguaggio.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori dettagli, vedere [estensione dell'Editor e i servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a usare il nuovo editor di API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="how-parameter-info-tooltips-work"></a>Funzionamento di descrizione comandi per informazioni di parametro  
 Quando si digita un'istruzione nell'editor, il pacchetto VSPackage Visualizza una finestra di descrizione comando di piccole dimensioni contenente la definizione dell'istruzione vengono digitato. Ad esempio, se si digita un'istruzione di Microsoft Foundation Classes (MFC) (ad esempio `pMainFrame ->UpdateWindow`) e premere un tasto della parentesi di apertura per iniziare a elencare i parametri, viene visualizzato un suggerimento di metodo la definizione del `UpdateWindow` metodo.  
  
 Descrizione comandi per informazioni di parametro vengono normalmente utilizzati in combinazione con il completamento delle istruzioni. Sono utili per le lingue che dispongono di parametri o altre informazioni formattate dopo la parola chiave o il nome del metodo.  
  
 Le descrizioni comandi informazioni sul parametro vengono avviate dal servizio di linguaggio tramite l'intercettazione di comando. Per intercettare i caratteri di utente, è necessario implementare l'oggetto servizio di linguaggio il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia e passare alla visualizzazione di testo di un puntatore al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementazione, chiamando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia. Il filtro dei comandi intercetta i comandi digitati nella finestra del codice. Monitorare le informazioni di comando per sapere quando visualizzare informazioni sui parametri per l'utente. È possibile utilizzare lo stesso filtro di comando per il completamento delle istruzioni, i marcatori di errore e così via.  
  
 Quando si digita una parola chiave per cui il servizio di linguaggio consente di fornire suggerimenti, il servizio di linguaggio crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> e viene chiamato il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia per notificare l'IDE per visualizzare un suggerimento. Creare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> utilizzando `VSLocalCreateInstance` e specificando la coclasse `CLSID_VsMethodTipWindow`. `VsLocalCreateInstance` è una funzione definita nel vsdoc.h di file di intestazione che chiama `QueryService` per il Registro di sistema locale e chiama `CreateInstance` su questo oggetto per il `CLSID_VsMethodTipWindow`.  
  
## <a name="providing-a-method-tip"></a>Fornire un suggerimento (metodo)  
 Per fornire un suggerimento sul metodo, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> interfaccia, passando l'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaccia.  
  
 Quando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> classe viene richiamata, i metodi vengono chiamati nell'ordine seguente:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Restituisce la posizione e la lunghezza dei dati nel buffer di testo corrente. Questo indica l'IDE non poco che i dati con la finestra di descrizione comandi.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Restituisce il numero di metodo (indice in base zero), che si dovrà essere visualizzato inizialmente. Ad esempio, se si restituisce zero, quindi il primo metodo di overload è inizialmente visualizzato.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Restituisce il numero di metodi di overload che sono applicabili nel contesto corrente. Se si restituisce un valore maggiore di 1 per questo metodo, quindi la visualizzazione del testo vengono visualizzate frecce su e giù per l'utente. Se si fa clic sulla freccia rivolta verso il basso, l'IDE chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> metodo. Se si fa clic sulla freccia in su, l'IDE chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> metodo.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Il testo della descrizione comando informazioni sul parametro è stato costruito durante diverse chiamate al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> metodi.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Restituisce il numero di parametri da visualizzare nel metodo.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Se viene restituito un numero di metodo corrispondente con l'overload che si desidera visualizzare, questo metodo viene chiamato, seguita da una chiamata al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metodo.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informa il servizio di linguaggio per aggiornare l'editor quando viene visualizzato un suggerimento di metodo. Nel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metodo, chiamare le operazioni seguenti:  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Si riceve una chiamata al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metodo quando si chiude la finestra di suggerimento di metodo.