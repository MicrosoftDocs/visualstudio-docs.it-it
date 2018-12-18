---
title: Opzioni, Editor di testo, C/C++, Sperimentale | Microsoft Docs
ms.custom: 
ms.date: 08/02/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.workload: cplusplus
ms.openlocfilehash: e7b9d0ef40fd0efc4bbf071ef5da75b13e8dd82a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="options-text-editor-cc-experimental"></a>Opzioni, Editor di testo, C/C++, Sperimentale

Modificando queste opzioni è possibile modificare il comportamento correlato a IntelliSense e il database di esplorazione quando si programma in C o C++. Queste funzionalità sono davvero sperimentali. È possibile che vengano modificate o rimossa da Visuali Studio in una versione futura. In questo argomento vengono descritte le opzioni di Visual Studio 2017. Per Visual Studio 2015, vedere [Opzioni, Editor di testo, C/C++, Sperimentale](https://msdn.microsoft.com/library/mt591979.aspx)

Per accedere a questa pagina delle proprietà, premere **CTRL + Q** per attivare `Quick Launch` e quindi digitare "sperimentale". Avvio veloce troverà la pagina dopo le prime lettere. È anche possibile accedere scegliendo **Strumenti | Opzioni**, espandendo **Editor di testo** e **C/C++** e quindi scegliendo **Sperimentale**.

In un'installazione di Visual Studio 2017 sono disponibili queste funzionalità.

> [!NOTE]
> I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Abilita IntelliSense predittivo

IntelliSense predittivo limita il numero di risultati visualizzati nell'elenco a discesa di IntelliSense, in modo che siano visualizzati solo i risultati pertinenti al contesto. Se ad esempio si digita <code>int x =</code> e si richiama l'elenco a discesa di IntelliSense, vengono visualizzati solo numeri interi o funzioni che restituiscono numeri interi. Per impostazione predefinita, IntelliSense predittivo è disattivato.

## <a name="enable-faster-project-load"></a>Abilita caricamento più rapido del progetto

**Visual Studio 2017 15.3 e versioni successive**: questa funzionalità è ora denominata **Abilita Caching progetto** ed è stata spostata nella pagina delle proprietà [Impostazioni di progetto di VC++](vcpp-project-settings-projects-and-solutions-options-dialog-box.md).
Questa opzione consente a Visual Studio di memorizzare nella cache i dati di progetto in modo che alla successiva apertura del progetto sia possibile caricare i dati presenti nella cache anziché rielaborare i dati dai file di progetto. L'uso dei dati memorizzati nella cache può accelerare i tempi di caricamento del progetto in modo significativo.

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Altre funzionalità in Visual Studio Marketplace

È possibile scoprire altre funzionalità dell'editor di testo in [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads). Un esempio è [Correzioni rapide per C++](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.CQuickFixes2017), che supporta quanto segue:

- **Aggiunta di #include mancante** : suggerisce gli #include rilevanti per i simboli sconosciuti nel codice

- **Aggiunta dell'uso dello spazio dei nomi/simbolo completo** : come l'elemento precedente, ma per gli spazi dei nomi

- **Aggiunta del punto e virgola mancante**

- **Guida in linea**: cercare informazioni online per i messaggi di errore

- E molto altro ancora.

## <a name="see-also"></a>Vedere anche

[Setting Language-Specific Editor Options](../../ide/reference/setting-language-specific-editor-options.md) (Impostazione delle opzioni dell'editor specifiche del linguaggio)  
[Refactoring in C++ (VC Blog)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
