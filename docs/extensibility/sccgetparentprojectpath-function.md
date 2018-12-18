---
title: Funzione SccGetParentProjectPath | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea52e0d4c6242c57447cd47d41b716ba5e93a2f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath (funzione)
Questa funzione determina il percorso del progetto padre di un progetto specificato. Questa funzione viene chiamata quando l'utente aggiunge un progetto di Visual Studio a controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] Il puntatore di contesto plug-in controllo di origine.  
  
 hWnd  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 lpUser  
 [in, out] Il nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione NULL).  
  
 lpProjPath  
 [in] Stringa che identifica il percorso del progetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).  
  
 lpAuxProjPath  
 [in, out] Ausiliario stringa che identifica il progetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).  
  
 lpParentProjPath  
 [in, out] Stringa di output che identifica il percorso del progetto padre (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Percorso del progetto padre è stata ottenuta correttamente.|  
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il progetto.|  
|SCC_E_INVALIDUSER|L'utente non può accedere per il plug-in controllo del codice sorgente.|  
|SCC_E_UNKNOWNPROJECT|Progetto è sconosciuto per il plug-in controllo del codice sorgente.|  
|SCC_E_INVALIDFILEPATH|Percorso del file non valido o è inutilizzabile.|  
|SCC_E_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_PROJSYNTAXERR|Sintassi non valida del progetto.|  
|SCC_E_CONNECTIONFAILURE|Problema di connessione di archivio.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Questa funzione restituisce un codice di esito positivo o negativo e, se ha esito positivo, inserisce la variabile `lpParentProjPath` con il percorso di progetto completo per il progetto specificato.  
  
 Questa funzione restituisce l'elemento padre di percorso del progetto di un progetto esistente. Per il progetto di primo livello, la funzione restituisce il percorso del progetto che è stato passato (vale a dire lo stesso progetto percorso radice). Si noti che un percorso di progetto è una stringa che è significativa solo per il plug-in controllo del codice sorgente.  
  
 L'IDE è pronto per accettare le modifiche per il `lpUser` e `lpAuxProjPath` nonché i parametri. L'IDE verrà mantenere queste stringhe e passarli al [SccOpenProject](../extensibility/sccopenproject-function.md) quando l'utente apre il progetto in futuro. Queste stringhe, pertanto, forniscono un modo per il plug-in per le informazioni di traccia è necessario associare a un progetto di controllo del codice sorgente.  
  
 Questa funzione è simile al [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ad eccezione del fatto che non visualizzata una richiesta all'utente di selezionare un progetto. Crea inoltre mai un nuovo progetto, ma funziona solo con un progetto esistente.  
  
 Quando `SccGetParentProjectPath` viene chiamato, `lpProjPath` e `lpAuxProjPath` non sarà vuoto e corrisponde a un progetto valido. Queste stringhe in genere vengono ricevute dall'IDE da una precedente chiamata al `SccGetProjPath` (funzione).  
  
 Il `lpUser` argomento è il nome utente. L'IDE lo stesso nome utente che ha ricevuto in precedenza da verrà passato il `SccGetProjPath` (funzione) e il plug-in controllo del codice sorgente devono utilizzare il nome come valore predefinito. Se l'utente dispone già di una connessione aperta con il plug-in, il plug-in deve provare a eliminare qualsiasi chiede di verificare che il funzionamento invisibile all'utente. Tuttavia, se l'account di accesso non riesce, il plug-in deve richiedere all'utente per un account di accesso e, quando riceve un account di accesso valido, passare il nome del nuovo `lpUser`. Dato che il plug-in potrebbe cambiare questa stringa, l'IDE verrà sempre allocare un buffer di dimensione (`SCC_USER_LEN`+ 1). Se la stringa viene modificata, la nuova stringa deve essere un nome di account di accesso valido (almeno come valido della stringa precedente).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Note tecniche per SccCreateSubProject e SccGetParentProjectPath  
 Aggiunta di soluzioni e progetti al controllo del codice sorgente è stata semplificata in Visual Studio per ridurre al minimo il numero di volte in cui che un utente viene richiesto di selezionare i percorsi nel sistema di controllo di origine. Queste modifiche sono attivate da Visual Studio, se un plug-in controllo del codice sorgente supporta sia delle nuove funzioni, il [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) e `SccGetParentProjectPath` (funzione). Tuttavia, la seguente voce del Registro di sistema consente di disattivare queste modifiche e ripristinare il comportamento precedente di Visual Studio (origine controllo plug-in API versione 1.1):  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
 Se questa voce del Registro di sistema non esiste o è impostata su DWORD: 00000000, Visual Studio tenterà di utilizzare le nuove funzioni, `SccCreateSubProject`e`SccGetParentProjectPath`.  
  
 Se la voce del Registro di sistema è impostata su DWORD: 00000001, Visual Studio non tenta di utilizzare le nuove funzioni e le operazioni di aggiunta al controllo del codice sorgente funzionano come nelle versioni precedenti di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)