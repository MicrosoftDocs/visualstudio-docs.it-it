---
title: Installare gli analizzatori di Roslyn in Visual Studio
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8a3b40b3b471e6bb57da561ac51f23086a0f01bd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="install-net-compiler-platform-analyzers"></a>Installare gli analizzatori di .NET Compiler Platform

Visual Studio 2017 include un set di base di .NET Compiler Platform (*Roslyn*) analizzatori. Gli analizzatori sono sempre attivati. È possibile installare gli analizzatori aggiuntivi come pacchetti NuGet o come estensioni di Visual Studio in *VSIX* file.

## <a name="to-install-nuget-package-analyzers"></a>Per installare gli analizzatori di pacchetto NuGet

1. [Determinare la versione del pacchetto analyzer](https://github.com/dotnet/roslyn-analyzers#recommended-version-of-analyzer-packages) da installare, in base alla versione di Visual Studio.

1. Installare il pacchetto in Visual Studio, utilizzando il [Console di gestione pacchetti](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) o il [Package Manager UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La pagina di nuget.org per ogni pacchetto analyzer Mostra il comando per incollare il **Console di gestione pacchetti**. È anche disponibile un pulsante utile copiare il testo negli Appunti.
   >
   > ![Pagina NuGet.org con comando della Console di gestione pacchetti](media/nuget-package-manager-command.png)

   Gli assembly dell'analizzatore sono installati e visualizzati **Esplora soluzioni** sotto **riferimenti** > **analizzatori**.

   ![Nodo analizzatori in Esplora soluzioni](media/solution-explorer-analyzers-node.png)

## <a name="to-install-vsix-analyzers"></a>Per installare gli analizzatori VSIX

1. In Visual Studio, selezionare **Tools** > **estensioni e aggiornamenti**.

   Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

   > [!NOTE]
   > In alternativa, scaricare l'estensione direttamente dal [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

1. Espandere **Online** nel riquadro sinistro e quindi selezionare **Visual Studio Marketplace**.

1. Nella casella di ricerca, digitare "analisi del codice" e cercare il **2017 di analisi codice Microsoft** estensione.

   ![Estensione di analisi del codice Microsoft](media/extensions-and-updates-code-analysis.png)

1. Selezionare **scaricare**.

   L'estensione viene scaricata.

1. Selezionare **OK** per chiudere la finestra di dialogo, quindi chiudere tutte le istanze di Visual Studio per avviare la **VSIX Installer**.

   Il **VSIX Installer** verrà visualizzata la finestra di dialogo.

   ![Programma di installazione VSIX per l'analisi codice Microsoft](media/vsix-installer-code-analysis.png)

1. Selezionare **Modify** per avviare l'installazione.

1. Dopo un minuto o due, il completamento dell'installazione. Selezionare **Chiudi**.

1. Aprire di nuovo Visual Studio.

Se si desidera controllare se l'estensione è installata, selezionare **Tools** > **estensioni e aggiornamenti**. Nel **estensioni e aggiornamenti** finestra di dialogo, seleziona il **installato** categoria a sinistra e quindi cercare l'estensione per nome.

## <a name="next-steps"></a>Passaggi successivi

- [Usare gli analizzatori di Roslyn in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vedere anche

- [Panoramica di Roslyn analizzatori in Visual Studio](../code-quality/roslyn-analyzers-overview.md)