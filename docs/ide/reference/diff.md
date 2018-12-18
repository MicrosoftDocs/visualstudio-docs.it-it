---
title: -Diff | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 016de0a06615caab723f83900e8bd4103cb142b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="diff"></a>/Diff
Confronta due file. Le differenze vengono visualizzate in una finestra speciale di Visual Studio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]  
```  
  
## <a name="arguments"></a>Argomenti  
 `SourceFile`  
 Obbligatorio. Percorso completo e nome del primo file da confrontare.  
  
 `TargetFile`  
 Obbligatorio. Percorso completo e nome del secondo file da confrontare.  
  
 `SourceDisplayName`  
 Facoltativo. Nome visualizzato del primo file.  
  
 `TargetDisplayName`  
 Facoltativo. Nome visualizzato del secondo file.