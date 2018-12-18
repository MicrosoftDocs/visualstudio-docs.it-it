---
title: CommentMarkProfile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ae602e6f28fc30c20c5b1f3c466d2e7afe458b8f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
La funzione `CommentMarkProfile` inserisce un indicatore numerico e una stringa di testo nel file VSP. Per l'indicatore e il commento da inserire, è necessario attivare la profilatura per il thread che contiene la funzione `CommentMarkProfile`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(  
                                   long lMarker,   
                                   LPCTSTR szComment);  
```  
  
#### <a name="parameters"></a>Parametri  
 `lMarker`  
  
 Indicatore numerico da inserire. L'indicatore deve essere maggiore o uguale a 0 (zero).  
  
 `szComment`  
  
 Puntatore alla stringa di testo da inserire. La stringa deve contenere meno di 256 caratteri, compreso il terminatore Null.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 La funzione indica esito l'esito positivo o negativo usando l'enumerazione **PROFILE_COMMAND_STATUS**. Il valore restituito può essere uno dei seguenti:  
  
|Enumerator|Descrizione|  
|----------------|-----------------|  
|MARK_ERROR_MARKER_RESERVED|Il parametro è minore o uguale a 0. Questi valori sono riservati. L'indicatore e il commento non vengono registrati.|  
|MARK_ERROR_MODE_NEVER|La modalità di profilatura è stata impostata su NEVER al momento della chiamata della funzione. L'indicatore e il commento non vengono registrati.|  
|MARK_ERROR_MODE_OFF|La modalità di profilatura è stata impostata su OFF al momento della chiamata della funzione. L'indicatore e il commento non vengono registrati.|  
|MARK_ERROR_NO_SUPPORT|Nessun supporto dell'indicatore in questo contesto. L'indicatore e il commento non vengono registrati.|  
|MARK_ERROR_OUTOFMEMORY|Non era disponibile memoria per registrare l'evento. L'indicatore e il commento non vengono registrati.|  
|MARK_TEXTTOOLONG|La stringa supera il numero massimo di 256 caratteri. La stringa di commento viene troncata e vengono registrati l'indicatore e il commento.|  
|MARK_OK|MARK_OK viene restituito per indicare l'esito positivo.|  
  
## <a name="remarks"></a>Note  
 Lo stato della profilatura per il thread che contiene la funzione di contrassegno del profilo deve essere attivo quando vengono inseriti indicatori e commenti con il comando Contrassegno di VSInstr o con le funzioni CommentMarkAtProfile, CommentMarkProfile o MarkProfile.  
  
 I contrassegni del profilo hanno ambito globale. Ad esempio, un contrassegno del profilo inserito in un solo thread può essere usato per contrassegnare l'inizio o la fine di un segmento di dati in qualsiasi thread del file VSP.  
  
> [!IMPORTANT]
>  Il metodo CommentMarkProfile può essere usato solo con la strumentazione.  
  
## <a name="net-framework-equivalent"></a>Equivalente .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informazioni sulla funzione  
  
|||  
|-|-|  
|**Intestazione**|Includere VSPerf.h|  
|**Libreria**|Usare VSPerf.lib|  
|**Unicode**|Implementato come `CommentMarkProfileW` (Unicode) e `CommentMarkProfileA` (ANSI).|  
  
## <a name="example"></a>Esempio  
 Il codice seguente illustra la chiamata della funzione CommentNameProfile. Nell'esempio si presuppone l'uso di macro di stringa Win32 e delle impostazioni del compilatore Unicode per stabilire se il codice chiama la funzione [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)].  
  
```  
void ExerciseCommentMarkProfile()  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkProfile(  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per le API del profiler di Visual Studio (native)](../profiling/visual-studio-profiler-api-reference-native.md)