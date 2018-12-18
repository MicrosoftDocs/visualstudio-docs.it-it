---
title: 'Procedura: implementare i marcatori di errore | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f1360f88dba797f96af766f65c9ee41abd6fc808
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-implement-error-markers"></a>Procedura: implementare i marcatori di errore
Marcatori di errore (o una sottolineatura ondulata di colore rossa) è più difficili le personalizzazioni di editor di testo per implementare. Tuttavia, i vantaggi che offrono agli utenti di un VSPackage possono superano di gran lunga il costo per fornire loro. Marcatori di errore contrassegnare leggermente il testo che il parser del linguaggio considera non corretto con una riga rossa ondulata o ondulata di colore. Questo indicatore consente ai programmatori visualizzando visivamente il codice non corretto.  
  
 Utilizzare gli indicatori di testo per implementare la sottolineatura ondulata di colore rossa. Come regola, servizi di linguaggio aggiungere ondulata di colore rosso per il buffer di testo come un passaggio di sfondo, a tempo di inattività o in un thread in background.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Per implementare la funzionalità di sottolineatura ondulata rossa  
  
1.  Selezionare il testo in cui si desidera posizionare la sottolineatura ondulata di colore rossa.  
  
2.  Creare un indicatore del tipo `MARKER_CODESENSE_ERROR`. Per ulteriori informazioni, vedere [procedura: aggiungere marcatori di testo Standard](../extensibility/how-to-add-standard-text-markers.md).  
  
3.  Successivamente, passare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> puntatore a interfaccia.  
  
 Questo processo consente inoltre di creare un menu di scelta rapida speciale o di testo del suggerimento su un marcatore specificato. Per ulteriori informazioni, vedere [procedura: aggiungere marcatori di testo Standard](../extensibility/how-to-add-standard-text-markers.md).  
  
 Gli oggetti seguenti sono necessari prima di visualizzare i marcatori di errore.  
  
-   Parser.  
  
-   Un provider di attività (ovvero, un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>) che mantiene un record delle modifiche nelle informazioni di riga per identificare le righe di nuovo l'analisi.  
  
-   Un filtro di visualizzazione di testo per l'acquisizione del punto di inserimento degli eventi di modifica dalla visualizzazione utilizzando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) metodo.  
  
 Il parser, provider di attività e filtro forniscono l'infrastruttura necessaria consentire i marcatori di errore. La procedura seguente illustra il processo per la visualizzazione di marcatori di errore.  
  
1.  In una vista che viene filtrata, il filtro Ottiene un puntatore per il provider di attività associato ai dati della visualizzazione.  
  
    > [!NOTE]
    >  È possibile utilizzare lo stesso filtro di comando per i suggerimenti di metodo, il completamento delle istruzioni, i marcatori di errore e così via.  
  
2.  Quando il filtro riceve un evento che indica che è stato spostato in un'altra riga, viene creata un'attività per verificare la presenza di errori.  
  
3.  Il gestore di attività verifica se la riga è dirty. In questo caso, viene analizzata la riga per gli errori.  
  
4.  Se vengono rilevati errori, il provider di attività crea un'istanza elemento di attività. Questa istanza viene creata l'indicatore di testo che l'ambiente viene utilizzato come un indicatore di errore nella visualizzazione di testo.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo degli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Procedura: aggiungere testo Standard marcatori](../extensibility/how-to-add-standard-text-markers.md)   
 [Procedura: creare marcatori di testo personalizzato](../extensibility/how-to-create-custom-text-markers.md)   
 [Procedura: utilizzare gli indicatori di testo](../extensibility/how-to-use-text-markers.md)