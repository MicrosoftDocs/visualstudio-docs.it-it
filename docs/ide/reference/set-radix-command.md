---
title: Comando Imposta radice | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e09b4d2673dda2e288915f36ff5d520aa5423c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="set-radix-command"></a>Comando Imposta radice
Imposta o restituisce la base numerica usata per visualizzare i valori integer.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## <a name="arguments"></a>Argomenti  
 `10` o `16` o `hex` o `dec`  
 Facoltativo. Indica un valore decimale (10 o dec) o esadecimale (16 o hex). Se un argomento viene omesso, viene restituito il valore della radice corrente.  
  
## <a name="example"></a>Esempio  
 Nell'esempio che segue, l'ambiente viene impostato per la visualizzazione dei valori integer in formato esadecimale.  
  
```  
>Debug.SetRadix hex  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)