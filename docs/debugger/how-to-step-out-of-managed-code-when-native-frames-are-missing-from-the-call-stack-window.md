---
title: 'Procedura: uscire da codice gestito quando sono visualizzati frame nativi dalla finestra Stack di chiamate | Documenti Microsoft'
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
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7599c99c9375cda7b5f24432db8c137c5c4357df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Procedura: uscire da codice gestito quando nella finestra Stack di chiamate non sono visualizzati frame nativi
Se il codice contiene frame nativi non visibili nella **Stack di chiamate** finestra uscita codice gestito può produrre risultati imprevisti. In alternativa, è possibile utilizzare un punto di interruzione anziché **Esci**.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Per uscire da codice gestito quando nella visualizzazione dello stack di chiamate non sono visualizzati frame nativi  
  
1.  Nel codice nativo impostare un punto di interruzione di posizione dopo la chiamata a codice gestito.  
  
2.  Nel **Debug** menu, scegliere **continua**.  
  
     Una volta completata la chiamata gestita, l'esecuzione si interromperà in corrispondenza del punto di interruzione nel codice nativo.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Usare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md)