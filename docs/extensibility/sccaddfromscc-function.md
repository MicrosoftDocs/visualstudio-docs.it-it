---
title: Funzione SccAddFromScc | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccAddFromScc
helpviewer_keywords: SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f92950bc833c2d2658c3e13cd7e800e877b32de9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc (funzione)
Questa funzione consente di individuare i file già presenti nel sistema di controllo di origine e successivamente rendere tali parte i file del progetto corrente. Ad esempio, questa funzione può ottenere un file di intestazione comune nel progetto corrente senza la copia del file. La matrice restituita di file, `lplpFileNames`, contiene l'elenco di file che l'utente desidera aggiungere al progetto IDE.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 hWnd  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 lpnFiles  
 [in, out] Un buffer per il numero di file che vengono aggiunti in. (Si tratta di `NULL` se la memoria a cui puntava `lplpFileNames` deve essere rilasciato. Vedere la sezione Osservazioni per informazioni dettagliate).  
  
 lplpFileNames  
 [in, out] Matrice di puntatori a tutti i nomi di file senza i percorsi di directory. Questa matrice viene allocata e liberata dai plug-in controllo del codice sorgente. Se `lpnFiles` = 1 e `lplpFileNames` non `NULL`, il nome della matrice a cui puntava `lplpFileNames` contiene la cartella di destinazione.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|I file sono stati correttamente Trova e aggiunto al progetto.|  
|SCC_I_OPERATIONCANCELED|Operazione annullata senza alcun effetto.|  
|SCC_I_RELOADFILE|Un progetto o il file deve essere ricaricato.|  
  
## <a name="remarks"></a>Note  
 L'IDE chiama questa funzione. Se il plug-in controllo del codice sorgente supporta la specifica di una cartella di destinazione locale, l'IDE passa `lpnFiles` = 1 e passa il nome di cartella locale in `lplpFileNames`.  
  
 Quando la chiamata al `SccAddFromScc` funzione viene restituito, il plug-in è assegnato valori a `lpnFiles` e `lplpFileNames`, allocare la memoria per la matrice di nome file in base alle esigenze (si noti che questa allocazione sostituisce il puntatore in `lplpFileNames`). Il plug-in controllo del codice sorgente è responsabile dell'immissione di tutti i file nella directory dell'utente o nella cartella designazione specificato. L'IDE aggiunge quindi i file al progetto IDE.  
  
 Infine, l'IDE chiama questa funzione una seconda volta, passando `NULL` per `lpnFiles`. Ciò viene interpretato come un segnale speciale per il plug-in per rilasciare la memoria allocata per la matrice di nomi di file nel controllo del codice sorgente`lplpFileNames``.`  
  
 `lplpFileNames`è un `char ***` puntatore. Il plug-in controllo del codice sorgente posiziona un puntatore a una matrice di puntatori ai nomi di file, quindi passando l'elenco nella modalità standard per questa API.  
  
> [!NOTE]
>  Le versioni iniziali dell'API VSSCI non ha fornito un modo per indicare il progetto di destinazione per i file aggiunti. Di conseguenza, la semantica del `lplpFIleNames` parametro sono stati migliorati per renderlo un parametro in/out anziché di un parametro di output. Se solo un singolo file è specificato, ovvero il valore a cui puntava `lpnFiles` = 1, quindi il primo elemento della `lplpFileNames` contiene la cartella di destinazione. Per usare questa nuova semantica, nell'IDE viene chiamato il `SccSetOption` utilizzabile con il `nOption`parametro impostato su `SCC_OPT_SHARESUBPROJ`. Se un plug-in controllo del codice sorgente non supporta la semantica, restituisce `SCC_E_OPTNOTSUPPORTED`. Questo modo viene disabilitata in questo caso l'utilizzo del **Aggiungi dal controllo del codice sorgente** funzionalità. Se un plug-in supporta il **Aggiungi dal controllo del codice sorgente** funzionalità (`SCC_CAP_ADDFROMSCC`), quindi deve supportare la nuova semantica e restituire `SCC_I_SHARESUBPROJOK`.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)