---
title: QUERYCHANGESFUNC | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d1df5f21ffed27c45ebee6315fcc29ee1dcc8fa4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Si tratta di una funzione di callback utilizzata per il [SccQueryChanges](../extensibility/sccquerychanges-function.md) operazione per enumerare una raccolta di nomi di file e determinare lo stato di ciascun file.  
  
 Il `SccQueryChanges` ha un elenco di file e un puntatore a funzione di `QUERYCHANGESFUNC` callback. Il plug-in controllo del codice sorgente enumera l'elenco specificato e fornisce lo stato (tramite questo callback) per ogni file nell'elenco.  
  
## <a name="signature"></a>Signature  
  
```cpp  
typedef BOOL (*QUERYCHANGESFUNC)(  
   LPVOID pvCallerData,  
   QUERYCHANGESDATA * pChangesData  
);  
```  
  
## <a name="parameters"></a>Parametri  
 pvCallerData  
 [in] Il `pvCallerData` parametro passato dal chiamante (IDE) di [SccQueryChanges](../extensibility/sccquerychanges-function.md). Il plug-in controllo del codice sorgente non deve formulare ipotesi sul contenuto di questo valore.  
  
 pChangesData  
 [in] Puntatore a un [QUERYCHANGESDATA struttura](#LinkQUERYCHANGESDATA) struttura che descrive le modifiche in un file.  
  
## <a name="return-value"></a>Valore restituito  
 Nell'IDE viene restituito un codice di errore appropriato:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Continuare l'elaborazione.|  
|SCC_I_OPERATIONCANCELED|Arrestare l'elaborazione.|  
|SCC_E_xxx|Qualsiasi errore di controllo del codice sorgente appropriato deve arrestare l'elaborazione.|  
  
##  <a name="LinkQUERYCHANGESDATA"></a> Struttura QUERYCHANGESDATA  
 La struttura passata per ogni file è simile al seguente:  
  
```cpp  
struct QUERYCHANGESDATA_A  
{  
    DWORD  dwSize;  
    LPCSTR lpFileName;  
    DWORD  dwChangeType;  
    LPCSTR lpLatestName;  
};  
  
typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;  
  
struct QUERYCHANGESDATA_W  
{  
    DWORD   dwSize;  
    LPCWSTR lpFileName;  
    DWORD   dwChangeType;  
    LPCWSTR lpLatestName;  
};  
```  
  
 dwSize diverso da  
 Dimensione della struttura (in byte).  
  
 lpFileName  
 Nome del file originale per questo elemento.  
  
 dwChangeType  
 Codice che indica lo stato del file:  
  
|Codice|Descrizione|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|Impossibile stabilire cosa è cambiato.|  
|`SCC_CHANGE_UNCHANGED`|Nessuna modifica di nome per il file.|  
|`SCC_CHANGE_DIFFERENT`|File con un'identità diversa, ma lo stesso nome esiste nel database.|  
|`SCC_CHANGE_NONEXISTENT`|File non esiste nel database o in locale.|  
|`SCC_CHANGE_DATABASE_DELETED`|File eliminato nel database.|  
|`SCC_CHANGE_LOCAL_DELETED`|File eliminato localmente, ma il file esista ancora nel database. Se questo non può essere determinato, restituire `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|File aggiunti al database ma non esiste in locale.|  
|`SCC_CHANGE_LOCAL_ADDED`|File non esiste nel database e un nuovo file locale.|  
|`SCC_CHANGE_RENAMED_TO`|File rinominati o spostati nel database come `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|File rinominati o spostati nel database da `lpLatestName`; se questa è troppo costosa da tracciare, restituisce un flag diverso, ad esempio `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 Il nome di file corrente per questo elemento.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Codici di errore](../extensibility/error-codes.md)