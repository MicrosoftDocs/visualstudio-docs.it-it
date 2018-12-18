---
title: Funzione SccWillCreateSccFile | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccWillCreateSccFile
helpviewer_keywords: SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6a0344177d50d7121b1116e80983db80233dac90
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile (funzione)
Questa funzione determina se il plug-in controllo del codice sorgente supporta la creazione del MSSCCPRJ. File di controllo del codice sorgente per ogni file specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] Il puntatore di contesto plug-in controllo di origine.  
  
 nFiles  
 [in] Il numero di nomi di file inclusi nel `lpFileNames` nonché la lunghezza della matrice di `pbSccFiles` matrice.  
  
 lpFileNames  
 [in] Una matrice di nomi di file completo per verificare (matrice deve essere allocata dal chiamante).  
  
 pbSccFiles  
 [in, out] Matrice in cui archiviare i risultati.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione completata.|  
|SCC_E_INVALIDFILEPATH|Uno dei percorsi nella matrice non è valido.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Questa funzione viene chiamata con un elenco di file per determinare se il plug-in controllo del codice sorgente fornisce il supporto nel MSSCCPRJ. File di controllo del codice sorgente per ogni file specificata (per ulteriori informazioni sul MSSCCPRJ. File di controllo del codice sorgente, vedere [MSSCCPRJ. File SCC](../extensibility/mssccprj-scc-file.md)). Plug-in del controllo codice sorgente è possibile dichiarare se hanno la possibilità di creare MSSCCPRJ. File SCC dichiarando `SCC_CAP_SCCFILE` durante l'inizializzazione. Il plug-in restituisce `TRUE` o `FALSE` per ogni file nel `pbSccFiles` matrice per indicare che i file specificati hanno MSSCCPRJ. Supporto di controllo del codice sorgente. Se il plug-in restituisce un codice di riuscita tramite la funzione, vengono rispettati i valori nella matrice restituita. In caso di errore, la matrice viene ignorata.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)