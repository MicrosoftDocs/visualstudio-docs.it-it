---
title: "Procedura: utilizzare il Visualizzatore dell'albero WPF | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 290231b7b700a26945227ba04ddc2e97cdfe4299
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Procedura: Usare il visualizzatore dell'albero di WPF
È possibile utilizzare il visualizzatore dell'albero di WPF per esplorare la struttura ad albero visuale di un oggetto WPF e visualizzare le proprietà di dipendenza WPF per gli oggetti contenuti in tale albero. Per ulteriori informazioni su strutture ad albero visuali, vedere [alberi in WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Per ulteriori informazioni sulle proprietà di dipendenza, vedere [Cenni preliminari sulle proprietà di dipendenza](/dotnet/framework/wpf/advanced/dependency-properties-overview).  
  
 Quando si apre il Visualizzatore dell'albero di WPF, si vedranno due riquadri: il **struttura ad albero visuale** a sinistra e il **delle proprietà del** *nome***:***tipo* riquadro a destra. Selezionare qualsiasi oggetto nel **struttura ad albero visuale** riquadro e il **delle proprietà di** *nome***:***tipo* riquadro viene aggiornato automaticamente per mostrare la proprietà per l'oggetto.  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>Per aprire il visualizzatore dell'albero di WPF  
  
1.  In un suggerimento dati, **espressioni di controllo** finestra **Auto** finestra o **variabili locali** accanto al nome di un oggetto WPF, fare clic sulla freccia accanto all'icona di lente di ingrandimento.  
  
     Verrà visualizzato un elenco di visualizzatori.  
  
2.  Fare clic su **Visualizzatore dell'albero WPF**.  
  
### <a name="to-search-the-visual-tree"></a>Per eseguire ricerche nella struttura ad albero visuale  
  
-   Nel **struttura ad albero visuale** riquadro, digitare la stringa di cui si desidera effettuare la ricerca per il **ricerca** casella.  
  
     Il visualizzatore dell'albero di WPF troverà immediatamente il primo oggetto nella struttura ad albero visuale che corrisponde alla stringa digitata. Digitare più caratteri per trovare una corrispondenza più accurata.  
  
    -   Per passare alla corrispondenza successiva all'interno di struttura ad albero visuale, fare clic su **Avanti**.  
  
    -   Per tornare alla corrispondenza precedente, fare clic su **Prev**.  
  
    -   Per cancellare i criteri di ricerca, fare clic su **deselezionare**.  
  
### <a name="to-search-the-properties-list"></a>Per eseguire ricerche nell'elenco di proprietà  
  
-   Nel **proprietà di** *nome***:***tipo* riquadro, digitare la stringa di cui si desidera effettuare la ricerca per il **filtro** casella.  
  
     Il visualizzatore dell'albero di WPF troverà immediatamente le proprietà che corrispondono alla stringa digitata; nell'elenco sono visualizzate soltanto le proprietà corrispondenti alla stringa digitata. Digitare più caratteri per trovare una corrispondenza più accurata.  
  
    -   Per cancellare i criteri di ricerca, fare clic su **deselezionare**.  
  
### <a name="to-close-the-visualizer"></a>Per chiudere il visualizzatore  
  
-   Fare clic su di **Chiudi** icona nell'angolo superiore destro della finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)   
 [Strutture ad albero in WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)   
 [Panoramica sulle proprietà di dipendenza](/dotnet/framework/wpf/advanced/dependency-properties-overview)