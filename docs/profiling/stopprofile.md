---
title: StopProfile | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: StopProfile
ms.assetid: be75b03c-7af5-4abe-a54a-6ee5479ad877
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 36da7be52d9b40c8f2e8c837bb137e8e1d9c296f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="stopprofile"></a>StopProfile
La funzione `StopProfile` imposta il contatore su 0 (OFF) per il livello di profilatura specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StopProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parametri  
 `Level`  
  
 Indica il livello di profilatura a cui può essere applicata la raccolta di dati sulle prestazioni. Gli enumeratori **PROFILE_CONTROL_LEVEL** seguenti possono essere usati per indicare uno dei tre livelli a cui può essere applicata la raccolta di dati sulle prestazioni:  
  
|Enumerator|Descrizione|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Impostazione del livello globale con effetti su tutti i processi e i thread nell'esecuzione della profilatura.|  
|PROFILE_PROCESSLEVEL|Impostazione del livello processo con effetti su tutti i thread che fanno parte del processo specificato.|  
|PROFILE_THREADLEVEL|Impostazione del livello thread con effetti sul thread specificato.|  
  
 `dwId`  
  
 Identificatore del processo o del thread generato dal sistema.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 La funzione indica esito l'esito positivo o negativo usando l'enumerazione **PROFILE_COMMAND_STATUS**. Il valore restituito può essere uno dei seguenti:  
  
|Enumerator|Descrizione|  
|----------------|-----------------|  
|PROFILE_ERROR_ID_NOEXIST|L'ID dell'elemento di profilatura non esiste.|  
|PROFILE_ERROR_LEVEL_NOEXIST|Il livello di profilatura specificato non esiste.|  
|PROFILE_ERROR_MODE_NEVER|La modalità di profilatura è stata impostata su NEVER al momento della chiamata della funzione.|  
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|La chiamata della funzione di profilatura, il livello di profilatura o la combinazione di chiamata e livello non sono ancora stati implementati.|  
|PROFILE_OK|La chiamata è stata completata correttamente.|  
  
## <a name="remarks"></a>Note  
 StartProfile e StopProfile controllano lo stato di Start/Stop per il livello di profilatura. Il valore predefinito di Start/Stop è 1. Il valore iniziale può essere modificato nel Registro di sistema. Ogni chiamata a StartProfile imposta Start/Stop su 1. Ogni chiamata a StopProfile lo imposta su 0.  
  
 Quando Start/Stop è maggiore di 0, lo stato di Start/Stop per il livello è impostato su ON. Quando è minore o uguale a 0, lo stato di Start/Stop è OFF.  
  
 Se lo stato di Start/Stop e lo stato di Suspend/Resume sono entrambi ON, lo stato di profilatura per il livello è ON. Affinché un thread venga incluso nella profilatura, gli stati dei livelli globale, processo e thread per il thread devono essere ON.  
  
## <a name="net-framework-equivalent"></a>Equivalente .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informazioni sulla funzione  
 Intestazione: dichiarata in VSPerf.h  
  
 Libreria di importazione: VSPerf.lib  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra il metodo StopProfile. Nell'esempio si presuppone che sia stata effettuata una chiamata al metodo StartProfile per lo stesso thread o processo identificato da [PROFILE_CURRENTID](../profiling/profile-currentid.md).  
  
```  
void ExerciseStopProfile()  
{  
    // StartProfile and StopProfile control the   
    // Start/Stop state for the profiling level.   
    // The default initial value of Start/Stop is 1.   
    // The initial value can be changed in the registry.   
    // Each call to StartProfile sets Start/Stop to 1;   
    // each call to StopProfile sets it to 0.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call  
    // to StopProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StopProfile(  
        PROFILE_THREADLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StopProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per le API del profiler di Visual Studio (native)](../profiling/visual-studio-profiler-api-reference-native.md)