---
title: Funzione SccGetVersion | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetVersion
helpviewer_keywords: SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2aef7ed21124c2e3555442819461f1989388ab22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetversion-function"></a>SccGetVersion (funzione)
Questa funzione Ottiene il numero di versione dell'API di plug-in controllo di origine supportata dal plug-in controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Parametri  
 Nessuno.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `LONG` tipo di dati che contiene il numero di versione dell'API di plug-in controllo di origine supportata:  
  
|WORD|Descrizione|  
|----------|-----------------|  
|HIWORD|Versione principale|  
|LOWORD|Versione secondaria|  
  
## <a name="remarks"></a>Note  
 Ad esempio, se un plug-in controllo del codice sorgente supporta la versione 1.3 dell'API plug-in controllo di origine, questa funzione restituirà 0x0103.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)