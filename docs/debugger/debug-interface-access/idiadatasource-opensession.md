---
title: 'Idiadatasource:: OpenSession | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6b7cfaf3e2cf7331576ca79b9820bafb761fc44c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Apre una sessione per eseguire query sui simboli.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 ppSession  
 [out] Restituisce un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) oggetto che rappresenta la sessione di aperta.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Nella tabella seguente mostra i valori restituiti possibili per questo metodo.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|E_UNEXPECTED|Il [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) oggetto non è già stato inizializzato con un'origine dei simboli.|  
|E_INVALIDARG|Non valido `ppSession` parametro.|  
|E_OUTOFMEMORY|Memoria insufficiente per aprire la sessione.|  
  
## <a name="remarks"></a>Note  
 Questo metodo apre un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) oggetto per un'origine dati.  
  
 `IDiaSession`gli oggetti implementare query nell'origine dati. Una sessione gestisce uno spazio di indirizzi per ogni set di simboli di debug. Se il file .exe o dll descritto dai simboli di origine dati è attivo nell'indirizzo più intervalli (ad esempio, in quanto più processi sono caricato), quindi deve essere utilizzata una sola sessione per ogni intervallo di indirizzi.  
  
## <a name="example"></a>Esempio  
  
```C++  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Panoramica](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Esecuzione di query nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)