---
title: Uso di Windows Runtime in JavaScript | Microsoft Docs
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: JavaScript, Windows Runtime
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c81f5d83056ceb87987e263f09c0d5e5017dbb6f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="using-the-windows-runtime-in-javascript"></a>Uso di Windows Runtime in JavaScript
Quando si scrive un'app della piattaforma UWP (Universal Windows Platform), è possibile usare le classi, i metodi e le proprietà di Windows Runtime in modo analogo all'uso di oggetti, metodi e proprietà nativi di JavaScript. Questo argomento include informazioni introduttive e collegamenti ad argomenti esplicativi sui concetti di base dell'uso di API di Windows Runtime in JavaScript, inclusa una spiegazione del modo in cui sono rappresentati i tipi di Windows Runtime, di come usare i metodi asincroni di Windows Runtime e come rimanere in ascolto di e gestire eventi di Windows Runtime.  
  
 Si può trovare la documentazione di riferimento di JavaScript in [Linguaggio di riferimento di JavaScript](../javascript/javascript-language-reference.md).  
  
> [!IMPORTANT]
>  Le funzionalità di Windows Runtime non sono disponibili per app eseguite in Internet Explorer.  
  
## <a name="windows-runtime-reference-documentation"></a>Documentazione di riferimento per Windows Runtime  
 Per la documentazione di riferimento, vedere [Documentazione di riferimento per Windows Runtime](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx). Esempi di codice sono disponibili in JavaScript e anche in C++, C# e Visual Basic.  
  
## <a name="writing-windows-runtime-components-in-c-c-or-visual-basic"></a>Scrittura di componenti di Windows Runtime Components in C++, C# o Visual Basic  
 Per istruzioni e linee guida per la scrittura di componenti di Windows Runtime che possano essere usare in JavaScript, vedere [Creazione di componenti Windows Runtime in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp) e [Creazione di componenti Windows Runtime in C# e Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
## <a name="casing-conventions-with-windows-runtime-features"></a>Convenzioni relative alla combinazione di maiuscole e minuscole con funzionalità di Windows Runtime  
 Le convenzioni relative alla combinazione di maiuscole e minuscole per le funzionalità di Windows Runtime in JavaScript sono leggermente diverse rispetto a quelle per gli altri linguaggi:  
  
-   Gli spazi dei nomi e le classi sono definiti in base alla convezione Pascal:  
  
    ```JavaScript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   Per i membri delle classi, inclusi i metodi e le proprietà, e i membri di strutture ed enumerazioni devono essere usati solo lettere minuscole:  
  
    ```JavaScript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   Per i nomi degli eventi devono essere usati caratteri minuscoli:  
  
    ```JavaScript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Considerazioni sull'uso dell'API di Windows Runtime](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [Uso di metodi asincroni di Windows Runtime](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [Gestione degli eventi di Windows Runtime in JavaScript](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [Rappresentazione JavaScript dei tipi di Windows Runtime](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [Proiezione JavaScript di DateTime e TimeSpan di Windows Runtime](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)