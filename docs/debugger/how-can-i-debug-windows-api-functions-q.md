---
title: Come è possibile eseguire il debug di funzioni API Windows? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 28d9aa387861de41b7d3f782fec85d8d26c7d3ae
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-can-i-debug-windows-api-functions"></a>Come è possibile eseguire il debug di funzioni API Windows?
Per eseguire il debug di una funzione API Windows con NT Symbols caricato, effettuare le operazioni seguenti.  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Per impostare un punto di interruzione su una funzione Windows API con NT Symbols caricato  
  
-   Immettere il nome della funzione e il nome della DLL in cui risiede la funzione. Nel codice a 32 bit, utilizzare la forma decorata del nome della funzione. Per impostare un punto di interruzione **MessageBeep**, ad esempio, è necessario immettere quanto segue.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Per ottenere il nome decorato, vedere [visualizzazione nomi decorati](http://msdn.microsoft.com/en-us/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul codice nativo debug](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)