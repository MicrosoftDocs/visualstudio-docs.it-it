---
title: "Questo metodo correlato è il metodo sottostante per il seguente predefiniti di inserimento, aggiornamento o eliminazione metodi | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: cb3f6c23d4994346dab26e800c116ad0c7301f4a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione
Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione. Se viene eliminato, verranno eliminati anche questi metodi. Continuare?  
  
 Il metodo `DataContext` selezionato viene usato attualmente come uno dei metodi di inserimento, aggiornamento o eliminazione per una delle classi di entità in Progettazione relazionale oggetti. L'eliminazione del metodo selezionato determinerà, per la classe di entità che lo stava usando, il ripristino del comportamento in fase di esecuzione predefinito per l'esecuzione dei comandi di inserimento, aggiornamento o eliminazione durante un aggiornamento.  
  
### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Per eliminare il metodo selezionato e determinare l'uso degli aggiornamenti in fase di esecuzione da parte della classe di entità  
  
-   Scegliere **Sì**.  
  
     Il metodo selezionato viene eliminato e per tutte le classi che utilizzavano tale metodo per l'override del comportamento di aggiornamento viene ripristinato l'uso del comportamento in fase di esecuzione LINQ to SQL predefinito.  
  
### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Per chiudere la finestra di messaggio e lasciare invariato il metodo selezionato  
  
-   Fare clic su **No**.  
  
     La finestra di messaggio viene chiusa e non vengono apportate modifiche.  
  
## <a name="see-also"></a>Vedere anche
[Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)