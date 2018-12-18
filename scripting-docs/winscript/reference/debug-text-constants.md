---
title: Costanti DEBUG_TEXT | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5126a9efefaab611cd27d2104c40918f8dc7c7e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="debugtext-constants"></a>Costanti DEBUG_TEXT
Utilizzato durante [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Costanti  
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION DWORD|0x00000001|Indica che il testo è un'espressione anziché un'istruzione. Questo flag può influenzare le modalità in cui il testo viene analizzato da alcuni linguaggi.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Se un valore restituito è disponibile, e verrà utilizzato dal chiamante.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Non consentire gli effetti collaterali. Se questo flag è impostato, la valutazione dell'espressione deve modificare nessuno stato di runtime.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Consenti i punti di interruzione durante la valutazione del testo. Se questo flag non è impostato, i punti di interruzione verrà ignorati durante la valutazione del testo.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Consente di segnalazioni di errore durante la valutazione del testo. Se non è impostato questo flag, quindi gli errori non verranno segnalati all'host durante la valutazione.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indica che l'espressione da valutare per un contesto di codice, anziché eseguire l'espressione stessa.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)