---
title: 'Procedura: Limitare la strumentazione a specifiche DLL | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b39689219b113343162aa0e814cfa68e2422f08d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62980915"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Procedura: Limitare la strumentazione a specifiche DLL

Usando il metodo di profilatura della strumentazione, è possibile limitare la raccolta dei dati di profilatura a una o più DLL di un'applicazione. Per eseguire la profilatura di una o più DLL di un'applicazione, creare una sessione di prestazioni che includa i file con estensione *dll* come destinazioni. È possibile specificare le DLL da profilare come progetti in una soluzione di Visual Studio o come file binari indipendenti.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Per limitare la strumentazione a specifiche DLL di una soluzione di Visual Studio

1. Aprire la soluzione contenente la DLL in Visual Studio.

2. Nel menu **Analizza** selezionare **Avvia Creazione guidata sessione di prestazioni**.

3. Scegliere **Strumentazione** come metodo di profilatura e quindi fare clic su **Avanti**.

4. In **Specificare le destinazioni da profilare** selezionare il nome del progetto con estensione **dll** e fare clic su *Avanti*.

5. Fare clic su **Fine** per chiudere la procedura guidata e visualizzare la nuova sessione di prestazioni nella finestra **Esplora prestazioni**.

6. Fare clic con il pulsante destro del mouse su **Destinazioni** e quindi selezionare **Aggiungi progetto di destinazione**.

7. Dall'elenco **Aggiungi progetto di destinazione** selezionare il progetto eseguibile da usare per verificare la DLL.

     Facoltativo. È possibile aggiungere qualsiasi progetto DLL che si vuole profilare.

8. Per impedire la raccolta di dati per un progetto aggiunto, fare clic con il pulsante destro del mouse sul nome del progetto e quindi deselezionare la casella di controllo **Strumento**.

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Per specificare determinate DLL da profilare come file binari indipendenti

1. Aprire Visual Studio.

2. Nel menu **Analizza** selezionare **Avvia Creazione guidata sessione di prestazioni**.

3. In **Specificare le destinazioni da profilare** selezionare **Profilatura di una libreria a collegamento dinamico (.DLL)** e quindi fare clic su **Avanti**.

4. Nella seconda pagina della procedura guidata eseguire i passaggi seguenti:

    - Digitare il percorso e il nome del file con estensione *dll* di cui eseguire la profilatura in **Percorso DLL**. È anche possibile fare clic sul pulsante con i puntini di sospensione (...) per individuare il file nella finestra di dialogo **Libreria a collegamento dinamico da profilare**. Si noti che è necessario specificare la copia del file con estensione *dll* che verrà avviato dal file eseguibile con estensione *exe* che si seleziona al passaggio successivo.

    - Digitare il percorso e il nome del file eseguibile con estensione *exe* che verrà usato per verificare la funzionalità del file con estensione *dll* in **Percorso eseguibile**. È anche possibile fare clic sul pulsante con i puntini di sospensione (...) per individuare il file nella finestra di dialogo **Eseguibile da avviare**.

    - Facoltativo. Digitare gli argomenti della riga di comando da passare al file eseguibile in **Argomenti della riga di comando**. Se necessario, specificare la directory di lavoro per l'applicazione in **Directory di lavoro**.

    - Scegliere **Avanti**.

5. Scegliere **Strumentazione** come metodo di profilatura e quindi fare clic su **Avanti**.

6. Fare clic su **Fine** per chiudere la procedura guidata e visualizzare la nuova sessione di prestazioni nella finestra **Esplora prestazioni**.

7. Facoltativo. Per aggiungere altri file con estensione *dll*, fare clic con il pulsante destro del mouse su **Destinazioni** e selezionare **Aggiungi binario di destinazione**. Selezionare i file dalla finestra di dialogo **Aggiungi binario di destinazione**.

    > [!NOTE]
    > Non specificare il file eseguibile con estensione *exe* che verifica la funzionalità delle DLL.

## <a name="see-also"></a>Vedere anche

[Controllare la raccolta dati](../profiling/controlling-data-collection.md)
[Procedura: Limitare la strumentazione a funzioni specifiche](../profiling/how-to-limit-instrumentation-to-specific-functions.md)