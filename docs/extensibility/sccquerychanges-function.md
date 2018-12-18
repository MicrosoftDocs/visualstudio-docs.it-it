---
title: Funzione SccQueryChanges | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d887c0cea989fa6a955edc2f39b9667e7421093d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccquerychanges-function"></a>SccQueryChanges (funzione)
Questa funzione enumera un elenco di file, che fornisce informazioni sulle modifiche di nome per ogni file tramite una funzione di callback specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] Il puntatore di contesto plug-in controllo di origine.  
  
 nFiles  
 [in] Numero di file in `lpFileNames` matrice.  
  
 lpFileNames  
 [in] Matrice di nomi di file per cui ottenere informazioni.  
  
 pfnCallback  
 [in] Funzione di callback da chiamare per ogni nome di file nell'elenco (vedere [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) per informazioni dettagliate).  
  
 pvCallerData  
 [in] Valore che verrà passato invariato alla funzione di callback.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Il processo di query completato.|  
|SCC_E_PROJNOTOPEN|Il progetto non è stato aperto nel controllo del codice sorgente.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete.|  
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato o generale.|  
  
## <a name="remarks"></a>Note  
 Le modifiche sottoposte a query per sono per lo spazio dei nomi: in particolare, la ridenominazione, aggiunta e rimozione di un file.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Codici di errore](../extensibility/error-codes.md)