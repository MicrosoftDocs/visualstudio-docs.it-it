---
title: Calcolare la metrica codice in Visual Studio
ms.date: 12/12/2017
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97bfe1c23e2681e90853bc55987317e3f27c7a08
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="code-metrics-values"></a>Valori della metrica del codice

La maggiore complessità delle applicazioni software moderne aumenta anche la difficoltà di rendere il codice affidabile e gestibile. La metrica del codice è un insieme di misure del software in grado di fornire agli sviluppatori una migliore comprensione del codice che stanno sviluppando. Sfruttando la metrica del codice, gli sviluppatori possono comprendere quali tipi e/o i metodi devono essere rielaborati oppure più approfonditi. I team di sviluppo possono identificare i potenziali rischi, comprendere lo stato corrente di un progetto e rilevare lo stato di avanzamento durante lo sviluppo di software.

Gli sviluppatori possono utilizzare Visual Studio per generare dati di metrica del codice che misurano la complessità e della manutenibilità del codice gestito. Dati di metrica codice possono essere generati per un'intera soluzione o un singolo progetto.

Per informazioni su come generare dati di metrica codice in Visual Studio, vedere [procedura: generare dati di metrica codice](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Misure del software

Nell'elenco seguente viene illustrato il codice risultati di metrica per il calcolo di Visual Studio:

- **Indice di manutenibilità** -calcola un valore di indice compreso tra 0 e 100 che rappresenta la relativa semplicità di gestione del codice. Un valore elevato indica una migliore gestibilità. Classificazioni codificato tramite colori consente di identificare rapidamente i punti critici del codice. Una classificazione verde è compreso tra 20 e 100 e indica che il codice ha una buona manutenibilità. Una classificazione gialla è compreso tra 10 e 19 e indica che il codice è moderatamente gestibile. Una classificazione rossa è compresa tra 0 e 9 e indica una manutenibilità insufficiente.

- **Complessità ciclomatica** -misura la complessità strutturale del codice. Viene creato per il calcolo del numero di percorsi del codice diversi nel flusso del programma. Un programma con il flusso di controllo complessi richiederà più test per ottenere un buon code coverage e sarà meno gestibile.

- **Profondità dell'ereditarietà** -indica il numero di definizioni di classi che estendono alla radice della gerarchia di classi. Maggiore è la profondità della gerarchia più difficile è possibile conoscere in cui vengono definiti determinati metodi e campi o / e ridefinito.

- **Accoppiamento** -misura l'accoppiamento di classi univoche tramite parametri, variabili locali, tipi restituiti, chiamate al metodo, creazioni di istanza generica o modello, le classi di base, le implementazioni dell'interfaccia, i campi definiti nei tipi esterni, e decorazione dell'attributo. Progettazione di software impone che i tipi e metodi devono avere coesione alta e accoppiamento basso. Accoppiamento elevato indica una progettazione che è difficile da riutilizzare e gestire a causa delle molte interdipendenze con altri tipi.

- **Righe di codice** -indica il numero approssimativo di righe di codice. Il conteggio è basato sul codice IL e pertanto non il numero esatto di righe nel file di codice sorgente. Un numero molto elevato potrebbe indicare che un tipo o metodo sta tentando di eseguire una quantità eccessiva di lavoro e deve essere suddiviso. Può inoltre indicare che il tipo o metodo potrebbe essere difficile da gestire.

## <a name="anonymous-methods"></a>Metodi anonimi

Un *metodo anonimo* è semplicemente un metodo che non ha nome. Metodi anonimi vengono utilizzati principalmente per passare un blocco di codice come un parametro del delegato. Risultati di metrica per un metodo anonimo che viene dichiarato in un membro, ad esempio un metodo o una funzione di accesso, sono associati al membro che dichiara il metodo. Non sono associate con il membro che chiama il metodo.

Per ulteriori informazioni su come metrica del codice tratta i metodi anonimi, vedere [metodi anonimi e analisi del codice](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Codice generato

Alcuni strumenti software e i compilatori di generano il codice che viene aggiunto a un progetto e che lo sviluppatore di progetto non consente di visualizzare o non deve modificare. In genere, la metrica del codice ignora il codice generato durante il calcolo dei valori delle metriche. In questo modo i valori della metrica in base a ciò che lo sviluppatore può visualizzare e modificare.

Codice generato per Windows Form non viene ignorato, poiché si tratta di codice che lo sviluppatore può visualizzare e modificare.

## <a name="next-steps"></a>Passaggi successivi

- [Procedura: generare dati di metrica codice](../code-quality/how-to-generate-code-metrics-data.md)
- [Utilizzare la finestra Risultati metrica codice](../code-quality/working-with-code-metrics-data.md)