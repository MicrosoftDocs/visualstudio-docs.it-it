---
title: Funzione SccIsMultiCheckoutEnabled | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccIsMultiCheckoutEnabled
helpviewer_keywords: SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b04cd593bd631ba92545901ff289a9f8ed4f1822
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled (funzione)
Questa funzione controlla se il plug-in controllo del codice sorgente consente le estrazioni multiple in un file.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 pbMultiCheckout  
 [out] Specifica se le estrazioni multiple sono abilitate per il progetto (diverso da zero indica che le estrazioni multiple sono supportate).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Il controllo ha avuto esito positivo.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 L'IDE effettua due controlli per determinare se i file possono essere estratti contemporaneamente da più di un utente. In primo luogo, il controllo del codice sorgente deve supportare estrazioni multiple. Il plug-in controllo del codice sorgente può specificare questa funzionalità durante l'inizializzazione, specificando il `SCC_CAP_MULTICHECKOUT`. Successivamente, come un secondo controllo, l'IDE chiama questa funzione per determinare se il progetto corrente supporta estrazioni multiple. Se le estrazioni multiple sono supportate per il progetto selezionato, i plug-in restituisce un esito positivo del codice e imposta `pbMultiCheckout` a diverso da zero (`TRUE`) o `FALSE`.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)