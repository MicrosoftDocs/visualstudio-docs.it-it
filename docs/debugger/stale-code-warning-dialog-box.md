---
title: Finestra di dialogo Avviso di codice obsoleti | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.stalecode
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Stale Code Warning dialog box
- code, stale code warning
- warnings, Stale Code Warning dialog box
- Edit and Continue, stale code
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec80baa04529bcc6a9705d1c8df03e120e6bc64e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="stale-code-warning-dialog-box"></a>Avviso di codice non aggiornato (finestra di dialogo)
Questa finestra di dialogo viene visualizzata quando sono state apportate modifiche al codice nativo che **modifica e continuazione** non può applicare immediatamente. Di conseguenza, il codice nativo nello stack frame corrente non sarà più aggiornato. Per ulteriori informazioni, vedere [procedura: utilizzare il codice non aggiornato](http://msdn.microsoft.com/en-us/c7536e95-66a6-44a0-995d-3fe5035250b4).  
  
 **Non visualizzare più questa finestra di dialogo**  
 Se si seleziona questa casella di controllo, la modalità Modifica e continuazione applicherà le modifiche al codice senza chiedere l'autorizzazione. È possibile attivare questo avviso nuovamente visitando il **opzioni** la finestra di dialogo, aprire il **debug** cartella, fare clic sul **modifica e continuazione** , quindi selezionare **Avvisa in caso di codice**.  
  
## <a name="see-also"></a>Vedere anche  
 [Modifiche al codice supportate (C++)](../debugger/supported-code-changes-cpp.md)   
 [Modifica e continuazione, debug, finestra di dialogo Opzioni](http://msdn.microsoft.com/Library/009d225f-ef65-463f-a146-e4c518f86103)