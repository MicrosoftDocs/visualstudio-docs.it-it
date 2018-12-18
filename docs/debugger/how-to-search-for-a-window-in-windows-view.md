---
title: 'Procedura: ricerca di una finestra nella visualizzazione di Windows | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4333a79e76358216ce87697975dcb54173570534
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Procedura: cercare una finestra nella visualizzazione finestre
È possibile cercare una finestra specifica nella visualizzazione di Windows utilizzando il relativo handle, didascalia, classe o una combinazione di titolo e classe come criterio di ricerca. È inoltre possibile specificare la direzione iniziale della ricerca. I campi nella finestra di dialogo verranno visualizzati gli attributi della finestra selezionata nell'albero della finestra.  
  
 Iniziare con la struttura ad albero espansa al secondo livello (tutte le finestre sono figli del desktop), in modo che sia possibile identificare desktop a livello di windows per il proprio nome di classe e un titolo. Dopo aver scelto una finestra di livello desktop, è possibile espandere tale livello per trovare una finestra figlio specifico.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Per cercare una finestra nella visualizzazione finestre  
  
1.  Disporre le finestre in modo che Spy + +, il [Windows Vista](../debugger/windows-view.md) finestra e finestra di destinazione sono visibili.  
  
2.  Dal **ricerca** menu, scegliere **Trova finestra**.  
  
     Il [finestra di dialogo ricerca](../debugger/window-search-dialog-box.md) apre.  
  
    > [!TIP]
    >  Per evitare confusione, selezionare il **Nascondi Spy + +** opzione. Questa opzione consente di nascondere la finestra principale di Spy + + e di lasciare solo il **ricerca finestre** la finestra di dialogo di primo piano rispetto alle altre applicazioni. La finestra principale di Spy + + viene ripristinata quando si fa clic **OK** o **Annulla**, o quando si cancella il **Nascondi Spy + +** opzione.  
  
3.  Trascinare il **strumento di ricerca** sulla finestra di destinazione. Quando si trascina, lo strumento di **ricerca finestre** la finestra di dialogo vengono visualizzati i dettagli sulla finestra selezionata.  
  
     - oppure -  
  
     Se si conosce l'handle della finestra di cui si desidera (ad esempio, dal debugger), è possibile digitare nel **gestire** casella.  
  
     - oppure -  
  
     Se si conosce il titolo e/o classe della finestra di cui si desidera, è possibile digitarli nel **didascalia** e **classe** caselle di testo e deselezionare il **gestire** casella di testo.  
  
4.  Scegliere **backup** o **verso il basso** per la direzione iniziale della ricerca.  
  
5.  Fare clic su **OK**.  
  
     Se la finestra corrispondente viene trovata, viene evidenziato nel [Windows Vista](../debugger/windows-view.md) finestra.