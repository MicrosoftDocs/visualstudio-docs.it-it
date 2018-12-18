---
title: Comando Percorso simboli | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1b35c5d55eed31111746f2e2dbf9befb4fb7591
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="symbol-path-command"></a>Comando Percorso simboli
Imposta l'elenco delle directory in cui il debugger deve eseguire la ricerca dei simboli.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>Argomenti  
 `pathname`  
 Facoltativo. Elenco di percorsi delimitato da punti e virgola usato dal debugger per la ricerca dei simboli.  
  
## <a name="remarks"></a>Note  
 Se non viene specificato un `pathname`, il comando elenca i percorsi dei simboli correnti.  
  
## <a name="example"></a>Esempio  
 In questo esempio vengono aggiunti due percorsi all'elenco delle directory dei simboli.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## <a name="example"></a>Esempio  
 In questo esempio viene visualizzato un elenco delimitato da punti e virgola dei percorsi dei simboli correnti.  
  
```  
Debug.SymbolPath  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)