---
title: "Procedura: eseguire il Debug in modalità mista | Documenti Microsoft"
ms.custom: 
ms.date: 06/19/2017
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
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 797724287439631b9398af43616116a1635381ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-in-mixed-mode"></a>Procedura: eseguire il debug in modalità mista
Nelle procedure riportate di seguito viene spiegato come eseguire il debug in modalità mista, ovvero sia di codice gestito che di codice nativo. Gli scenari possibili sono due, a seconda che la DLL o l'applicazione sia scritta in codice nativo:  
  
-   L'applicazione che chiama la DLL è scritta in codice nativo. In tal caso, la DLL è gestita ed è necessario attivare il debugger gestito e il debugger nativo. Questo è possibile archiviare il  **\<progetto > pagine delle proprietà** la finestra di dialogo. L'esecuzione di questa operazione varia a seconda che il debug venga avviato dal progetto della DLL o da quello dell'applicazione chiamante.  
  
-   L'applicazione che chiama la DLL è scritta in codice gestito e la DLL è scritta in codice nativo.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

Se non si dispone di accesso al progetto per l'applicazione chiamante, è possibile eseguire il debug di una DLL dal progetto di DLL. Per altre informazioni, vedere [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md). Non è necessario utilizzare mista per eseguire il debug solo il progetto di DLL.
  
### <a name="to-enable-mixed-mode-debugging-c-calling-app"></a>Per abilitare il debug in modalità mista (app di chiamata C++)  
  
1.  In **Esplora**, selezionare il progetto nativo.
  
2.  Nel **vista** menu, fare clic su **pagine delle proprietà**.
  
3.  Nel  **\<progetto > pagine delle proprietà** finestra di dialogo espandere il **le proprietà di configurazione** nodo e quindi selezionare **debug**.  
  
4.  Impostare **tipo di Debugger** a **misto** o **Auto**.

    ![Abilitare il debug in modalità mista](../debugger/media/dbg-mixed-mode-from-native.png "abilitare il debug in modalità mista")

### <a name="to-enable-mixed-mode-debugging-c-or-vb-calling-app"></a>Per abilitare debug in modalità mista (app chiamante di c# o Visual Basic)  
  
1.  In **Esplora**, selezionare il progetto gestito.  
  
2.  Nel **vista** menu, fare clic su **pagine delle proprietà**.  
  
3.  Nel  **\<progetto > pagine delle proprietà** la finestra di dialogo, seleziona il **Debug** scheda e quindi selezionare **Abilita debug codice nativo**

    ![Abilitare il debug di codice nativo](../debugger/media/dbg-mixed-mode-from-csharp.png "Abilita debug codice nativo")
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Eseguire il debug da un progetto di DLL](../debugger/how-to-debug-from-a-dll-project.md)