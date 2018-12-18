---
title: Selezione e installazione di interpreti Python
description: Elenco completo degli interpreti Python supportati in Visual Studio con brevi istruzioni su dove trovare i relativi programmi di installazione.
ms.date: 02/20/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: ed5ac9e470b55281d1273bfe665be0813b37bf55
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="installing-python-interpreters"></a>Installazione degli interpreti Python

Per impostazione predefinita, l'installazione del carico di lavoro di sviluppo Python in Visual Studio 2017 installa anche Python 3 (a 64 bit). È possibile scegliere facoltativamente di installare le versioni a 32 bit e a 64 bit di Python 2, Python 3, Anaconda 2 e Anaconda 3, come descritto in [Installazione](installing-python-support-in-visual-studio.md).

È anche possibile installare manualmente uno qualsiasi degli interpreti elencati nella tabella riportata di seguito al di fuori del programma di installazione di Visual Studio. Ad esempio, se Anaconda 3 è stato installato prima di installare Visual Studio, non è necessario eseguire nuovamente l'installazione tramite il programma di installazione di Visual Studio.

Per **Visual Studio 2015 e versioni precedenti** è necessario installare manualmente uno degli interpreti.

Visual Studio, in tutte le versioni, rileva automaticamente ogni interprete Python installato e il relativo ambiente controllando il Registro di sistema, come descritto in [PEP 514 - Python registration in the Windows registry](https://www.python.org/dev/peps/pep-0514/) (PEP 514 - Registrazione di Python nel Registro di sistema di Windows).

Se Visual Studio non rileva un ambiente installato, vedere [Manually identifying an existing environment](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment) (Identificazione manuale di un ambiente esistente).

Visual Studio visualizza tutti gli ambienti noti nella [finestra Ambienti Python](managing-python-environments-in-visual-studio.md) e rileva automaticamente gli aggiornamenti per gli interpreti esistenti.

| Interprete | Descrizione |
| --- | --- |
| [CPython](https://www.python.org/) | Interprete "nativo" più comunemente usato, disponibile nelle versioni a 32 bit e a 64 bit (consigliata la versione a 32 bit). Include le funzionalità più recenti del linguaggio e offre la massima compatibilità con i pacchetti Python, nonché il supporto completo per il debug e l'interoperabilità con [IPython](http://ipython.org/). Vedere anche: [Should I use Python 2 or Python 3?](http://wiki.python.org/moin/Python2orPython3) (Differenze tra Python 2 e Python 3). Si noti che Visual Studio 2015 e versioni precedenti non supportano Python 3.6 e possono segnalare l'errore "Versione 3.6 di Python non supportata". Usare Python 3.5 o versioni precedenti. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Implementazione .NET di Python, disponibile nelle versioni a 32 bit e a 64 bit, che offre interoperabilità con C#/F# e Visual Basic, accesso alle API .NET, debug Python standard (ma non debug C++ in modalità mista) e debug IronPython/C# in modalità mista. IronPython non supporta però gli ambienti virtuali. |
| [Anaconda](https://www.continuum.io) | Piattaforma Open Data Science basata su Python che include la versione più recente di CPython e la maggior parte dei pacchetti difficili da installare. È la piattaforma consigliata se non è possibile sceglierne una diversa. |
| [PyPy](http://www.pypy.org/) | Implementazione JIT di traccia ad alte prestazioni di Python, ideale per applicazioni a esecuzione prolungata e situazioni in cui si verificano problemi di prestazioni, ma non si riesce a trovare altre soluzioni. Funziona con Visual Studio, ma offre supporto limitato per le funzionalità avanzate di debug. |
| [Jython](http://www.jython.org/) | Implementazione di Python in Java Virtual Machine (JVM). Analogamente a IronPython, il codice in esecuzione in Jython può interagire con librerie e classi Java, ma potrebbe non essere in grado di usare molte librerie destinate a CPython. Funziona con Visual Studio, ma offre supporto limitato per le funzionalità avanzate di debug. |

Se si intende offrire nuove forme di rilevamento per gli ambienti Python, vedere [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (Rilevamento degli ambienti PTVS) su github.com.

## <a name="moving-an-interpreter"></a>Spostamento di un interprete

Se si sposta un interprete esistente in una nuova posizione nel file system, Visual Studio non rileva automaticamente la modifica.

- Se il percorso dell'interprete è stato specificato in origine tramite la finestra **Ambienti Python**, modificarne l'ambiente tramite la scheda **Configura** in tale finestra per identificare il nuovo percorso. Vedere [Manually identifying an existing environment](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment) (Identificazione manuale di un ambiente esistente).

- Se l'interprete è stato installato usando un programma di installazione, seguire questa procedura per reinstallare l'interprete nel nuovo percorso:

  1. Ripristinare l'interprete Python nel percorso originale.
  2. Disinstallare l'interprete usando il relativo programma di installazione, in modo da cancellare le voci del Registro di sistema.
  3. Reinstallare l'interprete nel percorso desiderato.
  4. Riavviare Visual Studio, in modo che rilevi automaticamente il nuovo percorso, al posto del precedente.

Seguendo questa procedura si assicura il corretto aggiornamento delle voci del Registro di sistema che identificano il percorso dell'interprete, usato da Visual Studio. L'uso di un programma di installazione consente anche di gestire eventuali altri effetti collaterali.

## <a name="see-also"></a>Vedere anche

- [Gestione degli ambienti Python](managing-python-environments-in-visual-studio.md)
- [Selezionare un interprete per un progetto](selecting-a-python-environment-for-a-project.md)
- [Uso di requirements.txt per le dipendenze](managing-required-packages-with-requirements-txt.md)
- [Percorsi di ricerca](search-paths.md)
- [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md)