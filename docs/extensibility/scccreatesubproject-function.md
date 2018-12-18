---
title: Funzione SccCreateSubProject | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa87be4c9d22aca46814e8fa284fda9d587386a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject (funzione)
Questa funzione crea un sottoprogetto con il nome specificato in un progetto padre esistente specificato per il `lpParentProjPath` argomento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccCreateSubProject(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpParentProjPath,  
   LPCSTR lpSubProjName,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpSubProjPath  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] Il puntatore di contesto plug-in controllo di origine.  
  
 hWnd  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 lpUser  
 [in, out] Il nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione NULL).  
  
 lpParentProjPath  
 [in] Stringa che identifica il percorso del progetto principale (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).  
  
 lpSubProjName  
 [in] Il nome suggerito sottoprogetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).  
  
 lpAuxProjPath  
 [in, out] Ausiliario stringa che identifica il progetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).  
  
 lpSubProjPath  
 [in, out] Stringa di output che identifica il percorso per il sottoprogetto (fino a SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Sottoprogetto creato correttamente.|  
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il progetto principale.|  
|SCC_E_INVALIDUSER|L'utente non può accedere per il controllo del codice sorgente.|  
|SCC_E_COULDNOTCREATEPROJECT|Impossibile creare il sottoprogetto.|  
|SCC_E_PROJSYNTAXERR|Sintassi non valida del progetto.|  
|SCC_E_UNKNOWNPROJECT|Il progetto principale è sconosciuto per il plug-in controllo del codice sorgente.|  
|SCC_E_INVALIDFILEPATH|Percorso del file non valido o è inutilizzabile.|  
|SCC_E_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_CONNECTIONFAILURE|Si è verificato un problema di connessione del plug-in controllo di origine.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Se esiste già un sottoprogetto con il nome, la funzione può modificare il nome predefinito per creare uno univoco, ad esempio aggiungendo "_\<numero >" a esso. Il chiamante deve essere preparato ad accettare le modifiche apportate a `lpUser`, `lpSubProjPath`, e `lpAuxProjPath`. Il `lpSubProjPath` e`lpAuxProjPath` gli argomenti vengono quindi utilizzati in una chiamata al [SccOpenProject](../extensibility/sccopenproject-function.md). Non devono essere modificati dal chiamante al momento della restituzione. Queste stringhe forniscono un modo per il plug-in per tenere traccia delle informazioni che è necessario associare a un progetto di controllo del codice sorgente. Il chiamante IDE non visualizzerà questi due parametri al momento della restituzione, in quanto il plug-in può utilizzare una stringa formattata che potrebbe non essere appropriata per la visualizzazione. La funzione restituisce un codice di esito positivo o negativo e, se ha esito positivo, inserisce la variabile `lpSubProjPath` con il percorso di progetto completo al nuovo progetto.  
  
 Questa funzione è simile al [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ad eccezione del fatto che viene creato automaticamente un progetto, anziché richiedere all'utente di selezionare uno. Quando il `SccCreateSubProject` funzione viene chiamata, `lpParentProjName` e `lpAuxProjPath` non sarà vuoto e corrisponde a un progetto valido. Queste stringhe in genere vengono ricevute dall'IDE da una precedente chiamata al `SccGetProjPath` funzione o [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).  
  
 Il `lpUser` argomento è il nome utente. L'IDE verrà passato lo stesso nome utente che ha ricevuto in precedenza da `SccGetProjPath`, e il plug-in controllo del codice sorgente è necessario utilizzare il nome come valore predefinito. Se l'utente dispone già di una connessione aperta con il plug-in, il plug-in deve provare a eliminare qualsiasi chiede di verificare che il funzionamento invisibile all'utente. Tuttavia, se l'account di accesso non riesce, il plug-in deve richiedere all'utente per un account di accesso e, quando riceve un account di accesso valido, passare il nome del nuovo `lpUser`. Dato che il plug-in potrebbe cambiare questa stringa, l'IDE verrà sempre allocare un buffer di dimensione (SCC_USER_LEN + 1 o SCC_USER_SIZE, che include lo spazio per il carattere di terminazione null). Se la stringa viene modificata, la nuova stringa deve essere un nome di account di accesso valido (almeno come valido della stringa precedente).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Note tecniche per SccCreateSubProject e SccGetParentProjectPath  
 Aggiunta di soluzioni e progetti al controllo del codice sorgente è stata semplificata in Visual Studio per ridurre al minimo il numero di volte in cui che un utente viene richiesto di selezionare i percorsi nel sistema di controllo di origine. Queste modifiche sono attivate da Visual Studio, se un plug-in controllo del codice sorgente supporta sia delle nuove funzioni, `SccCreateSubProject` e `SccGetParentProjectPath`. Tuttavia, la seguente voce del Registro di sistema consente di disabilitare queste modifiche e ripristinare il comportamento precedente di Visual Studio (origine controllo plug-in API versione 1.1):  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
 Se questa voce del Registro di sistema non esiste o è impostata su DWORD: 00000000, Visual Studio tenterà di utilizzare le nuove funzioni, `SccCreateSubProject` e `SccGetParentProjectPath`.  
  
 Se la voce del Registro di sistema è impostata su DWORD: 00000001, Visual Studio non tenta di utilizzare le nuove funzioni e le operazioni di aggiunta al controllo del codice sorgente funzionano come nelle versioni precedenti di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)