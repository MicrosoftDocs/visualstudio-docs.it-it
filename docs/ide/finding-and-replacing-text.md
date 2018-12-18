---
title: Ricerca e sostituzione di testo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- find, text
- Find in Files dialog box
- find
- text searches, finding and replacing text
- Replace dialog box
- text, finding and replacing
- find, symbol
- find and replace
- replace
- find text
- replacing text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 72081f6c140c4634918e67098493cb37bb324848
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="finding-and-replacing-text"></a>Finding and Replacing Text
È possibile trovare e sostituire testo nell'editor di codice di Visual Studio e in alcune finestre di output basate su testo, quali le finestre di **Risultati ricerca**, usando il controllo **Trova e sostituisci** o **Find/Replace in Files** (Trova/Sostituisci nei file). È inoltre possibile eseguire la ricerca e sostituzione in alcune finestre di progettazione, quali la finestra di progettazione XAML, Progettazione Windows Form e le finestre degli strumenti  
  
 È possibile definire l'ambito di ricerca per il documento corrente, la soluzione corrente o un set di cartelle personalizzato. È inoltre possibile specificare un set di estensioni di nomi di file per le ricerche su più file. È possibile personalizzare la sintassi di ricerca con espressioni regolari .NET.  
  
 Per le espressioni regolari di ricerca e sostituzione, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
> [!TIP]
>  La casella **Trova/Comando** è ancora disponibile nella barra degli strumenti, ma non è più visibile per impostazione predefinita. È possibile visualizzare la casella **Trova/Comando** scegliendo **Aggiungi o rimuovi pulsanti** nella barra degli strumenti **Standard** e scegliendo **Trova**. Per ulteriori informazioni, vedere [Casella Trova/Comando](../ide/find-command-box.md).  
  
## <a name="find-and-replace-control"></a>Controllo Trova e sostituisci  
 Il controllo **Trova e sostituisci** viene visualizzato nell'angolo superiore destro della finestra dell'editor di codice. Il controllo **Trova e sostituisci** evidenzia immediatamente tutte le occorrenze della stringa di ricerca specificata nel documento corrente. È possibile spostarsi da un'occorrenza all'altra scegliendo il pulsante **Trova successivo** o **Trova precedente** nel controllo di ricerca.  
  
 È possibile accedere alle opzioni di sostituzione scegliendo il pulsante accanto alla casella di testo **Trova**. Per eseguire una sostituzione per volta, scegliere il pulsante **Sostituisci successivo** accanto alla casella di testo **Sostituisci** . Per sostituire tutte le corrispondenze, scegliere il pulsante **Sostituisci tutto**.  
  
 Per modificare il colore di evidenziazione per le corrispondenze, scegliere il menu **Strumenti**, selezionare **Opzioni**, quindi scegliere **Ambiente** e selezionare **Tipi di carattere e colori**. Nell'elenco **Show settings for** (Mostra impostazioni per), selezionare **Editor di testo**, quindi nell'elenco **Elementi visualizzati**, selezionare **Trova evidenziato (estensione)**.  
  
### <a name="searching-tool-windows"></a>Finestre dello strumento di ricerca  
 È possibile utilizzare il controllo **Trova** nelle finestre del codice o del testo, quali le finestre **Output** e le finestre **Risultati ricerca**, scegliendo **Trova e sostituisci** dal menu **Modifica** o (CTRL + F).  
  
 Una versione del controllo di ricerca è disponibile anche in alcune finestre degli strumenti. Ad esempio, è ora possibile filtrare l'elenco di controlli nella finestra **Casella degli strumenti** immettendo il testo nella casella di ricerca. Tra le altre finestre degli strumenti che ora consentono di cercare il relativo contenuto sono incluse **Esplora soluzioni**, **Proprietà** e **Team Explorer**.  
  
## <a name="findreplace-in-files"></a>Ricerca/sostituzione nei file  
 **Find/Replace in Files** (Trova/Sostituisci nei file) funziona come il controllo **Trova e sostituisci**, con la differenza che è possibile definire un ambito per la ricerca. Non solo è possibile cercare il file aperto corrente nell'editor, ma anche tutti i documenti aperti, l'intera soluzione, il progetto corrente e gli insiemi di cartelle selezionati. È inoltre possibile eseguire la ricerca in base all'estensione del nome file. Per accedere alla finestra di dialogo **Find/Replace in Files** (Trova/Sostituisci nei file) scegliere **Trova e sostituisci** dal menu **Modifica** (o CTRL + MAIUSC + F).  
  
 Quando si sceglie **Find All**  (Trova tutti), si apre una finestra **Risultati ricerca** che elenca le corrispondenze della ricerca. Selezionando un risultato nell'elenco viene visualizzato il file associato ed evidenziata la corrispondenza. Se il file non è già aperto per la modifica, viene aperto in una scheda di anteprima a destra della finestra scheda. È possibile utilizzare il controllo **Trova** per eseguire la ricerca nell'elenco dei **Risultati ricerca**.  
  
### <a name="creating-custom-search-folder-sets"></a>Creazione di set personalizzati di cartelle di ricerca  
 È possibile definire un ambito di ricerca scegliendo il pulsante **Seleziona cartelle di ricerca** (simile a **...** ) accanto alla casella **Cerca in**. Nella finestra di dialogo **Seleziona cartelle di ricerca**, è possibile specificare un set di cartelle in cui eseguire la ricerca ed è possibile salvare la specifica in modo da poterla riutilizzare successivamente. È possibile specificare le cartelle in un computer remoto solo se è stato eseguito il mapping della relativa unità nel computer locale.  
  
### <a name="creating-custom-component-sets"></a>Creazione di set di componenti personalizzati  
 È possibile definire set di componenti nell'ambito di ricerca scegliendo il pulsante **Modifica insieme di componenti personalizzato** accanto alla casella **Cerca in**. È possibile specificare i componenti .NET o COM installati, i progetti Visual Studio che sono inclusi nella soluzione, o qualunque assembly o libreria dei tipi (.dll, .tlb, .olb, .exe o .ocx). Per individuare i riferimenti, selezionare la casella **Cerca in riferimenti**.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)