---
title: "Simboli per il debug in modalità mista con Python/C++ in Visual Studio | Microsoft Docs"
description: "Come Visual Studio offre la possibilità di caricare i simboli per il debug completo in modalità mista con C++ e Python."
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 2f309e50337195dc0e4057ce34f56e2575ec1b61
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="installing-debugging-symbols-for-python-interpreters"></a>Installazione dei simboli di debug per interpreti Python

Per offrire un'esperienza di debug completa, il [debugger in modalità mista di Python](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) in Visual Studio ha bisogno dei simboli di debug per l'interprete Python in uso per analizzare numerose strutture dei dati interne. Per python27.dll, ad esempio, il file di simboli corrispondente è python27.pdb, per python36.dll il file di simboli è python36.pdb. Per ogni versione dell'interprete sono disponibili anche i file di simboli per un'ampia gamma di moduli.

Con Visual Studio 2017, gli interpreti "Python 3" e "Anaconda 3" installano automaticamente i rispettivi simboli, che Visual Studio trova automaticamente. Per Visual Studio 2015 e versioni precedenti, o quando si usano altri interpreti, è necessario scaricare i simboli separatamente e quindi impostare Visual Studio in modo che punti ai simboli usando la finestra di dialogo **Strumenti > Opzioni** della scheda **Debug > Simboli**. Questi passaggi sono descritti in dettaglio nelle sezioni successive.

È possibile che Visual Studio richieda i simboli se sono necessari, di solito quando avvia una sessione di debug in modalità mista. In questo caso, viene visualizzata una finestra di dialogo con due opzioni:

- **Apri finestra di dialogo per le impostazioni dei simboli** apre la finestra di dialogo **Opzioni** che consente di passare alla scheda **Debug > Simboli**.
- **Scarica i simboli per l'interprete personale** apre questa pagina della documentazione e in questo caso consente di selezionare **Strumenti > Opzioni** e passare alla scheda **Debug > Simboli** per continuare.

    ![Prompt per i simboli del debugger in modalità mista](media/mixed-mode-debugging-symbols-required.png)

## <a name="downloading-symbols"></a>Download dei simboli

- Python 3.5 e versioni successive: acquisire i simboli di debug usando il programma di installazione di Python. Selezionare **Custom installation** (Installazione personalizzata), selezionare **Next** (Avanti) per passare ad **Advanced Options** (Opzioni avanzate) e quindi selezionare le caselle delle opzioni **Download debugging symbols** (Scarica simboli di debug) e **Download debug binaries** (Scarica file binari di debug):

    ![Programma di installazione di Python 3.x con l'opzione per includere i simboli di debug](media/mixed-mode-debugging-symbols-installer35.png)

    I file di simboli (`.pdb`) sono nella cartella radice di installazione. Anche i file di simboli per i singoli moduli sono nella cartella `DLLs`. Per questo motivo, Visual Studio li trova automaticamente e non sono necessari altri passaggi.

- Python 3.4.x e versioni precedenti: i simboli sono disponibili come file con estensione zip scaricabili dalle [distribuzioni ufficiali](#official-distributions) o da [Enthought Canopy](#enthought-canopy). Dopo il download, estrarre i file in una cartella locale per continuare, ad esempio una cartella `Symbols` nella cartella di Python.

    > [!Important]
    > I simboli sono diversi tra le diverse build secondarie di Python, nonché tra la build a 32 bit e quella a 64 bit, quindi è importante che le versioni corrispondano esattamente. Per verificare l'interprete in uso, espandere il **nodo** *Python Environments* nel progetto in Esplora soluzioni e annotare il nome dell'ambiente. Passare alla **finestra** *Python Environments* e prendere nota del percorso di installazione. Aprire quindi una finestra di comando in tale percorso e avviare `python.exe`, che visualizza la versione esatta e indica se è una versione a 32 o a 64 bit.

- Per qualsiasi altra distribuzione Python di terze parti, ad esempio ActiveState Python: contattare gli autori della distribuzione e richiedere loro i relativi simboli. WinPython tuttavia incorpora l'interprete Python standard senza modifiche, quindi usare i simboli della distribuzione ufficiale per il numero di versione corrispondente.

## <a name="pointing-visual-studio-to-the-symbols"></a>Impostare Visual Studio in modo che punti ai simboli

Se i simboli sono stati scaricati separatamente, eseguire i passaggi riportati di seguito per indicarlo a Visual Studio. Se i simboli sono stati installati con il programma di installazione di Python 3.5 o versione successiva, Visual Studio li trova automaticamente.

1. Selezionare il menu **Strumenti > Opzioni** e passare a **Debug > Simboli**.
    
1. Selezionare il pulsante **Aggiungi** sulla barra degli strumenti (evidenziata nell'immagine), immettere la cartella in cui sono stati espansi i simboli scaricati, ovvero dove si trova `python.pdb`, ad esempio `c:\python34\Symbols` nell'immagine, e selezionare **OK**. 

    ![Opzioni per i simboli del debugger in modalità mista](media/mixed-mode-debugging-symbols.png)

1. Durante una sessione di debug Visual Studio potrebbero anche richiedere il percorso di un file di origine per l'interprete Python. Se sono stati scaricati file di origine, ad esempio da [python.org/downloads](https://www.python.org/downloads), è ovviamente possibile fare riferimento anche a questi.

> [!Note]
> Le funzionalità di memorizzazione nella cache dei simboli presenti nella finestra di dialogo consentono di creare una cache locale dei simboli ottenuti da un'origine online. Queste funzionalità non sono necessarie con i simboli dell'interprete Python, poiché questi sono già disponibili in locale. In ogni caso, per informazioni dettagliate, vedere l'articolo relativo alla [definizione dei simboli e dei file di origine nel debugger di Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="official-distributions"></a>Distribuzioni ufficiali

| Versione di Python | Download | 
| --- | --- | 
| 3.5 e versioni successive | Installare i simboli usando il programma di installazione di Python. | 
| 3.4.4 | [32 bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32 bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32 bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32 bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32 bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32 bit](http://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64 bit](http://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32 bit](http://python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64 bit](http://python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32 bit](http://python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64 bit](http://python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32 bit](http://python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64 bit](http://python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32 bit](http://python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64 bit](http://python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32 bit](http://python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64 bit](http://python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.11 | [32 bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32 bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32 bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32 bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32 bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32 bit](http://python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64 bit](http://python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32 bit](http://python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64 bit](http://python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32 bit](http://python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64 bit](http://python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32 bit](http://python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64 bit](http://python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32 bit](http://python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64 bit](http://python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32 bit](http://python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64 bit](http://python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |


## <a name="enthought-canopy"></a>Enthought Canopy

Enthought Canopy fornisce i simboli per i relativi file binari a partire dalla versione 1.2. I simboli vengono installati automaticamente insieme alla distribuzione, ma è comunque necessario aggiungere manualmente la cartella che li contiene al percorso dei simboli come descritto in precedenza. Per un'installazione tipica per utente di Canopy, i simboli si trovano in `%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts` per la versione a 64 bit e in `%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts` per la versione a 32 bit.

Enthought Canopy 1.1 e versioni precedenti, così come Enthought Python Distribution (EPD), non forniscono simboli per l'interprete e pertanto non sono compatibili con il debug in modalità mista.