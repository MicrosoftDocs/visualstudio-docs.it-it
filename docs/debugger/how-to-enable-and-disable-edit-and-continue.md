---
title: 'Procedura: abilitare e disabilitare Modifica e continuazione (c#, VB, C++) | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 9070913d1106eb5e2ca04160ad95c6a6fd46f752
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Procedura: abilitare e disabilitare Modifica e continuazione (c#, VB, C++)
È possibile disabilitare o abilitare Modifica e continuazione di **opzioni** la finestra di dialogo in fase di progettazione. Non è possibile modificare questa impostazione durante il debug.  
  
La funzionalità Modifica e continuazione può essere utilizzata solo nelle build di debug. Per il codice C++ nativo, la funzionalità Modifica e continuazione richiede l'utilizzo dell'opzione /INCREMENTAL. Per ulteriori informazioni sui requisiti di funzionalità in C++, vedere questo [post di blog](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/) e [modifica e continuazione (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).
  
#### <a name="to-enabledisable-edit-and-continue"></a>Per abilitare o disabilitare Modifica e continuazione  
  
1.  Se trovano in una sessione di debug, terminare il debug (**MAIUSC + F5**).

2.  Apri pagina delle opzioni di debug (**strumenti > Opzioni > debug**).
  
3.  Selezionare **generale**, scorrere fino a **modifica e continuazione** categoria (riquadro a destra).  
  
4.  Per abilitare, selezionare il **Abilita modifica e continuazione** casella di controllo. Per disabilitarla, deselezionare la casella di controllo.  
  
    > [!NOTE]
    >  Se IntelliTrace è abilitato e si raccolgono sia eventi IntelliTrace sia informazioni sulle chiamate, la funzionalità Modifica e continuazione viene disabilitata. Per ulteriori informazioni, vedere [IntelliTrace](../debugger/intellitrace.md).

5. (C++) Per abilitare, selezionare **abilitare Modifica e continuazione nativo**. Per disabilitarla, deselezionare la casella di controllo.

6. (C++) Impostare opzioni aggiuntive per il codice nativo.

    - **Applicare le modifiche durante la continuazione (solo nativo)**  
        Visual Studio compila e applica automaticamente le modifiche di codice in sospeso apportate quando il processo viene ripreso da uno stato di interruzione. Se non è selezionata, è possibile scegliere di applicare le modifiche utilizzando l'elemento "Applica modifiche del codice" nel menu Debug.  
  
    - **Avvisa in codice non aggiornato (solo nativo)**  
        Consente di ricevere avvisi relativi al codice non aggiornato. 
  
7.  Fare clic su **OK**.    
  
## <a name="see-also"></a>Vedere anche  
 [Modifica e continuazione](../debugger/edit-and-continue.md)