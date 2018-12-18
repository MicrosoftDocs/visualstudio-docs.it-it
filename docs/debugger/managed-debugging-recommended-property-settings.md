---
title: 'Il debug gestito: Impostazioni consigliate delle proprietà | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e1c4b725871012f1fbf2c80f3e978f133d4db5b0
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="managed-debugging-recommended-property-settings"></a>Debug gestito: impostazioni consigliate delle proprietà
Determinate proprietà devono essere impostate nello stesso modo per tutti gli scenari di debug gestito.  
  
 Nelle tabelle riportate di seguito sono indicate le impostazioni consigliate delle proprietà.  
  
 Le impostazioni non specificate in queste tabelle possono variare in base al tipo di progetto gestito. Ad esempio, **azione di avvio** verrà impostato in modo diverso in un progetto Windows Form e in un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] progetto.  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Proprietà di configurazione disponibili nella scheda Compila (C#) o Compila (Visual Basic)  
  
|**Nome della proprietà**|**Impostazione**|  
|-----------------------|-----------------|  
|**Definisci costante DEBUG**|C# e F#: selezionare la casella di controllo per consentire all'applicazione di utilizzare la classe Debug.|  
|**Definisci costante TRACE**|C# e F#: selezionare la casella di controllo per consentire all'applicazione di utilizzare la classe Trace.|  
|**Ottimizza codice**|C#, F# e Visual Basic: impostare su false. L'esecuzione del debug di codice ottimizzato è più complessa perché le istruzioni generate non corrispondono direttamente al codice sorgente. Se si nota un bug presente solo nel codice ottimizzato del programma, è possibile attivare questa impostazione, ma tenere presente che il codice riportato nel **Disassembly** finestra viene generata da codice sorgente ottimizzato che potrebbe non corrispondere a ciò che viene visualizzato nel codice Editor. Per eseguire il debug di codice ottimizzato, disattivare Just My Code. (Vedere [limitare l'accesso a Just My Code](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> Per ulteriori informazioni, vedere [le impostazioni di progetto per configurazioni di Debug c#](../debugger/project-settings-for-csharp-debug-configurations.md) o [le impostazioni di progetto per una configurazione di Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Percorso output**|Impostato su bin\Debug\\.|  
|**Opzioni di compilazione avanzate**|Solo Visual Basic. Fare clic su **avanzate** per impostare le proprietà avanzate descritte nella tabella seguente.|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>Finestra di dialogo Impostazioni del compilatore avanzate  
  
|**Nome della proprietà**|**Impostazione**|  
|-----------------------|-----------------|  
|**Abilita ottimizzazioni**|Impostare su false per i motivi indicati nella **Ottimizza codice** opzione nella tabella precedente.|  
|**Genera informazioni di debug**|Selezionare questa casella di controllo se si desidera che durante la compilazione venga impostato il flag /DEBUG. In questo modo verranno generate le informazioni necessarie per semplificare il debug.|  
|**Definisci costante DEBUG**|Selezionare questa casella di controllo per definire la costante `DEBUG`, che consente all'applicazione di utilizzare la classe <xref:System.Diagnostics.Debug>.|  
|**Definisci costante TRACE**|Selezionare questa casella di controllo per definire la costante `TRACE`, che consente all'applicazione di utilizzare la classe <xref:System.Diagnostics.Trace>.|  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)