---
title: Scheda finestre, finestra di dialogo Proprietà finestra | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Windows Tab
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3589f3242c72002bf28e8aee135b2713c39fdb7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="windows-tab-window-properties-dialog-box"></a>Scheda Finestre, finestra di dialogo Proprietà finestra
Utilizzare il **Windows** scheda per visualizzare informazioni sulle finestre correlate alla finestra selezionata. Per visualizzare il [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo per il [Windows Vista](../debugger/windows-view.md) finestra. Selezionare qualsiasi nodo finestra nell'albero, quindi scegliere **proprietà** dal **vista** menu.  
  
 Le impostazioni seguenti sono disponibili sul **Windows** scheda:  
  
|Voce|Descrizione|  
|-----------|-----------------|  
|**Finestra successiva**|L'handle della finestra di pari livello successiva nella stessa sequenza (Z-order) mostrata nella visualizzazione struttura ad albero della finestra ("none" se è presente alcuna finestra successiva). Scegliere questa voce per visualizzare le proprietà della finestra successiva.|  
|**Finestra precedente**|L'handle della finestra di pari livello precedente nella stessa sequenza (Z-order) mostrata nella visualizzazione struttura ad albero della finestra ("none" se è presente alcuna finestra precedente). Scegliere questa voce per visualizzare le proprietà della finestra precedente.|  
|**Finestra padre**|Handle della finestra padre della finestra ("none" se è presente alcun padre). Scegliere questa voce per visualizzare le proprietà della finestra padre.|  
|**Primo elemento figlio**|Handle della finestra della finestra primo figlio, in sequenza (Z-order) mostrato nella visualizzazione struttura ad albero della finestra ("none" se vi sono finestre figlio). Scegliere questo valore per visualizzare le proprietà della prima finestra figlio.|  
|**Finestra proprietaria**|Handle della finestra proprietaria della finestra corrente. Finestra principale di un'applicazione proprietaria in genere windows di finestra di dialogo modali del sistema, ad esempio ("none" Se non esiste alcun proprietario). Scegliere questa voce per visualizzare le proprietà della finestra proprietaria.|