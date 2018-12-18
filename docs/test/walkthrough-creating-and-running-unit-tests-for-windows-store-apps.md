---
title: Creazione ed esecuzione di unit test per le app UWP in Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: bbb1da5474dcb36e9b102f85f21c4945b3ebb33c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Procedura dettagliata: Creare ed eseguire unit test per le app UWP

Visual Studio include il supporto per gli unit test delle app della piattaforma UWP (Universal Windows Platform). Sono inclusi i modelli di progetto di unit test per Visual C#, Visual Basic e Visual C++.

> [!TIP]
> Per altre informazioni sullo sviluppo di app per la piattaforma UWP, vedere [Introduzione alle app UWP](/windows/uwp/get-started/).

Le procedure riportate di seguito descrivono i passaggi per creare, eseguire ed eseguire il debug di unit test per un'app UWP.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Creare un progetto di unit test per un'app UWP

1.  Scegliere **Nuovo progetto** dal menu **File**.

     Verrà visualizzata la finestra di dialogo Nuovo progetto.

2.  In Modelli scegliere il linguaggio di programmazione con cui creare gli unit test e quindi scegliere la libreria di unit test per Windows Universal associata. Ad esempio, scegliere **Visual C#**, **Windows Universal** e quindi **Libreria unit test (Universal Windows)**.

3.  (Facoltativo) Nella casella di testo **Nome** immettere il nome che si vuole usare per il progetto.

4.  (Facoltativo) Modificare il percorso in cui si vuole creare il progetto immettendolo nella casella di testo **Percorso** oppure scegliendo il pulsante **Sfoglia**.

5.  (Facoltativo) Nella casella di testo del nome **Soluzione** immettere il nome che si desidera usare per la soluzione.

6.  Lasciare selezionata l'opzione **Crea directory per soluzione** e scegliere il pulsante **OK** .

     ![Libreria unit test personalizzata](../test/media/unit_test_win8_1.png "Unit_Test_Win8_1")

     Esplora soluzioni verrà popolato con il nuovo progetto di unit test per UWP e l'editor di codice visualizzerà lo unit test predefinito denominato UnitTest1.

     ![Nuovo progetto di unit test personalizzato](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png "Unit_Test_Win8_UnitTestExplorer_NewProjectCreated")

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Modificare il file manifesto dell'applicazione UWP del progetto di unit test

1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul file *Package.appxmanifest* e scegliere **Apri**.

     Verrà visualizzata la finestra Progettazione manifesto nella quale sarà possibile apportare le modifiche al manifesto.

2.  In Progettazione manifesto scegliere la scheda **Funzionalità** .

3.  Nell'elenco in **Funzionalità**selezionare le funzionalità necessarie per lo unit test e il codice per il test. Ad esempio, selezionare la casella di controllo **Internet** se lo unit test e il codice di cui si sta eseguendo il test necessitano della funzionalità di accesso a Internet.

    > [!NOTE]
    > Le funzionalità selezionate devono includere solo quelle necessarie affinché lo unit test funzioni correttamente.

     ![Manifesto unit test](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Scrivere il codice per lo unit test di un'app UWP

Nell'Editor di codice modificare lo unit test e aggiungere le asserzioni e la logica richieste per il test.

## <a name="run-unit-tests"></a>Eseguire unit test

### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Per compilare la soluzione ed eseguire lo unit test usando Esplora test

1.  Dal menu **Test** scegliere **Finestre**, quindi scegliere **Esplora test**.

     Verrà visualizzato Esplora senza il test elencato.

2.  Scegliere **Compila soluzione** dal menu **Compila**.

     Lo unit test viene elencato.

    > [!NOTE]
    > È necessario compilare la soluzione per aggiornare l'elenco degli unit test in Esplora test.

3.  In Esplora test, scegliere lo unit test creato.

    > [!TIP]
    > In Esplora test viene fornito un collegamento al codice sorgente accanto a **Origine:**.

4.  Scegliere **Esegui tutto**.

     ![Esplora unit test &#45; esegui unit test](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

    > [!TIP]
    > È possibile selezionare uno o più unit test elencati in Esplora test, quindi fare clic con il pulsante destro del mouse e scegliere **Esegui test selezionati**.
    >
    > Inoltre, è possibile scegliere di **eseguire il debug dei test selezionati**, di **aprire il test**e di usare l'opzione **Proprietà** .
    >
    > ![Esplora unit test &#45; menu di scelta rapida unit test](../test/media/unit_test_win8_unittestexplorer_contextmenu.png "Unit_Test_Win8_UnitTestExplorer_ContextMenu")

    Lo unit test viene eseguito. Al termine, in Esplora test viene visualizzato lo stato del test, il tempo trascorso e viene fornito un collegamento all'origine.

    ![Esplora unit test &#45; test completato](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Vedere anche

- [Test delle app UWP con Visual Studio](../test/testing-store-apps-with-visual-studio.md)
- [Compilare e testare un'app UWP](/vsts/build-release/apps/windows/universal?tabs=vsts)
