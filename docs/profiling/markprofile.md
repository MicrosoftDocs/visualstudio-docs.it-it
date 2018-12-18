---
title: MarkProfile | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MarkProfile
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f9bc5537bf877afd3ff83d91516fe37d472c859f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="markprofile"></a>MarkProfile
Il metodo `MarkProfile` inserisce un contrassegno del profilo nel file con estensione vsp. La profilatura per il thread che contiene la funzione `MarkProfile` deve essere impostata su ON affinché il contrassegno possa essere inserito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );  
```  
  
#### <a name="parameters"></a>Parametri  
 `lMarker`  
  
 Marcatore da inserire. Il marcatore deve essere maggiore o uguale a 0 (zero).  
  
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
 Il valore del contrassegno viene inserito nel file con estensione vsp ogni volta che il codice viene eseguito se il thread che contiene la funzione MarkProfile è in corso di profilatura. È possibile chiamare MarkProfile più volte.  
  
 I contrassegni di profilatura hanno ambito globale. Ad esempio, un contrassegno di profilatura inserito in un thread può essere usato per contrassegnare l'inizio o alla fine di un segmento di dati in qualsiasi thread nel file vsp.  
  
 Lo stato di profilatura per il thread che contiene la funzione del contrassegno di profilatura deve essere attivo quando vengono inseriti contrassegni e commenti con il comando Contrassegno o con le funzioni API (CommentMarkAtProfile, CommentMarkProfile o MarkProfile).  
  
> [!IMPORTANT]
>  Il metodo MarkProfile deve essere usato solo con la profilatura con il metodo di strumentazione.  
  
## <a name="net-framework-equivalent"></a>Equivalente .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informazioni sulla funzione  
 Intestazione: dichiarata in VSPerf.h  
  
 Libreria di importazione: VSPerf.lib  
  
## <a name="example"></a>Esempio  
 Il codice seguente illustra la funzione MarkProfile.  
  
```  
void ExerciseMarkProfile()  
{  
    // Declare and initialize variables to pass to   
    // MarkProfile.  The values of these parameters   
    // are assigned based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variables are assigned arbitrary values.  
    int markId = 03;  
  
    // Declare enumeration to hold return value of   
    // call to MarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    markResult = MarkProfile(markId);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("MarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per le API del profiler di Visual Studio (native)](../profiling/visual-studio-profiler-api-reference-native.md)