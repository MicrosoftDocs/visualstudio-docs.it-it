---
title: Scheda Generale, finestra di dialogo Proprietà finestra | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f762d935edab5720ccd9add155dac3d0e5f2f186
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="general-tab-window-properties-dialog-box"></a>Scheda Generale, finestra di dialogo Proprietà finestra
Utilizzare il **generale** scheda per visualizzare le informazioni sulla finestra selezionata. Per visualizzare il [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo per il [Windows Vista](../debugger/windows-view.md) finestra. Selezionare qualsiasi nodo finestra nell'albero, quindi scegliere **proprietà** dal **vista** menu.  
  
 Le impostazioni seguenti sono disponibili sul **generale** scheda:  
  
|Voce|Descrizione|  
|-----------|-----------------|  
|**Didascalia della finestra**|Il testo della didascalia della finestra, o contenuti in una finestra, se si tratta di un controllo.|  
|**Handle di finestra**|ID univoco di questa finestra. I numeri degli handle di finestra vengono riutilizzati; una finestra consentono di identificare solo per la durata di tale finestra.|  
|**Procedura di finestra**|L'indirizzo virtuale della funzione di routine della finestra per la finestra. Questo campo indica inoltre se questa finestra è una finestra di Unicode e se è impostata come sottoclasse.|  
|**rettangolo**|Il rettangolo di delimitazione per la finestra. Viene visualizzata anche le dimensioni del rettangolo. Le unità sono i pixel in coordinate dello schermo.|  
|**Rettangolo ripristinato**|Il rettangolo di delimitazione della finestra ripristinata. Viene visualizzata anche le dimensioni del rettangolo. Il rettangolo ripristinato differisce dal rettangolo solo quando la finestra è ingrandita o ridotta. Le unità sono i pixel in coordinate dello schermo.|  
|**Rettangolo client**|Il rettangolo di delimitazione per l'area client della finestra. Viene visualizzata anche le dimensioni del rettangolo. Le unità sono i pixel relativo alla parte superiore sinistra dell'area client della finestra.|  
|**Handle di istanza**|L'handle dell'istanza dell'applicazione. Handle di istanza non sono univoci.|  
|**ID di controllo o Handle di Menu**|Se la finestra viene visualizzata una finestra figlio, viene visualizzata l'etichetta dell'ID di controllo. ID di controllo è un numero intero che identifica l'ID del controllo. della finestra figlio Se la finestra visualizzata non è una finestra figlio, viene visualizzata l'etichetta Menu Handle. Handle di menu è un numero intero che identifica l'handle del menu associato a questa finestra.|  
|**Dati utente**|Dati specifici dell'applicazione associato alla struttura della finestra.|  
|**Byte di finestra**|Il numero di byte aggiuntivi associati a questa finestra. Il significato di questi byte è determinato dall'applicazione. Espandere la casella di riepilogo per visualizzare i valori di byte in formato DWORD.|