---
title: Funzione SccQueryInfo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5e2838709d7c2c2ad6e6b1eeef36c2cc0018a1a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo (funzione)
Questa funzione Ottiene informazioni sullo stato per un set di file selezionati nel controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 nFiles  
 [in] Numero di file specificato per il `lpFileNames` matrice e la lunghezza del `lpStatus` matrice.  
  
 lpFileNames  
 [in] Una matrice di nomi di file da recuperare.  
  
 lpStatus  
 [in, out] Matrice in cui il plug-in controllo del codice sorgente restituisce i flag di stato per ogni file. Per ulteriori informazioni, vedere [codice di stato File](../extensibility/file-status-code-enumerator.md).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Query completata.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema con l'accesso al sistema di controllo di origine, probabilmente causato da problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_PROJNOTOPEN|Il progetto non è aperto in controllo del codice sorgente.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Se `lpFileName` è una stringa vuota, non sono attualmente disponibili informazioni di stato per aggiornare. In caso contrario, è il nome e percorso completo del file per cui sia stato modificato le informazioni sullo stato.  
  
 La matrice restituita può essere una maschera di bit di `SCC_STATUS_xxxx` bits. Per ulteriori informazioni, vedere [codice di stato File](../extensibility/file-status-code-enumerator.md). Un controllo del codice sorgente potrebbe non supportare tutti i tipi di bit. Ad esempio, se `SCC_STATUS_OUTOFDATE` non è disponibile, ma non viene impostato il bit.  
  
 Quando si utilizza questa funzione per estrarre i file, tenere presente quanto segue `MSSCCI` requisiti di stato:  
  
-   `SCC_STATUS_OUTBYUSER` viene impostato quando l'utente corrente ha estratto il file.  
  
-   `SCC_STATUS_CHECKEDOUT` non può essere impostata a meno che non `SCC_STATUS_OUTBYUSER` è impostata.  
  
-   `SCC_STATUS_CHECKEDOUT` viene impostata solo quando il file viene estratto nella directory di lavoro designato.  
  
-   Se il file è stato estratto dall'utente corrente in una directory diversa dalla directory di lavoro, `SCC_STATUS_OUTBYUSER` è impostata ma `SCC_STATUS_CHECKEDOUT` non.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Codice di stato file](../extensibility/file-status-code-enumerator.md)