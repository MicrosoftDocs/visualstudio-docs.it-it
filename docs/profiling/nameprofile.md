---
title: NameProfile | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- NameProfile
- NameProfileA
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0b717882e943a37857bbdadf3d318f94b4900dc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="nameprofile"></a>NameProfile
La funzione `NameProfile` assegna una stringa al processo o al thread specificato.  
  
 L'API NameProfile è disponibile solo per la profilatura con il metodo di strumentazione. L'API NameProfile non è supportata per la profilatura con il metodo di campionamento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszName`  
  
 Nome dell'elemento di profilatura. Un nome non è valido (NameProfileA restituisce NAME_ERROR_INVALID_NAME) se:  
  
-   Il puntatore passato in NameProfileA è un valore NULL  
  
-   La stringa di dati di pszName inizia con un numero  
  
-   La stringa di dati di pszName contiene uno spazio  
  
-   La stringa dati di pszName contiene uno dei caratteri seguenti: ,;.`~!@#$%^&*()=[]{}&#124;\\?/<>  
  
 `Level`  
  
 Indica il livello di profilatura a cui può essere applicata la raccolta di dati sulle prestazioni. I valori **PROFILE_CONTROL_LEVEL** seguenti possono essere usati per indicare uno dei tre livelli a cui può essere applicata la raccolta di dati sulle prestazioni:  
  
|Enumerator|Descrizione|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Impostazione del livello globale con effetti su tutti i processi e i thread nell'esecuzione della profilatura.|  
|PROFILE_PROCESSLEVEL|Impostazione del livello processo con effetti su tutti i thread che fanno parte del processo specificato.|  
|PROFILE_THREADLEVEL|Impostazione del livello thread con effetti sul thread specificato.|  
  
 `dwId`  
  
 Identificatore del livello di profilatura. Usare l'identificatore del processo o del thread generato dal sistema.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 La funzione indica esito l'esito positivo o negativo usando l'enumerazione **PROFILE_COMMAND_STATUS**. Il valore restituito può essere uno dei seguenti:  
  
|Enumerator|Descrizione|  
|----------------|-----------------|  
|NAME_ERROR_ID_NOEXIST|L'elemento di profilatura specificato non esiste.|  
|NAME_ERROR_INVALID_NAME|Il nome non è valido.|  
|NAME_ERROR_LEVEL_NOEXIST|Il livello di profilatura specificato non esiste.|  
|NAME_ERROR_NO_SUPPORT|L'operazione specificata non è supportata.|  
|NAME_ERROR_OUTOFMEMORY|Non era disponibile memoria per registrare l'evento.|  
|NAME_ERROR_REDEFINITION|È già stato assegnato un nome all'elemento del profilo. Il nome in questa funzione viene ignorato.|  
|NAME_ERROR_TEXTTRUNCATED|Il testo del nome supera i 32 caratteri, incluso il carattere null e pertanto è stato troncato.|  
|NAME_OK|Il nome è stato registrato correttamente.|  
  
## <a name="remarks"></a>Note  
 A ogni processo o thread è possibile assegnare un solo nome. Dopo aver assegnato un nome a un elemento di profilatura, le chiamate successive a NameProfile per tale elemento vengono ignorate.  
  
 Se lo stesso nome viene assegnato a thread o processi diversi, il report includerà i dati da tutti gli elementi di tale livello con lo stesso nome.  
  
 Se si specifica un processo o thread diverso da quello corrente, è necessario assicurarsi che sia stato inizializzato e che sia iniziata l'esecuzione prima dell'assegnazione del nome. In caso contrario, il metodo NameProfile ha esito negativo.  
  
> [!IMPORTANT]
>  Le funzioni API CreateProcess () e CreateThread possono restituire il controllo prima dell'inizializzazione del thread o del processo.  
  
## <a name="net-framework-equivalent"></a>Equivalente .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informazioni sulla funzione  
  
|||  
|-|-|  
|**Intestazione**|Includere VSPerf.h|  
|**Libreria**|Usare VSPerf.lib|  
|**Unicode**|Implementato come `NameProfileW` (Unicode) e `NameProfileA` (ANSI).|  
  
## <a name="example"></a>Esempio  
 Il codice seguente illustra la chiamata della funzione NameProfile. Nell'esempio si presuppone l'uso di macro stringa Win32 e delle impostazioni del compilatore per ANSI per stabilire se il codice chiama la funzione abilitata per ANSI.  
  
```  
void ExerciseNameProfile()  
{  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Create and initialize variables to pass to   
    // ExerciseNameProfile.  The value of this   
    // parameter is based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variable is assigned an arbitrary value.  
    TCHAR * profileName = TEXT("ExerciseNameProfile");  
  
    // Declare enumeration to hold result of call to   
    // ExerciseNameProfle.  
    PROFILE_COMMAND_STATUS nameResult;  
  
    nameResult =  NameProfile(  
        profileName,  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("NameProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, nameResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per le API del profiler di Visual Studio (native)](../profiling/visual-studio-profiler-api-reference-native.md)