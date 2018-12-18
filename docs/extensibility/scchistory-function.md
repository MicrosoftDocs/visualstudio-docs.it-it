---
title: Funzione SccHistory | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccHistory
helpviewer_keywords: SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cf621b3050382d79fcf44df2ac5d50d9885e03d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="scchistory-function"></a>SccHistory (funzione)
Questa funzione consente di visualizzare la cronologia dei file specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pvContext`  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 `hWnd`  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 `nFiles`  
 [in] Numero di file specificato per il `lpFileName` matrice.  
  
 `lpFileName`  
 [in] Matrice di nomi completi di file.  
  
 `fOptions`  
 [in] Flag di comando (attualmente non utilizzato).  
  
 `pvOptions`  
 [in] Opzioni specifiche plug-in controllo di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Cronologia delle versioni è stata ottenuta correttamente.|  
|SCC_I_RELOADFILE|Il controllo del codice sorgente modificato effettivamente il file su disco durante il recupero della cronologia (ad esempio, per ottenere una versione precedente dello stesso), pertanto l'IDE di ricaricare il file.|  
|SCC_E_FILENOTCONTROLLED|Il file non è incluso nel controllo del codice sorgente.|  
|SCC_E_OPNOTSUPPORTED|Il controllo del codice sorgente non supporta questa operazione.|  
|SCC_E_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_PROJNOTOPEN|Il non progetto è stato aperto.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico. Non è stato possibile ottenere la cronologia dei file.|  
  
## <a name="remarks"></a>Note  
 Il plug-in controllo del codice sorgente è possibile visualizzare una finestra di dialogo per visualizzare la cronologia di ogni file, utilizzando `hWnd` come finestra padre. In alternativa, il testo facoltativo output callback funzione fornita per il [SccOpenProject](../extensibility/sccopenproject-function.md) può essere utilizzato, se è supportato.  
  
 Si noti che in determinate circostanze, il file in corso l'analisi può cambiare durante l'esecuzione di questa chiamata. Ad esempio, il [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] comando Cronologia consente all'utente per ottenere una versione precedente del file. In tal caso, il controllo origine plug-in restituisce `SCC_I_RELOAD` per avvisare l'IDE ed è necessario ricaricare il file.  
  
> [!NOTE]
>  Se il plug-in controllo del codice sorgente non supporta questa funzione per una matrice di file, è possibile visualizzare solo la cronologia file per il primo file.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)