---
title: 'Idiadatasource:: OpenSession | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 39fe9bf3a67d3ad5f26ff7c4ccdaa9772cf1346b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
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
  
 `IDiaSession` gli oggetti implementare query nell'origine dati. Una sessione gestisce uno spazio di indirizzi per ogni set di simboli di debug. Se il file .exe o dll descritto dai simboli di origine dati è attivo nell'indirizzo più intervalli (ad esempio, in quanto più processi sono caricato), quindi deve essere utilizzata una sola sessione per ogni intervallo di indirizzi.  
  
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