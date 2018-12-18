---
title: Eseguire la migrazione di registrazione della classe COM debugger a 64 bit | Documenti Microsoft
ms.custom: ''
ms.date: 11/10/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: douge
ms.workload:
- greggm
ms.openlocfilehash: 28516038170dd34028d11bf9a070cf265ecfd830
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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
