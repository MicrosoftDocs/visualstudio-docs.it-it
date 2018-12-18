---
title: "Scheda classe, finestra di dialogo Proprietà finestra | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cb10cf8a571d37f27244398e6c957c46cee87f8b
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
---
# <a name="class-tab-window-properties-dialog-box"></a>Scheda Classe, finestra di dialogo Proprietà finestra
Utilizzare il **classe** scheda per visualizzare informazioni sulla classe della finestra selezionata. Per visualizzare il [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo per il [Windows Vista](../debugger/windows-view.md) finestra. Selezionare qualsiasi nodo finestra nell'albero, quindi scegliere **proprietà** dal **vista** menu.  
  
 Le impostazioni seguenti sono disponibili sul **classe** scheda:  
  
|Voce|Descrizione|  
|-----------|-----------------|  
|**Nome di classe**|Il nome (o numero ordinale) di questa classe di finestra.|  
|**Stili di classe**|Una combinazione di codici di stile di classe.|  
|**Classe byte**|Dati specifici dell'applicazione associati a questa classe di finestra.|  
|**Classe Atom**|Atom per la classe restituita dal **RegisterClass** chiamare.|  
|**Handle di istanza**|L'handle dell'istanza del modulo che ha registrato la classe. Handle di istanza non sono univoci.|  
|**Byte di finestra**|Il numero di byte aggiuntivi associati a ogni finestra di questa classe. Il significato di questi byte è determinato dall'applicazione. Espandere la casella di riepilogo per visualizzare i valori di byte in formato DWORD.|  
|**Procedura di finestra**|L'indirizzo corrente del **WndProc** funzione per le finestre di questa classe. Questo comportamento è diverso da **procedura di finestra** sul **generale** se la finestra è una sottoclasse.|  
|**Nome del menu**|Il nome del menu principale associata a windows di questa classe ("none" se è presente alcun menu).|  
|**Handle dell'icona**|Handle per l'icona associata a windows di questa classe ("none" se è presente nessuna icona).|  
|**Handle del cursore**|L'handle del cursore associato alle finestre di questa classe ("none" se è presente alcun cursore).|  
|**Pennello di sfondo**|L'handle per il pennello di sfondo associato alle finestre di questa classe o uno dei colori predefiniti Color _ * per disegnare lo sfondo della finestra ("none" se è presente Nessun pennello).|