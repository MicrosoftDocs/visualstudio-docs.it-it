---
title: Unit test per Python | Microsoft Docs
description: Configurazione di unit test per il codice Python in Visual Studio per usufruire delle funzionalità di Esplora test per l'individuazione, l'esecuzione e il debug dei test.
ms.custom: ''
ms.date: 07/13/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: eee1ec05a46050c5a994aa2d774a5be0090171f3
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="setting-up-unit-testing-for-python-code"></a>Configurazione degli unit test per il codice Python

Gli unit test sono parti di codice che testano altre unità di codice in un'applicazione, in genere funzioni isolate, classi e così via. Se un'applicazione supera tutti gli unit test, si può ritenere con una certa fiducia che almeno la funzionalità di basso livello sia corretta.

In Python gli unit test vengono usati frequentemente per convalidare gli scenari durante la progettazione di un programma. Il supporto di Python in Visual Studio include l'individuazione, l'esecuzione e il debug di unit test direttamente all'interno del contesto del processo di sviluppo, senza la necessità di eseguire i test separatamente.

Questo articolo illustra brevemente le funzionalità di testing unità in Visual Studio con Python. Per altre informazioni di carattere generale sull'esecuzione di unit test, vedere [Eseguire unit test del codice](../test/unit-test-your-code.md).

|   |   |
|---|---|
| ![icona della telecamera](../install/media/video-icon.png "Guardare un video") | [Guardare un video (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Testing-Python-hb46k6LWE_405918567) sul testing unità in Python (2m 31s). |

## <a name="discovering-and-viewing-tests"></a>Individuazione e visualizzazione di test

Per convenzione, Visual Studio identifica i test come metodi il cui nome inizia con `test`. Per vedere questo comportamento, attenersi alla procedura seguente:

1. Aprire un [progetto Python](managing-python-projects-in-visual-studio.md) caricato in Visual Studio, fare clic con il pulsante destro del mouse sul progetto, scegliere **Aggiungi > Nuovo elemento** e quindi selezionare **Unit test Python** seguito da **Aggiungi**.

1. Verrà creato un file `test1.py` contenente il codice che importa il modulo standard `unittest`, deriva una classe di test da `unittest.TestCase` e richiama `unittest.main()` se si esegue lo script direttamente:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Se necessario, salvare il file e aprire Esplora test con il comando di menu **Test > Windows > Esplora test**.

1. Esplora test cerca i test nel progetto e li visualizza come illustrato di seguito. Fare doppio clic su un test per aprirne il file di origine.

    ![Esplora test con test_A predefinito](media/unit-test-A.png)

1. Via via che si aggiungono altri test al progetto, è possibile organizzare la visualizzazione in Esplora test tramite il menu Raggruppa per della barra degli strumenti:

    ![Menu Raggruppa per della barra degli strumenti in Esplora test](media/unit-test-group-menu.png)

1. È anche possibile immettere testo nel campo di ricerca per filtrare i test in base al nome.

Per altre informazioni sul modulo `unittest` e sulla scrittura dei test, vedere la [documentazione di Python 2.7](https://docs.python.org/2/library/unittest.html) oppure la [documentazione di Python 3.4](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="running-tests"></a>Esecuzione di test

In Esplora test è possibile eseguire test in diversi modi:

- L'opzione **Esegui tutto** esegue chiaramente tutti i test visualizzati, tenendo conto degli eventuali filtri applicati.
- Il menu **Esegui** include i comandi per eseguire in gruppo test non superati, superati o non eseguiti.
- È possibile selezionare uno o più test, fare clic con il pulsante destro del mouse e scegliere **Esegui test selezionati**.

I test vengono eseguiti in background ed Esplora test aggiorna lo stato di ogni test non appena viene completato:

- I test superati sono contraddistinti da un segno di spunta verde, nonché dall'indicazione del tempo necessario per eseguirli:

    ![test_A superato](media/unit-test-A-pass.png)

- I test non superati sono contraddistinti da una croce rossa e includono un collegamento **Output** che mostra l'output della console e l'output di `unittest` restituito dall'esecuzione dei test:

    ![test_A non superato](media/unit-test-A-fail.png)

    ![test_A non superato con motivo](media/unit-test-A-fail-reason.png)

## <a name="debugging-tests"></a>Debug di test

Dal momento che gli unit test sono parti di codice, sono soggetti a bug esattamente come qualsiasi altro tipo di codice e a volte può essere necessario eseguirli in un debugger, in cui è possibile impostare punti di interruzione, esaminare le variabili ed eseguire il codice istruzione per istruzione. Visual Studio include anche strumenti di diagnostica per gli unit test.

Per avviare il debug, impostare un punto di interruzione iniziale nel codice, fare clic con il pulsante destro del mouse sul test (o su una selezione) in Esplora test e quindi scegliere **Esegui debug test selezionati**. Visual Studio avvia il debugger di Python come farebbe per il codice dell'applicazione.

![Debug di un test](media/unit-test-debugging.png)

A seconda della versione di Visual Studio, è anche possibile usare i comandi **Analizza code coverage per i test selezionati** ed **Esegui profilatura test**. Vedere la [matrice delle funzionalità](overview-of-python-tools-for-visual-studio.md#features-matrix).

### <a name="known-issues"></a>Problemi noti

- Quando si avvia il debug, Visual Studio sembra avviare e arrestare il debug e quindi avviarlo di nuovo. Questo è il comportamento previsto.
- Durante il debug di più test, ognuno di essi viene eseguito in modo indipendente e questo causa l'interruzione della sessione di debug.
- Di tanto in tanto Visual Studio non riesce ad avviare un test durante il debug. In genere, il problema si risolve ripetendo il debug del test.
- Durante il debug, è possibile uscire da un test nell'implementazione di `unittest`. Di solito il passaggio successivo viene eseguito alla fine del programma e arresta il debug.
