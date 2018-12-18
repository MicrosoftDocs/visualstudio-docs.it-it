---
title: Funzione SccSetOption | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccSetOption
helpviewer_keywords: SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 70fe624984adce58191ee7d354185eac0bb527ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="sccsetoption-function"></a>SccSetOption (funzione)
La funzione imposta le opzioni che controllano il comportamento di plug-in controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 nOption  
 [in] L'opzione da impostare.  
  
 dwVal  
 [in] Impostazioni per l'opzione.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|È stata impostata l'opzione.|  
|SCC_I_SHARESUBPROJOK|Restituito se `nOption` stato `SCC_OPT_SHARESUBPROJ` e il plug-in controllo del codice sorgente consente l'IDE impostare la cartella di destinazione.|  
|SCC_E_OPNOTSUPPORTED|L'opzione non è stata impostata e non è affidabile.|  
  
## <a name="remarks"></a>Note  
 L'IDE chiama questa funzione per controllare il comportamento di plug-in controllo del codice sorgente. Il primo parametro, `nOption`, indica il valore è impostato, mentre il secondo, `dwVal`, indica che cosa fare con tale valore. Il plug-in archivia le informazioni associate un `pvContext``,` l'IDE è necessario chiamare questa funzione dopo la chiamata di [SccInitialize](../extensibility/sccinitialize-function.md) (ma non necessariamente dopo ogni chiamata al [SccOpenProject](../extensibility/sccopenproject-function.md)).  
  
 Riepilogo delle opzioni e i relativi valori:  
  
|`nOption`|`dwValue`|Descrizione|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Abilita/disabilita l'accodamento messaggi di eventi in background.|  
|`SCC_OPT_USERDATA`|Valore arbitrario|Specifica un valore dall'utente deve essere passato il [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) funzione di callback.|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indica se l'IDE supporta attualmente un'operazione di annullamento.|  
|`SCC_OPT_NAMECHANGEPFN`|Puntatore al [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) funzione di callback|Imposta un puntatore a una funzione di callback modifica del nome.|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indica se l'IDE consente l'estrazione i file manualmente (tramite interfaccia utente del controllo di origine) o se è necessario estrarre solo tramite il plug-in controllo del codice sorgente.|  
|`SCC_OPT_SHARESUBPROJ`|N/D|Se il plug-in controllo del codice sorgente consente l'IDE specificare la cartella del progetto locale, il plug-in restituisce `SCC_I_SHARESUBPROJOK`.|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 Se `nOption` è `SCC_OPT_EVENTQUEUE`, l'IDE è disabilitazione (o la riabilitazione) l'elaborazione in background. Ad esempio, durante una compilazione, l'IDE può indicare il plug-in per arrestare l'elaborazione su inattivo di qualsiasi tipo di controllo del codice sorgente. Dopo la compilazione, abilitano nuovamente l'elaborazione in background per mantenere aggiornato coda eventi il plug-in. Corrispondente per il `SCC_OPT_EVENTQUEUE` valore `nOption`, esistono due possibili valori per `dwVal`, vale a dire, `SCC_OPT_EQ_ENABLE` e `SCC_OPT_EQ_DISABLE`.  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 Se il valore per `nOption` è `SCC_OPT_HASCANCELMODE`, l'IDE consente agli utenti di annullare l'esecuzione di operazioni lunghe. Impostazione `dwVal` a `SCC_OPT_HCM_NO` (predefinito) indica che l'IDE non possiede alcuna modalità di annullamento. Se desidera che l'utente sia in grado di annullare, il plug-in controllo del codice sorgente deve offrire il proprio pulsante Annulla. `SCC_OPT_HCM_YES`indica che l'IDE offre la possibilità di annullare un'operazione, pertanto il plug-in controllo del codice sorgente non è necessario visualizzare un pulsante Annulla. Se l'IDE imposta `dwVal` a `SCC_OPT_HCM_YES`, si è pronti a `SCC_MSG_STATUS` e `DOCANCEL` i messaggi inviati al `lpTextOutProc` funzione di callback (vedere [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Se l'IDE non impostare questa variabile, il plug-in non devono inviare questi due messaggi.  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 Se nOption è impostata su `SCC_OPT_NAMECHANGEPFN`, sia l'origine e plug-in controllo e l'IDE lo consentono, il plug-in effettivamente rinominare o spostare un file durante un'operazione di controllo del codice sorgente. Il `dwVal` verrà impostato su un puntatore a funzione di tipo [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Durante un'operazione di controllo del codice sorgente, il plug-in può chiamare questa funzione, il passaggio di tre parametri. Questi sono il nome esistente (con il percorso completo) di un file, il nuovo nome (con il percorso completo) del file e un puntatore alle informazioni che sono pertinente per l'IDE. L'IDE invia in questo ultimo puntatore chiamando `SccSetOption` con `nOption` impostato su `SCC_OPT_USERDATA`, con `dwVal` che punta ai dati. Supporto per questa funzione è facoltativo. Un plug VSSCI-che utilizza questa possibilità deve inizializzare le variabili di dati utente e puntatore funzione per `NULL`, e non deve chiamare una funzione rename a meno che non abbia ricevuto uno. Deve inoltre essere preparata per contenere il valore specificato o per modificare le impostazioni in risposta a una nuova chiamata a `SccSetOption`. Questa operazione non verrà eseguita all'interno di un'operazione di comando di controllo codice sorgente, ma potrebbe verificarsi tra i comandi.  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 Se nOption è impostata su `SCC_OPT_SCCCHECKOUTONLY`, l'IDE indica che i file di progetto aperto non devono mai essere estratti manualmente tramite l'interfaccia utente del sistema di controllo di origine. Al contrario, i file devono essere estratto solo tramite il controllo del codice sorgente plug-nel controllo IDE. Se `dwValue` è impostato su `SCC_OPT_SCO_NO`, significa che i file devono essere trattati in genere per il plug-in e possono essere estratti tramite il controllo del codice sorgente dell'interfaccia utente. Se `dwValue` è impostato su `SCC_OPT_SCO_YES`, quindi solo il plug-in è possibile estrarre i file e dell'interfaccia utente del sistema di controllo di origine non deve essere richiamato. Si tratta di situazioni in cui l'IDE potrebbe dispone "pseudo-file" senso per estrarre solo tramite l'IDE.  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 Se`nOption` è impostato su `SCC_OPT_SHARESUBPROJ`, l'IDE è la verifica se il plug-in controllo del codice sorgente è possibile utilizzare una cartella locale specificata quando si aggiungono file dal controllo del codice sorgente. Il valore di `dwVal` parametro non è importante in questo caso. Se il plug-in consente l'IDE specificare la cartella di destinazione locale in cui i file verranno aggiunte dall'origine controllare quando il [SccAddFromScc](../extensibility/sccaddfromscc-function.md) viene chiamato, il plug-in deve restituire `SCC_I_SHARESUBPROJOK` quando il `SccSetOption` è (funzione) chiamato. L'IDE Usa quindi il `lplpFileNames` parametro il `SccAddFromScc` funzione passare nella cartella di destinazione. Il plug-in utilizza tale cartella di destinazione per inserire i file aggiunti dal controllo del codice sorgente. Se il plug-in non restituisce `SCC_I_SHARESUBPROJOK` quando il `SCC_OPT_SHARESUBPROJ` opzione è impostata, l'IDE si presuppone che il plug-in è in grado di aggiungere i file soltanto nella cartella locale corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)