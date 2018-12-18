---
title: POPLISTFUNC | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: POPDIRLISTFUNC
helpviewer_keywords: POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dc15af65c6541df5ef77a3bdc85ee0e59fa20991
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="poplistfunc"></a>POPLISTFUNC
Questo callback viene fornito per il [SccPopulateList](../extensibility/sccpopulatelist-function.md) dall'IDE e viene utilizzato il plug-in controllo del codice sorgente per aggiornare un elenco di file o directory (anche fornito per il `SccPopulateList` funzione).  
  
 Quando un utente sceglie il **ottenere** comando nell'IDE, l'IDE visualizza una casella di riepilogo di tutti i file che l'utente può ottenere. Purtroppo, l'IDE non conosce l'esatto elenco di tutti i file che l'utente potrebbe visualizzare; solo il plug-in dispone di questo elenco. Se altri utenti aggiungere file al progetto di controllo del codice sorgente, questi file devono essere visualizzato nell'elenco, ma l'IDE non informati. L'IDE compila un elenco dei file che ritiene che l'utente può ottenere. Prima che questo elenco viene visualizzato all'utente, chiama il [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` assegnando il plug-in controllo del codice sorgente la possibilità di aggiungere ed eliminare i file dall'elenco.  
  
## <a name="signature"></a>Signature  
 Il plug-in controllo del codice sorgente modificato l'elenco chiamando una funzione implementata IDE con il seguente prototipo:  
  
```cpp  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Parametri  
 pvCallerData  
 Il `pvCallerData` parametro passato dal chiamante (IDE) per il [SccPopulateList](../extensibility/sccpopulatelist-function.md). Il plug-in controllo del codice sorgente di deve presupporre alcuna informazione sul contenuto di questo parametro.  
  
 fAddRemove  
 Se `TRUE`, `lpFileName` è un file che deve essere aggiunti all'elenco di file. Se `FALSE`, `lpFileName` è un file che deve essere eliminato dall'elenco di file.  
  
 nStatus  
 Stato di `lpFileName` (una combinazione del `SCC_STATUS` bits, vedere [codice di stato File](../extensibility/file-status-code-enumerator.md) per informazioni dettagliate).  
  
 lpFileName  
 Percorso completo della directory il nome del file per aggiungere o eliminare dall'elenco.  
  
## <a name="return-value"></a>Valore restituito  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`TRUE`|Il plug-in possono continuare a chiamare questa funzione.|  
|`FALSE`|Si è verificato un problema sul lato di IDE (ad esempio di situazione di memoria insufficiente). Il plug-in deve interrompere l'operazione.|  
  
## <a name="remarks"></a>Note  
 Per ogni file di plug-in controllo del codice sorgente si desidera aggiungere o eliminare dall'elenco dei file, chiama questa funzione, passando il `lpFileName`. Il `fAddRemove` flag indica un nuovo file da aggiungere all'elenco o un vecchio file da eliminare. Il `nStatus` parametro fornisce lo stato del file. Al termine del plug-in controllo configurazione sistema aggiungendo ed eliminando file, restituisce il [SccPopulateList](../extensibility/sccpopulatelist-function.md) chiamare.  
  
> [!NOTE]
>  Il `SCC_CAP_POPULATELIST` bit funzionalità è necessaria per Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Plug-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Codice di stato file](../extensibility/file-status-code-enumerator.md)