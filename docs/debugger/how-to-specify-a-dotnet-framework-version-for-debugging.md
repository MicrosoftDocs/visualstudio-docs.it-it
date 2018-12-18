---
title: 'Procedura: specificare una versione di .NET Framework per il debug | Documenti Microsoft'
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
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2cb8da54b53814e7f044c67855e8071c627cf2e1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Procedura: specificare una versione di .NET Framework per il debug
Il debugger di [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] supporta il debug delle versioni precedenti di Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], oltre che della versione corrente. Se si avvia un'applicazione da Visual Studio, il debugger è sempre di identificare la versione corretta del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] per l'applicazione a cui si esegue il debug. Se l'applicazione è già in esecuzione e si utilizza **allegarvi**, il debugger potrebbe non essere sempre in grado di identificare una versione precedente del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. In questo caso, verrà visualizzato un messaggio di errore simile al seguente:  
  
 Il debugger ha interpretato erroneamente la versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] che verrà utilizzata dall'applicazione.  
  
 In questi rari casi, è possibile impostare una chiave del Registro di sistema per indicare al debugger quale versione utilizzare.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Per specificare una versione di .NET Framework per il debug  
  
1.  Cercare nella directory Windows\Microsoft.NET\Framework le versioni di .NET Framework installate nel computer. I numeri di versione saranno simili al seguente:  
  
     `V1.1.4322`  
  
     Identificare il numero di versione corretto e annotarlo.  
  
2.  Avviare il **Editor del Registro di sistema** (regedit).  
  
3.  Nel **Editor del Registro di sistema**, aprire la cartella HKEY_LOCAL_MACHINE.  
  
4.  Passare a: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Se la chiave non esiste, fare doppio clic su HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine e scegliere **nuova chiave**. Denominare la nuova chiave `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  Dopo l'accesso a {449EC4CC-30D2-4032-9256-EE18EB41B62B}, esaminare il **nome** colonna e chiave CLRVersionForDebugging.  
  
    1.  Se la chiave non esiste, fare doppio clic su {449EC4CC-30D2-4032-9256-EE18EB41B62B} e fare clic su **nuovo valore stringa**. Quindi fare doppio clic su nuovo valore di stringa, fare clic su **rinominare**e il tipo `CLRVersionForDebugging`.  
  
6.  Fare doppio clic su **CLRVersionForDebugging**.  
  
7.  Nel **Modifica stringa** , digitare il numero di versione di .NET Framework di **valore** casella. Ad esempio: V1.1.4322  
  
8.  Fare clic su **OK**.  
  
9. Chiudi il **Editor del Registro di sistema**.  
  
     Se all'avvio del debug viene di nuovo visualizzato un messaggio di errore, verificare di avere immesso il numero di versione corretto nel Registro di sistema. Verificare inoltre che la versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] in uso sia supportata da Visual Studio. Il debugger è compatibile con la versione di .NET Framework corrente e le versioni precedenti, ma potrebbe non essere compatibile con le versioni future.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)