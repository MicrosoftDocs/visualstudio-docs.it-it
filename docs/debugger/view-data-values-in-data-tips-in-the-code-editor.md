---
title: Visualizzare i valori dei dati nei suggerimenti dati nell'editor di codice | Documenti Microsoft
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 178bd1768474eaaaf760e2ef4feecfe0e1519bee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Visualizza i valori dei dati nei suggerimenti dati nell'editor di codice
I suggerimenti dati sono un modo pratico per visualizzare le informazioni sulle variabili nel programma durante il debug. I suggerimenti dati funzionano solo in modalità di interruzione e solo con variabili che si trovano nell'ambito di esecuzione corrente.
  
### <a name="to-display-a-datatip"></a>Per visualizzare un suggerimento dati  
  
1. Impostare un punto di interruzione e avviare il debug (premere **F5**).

2. Se la pausa nel debugger, posizionare il puntatore del mouse su qualsiasi variabile nell'ambito corrente.
  
     Viene visualizzato un suggerimento dati.
  
3.  Il suggerimento dati scompare quando si rimuove il puntatore del mouse. Per bloccare il suggerimento dati in modo che resti aperta, fare clic su di **blocca a origine** , sull'icona o sul pulsante destro del mouse su una variabile, quindi fare clic su **blocca a origine**.

    ![Aggiunta di un suggerimento dati](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

    > [!NOTE]
    > I suggerimenti dati vengono sempre valutati nel contesto in cui l'esecuzione viene sospesa, non nel punto in cui passa il cursore. Se si passa il puntatore su una variabile in un'altra funzione con lo stesso nome di una variabile presente nel contesto corrente, il valore della variabile nell'altra funzione viene visualizzato come valore della variabile nel contesto corrente.
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Per sbloccare un suggerimento dati e far sì che scorra  
  
-   In un suggerimento dati bloccato fare clic su di **Sblocca da origine** icona.  
  
     L'icona di blocco passa alla posizione sbloccata. Il suggerimento dati scorre ora nella parte superiore delle finestre aperte. Il suggerimento dati mobile verrà chiuso al termine della sessione di debug.  
  
### <a name="to-repin-a-floating-datatip"></a>Per ribloccare un suggerimento dati mobile  
  
-   In un suggerimento dati fare clic sull'icona di blocco.  
  
     L'icona passa alla posizione bloccata. Se il suggerimento dati è al di fuori di una finestra di origine, l'icona di blocco è disabilitata e il suggerimento dati non può essere bloccato.  
  
### <a name="to-close-a-datatip"></a>Per chiudere un suggerimento dati  
  
-   Posizionare il puntatore del mouse su un suggerimento dati e quindi fare clic su di **Chiudi** icona.  
  
### <a name="to-close-all-datatips"></a>Per chiudere tutti i suggerimenti dati  
  
-   Nel **Debug** menu, fare clic su **deselezionare tutti i suggerimenti dati**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Per chiudere tutti i suggerimenti dati di un file specifico  
  
-   Nel **Debug** menu, fare clic su **deselezionare tutti i suggerimenti dati bloccati a** *File*.  
  
## <a name="expand-and-edit-information"></a>Espandere e modificare le informazioni  
 È possibile utilizzare i suggerimenti dati per espandere una matrice, una struttura o un oggetto e visualizzarne i membri. È anche possibile modificare il valore di una variabile da un suggerimento dati.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Per espandere una variabile per visualizzarne gli elementi  
  
-   In un suggerimento dati posizionare il puntatore del mouse di  **+**  sign che precede il nome della variabile.  
  
    La variabile si espande per visualizzare i relativi elementi in formato ad albero.

    ![Visualizzare un suggerimento dati](../debugger/media/dbg-tour-data-tips.gif "consente di visualizzare un suggerimento dati")
  
    Quando la variabile è espansa, è possibile utilizzare i tasti di direzione sulla tastiera per spostarsi verso l'alto e verso il basso. In alternativa, è possibile utilizzare il mouse.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Per modificare il valore di una variabile utilizzando un suggerimento dati  
  
1.  In un suggerimento dati, fare clic sul valore. Questa opzione non è disponibile per i valori di sola lettura.  
  
2.  Digitare un nuovo valore e premere INVIO.  
  
## <a name="making-a-datatip-transparent"></a>Rendere trasparente un suggerimento dati  
 Per visualizzare il codice che sta dietro a un suggerimento dati, è possibile renderlo temporaneamente trasparente. Ciò non si applica a suggerimenti dati bloccati o mobili.  
  
#### <a name="to-make-a-datatip-transparent"></a>Per rendere trasparente un suggerimento dati  
  
-   In un suggerimento dati, premere CTRL.  
  
     Il suggerimento dati resterà trasparente finché si terrà premuto il tasto CTRL.  
  
## <a name="visualize-complex-data-types"></a>Visualizzare i tipi di dati complessi  
 Se viene visualizzata un'icona di lente di ingrandimento accanto a un nome di variabile in un suggerimento dati, uno o più [visualizzatori](../debugger/create-custom-visualizers-of-data.md), ad esempio il [stringa visualizzatori](../debugger/string-visualizer-dialog-box.md), sono disponibili per le variabili di quel tipo di dati. È possibile utilizzare un visualizzatore per visualizzare le informazioni in un formato più significativo, generalmente grafico.
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Per visualizzare il contenuto di una variabile utilizzando un visualizzatore  
  
-   Fare clic sull'icona di lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icona Visualizzatore") per selezionare il visualizzatore predefinito per il tipo di dati.  
  
     oppure  
  
     Fare clic sulla freccia popup accanto al visualizzatore per selezionare da un elenco di visualizzatori appropriati per il tipo di dati.  
  
     Un visualizzatore visualizzerà le informazioni.  
  
## <a name="add-information-to-a-watch-window"></a>Aggiungere informazioni a una finestra Espressioni di controllo  
 Se si desidera continuare a controllare una variabile in una visualizzazione elenco, è possibile aggiungere la variabile di **espressioni di controllo** finestra da un suggerimento dati.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Per aggiungere una variabile alla finestra Espressioni di controllo  
  
-   Fare doppio clic su un suggerimento dati e quindi fare clic su **Aggiungi espressione di controllo**.  
  
     La variabile viene aggiunta per il **espressioni di controllo** finestra. Se si utilizza un'edizione che supporta più **espressioni di controllo** windows, la variabile verrà aggiunta a **espressioni di controllo 1.**  
  
## <a name="import-and-export-datatips"></a>Importare ed esportare suggerimenti dati  
 È possibile esportare suggerimenti dati in un file XML, per poi condividerlo con un collega o modificarlo mediante un editor di testo.  
  
#### <a name="to-export-datatips"></a>Per esportare suggerimenti dati  
  
1.  Dal menu Debug, fare clic su **Esporta suggerimenti dati**.  
  
     Il **Esporta suggerimenti dati** viene visualizzata la finestra di dialogo.  
  
2.  Utilizzare tecniche di file standard per passare al percorso in cui si desidera salvare il file XML, digitare un nome per il file di **nome File** casella e quindi fare clic su **OK**.  
  
#### <a name="to-import-datatips"></a>Per importare suggerimenti dati  
  
1.  Dal menu Debug, fare clic su **Importa suggerimenti dati**.  
  
     Il **Importa suggerimenti dati** viene visualizzata la finestra di dialogo.  
  
2.  Utilizzare la finestra di dialogo per trovare il file XML che si desidera aprire e fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione dei dati nel Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Espressioni di controllo e finestre di controllo immediato](../debugger/watch-and-quickwatch-windows.md)   
 [Creazione di visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)   