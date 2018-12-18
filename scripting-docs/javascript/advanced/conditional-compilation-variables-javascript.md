---
title: Variabili di compilazione condizionale (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: conditional compilation, variables
ms.assetid: d6f9827d-c558-412c-8e68-de04c19c3d9d
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 900a44dab0ad418cd2899af6423f78016c90fe2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-compilation-variables-javascript"></a>Variabili di compilazione condizionale (JavaScript)
Di seguito sono riportate le variabili predefinite disponibili per la compilazione condizionale. Se la variabile non è **true**, non è definita e si comporta come `NaN` quando vi si accede.  
  
> [!WARNING]
>  La compilazione condizionale è supportata in tutte le versioni di Internet Explorer precedenti a Internet Explorer 11. A partire dalla modalità standard di Internet Explorer 11 e nelle applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] la compilazione condizionale non è supportata.  
  
## <a name="variables"></a>Variabili  
  
|Variabile|Descrizione|  
|--------------|-----------------|  
|@_win32|True se in esecuzione in un sistema Win32.|  
|@_win16|True se in esecuzione in un sistema Win16.|  
|@_mac|True se in esecuzione in un sistema Apple Macintosh.|  
|@_alpha|True se in esecuzione in un processore DEC Alpha.|  
|@_x86|True se in esecuzione in un processore Intel.|  
|@_mc680x0|True se in esecuzione in un processore Motorola 680x0.|  
|@_PowerPC|True se in esecuzione in un processore Motorola PowerPC.|  
|@_jscript|Sempre true.|  
|@_jscript_build|Contiene il numero di build del motore di script di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
|@_jscript_version|Contiene il numero di versione di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] in formato maggiore.minore.|