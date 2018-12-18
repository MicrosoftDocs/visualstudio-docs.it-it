---
title: 'Procedura: visualizzare le informazioni di traccia WPF | Documenti Microsoft'
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
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3e210d575b17552d7b5e4d6dc126335ff3711ee5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-wpf-trace-information"></a>Procedura: visualizzare le informazioni di traccia WPF
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]può ricevere informazioni di traccia di debug da applicazioni WPF e visualizzare tali informazioni nella **Output** finestra. Per visualizzare le informazioni di traccia di debug, è necessario abilitare la tracciatura WPF.  
  
 È possibile abilitare la tracciatura WPF nel file App.Config o a livello di codice utilizzando la classe <xref:System.Diagnostics.PresentationTraceSources>. Un modo più semplice per abilitare la tracciatura WPF è tramite il **opzioni** finestra. La tracciatura WPF per applicazioni Web non è supportata.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Per abilitare o personalizzare le informazioni di traccia WPF  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nel **opzioni** aprire la finestra di dialogo, nella casella a sinistra di **debug** nodo.  
  
3.  In **debug**, fare clic su **finestra di Output**.  
  
4.  In **impostazioni generali di Output**selezionare **tutto l'output di debug**.  
  
5.  Nella casella sulla destra ricercare **impostazioni di traccia WPF**.  
  
6.  Aprire il **impostazioni di traccia WPF** nodo.  
  
7.  In **impostazioni di traccia WPF**, fare clic sulla categoria di impostazioni che si desidera abilitare (ad esempio, **Data Binding**).  
  
     Un controllo elenco a discesa verrà visualizzato nella colonna Impostazioni accanto ad **Data Binding** o qualsiasi categoria selezionata.  
  
8.  Fare clic sull'elenco a discesa e selezionare il tipo di informazioni di traccia che si desidera visualizzare: **tutti**, **critico**, **errore**, **avviso**,  **Informazioni**, **Verbose**, o **ActivityTracing**.  
  
     **Critico** abilita la tracciatura di solo eventi critici.  
  
     **Errore** abilita la tracciatura di eventi critico ed errore.  
  
     **Avviso** abilita la tracciatura di critico, errore e gli eventi di avviso.  
  
     **Informazioni** abilita la tracciatura di eventi critico, errore, avviso e informazioni.  
  
     **Verbose** abilita la tracciatura di eventi critico, errore, avviso, informazioni e dettagliato.  
  
     **ActivityTracing** abilita la tracciatura di eventi di arresto, avvio, sospensione, trasferimento e Resume.  
  
     Per ulteriori informazioni sul significato di questi livelli di informazioni di traccia, vedere <xref:System.Diagnostics.SourceLevels>.  
  
9. Fare clic su **OK**.  
  
### <a name="to-disable-wpf-trace-information"></a>Per disabilitare le informazioni di traccia WPF  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nel **opzioni** aprire la finestra di dialogo, nella casella a sinistra di **debug** nodo.  
  
3.  In **debug**, fare clic su **finestra di Output**.  
  
4.  Nella casella sulla destra ricercare **impostazioni di traccia WPF**.  
  
5.  Aprire il **impostazioni di traccia WPF** nodo.  
  
6.  In **impostazioni di traccia WPF**, fare clic sulla categoria di impostazioni che si desidera abilitare (ad esempio, **Data Binding**).  
  
     Un controllo elenco a discesa verrà visualizzato nella colonna Impostazioni accanto ad **Data Binding** o qualsiasi categoria selezionata.  
  
7.  Fare clic sull'elenco a discesa e selezionare **Off**.  
  
8.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di WPF](../debugger/debugging-wpf.md)