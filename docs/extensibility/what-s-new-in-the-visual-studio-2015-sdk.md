---
title: Novità&#39;s New in Visual Studio 2015 SDK | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6488f28f2963e17c716c2e9d395ddf77f270e7b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Novità&#39;s New in Visual Studio 2015 SDK
Visual Studio SDK include le seguenti funzionalità nuove e aggiornate per Visual Studio 2015, Visual Studio 2015 aggiornate e Visual Studio 2017.  
  
## <a name="vs-2015-sdk-update-1"></a>Visual Studio 2015 SDK Update 1  
 Update 1 include strumenti che facilitano l'estensione per il corretto funzionamento con temi di colori e il servizio di immagini di Visual Studio.  
  
 Questi argomenti sono sotto il [VSSDK utilità](../extensibility/internals/vssdk-utilities.md) sezione:  
  
-   Il [colore dei temi strumenti](../extensibility/internals/color-theming-tools.md) consentono di creare e modificare i colori personalizzati per Visual Studio.  
  
-   Il [strumenti servizio immagini](../extensibility/internals/image-service-tools.md) consentono di cui si lavora con i file manifesto di immagini di Visual Studio.  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nuovo modo per aggiungere Visual Studio SDK a Visual Studio  
 A partire da Visual Studio 2015, non è necessario scaricare separatamente il SDK di Visual Studio. In alternativa, è possibile installarlo come parte del processo di installazione normale, o è possibile scegliere di installarlo in un secondo momento. Quando si apre o creare una soluzione VSIX, Visual Studio verrà chiesto di installare strumenti di estendibilità di Visual Studio. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="new-ways-of-creating-extensions"></a>Nuove modalità di creazione di estensioni  
 A partire da Visual Studio 2015 SDK, sono disponibili opzioni diverse per la creazione di estensioni, in base al linguaggio di programmazione in uso.  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# e Visual Basic  
 In c# e Visual Basic, è una gamma completa di modelli di elemento di progetto che consentono di creare VSPackage, i comandi di menu, finestre degli strumenti, classificatori editor, editor valutano ed estensioni di editor margine. È possibile aggiungere uno o tutti questi al progetto VSIX standard. Per altre informazioni, vedere:  
  
-   [Creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [Creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [Creazione di un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [Creazione di un'estensione con un pacchetto VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     La procedura guidata pacchetto VSPackage non crea più estensioni in c# o Visual Basic.  
  
### <a name="c"></a>C++  
 Per C++, la procedura guidata VSPackage supporta i comandi di menu e finestre degli strumenti editor personalizzati. Cercare nel **nuovo progetto** nella finestra di dialogo **Visual C++ / Extensibility**.  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Assembly di riferimento SDK di Visual Studio tramite NuGet  
 Per garantire una maggiore portabilità e la condivisione dei progetti di estendibilità, è possibile utilizzare le versioni di NuGet di assembly di riferimento di Visual Studio SDK.  Questi sono disponibili in [nuget.org](http://www.nuget.org) pubblicati da [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) e possono essere facilmente aggiunte al progetto o soluzione tramite Visual Studio **fa riferimento / gestione NuGet Pacchetti** finestra di dialogo. È possibile aggiungere singoli riferimenti agli assembly di estendibilità specifico o aggiungere tutto il SDK di Visual Studio di fa riferimento ad assembly in una sola volta tramite il SDK di Visual Studio [pacchetto Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Per ulteriori informazioni su NuGet, vedere il [documentazione di NuGet](/NuGet) e [UI Package Manager](/NuGet/Tools/Package-Manager-UI) argomenti.  
  
 Quando si utilizzano le versioni di NuGet di assembly di riferimento di Visual Studio SDK, un altro utente non è necessario installare il SDK di Visual Studio per aprire e compilare il progetto.  Gli strumenti di compilazione di VS SDK e gli assembly di riferimento NuGet verranno installati automaticamente nel proprio computer per il progetto.  
  
 I modelli di elemento di Visual Studio SDK utilizzano NuGet per i riferimenti e strumenti di compilazione, pertanto si ottengono i vantaggi di NuGet per impostazione predefinita.  
  
> [!NOTE]
>  È possibile continuare a utilizzare gli assembly di riferimento di VS SDK installato con i progetti (sotto \<percorso di installazione di Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) e non è necessario che i progetti di estendibilità esistente aggiornato per l'utilizzo di pacchetti NuGet.  Il progetto **fa riferimento / Aggiungi riferimento** finestra di dialogo continua a utilizzare gli assembly di riferimento di VS SDK installato.  
>   
>  Se si desidera modificare i progetti esistenti usare NuGet, vedere [procedura: eseguire la migrazione di VSPackage in Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) che dispone di una sezione sull'aggiornamento di progetti di estendibilità ai pacchetti NuGet.  
  
## <a name="light-bulbs"></a>Le lampadine  
 Uno dei modi più interessanti nuovo della scrittura del codice di estensione verrà fornito dal progetto Roslyn. Per ulteriori informazioni, vedere [Roslyn](https://github.com/dotnet/Roslyn).  
  
 Le lampadine sono una nuova funzionalità che viene fornito con Visual Studio SDK. Si tratta di icone utilizzate nell'editor di Visual Studio che si espandono per visualizzare un set di azioni di refactoring di codice o correzioni di problemi identificati dagli analizzatori di codice predefiniti. Per ulteriori informazioni, vedere [procedura dettagliata: visualizzazione dei suggerimenti di lampadina](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
## <a name="updated-user-experience-guidelines"></a>Linee guida sull'esperienza utente aggiornato  
 Progettazione di nuove estensioni o le funzionalità di Visual Studio? Controllare l'aggiornato ed espanso [linee guida esperienza utente di Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  È possibile trovare il [i token di colore](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [le dimensioni dei caratteri](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [specifiche del layout della finestra di dialogo](../extensibility/ux-guidelines/layout-for-visual-studio.md)e altre indicazioni necessarie per la nuova interfaccia utente si integrano facilmente con Visual Studio.