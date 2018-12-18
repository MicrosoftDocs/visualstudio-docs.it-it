---
title: "Modalità mista di debug per x64 processi è supportato solo quando si utilizza Microsoft.NET Framework 4 o versione successiva | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 37d5c52192c30ccc3b34bfa609c3f6a7ffb99566
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>Il debug in modalità mista per i processi x64 è supportato solo quando si utilizza Microsoft .NET Framework 4 o versione successiva
Le versioni di .NET Framework precedenti alla 4 non forniscono alcun supporto per il debug in modalità mista di processi x64. Ciò significa che non è possibile passare dal codice gestito al codice nativo, o viceversa, durante l'esecuzione del debug.  
  
### <a name="workarounds"></a>Soluzioni  
  
-   Aggiornare il progetto per l'utilizzo di Microsoft .NET Framework 4 o versione successiva.  
  
     oppure  
  
     Eseguire il debug del codice gestito e del codice nativo in sessioni di debug separate.  
  
     oppure  
  
     Eseguire il debug del codice misto come processo a 32 bit, come descritto nelle procedure che seguono.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Per impostare la piattaforma su 32 bit (Visual Basic o C#)  
  
1.  In **Esplora**mouse sul progetto e quindi fare clic su **proprietà**.  
  
2.  Nelle pagine delle proprietà, fare clic su di **compilare** o **Debug** scheda.  
  
3.  Fare clic su **piattaforma** e selezionare x86 dall'elenco di piattaforme.  
  
     Per impostazione predefinita, i compilatori Visual Basic e C# producono codice eseguibile in qualsiasi CPU. In un computer a 64 bit, questi binari sono eseguiti come processi a 64 bit. Per eseguire in un processo a 32 bit, è necessario scegliere **Win32**, non **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Per impostare la piattaforma su 32 bit (C/C++)  
  
1.  In **Esplora**, mouse sul progetto, quindi fare clic su **proprietà**.  
  
2.  Nelle pagine delle proprietà, fare clic su **piattaforma** e selezionare Win32 dall'elenco di piattaforme.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Vedere [impostazione del debug SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il debug di applicazioni a 64 Bit](../debugger/debug-64-bit-applications.md)