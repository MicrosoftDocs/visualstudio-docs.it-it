---
title: 'Procedura: cercare un messaggio nella visualizzazione dei messaggi | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: df8fc9ee13a721f98a942a3bb6d10f6c8d844ddf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Procedura: cercare un thread nella visualizzazione messaggi
È possibile cercare un messaggio specifico nella visualizzazione dei messaggi tramite il relativo handle, un tipo o un ID messaggio come criterio di ricerca. Uno di questi, o una combinazione, saranno i criteri di ricerca valido. Inoltre possibile specificare la direzione iniziale della ricerca. I campi nella finestra di dialogo vengono precaricati con gli attributi del messaggio attualmente selezionato.  
  
### <a name="to-search-for-a-message-in-messages-view"></a>Per cercare un messaggio nella visualizzazione messaggi  
  
1.  Disporre le finestre in modo che Spy + + e attivo [visualizzazione messaggi](../debugger/messages-view.md) finestra sono visibili.  
  
2.  Dal **ricerca** menu, scegliere **Trova messaggio**.  
  
     Il [dialogo Ricerca messaggi](../debugger/message-search-dialog-box.md) apre.  
  
3.  Trascinare il **strumento di ricerca** sopra la finestra desiderata. Quando si trascina, lo strumento di **ricerca messaggi** la finestra di dialogo vengono visualizzati i dettagli sulla finestra selezionata.  
  
     - oppure -  
  
     Se si dispone di handle della finestra di cui si desidera esaminare i messaggi, digitarla nella **gestire** casella di testo.  
  
     - oppure -  
  
     Se si conosce il tipo di messaggio e/o ID messaggio desiderati, selezionarli il **tipo** e **messaggio** menu a discesa e deselezionare il **gestire** casella di testo.  
  
4.  Deselezionare tutti i campi per cui non si desidera specificare i valori.  
  
    > [!TIP]
    >  Per evitare confusione, selezionare il **Nascondi Spy + +** opzione. Questa opzione consente di nascondere la finestra principale di Spy + + e di mantenere solo il **Trova finestra** la finestra di dialogo di primo piano rispetto alle altre applicazioni. La finestra principale di Spy + + viene ripristinata quando si fa clic **OK** o **Annulla**, o quando si cancella il **Nascondi Spy + +** opzione.  
  
5.  Scegliere **backup** o **verso il basso** per la direzione iniziale della ricerca.  
  
6.  Fare clic su **OK**.  
  
 Se viene trovato un messaggio corrispondente, questo viene evidenziato nella finestra di visualizzazione di messaggi. Vedere [la visualizzazione messaggi](../debugger/messages-view.md).