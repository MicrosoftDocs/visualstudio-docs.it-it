---
title: Come vengono applicati i percorsi di ricerca di Python | Microsoft Docs
description: Panoramica dell'uso dei percorsi di ricerca Python in Visual Studio per i progetti e gli ambienti.
ms.custom: ''
ms.date: 03/05/2018
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
ms.openlocfilehash: 9ebb5ac043253db76cc9613ac67e5d980d911bd3
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Come vengono usati i percorsi di ricerca di Python Visual Studio

Quando Python viene usato normalmente, il percorso di ricerca predefinito per i file di modulo viene fornito dalla variabile di ambiente `PYTHONPATH` (o `IRONPYTHONPATH` e così via). Quando si usa un'istruzione `from <name> import...` o `import <name>`, Python esegue la ricerca di un nome corrispondente nelle posizioni seguenti nell'ordine indicato:

1. I moduli predefiniti di Python.
1. La cartella contenente il codice Python in esecuzione.
1. Il "percorso di ricerca del modulo" come definito dalla variabile di ambiente applicabile. Vedere [The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) (Percorso di ricerca del modulo) e [Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (Variabili di ambiente) nella documentazione principale di Python.

Visual Studio ignora tuttavia la variabile di ambiente del percorso di ricerca, anche se è stata impostata per l'intero sistema. In realtà, viene ignorata proprio *perché* è impostata per l'intero sistema e non consente di rispondere automaticamente a domande di questo tipo: i moduli di riferimento sono validi per Python 2.7 o per Python 3.6? Sostituiranno i moduli di libreria standard? Lo sviluppatore è a conoscenza di questo comportamento o si tratta di un tentativo di hijack effettuato da utenti malintenzionati?

Visual Studio consente quindi di specificare direttamente i percorsi di ricerca sia negli ambienti che nei progetti. Il codice eseguito o sottoposto a debug in Visual Studio riceve i percorsi di ricerca nel valore di `PYTHONPATH` (e altre variabili equivalenti). Quando si aggiungono percorsi di ricerca, Visual Studio controlla le librerie in questi percorsi e crea i database di IntelliSense corrispondenti all'occorrenza (Visual Studio 2017 versione 15.5 e precedenti; la creazione dei database potrebbe richiedere tempo a seconda del numero di librerie).

Per aggiungere un percorso di ricerca, fare clic con il pulsante destro del mouse sull'elemento **Percorsi di ricerca** in Esplora soluzioni, scegliere **Aggiungi cartella al percorso di ricerca** e selezionare la cartella da includere. Questo percorso viene usato per qualsiasi ambiente associato al progetto. (È possibile riscontrare errori se l'ambiente è basato su Python 3 e si tenta di aggiungere un percorso di ricerca per i moduli Python 2.7.)

È possibile aggiungere come percorsi di ricerca i file con estensione `.zip` o `.egg`, selezionando **Aggiungi archivio ZIP al percorso di ricerca**. Come con le cartelle, il contenuto di questi file viene analizzato e reso disponibile per IntelliSense.

Se si usa regolarmente gli stessi percorsi di ricerca e il contenuto non cambia spesso, può risultare più comodo eseguire l'installazione nella cartella dei pacchetti del sito. Il percorso di ricerca viene quindi analizzato e archiviato nel database di IntelliSense ed è sempre associato all'ambiente di destinazione indicato. Non è inoltre più necessario aggiungere un percorso di ricerca a ogni progetto.

## <a name="see-also"></a>Vedere anche

- [Gestione di ambienti Python in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Selezionare un interprete per un progetto](selecting-a-python-environment-for-a-project.md)
- [Uso di requirements.txt per le dipendenze](managing-required-packages-with-requirements-txt.md)
- [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md)