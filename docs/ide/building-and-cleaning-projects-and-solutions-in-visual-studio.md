---
title: Compilazione e pulizia di progetti e soluzioni in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 190bcbbb990c0dce447e4153d747fb9f4d6156d4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>Compilazione e pulizia di progetti e soluzioni in Visual Studio
Tramite le procedure descritte in questo argomento è possibile compilare, ricompilare o pulire tutti o alcuni progetti o elementi di progetto di una soluzione. Per un'esercitazione dettagliata, vedere [Procedura dettagliata: Compilazione di un'applicazione](../ide/walkthrough-building-an-application.md).  
  
> [!NOTE]
> L'interfaccia utente dell'edizione di Visual Studio in uso potrebbe essere diversa da quanto descritto in questo argomento, a seconda delle impostazioni attive. Per modificare le impostazioni, ad esempio per implementare le impostazioni **Generali** o **Visual C++**, scegliere **Strumenti** > **Importa/Esporta impostazioni** e quindi scegliere **Reimposta tutte le impostazioni**.
  
## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Per compilare, ricompilare o pulire un'intera soluzione  
  
1.  In **Esplora soluzioni**  scegliere una soluzione o aprire la soluzione voluta.  
  
2.  Nella barra dei menu, scegliere **Compila** e quindi scegliere uno dei comandi seguenti:  
  
    -   Scegliere **Compila** o **Compila soluzione** per compilare solo i file e i componenti del progetto che sono stati modificati dalla compilazione più recente.  
  
        > [!NOTE]
        >  Il comando **Compila** diventa **Compila soluzione** se una soluzione include più progetti.  
  
    -   Scegliere **Ricompila soluzione** per "pulire" la soluzione e quindi compilare tutti i componenti e i file dei progetti.  
  
    -   Scegliere **Pulisci soluzione** per eliminare eventuali file intermedi e di output. Quando sono rimasti solo i file dei componenti e dei progetti, è possibile compilare nuove istanze di file intermedi e di output.  
  
## <a name="to-build-or-rebuild-a-single-project"></a>Per compilare o ricompilare un progetto singolo  
  
1.  In **Esplora soluzioni**  scegliere un progetto o aprire il progetto voluto.  
  
2.  Nella barra dei menu scegliere **Compila** e quindi scegliere **Compila** *NomeProgetto* o **Ricompila** *NomeProgetto*.  
  
    -   Scegliere **Compila**  *NomeProgetto* per compilare solo i componenti del progetto che sono stati modificati dopo la build più recente.  
  
    -   Scegliere **Ricompila** *NomeProgetto* per "pulire" il progetto e quindi compilare i file e tutti i componenti del progetto.  
  
## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Per compilare il progetto di avvio e le relative dipendenze  
  
1.  Nella barra dei menu scegliere **Strumenti** > **Opzioni**.  
  
2.  Nella finestra di dialogo **Opzioni** espandere il nodo **Progetti e soluzioni** e quindi scegliere la pagina **Compila ed esegui**.  
  
     Si apre la finestra di dialogo **Compila ed esegui** > **Progetti e soluzioni** > **Opzioni**.  
  
3.  Selezionare la casella di controllo **Compila progetti di avvio e dipendenze solo in fase di esecuzione**.  
  
     Se questa casella di controllo è selezionata, solo il progetto di avvio corrente e le relative dipendenze vengono compilati quando si esegue la procedura seguente:  
  
    -   Nella barra dei menu scegliere **Debug** > **Avvia** (**F5**).  
  
    -   Nella barra dei menu scegliere **Compila** > **Compila soluzione** (**CTRL**+**MAIUSC**+**B**).  
  
    Quando questa casella di controllo è deselezionata e si eseguono i comandi precedenti vengono compilati tutti i progetti, le relative dipendenze e i file della soluzione. Per impostazione predefinita, questa casella di controllo è deselezionata.  
  
## <a name="to-build-only-the-selected-visual-c-project"></a>Per compilare solo il progetto di Visual C++ selezionato  
  
Scegliere un progetto di [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] e quindi nella barra dei menu scegliere **Compila** > **Solo progetto** e quindi uno dei comandi seguenti:  

- **Build Only** (Compila solo) *NomeProgetto*  
  
- **Rebuild Only** (Ricompila solo) *NomeProgetto*  
  
- **Clean Only** (Pulisci solo) *NomeProgetto*  
  
- **Link Only** (Collega solo) *NomeProgetto*  

Questi comandi si applicano solo al progetto di [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] scelto. Non eseguono la compilazione, la ricompilazione, la pulizia o il collegamento di eventuali dipendenze del progetto o file di soluzione. A seconda della versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], il sottomenu **Project Only** (Solo progetto) potrebbe contenere altri comandi.  
  
## <a name="to-compile-multiple-c-project-items"></a>Per compilare più elementi di un progetto C++  
  
In **Esplora soluzioni** scegliere più file che dispongono di azioni che possono essere compilate, aprire il menu di scelta rapida per uno di questi file e quindi scegliere **Compila**.  

Se i file hanno dipendenze, vengono compilati in ordine di dipendenza. L'operazione di compilazione non riesce se i file richiedono un'intestazione precompilata che non disponibile in fase di compilazione. L'operazione di compilazione usa la configurazione della soluzione attiva corrente.  
  
## <a name="to-stop-a-build"></a>Per interrompere una compilazione  
  
Effettuare uno dei passaggi seguenti:  

- Nella barra dei menu selezionare **Compila** > **Annulla**.  
  
- Premere **CTRL**+**INTERR**.  
  
## <a name="see-also"></a>Vedere anche

[Procedura: Visualizzare, salvare e configurare file di log di compilazione](../ide/how-to-view-save-and-configure-build-log-files.md)  
[Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md)  
[Compilazione e creazione in Visual Studio](../ide/compiling-and-building-in-visual-studio.md)  
[Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md)  
[Procedura: Impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md)  
[Riferimenti alla compilazione in C/C++](/cpp/build/reference/c-cpp-building-reference)  
[Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md)  
[Soluzioni e progetti](../ide/solutions-and-projects-in-visual-studio.md)
