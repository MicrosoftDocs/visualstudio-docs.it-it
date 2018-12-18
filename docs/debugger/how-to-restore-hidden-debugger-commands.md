---
title: 'Procedura: ripristinare comandi nascosti del Debugger | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
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
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ebd03748a94c13dd80a9f38b0fa11c1c20e7e2eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Procedura: ripristinare comandi nascosti del debugger
Quando si installa Visual Studio, viene chiesto di scegliere una serie di impostazioni IDE predefinite per il linguaggio di programmazione principale. Le impostazioni IDE predefinite per alcuni linguaggi possono nascondere determinati comandi del debugger.  
  
 Se si desidera utilizzare una funzionalità del debugger nascosta dalle impostazioni IDE predefinite, è possibile aggiungere di nuovo il comando al menu come descritto nella procedura riportata di seguito.  
  
### <a name="to-restore-hidden-debugger-commands"></a>Per ripristinare comandi nascosti del debugger  
  
1.  Con un progetto aperto, scegliere il **strumenti** menu, fare clic su **Personalizza**.  
  
2.  Nel **Personalizza** la finestra di dialogo, fare clic sul **comandi** scheda.  
  
3.  Nel **barra dei Menu:** elenco a discesa, selezionare il **Debug** menu che si desidera includere il comando ripristinato.  
  
4.  Fare clic su di **comando Aggiungi...**  pulsante.  
  
5.  Nel **Aggiungi comando** , selezionare il comando che si desidera aggiungere, quindi scegliere **OK**.  
  
6.  Ripetere il passaggio precedente per aggiungere un altro comando.  
  
7.  Fare clic su **Chiudi** quando aver completato l'aggiunta di comandi al menu.  
  
    > [!WARNING]
    >  Alcune voci di menu vengono visualizzate solo quando nel debugger è attivata una particolare modalità, ad esempio la modalità di esecuzione o la modalità di interruzione. Le voci aggiunte potrebbero quindi non essere immediatamente visualizzate al termine di questa procedura.  
  
## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Ripristino di comandi non disponibili nella finestra di dialogo Personalizza  
 Alcuni comandi, in particolare quelli facenti parte di menu gerarchici, non possono essere ripristinati dal **Personalizza** la finestra di dialogo. Per ripristinare tali comandi, è necessario importare una nuova raccolta di impostazioni IDE.  
  
#### <a name="to-import-new-ide-settings"></a>Per importare nuove impostazioni IDE  
  
1.  Nel **strumenti** menu, fare clic su **Importa / Esporta impostazioni**.  
  
2.  Nel **iniziale per l'importazione / esportazione guidata delle impostazioni** pagina, fare clic su **Importa le impostazioni di ambiente selezionate**, quindi fare clic su **Avanti**.  
  
3.  Nel **salvare le impostazioni correnti** pagina, decidere se inviare o meno salvare le impostazioni e quindi fare clic su **Avanti**.  
  
4.  Nel **scegliere una raccolta di impostazioni da importare** nella pagina di **impostazioni predefinite** cartella, scegliere una raccolta di impostazioni di sviluppo contenente i comandi che si desidera utilizzare. Se non si conosce quale insieme di scegliere, provare a **impostazioni generali per lo sviluppo** o **delle impostazioni di sviluppo di Visual C++**, che contengono più comandi del debugger.  
  
5.  Scegliere **Avanti**.  
  
6.  Nel **scegliere le impostazioni da importare** pagina **opzioni**, assicurarsi che **debug** è selezionata. Deselezionare le altre caselle di controllo, a meno che non si desideri importare anche tali impostazioni.  
  
7.  Scegliere **Fine**.  
  
8.  Nel **importazione completa** pagina, esaminare gli eventuali errori associati alla riconfigurazione delle impostazioni in **dettagli**.  
  
9. Fare clic su **Chiudi**.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debugger Basics](../debugger/debugger-basics.md) (Nozioni di base sul debugger)