---
title: Funzione SccUninitialize | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccUninitialize
helpviewer_keywords: SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5976313939ee9efa81c71e7894da8e5f45e2d017
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="sccuninitialize-function"></a>SccUninitialize (funzione)
Questa funzione pulisce le allocazioni o connessioni aperte create da una chiamata precedente al [SccInitialize](../extensibility/sccinitialize-function.md) in preparazione per l'arresto di plug-in controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] Il puntatore alla struttura contesto plug-in controllo di origine creati nel [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|La pulizia completata.|  
  
## <a name="remarks"></a>Note  
 Il plug-in controllo del codice sorgente è responsabile per la preparazione di arrestare il computer e per liberare la memoria allocata il plug-in per la struttura di contesto. La funzione viene chiamata una volta per ogni istanza specifica di un plug-in. Una chiamata al [SccInitialize](../extensibility/sccinitialize-function.md) precede questa chiamata. Nessun progetto è ancora possibile aprire al momento della chiamata a `SccUninitialize`.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)