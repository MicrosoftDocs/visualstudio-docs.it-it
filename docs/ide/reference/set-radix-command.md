---
title: Comando Imposta radice | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0ba6b4d3ce4aa362c63cace8481bacec90c91716
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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