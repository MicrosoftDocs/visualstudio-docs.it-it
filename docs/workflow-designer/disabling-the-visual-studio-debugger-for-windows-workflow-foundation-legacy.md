---
title: Disabilitazione Debugger di Visual Studio per Windows Workflow Foundation (Legacy) | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a609062f3f84538f7c1655cd5ca82971fc608f62
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Disattivazione del debugger di Visual Studio per Windows Workflow Foundation (legacy)

In questo argomento viene descritto come disabilitare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizzando il file di configurazione durante la compilazione del Debugger [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] applicazioni in Progettazione flussi di lavoro Windows legacy. Usare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Per impostazione predefinita, il debugger di [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] per [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] è abilitato per un processo host. Per disabilitare il debug del flusso di lavoro, è necessario disattivarlo in modo esplicito aggiungendo la voce "disableworkflowdebugging al"  **\<commutatori >** elemento il  **\<System. Diagnostics >**sezione del file di configurazione host.

 Nell’esempio seguente viene illustrato come modificare il file di configurazione dell’host per disabilitare il debug del flusso di lavoro.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <system.diagnostics>
      <switches>
         <add name="DisableWorkflowDebugging" value="true"/>
      </switches>
   </system.diagnostics>
</configuration>
```

## <a name="see-also"></a>Vedere anche

- [Richiamo del debugger di Visual Studio per Windows Workflow Foundation (legacy)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)