---
title: PROFILE_CURRENTID | Microsoft Docs
description: Informazioni su come usare il PROFILE_CURRENTID per fare in modo che la funzione operi sul thread o sul processo corrente, anziché su uno specifico.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- PROFILE_CURRENTID
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5e5c888e1b285bb92ea44c32e26834f16668b8dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936366"
---
# <a name="profile_currentid"></a>PROFILE_CURRENTID
PROFILE_CURRENTID restituisce il pseudotoken per l'ID del thread o l'ID del processo in una chiamata alle funzioni NameProfile, StartProfile, StopProfile, SuspendProfile e ResumeProfile. Usare questo parametro per fare in modo che la funzione venga applicata al thread o al processo corrente, anziché a uno indicato specificatamente.

## <a name="example-1"></a>Esempio 1
 Il parametro PROFILE_CURRENTID è definito in *VSPerf.h* come:

```cpp
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;
```

## <a name="example-2"></a>Esempio 2
 L'esempio seguente illustra PROFILE_CURRENTID. In questo esempio PROFILE_CURRENTID viene usato come parametro per identificare il thread corrente in una chiamata alla funzione [StartProfile](../profiling/startprofile.md).

```cpp
void ExerciseProfileCurrentID()
{
    // Declare ProfileOperationResult enumeration
    // to hold return value of a call to StartProfile.
    PROFILE_COMMAND_STATUS profileResult;

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    profileResult = StartProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("StartProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Vedi anche
- [Riferimento all'API del profiler di Visual Studio (nativo)](../profiling/visual-studio-profiler-api-reference-native.md)
- [NameProfile](../profiling/nameprofile.md)
- [ResumeProfile](../profiling/resumeprofile.md)
- [StartProfile](../profiling/startprofile.md)
- [StopProfile](../profiling/stopprofile.md)
- [SuspendProfile](../profiling/suspendprofile.md)
