---
title: Funzione SccGetProjPath | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ef5041b483e85e0806827f7d1188d432b476c5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath (funzione)
Questa funzione è richiesto all'utente per un percorso di progetto, è una stringa che è significativa solo per il plug-in controllo del codice sorgente. Viene chiamato quando l'utente è:  
  
-   Crea un nuovo progetto  
  
-   Aggiunta di un progetto esistente al controllo della versione  
  
-   Tentativo di trovare un progetto di controllo di versione esistente  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccGetProjPath (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPSTR  lpProjName,  
   LPSTR  lpLocalPath,  
   LPSTR  lpAuxProjPath,  
   BOOL   bAllowChangePath,  
   LPBOOL pbNew  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 hWnd  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 lpUser  
 [in, out] Il nome utente (da non superare SCC_USER_SIZE, incluso il carattere di terminazione NULL)  
  
 lpProjName  
 [in, out] Il nome del progetto IDE, dell'area di lavoro di progetto o makefile (da non superare SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).  
  
 lpLocalPath  
 [in, out] Percorso di lavoro del progetto. Se `bAllowChangePath` è `TRUE`, il plug-in controllo del codice sorgente è possibile modificare questa stringa (da non superare MAX_PATH, incluso il carattere di terminazione null).  
  
 lpAuxProjPath  
 [in, out] Un buffer per il percorso del progetto restituiti (da non superare SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).  
  
 bAllowChangePath  
 [in] Se si tratta di `TRUE`, il plug-in controllo del codice sorgente è possibile richiedere e modificare il `lpLocalPath` stringa.  
  
 pbNew  
 [in, out] Presto nel valore indica se creare un nuovo progetto. Valore restituito indica l'esito positivo della creazione di un progetto:  
  
|in ingresso|Interpretazione|  
|--------------|--------------------|  
|true|L'utente può creare un nuovo progetto.|  
|false|L'utente non può creare un nuovo progetto.|  
  
|In uscita|Interpretazione|  
|--------------|--------------------|  
|true|È stato creato un nuovo progetto.|  
|false|È stato selezionato un progetto esistente.|  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Il progetto è stato creato o recuperato.|  
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete.|  
|SCC_E_CONNECTIONFAILURE|Si è verificato un problema durante il tentativo di connettersi al sistema di controllo di origine.|  
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato.|  
  
## <a name="remarks"></a>Note  
 Lo scopo di questa funzione è per l'ambiente IDE di acquisire i parametri `lpProjName` e `lpAuxProjPath`. Dopo il plug-in controllo del codice sorgente richiede l'immissione di queste informazioni, passa questi due stringhe nell'IDE L'IDE persiste queste stringhe nel file di soluzione e li passa al [SccOpenProject](../extensibility/sccopenproject-function.md) ogni volta che l'utente apre il progetto. Queste stringhe di abilitare il plug-in tenere traccia delle informazioni associate a un progetto.  
  
 Quando viene innanzitutto chiamata la funzione, `lpAuxProjPath` è impostata su una stringa vuota. `lProjName` potrebbe anche essere vuota o contenere il nome del progetto IDE, che può usare o ignorare il plug-in del controllo del codice sorgente. Quando la funzione restituisce correttamente, il plug-in restituisce le due stringhe corrispondenti. L'IDE non fa alcuna ipotesi sulle stringhe di queste non verrà utilizzati e non consente all'utente di modificarli. Se l'utente decide di modificare le impostazioni, l'IDE chiamerà `SccGetProjPath` nuovamente, passando gli stessi valori ha ricevuto l'ora precedente. In questo modo il plug-in del controllo completo su questi due stringhe.  
  
 Per `lpUser`, l'IDE è possibile passare un nome utente o può semplicemente passare un puntatore a una stringa vuota. Se è presente un nome utente, il plug-in controllo del codice sorgente necessario utilizzarlo come valore predefinito. Tuttavia, se è stato passato alcun nome o l'account di accesso non riuscito con il nome specificato, il plug-in deve richiedere all'utente di accesso e passare nuovamente il nome `lpUser` quando riceve un account di accesso valido. Dato che il plug-in potrebbe cambiare questa stringa, l'IDE verrà sempre allocare un buffer di dimensione (`SCC_USER_LEN`+ 1).  
  
> [!NOTE]
>  La prima azione che esegue l'IDE può essere una chiamata a uno di `SccOpenProject` funzione o `SccGetProjPath` (funzione). Di conseguenza, essi dispongono di identica `lpUser` parametro, che consente l'accesso dell'utente in fase di plug-in controllo del codice sorgente. Anche se il valore restituito dalla funzione indica un errore, il plug-in necessario inserire la stringa con un nome di account di accesso valido.  
  
 `lpLocalPath` è la directory in cui l'utente mantiene il progetto. Può essere una stringa vuota. Se è disponibile alcuna directory attualmente definito (come nel caso di un utente è stato eseguito un tentativo di scaricare un progetto dal sistema di controllo di origine) e `bAllowChangePath` è `TRUE`, il plug-in controllo del codice sorgente può richiedere l'input dell'utente o utilizzare un altro metodo per inserire la proprietà stringa in `lpLocalPath`. Se `bAllowChangePath` è `FALSE`, il plug-in necessario non modificare la stringa, perché l'utente sta già nella directory specificata.  
  
 Se l'utente crea un nuovo progetto da inserire nel controllo del codice sorgente, il plug-in controllo del codice sorgente potrebbe non effettivamente crearla nel sistema di controllo di origine al momento `SccGetProjPath` viene chiamato. Invece, passa nuovamente la stringa lungo con un valore diverso da zero per `pbNew`, che indica che il progetto verrà creato nel sistema di controllo di origine.  
  
 Ad esempio, se un utente di **nuovo progetto** in Visual Studio viene aggiunto il proprio progetto al controllo del codice sorgente, Visual Studio chiama questa funzione e determina il plug-in se è possibile creare un nuovo progetto nel sistema di controllo di origine per contiene il progetto di Visual Studio. Se l'utente fa clic **Annulla** prima di completare la procedura guidata, non è mai stato creato il progetto. Se l'utente fa clic **OK**, Visual Studio chiama `SccOpenProject`, passando `SCC_OPT_CREATEIFNEW`, e viene creato il progetto di controllo del codice sorgente in quel momento.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)