---
title: Uso di un file requirements.txt per gestire i requisiti dei pacchetti | Microsoft Docs
description: È possibile usare un file requirements.txt per gestire le dipendenze di un progetto. Se si riceve un progetto che contiene un file requirements.txt, è possibile installare facilmente tali dipendenze in un unico passaggio.
ms.custom: ''
ms.date: 02/20/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: b9d1a35d8ba34561c56ca14261591c7b80bacdb0
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="managing-required-packages-with-requirementstxt"></a>Gestione dei pacchetti necessari con requirements.txt

Se si condivide un progetto con altri utenti usando un sistema di compilazione oppure si intende [pubblicarlo in Microsoft Azure](python-azure-cloud-service-project-template.md), è necessario specificare i pacchetti esterni richiesti dal progetto. L'approccio consigliato prevede l'uso di un [file requirements.txt](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org), che contiene un elenco dei comandi per pip e che consente di installare le versioni richieste di pacchetti dipendenti.

Dal punto di vista tecnico, per tenere traccia dei requisiti è possibile usare un qualsiasi nome file (usando `-r <full path to file>` quando si installa un pacchetto), ma Visual Studio fornisce supporto specifico per `requirements.txt`:

- Se è stato caricato un progetto che contiene `requirements.txt` e si vogliono installare tutti i pacchetti elencati nel file, espandere il nodo **Ambienti Python** in **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul progetto e scegliere **Installa da requirements.txt**:

    ![Installa da requirements.txt](media/environments-requirements-txt-install.png)

- Se tutti i pacchetti necessari sono già installati in un ambiente, è possibile fare clic con il pulsante destro del mouse su tale ambiente in Esplora soluzioni e scegliere **Genera requirements.txt** per creare il file necessario. Se il file esiste già, viene visualizzato un prompt che chiede come aggiornarlo:

    ![Opzioni per l'aggiornamento di requirements.txt](media/environments-requirements-txt-replace.png)

  - **Sostituisci intero file**: rimuove tutti gli elementi, i commenti e le opzioni esistenti.
  - **Aggiorna voci esistenti**: rileva i requisiti del pacchetto e aggiorna gli identificatori di versione in base alla versione attualmente installata.
  - **Aggiorna e aggiungi voci**: aggiorna eventuali requisiti trovati e aggiunge tutti gli altri pacchetti alla fine del file.

Dal momento che i file `requirements.txt` servono a bloccare i requisiti di un ambiente, vengono indicate le versioni precise per tutti i pacchetti installati. L'uso di versioni precise garantisce di poter riprodurre facilmente l'ambiente in un altro computer. I pacchetti vengono inclusi anche se sono stati installati con un intervallo di versioni, come dipendenza di un altro pacchetto o con un programma di installazione diverso da pip.

Se pip non riesce a installare un pacchetto e questo è presente in un file `requirements.txt`, l'intera installazione non riesce. In questo caso, modificare manualmente il file in modo da escludere questo pacchetto oppure usare le [opzioni di pip](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) in modo che facciano riferimento a una versione installabile del pacchetto. È ad esempio possibile che si preferisca usare [`pip wheel`](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) per compilare una dipendenza e aggiungere l'opzione `--find-links <path>` al file `requirements.txt`:

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="see-also"></a>Vedere anche

- [Gestione di ambienti Python in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Selezionare un interprete per un progetto](selecting-a-python-environment-for-a-project.md)
- [Percorsi di ricerca](search-paths.md)
- [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md)