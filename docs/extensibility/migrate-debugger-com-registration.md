---
title: Eseguire la migrazione di registrazione della classe COM debugger a 64 bit | Documenti Microsoft
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: "1"
author: gregg-miskelly
ms.author: greggm
manager: ghogen
ms.workload: greggm
ms.openlocfilehash: 737c970555fce8f3cdac118421eddb09f52d7c53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Eseguire la migrazione di registrazione della classe COM debugger a 64 bit

Per le estensioni di debugger registrare classi COM in HKEY_CLASSES_ROOT (regasm, regsvr32, o alla scrittura direttamente nel Registro di sistema) e caricati msvsmon.exe (il debugger remoto), è ora possibile fornire la registrazione a msvsmon senza che sia necessario per scrivere in HKEY_CLASSES_ROOT. Ciò influisce sul analizzatori di espressioni del debugger .NET legacy o motori di debug che sono configurati per il caricamento del processo msvsmon.exe.

## <a name="msvsmon-comclass-def"></a>definizione di comclass msvsmon

Per utilizzare questa tecnica, aggiungere un file *.msvsmon-comclass-def.json accanto msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64).

Ecco un esempio di file msvsmon comclass-definizione che registra uno gestito e una classe nativa:

Nome file: MyCompany.MyExample.msvsmon-comclass-def.json

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
