---
title: CommentMarkAtProfile | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7f196a9e2c5951037c215dfd69fd29864b72cd41
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
Il metodo `CommentMarkAtProfile` inserisce un valore di timestamp, un indicatore numerico e una stringa di commento nel file VSP. Il valore di timestamp può essere usato per sincronizzare gli eventi esterni. Per l'indicatore e il commento da inserire, è necessario attivare la profilatura per il thread che contiene la funzione CommentMarkAtProfile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
                                   __int64 dnTimestamp,  
                                   long lMarker,  
                                   LPCTSTR szComment);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dnTimestamp`  
  
 Intero a 64 bit che rappresenta un valore di timestamp.  
  
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
 Lo stato della profilatura per il thread che contiene la funzione di contrassegno del profilo deve essere attivo quando vengono inseriti indicatori e commenti con il comando Contrassegno o con le funzioni API (CommentMarkAtProfile, CommentMarkProfile o MarkProfile). I contrassegni del profilo hanno ambito globale. Ad esempio, un contrassegno del profilo inserito in un solo thread può essere usato per contrassegnare l'inizio o la fine di un segmento di dati in qualsiasi thread del file VSP.  
  
> [!IMPORTANT]
>  I metodi CommentMarkAtProfile devono essere usati con solo con la strumentazione.  
  
## <a name="net-framework-equivalent"></a>Equivalente .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informazioni sulla funzione  
  
|||  
|-|-|  
|**Intestazione**|Includere VSPerf.h|  
|**Libreria**|Usare VSPerf.lib|  
|**Unicode**|Implementato come CommentMarkAtProfileW (Unicode) e CommentMarkAtProfileA (ANSI).|  
  
## <a name="example"></a>Esempio  
 Il codice seguente illustra l'uso della chiamata della funzione generica CommentMarkAtProfile. Nell'esempio si presuppone l'uso di macro stringa Win32 e delle impostazioni del compilatore per ANSI per stabilire se il codice chiama la funzione abilitata per ANSI.  
  
```  
void ExerciseCommentMarkAtProfile(void)  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkAtProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    int64 timeStamp = 0x1111;  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkAtProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkAtProfile(  
        timeStamp,  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
    pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per le API del profiler di Visual Studio (native)](../profiling/visual-studio-profiler-api-reference-native.md)