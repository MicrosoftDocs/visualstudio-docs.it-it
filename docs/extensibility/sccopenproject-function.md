---
title: Funzione SccOpenProject | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 15d9cf6d5fa4533b5ee0ff65f8aeae86df3d571a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccopenproject-function"></a>SccOpenProject (funzione)
Questa funzione consente di aprire un progetto di controllo di origine esistente o crearne una nuova.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccOpenProject (  
   LPVOID        pvContext,  
   HWND          hWnd,  
   LPSTR         lpUser,  
   LPCSTR        lpProjName,  
   LPCSTR        lpLocalProjPath,  
   LPSTR         lpAuxProjPath,  
   LPCSTR        lpComment,  
   LPTEXTOUTPROC lpTextOutProc,  
   LONG          dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 hWnd  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 lpUser  
 [in, out] Il nome dell'utente (da non superare SCC_USER_SIZE, incluso il carattere di terminazione NULL).  
  
 lpProjName  
 [in] Stringa che identifica il nome del progetto.  
  
 lpLocalProjPath  
 [in] Il percorso alla cartella di lavoro per il progetto.  
  
 lpAuxProjPath  
 [in, out] Stringa facoltativa ausiliaria identificazione del progetto (da non superare SCC_AUXPATH_SIZE, incluso il carattere di terminazione NULL).  
  
 lpComment  
 [in] Commento a un nuovo progetto da creare.  
  
 lpTextOutProc  
 [in] Una funzione di callback facoltativo per visualizzare il testo di output dal plug-in controllo del codice sorgente.  
  
 dwFlags  
 [in] Segnala se deve essere creato se il progetto è sconosciuto all'origine di un nuovo progetto di controllo di plug-in. Valore può essere una combinazione di `SCC_OP_CREATEIFNEW` e `SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione completata durante l'apertura del progetto.|  
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il progetto.|  
|SCC_E_INVALIDUSER|L'utente non può accedere per il controllo del codice sorgente.|  
|SCC_E_COULDNOTCREATEPROJECT|Il progetto non esisteva prima della chiamata.  il `SCC_OPT_CREATEIFNEW` è stato impostato, ma il progetto non è stato creato.|  
|SCC_E_PROJSYNTAXERR|Sintassi non valida del progetto.|  
|SCC_E_UNKNOWNPROJECT|Il progetto è sconosciuto al plug-in, il controllo del codice sorgente e `SCC_OPT_CREATEIFNEW` flag non è stato impostato.|  
|SCC_E_INVALIDFILEPATH|Percorso del file non valido o è inutilizzabile.|  
|SCC_E_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NONSPECFICERROR|Un errore non specifico. il controllo del codice sorgente non è stato inizializzato.|  
  
## <a name="remarks"></a>Note  
 L'IDE è possibile passare un nome utente (`lpUser`), o può semplicemente passare un puntatore a una stringa vuota. Se è presente un nome utente, il plug-in controllo del codice sorgente necessario utilizzarlo come valore predefinito. Tuttavia, se è stato passato alcun nome, o se l'account di accesso non riuscito con il nome specificato, il plug-in deve richiedere all'utente di accesso e restituirà il nome valido in `lpUser` quando riceve un account di accesso valido`.` perché la stringa del nome utente può modificare il plug-in , l'IDE verrà sempre allocare un buffer di dimensione (`SCC_USER_LEN`+ 1 o SCC_USER_SIZE, che include lo spazio per il carattere di terminazione null).  
  
> [!NOTE]
>  La prima azione IDE potrebbe essere necessario eseguire può essere una chiamata al `SccOpenProject` funzione o [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Per questo motivo, essi dispongono di un'identica `lpUser` parametro.  
  
 `lpAuxProjPath` e`lpProjName` vengono lette dal file di soluzione o vengono restituiti da una chiamata al `SccGetProjPath` (funzione). Questi parametri contengano le stringhe che associa il controllo del codice sorgente plug-in al progetto e sono significativi solo per il plug-in. Se tali stringhe non sono presenti nel file di soluzione e l'utente non è stato richiesto di passare (che restituisce una stringa tramite il `SccGetProjPath` (funzione)), l'IDE passa stringhe vuote per entrambi `lpAuxProjPath` e `lpProjName`e non prevede questi valori da aggiornare per il plug-in quando questa funzione restituisce.  
  
 `lpTextOutProc` è un puntatore a una funzione di callback fornita dall'IDE per il plug-in per la visualizzazione di output dei risultati comando controllo del codice sorgente. Questa funzione di callback è descritto dettagliatamente in [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
> [!NOTE]
>  Se il plug-in controllo del codice sorgente intenzione di sfruttare i vantaggi di questo, è necessario impostare il `SCC_CAP_TEXTOUT` flag nel [SccInitialize](../extensibility/sccinitialize-function.md). Se tale flag non è stata impostata o se l'IDE non supporta questa funzionalità, `lpTextOutProc` sarà `NULL`.  
  
 Il `dwFlags` parametro controlla il risultato nel caso in cui il progetto viene aperto non esiste. È costituito da due flag di bit, `SCC_OP_CREATEIFNEW` e `SCC_OP_SILENTOPEN`. Se esiste il progetto è già aperto, la funzione semplicemente il progetto viene aperto e restituisce `SCC_OK`. Se il progetto non esiste e se il `SCC_OP_CREATEIFNEW` flag è attivato, il plug-in controllo del codice sorgente può creare il progetto nel sistema di controllo di origine, aprirlo e restituire `SCC_OK`. Se il progetto non esiste e se il `SCC_OP_CREATEIFNEW` flag è disattivata, il plug-in deve quindi cercare la `SCC_OP_SILENTOPEN` flag. Se tale flag non è abilitata, il plug-in potrebbe richiedere all'utente un nome di progetto. Se tale flag è attivato, il plug-in deve semplicemente restituire `SCC_E_UNKNOWNPROJECT`.  
  
## <a name="calling-order"></a>Ordine di chiamata  
 Durante il normale funzionamento degli eventi, il [SccInitialize](../extensibility/sccinitialize-function.md) deve essere chiamato prima di tutto per aprire una sessione di controllo di origine. Una sessione può essere costituito da una chiamata a `SccOpenProject`, seguito da altre chiamate di funzioni API plug-in controllo di origine e terminerà con una chiamata al [SccCloseProject](../extensibility/scccloseproject-function.md). Tali sessioni possono essere ripetuti più volte prima di [SccUninitialize](../extensibility/sccuninitialize-function.md) viene chiamato.  
  
 Se l'origine del controllo di set di plug-in di `SCC_CAP_REENTRANT` bit `SccInitialize`, quindi la sequenza di sessione precedente può essere ripetuta più volte in parallelo. Diversi `pvContext` strutture di rilevare le diverse sessioni in cui ogni `pvContext` è associata a un progetto aperto in una fase. In base il`pvContext` parametro, il plug-in può determinare quale progetto fa riferimento in qualsiasi chiamata particolare. Se la funzionalità di bit `SCC_CAP_REENTRANT` non è impostata, nonreentrant plug-in del controllo codice sorgente sono limitate per la capacità di lavorare con più progetti.  
  
> [!NOTE]
>  Il `SCC_CAP_REENTRANT` bit è stata introdotta nella versione 1.1 dell'API plug-in controllo di origine. Non è impostata oppure viene ignorato nella versione 1.0 e tutti versione 1.0 origine plug-in del controllo vengono considerati come nonreentrant.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [Restrizioni sulle lunghezze di stringa](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)