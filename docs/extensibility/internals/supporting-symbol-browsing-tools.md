---
title: Supporto di strumenti di esplorazione simbolo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 78a4e910dbd2c6063f4bdf7b0dff3f27f79b218e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-symbol-browsing-tools"></a>Supporto di strumenti di esplorazione di simbolo
**Visualizzatore oggetti**, **Visualizzazione classi**, **Visualizzatore chiamate** e **risultati ricerca simbolo** strumenti di forniscono un simbolo di esplorazione delle funzionalità in Visual Studio. Questi strumenti visualizzazioni struttura ad albero gerarchica dei simboli e mostrano le relazioni tra i simboli nella struttura. I simboli possono rappresentare gli spazi dei nomi, gli oggetti, classi, membri della classe e altri elementi del linguaggio contenuti nei vari componenti. I componenti includono i progetti di Visual Studio, esterni [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] componenti e le librerie dei tipi (tlb). Per altre informazioni, vedere [Viewing the Structure of Code](../../ide/viewing-the-structure-of-code.md) (Visualizzazione della struttura del codice).  
  
## <a name="symbol-browsing-libraries"></a>Librerie di simboli per l'esplorazione  
 Come responsabile dell'implementazione lingua, è possibile estendere le funzionalità di Visual Studio per l'esplorazione del simbolo mediante la creazione di librerie di rilevare i simboli nei componenti che forniscono gli elenchi di simboli per il gestore di oggetti di Visual Studio tramite un set di interfacce. Una libreria verrà indicata il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> interfaccia. Gestione degli oggetti di Visual Studio risponde alle richieste per i nuovi dati da strumenti di esplorazione simbolo tramite le librerie per ottenere i dati e l'organizzazione. È successivamente inserisce o aggiorna gli strumenti con i dati richiesti. Per ottenere un riferimento al gestore di oggetti di Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, passare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> ID al servizio di `GetService` metodo.  
  
 Ogni libreria è necessario registrare con il gestore di oggetti di Visual Studio, che raccoglie le informazioni su tutte le librerie. Per registrare una libreria, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodo. A seconda dello strumento avvia la richiesta, il gestore di oggetti di Visual Studio consente di trovare la libreria appropriata e richiede i dati. I dati trasmessi tra le librerie e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di gestione degli oggetti negli elenchi dei simboli descritti dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfaccia.  
  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di gestione degli oggetti è responsabile per aggiornare periodicamente gli strumenti per l'esplorazione del simbolo per riflettere i dati più recenti delle librerie di contenuto.  
  
 Nel diagramma seguente è incluso un esempio di elementi chiave del processo di exchange/richiede i dati tra una libreria e la gestione di oggetti di Visual Studio. Le interfacce nel diagramma sono parte di un'applicazione in codice gestito.  
  
 ![Flusso di dati tra una libreria e la gestione degli oggetti](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Per fornire gli elenchi di simboli per il gestore di oggetti di Visual Studio, è prima necessario registrare la libreria con il gestore di oggetti di Visual Studio chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodo. Dopo aver registrata la libreria, il gestore di oggetti di Visual Studio richiede alcune informazioni sulle funzionalità della libreria. Ad esempio, richiede i flag di libreria e supportati categorie chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> metodi. A un certo punto, quando uno degli strumenti richiede dati da questa raccolta, il gestore di oggetti richiede l'elenco principale di simboli chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> metodo. In risposta, la libreria produce un elenco di simboli e lo espone al gestore di oggetti di Visual Studio tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfaccia. Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] manager oggetto determina il numero di elementi presenti nell'elenco chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> metodo. Tutte le richieste seguenti si riferiscono a un determinato elemento nell'elenco e specificare il numero di indice di elemento in ogni richiesta. Gestione degli oggetti di Visual Studio continua a raccogliere le informazioni sul tipo, l'accessibilità e altre proprietà dell'elemento chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> metodo.  
  
 Determina il nome dell'elemento chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> metodo e richiede le informazioni di icona chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> metodo. L'icona è visualizzata a sinistra del nome dell'elemento e illustra il tipo di elemento, l'accessibilità e altre proprietà.  
  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] object manager chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> metodo per determinare se un elemento di elenco specificato espandibile con elementi figlio. Se l'interfaccia utente invia una richiesta per espandere un elemento, il gestore di oggetti richiede elenco figlio di simboli chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> metodo. Il processo prosegue con le parti diverse della struttura ad albero viene compilato su richiesta.  
  
> [!NOTE]
>  Per implementare un provider di simboli di codice nativo, utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> interfacce.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: registrare una libreria con il gestore oggetti](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Procedura: esporre elenchi dei simboli forniti dalla libreria per la gestione di oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Procedura: Identificare i simboli in una libreria](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)