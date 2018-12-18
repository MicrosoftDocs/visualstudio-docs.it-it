---
title: Esecuzione simbolica dinamica | Strumento di test per sviluppatori Microsoft IntelliTest | Microsoft Docs
ms.date: 05/02/2017
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Dynamic symbolic execution
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 083ee0e340688065ab765961676da63c405fd434
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="input-generatation-using-dynamic-symbolic-execution"></a>Generazione di input con l'esecuzione simbolica dinamica

IntelliTest genera input per gli [unit test con parametri](test-generation.md#parameterized-unit-testing) analizzando le condizioni di ramo nel programma. Gli input di test vengono scelti in base alla loro capacità di attivare nuovi comportamenti di creazione rami del programma. L'analisi è un processo incrementale. Ottimizza un predicato **q: I -> {true, false}** sui parametri di input di test formali **I**. **q** rappresenta l'insieme di comportamenti già osservati da IntelliTest. Inizialmente **q: = false** perché non è ancora stato osservato nessun comportamento.

Le fasi del ciclo sono:

1. IntelliTest determina input **i** come **q(i)=false** mediante un [risolutore di vincoli](#constraint-solver). 
   Per costruzione, l'input **i** adotta un percorso di esecuzione non rilevato in precedenza. Inizialmente ciò significa che **i** può essere qualsiasi input, perché non è ancora stato scoperto nessun percorso di esecuzione.

1. IntelliTest esegue il test con l'input **i** scelto e controlla l'esecuzione del test e il programma sottoposto al test.

1. Durante l'esecuzione il programma accetta un percorso specifico, determinato da tutti i rami condizionali del programma. Il set di tutte le condizioni che determinano l'esecuzione è detto *condizione di percorso*, scritta sotto forma di predicato **p: -> {true, false}** sui parametri di input formali. IntelliTest calcola una rappresentazione del predicato.

1. IntelliTest imposta **q := (q o p)**. In altre parole registra il fatto che ha rilevato il percorso rappresentato da **p**.

1. Andare al passaggio 1.

Il [risolutore di vincoli](#constraint-solver) di IntelliTest può gestire valori di tutti i tipi presenti nelle applicazioni .NET:

* [Integer](#integers-and-floats) e [Float](#integers-and-floats)
* [Oggetti](#objects)
* [Struct](#structs)
* [Array](#arrays-and-strings) e [String](#arrays-and-strings)

IntelliTest esclude gli input che violano i presupposti dichiarati.

Oltre agli input immediati (argomenti di [unit test con parametri](test-generation.md#parameterized-unit-testing)), un test può estrarre altri valori di input dalla classe statica [PexChoose](static-helper-classes.md#pexchoose). Le scelte determinano anche il comportamento degli [oggetti fittizi con parametri](#parameterized-mocks).

<a name="constraint-solver"></a>
## <a name="constraint-solver"></a>Risolutore di vincoli

IntelliTest usa un risolutore di vincoli per determinare i valori di input rilevanti per il test e il programma sottoposto a test.

IntelliTest usa il risolutore di vincoli [Z3](https://github.com/Z3Prover/z3/wiki).

<a name="dynamic-code-coverage"></a>
## <a name="dynamic-code-coverage"></a>Code coverage dinamico

Come effetto collaterale del monitoraggio in fase di esecuzione, IntelliTest consente di raccogliere dati di code coverage dinamico. Il termine *dinamico* indica che IntelliTest agisce solo su codice già eseguito, pertanto non può specificare valori assoluti per il coverage come fanno altri strumenti. 

Ad esempio, quando IntelliTest segnala come code coverage dinamico 5/10 blocchi di base, ciò significa che sono stati analizzati cinque blocchi su dieci e che dieci è il numero totale di blocchi in tutti i metodi raggiunti finora dall'analisi (e non di tutti i metodi esistenti nell'assembly sottoposto a test).
In una fase successiva dell'analisi, man mano che vengono rilevati altri metodi raggiungibili, è possibile che aumentino sia il numeratore (5) che il denominatore (10) della frazione di questo esempio.

<a name="integers-and-floats"></a>
## <a name="integers-and-floats"></a>Integer e float

Il [risolutore di vincoli](#constraint-solver) di IntelliTest determina i valori di input di test dei tipi primitivi quali **byte**, **int**, **float** e altri ancora, per attivare percorsi di esecuzione diversi per il test e il programma sottoposto a test.

<a name="objects"></a>
## <a name="objects"></a>Oggetti

IntelliTest può [creare istanze di classi .NET esistenti](#existing-classes) oppure può essere usato per [creare automaticamente oggetti fittizi](#parameterized-mocks) che implementano un'interfaccia specifica e presentano comportamenti diversi a seconda dell'uso.

<a name="existing-classes"></a>
## <a name="instantiating-existing-classes"></a>Creazione di istanze di classi esistenti

**Definizione del problema**

IntelliTest consente di monitorare le istruzioni completate quando esegue un test e il programma sottoposto a test. In particolare esegue il monitoraggio di tutti gli accessi ai campi. Quindi usa un [risolutore di vincoli](#constraint-solver) per determinare i nuovi input di test, inclusi gli oggetti e i valori dei campi corrispondenti, in modo che il test e il programma sottoposto a test adottino altri comportamenti interessanti.

Pertanto IntelliTest deve essere in grado di creare oggetti di determinati tipi e di impostare i valori dei campi di tali oggetti. Se la classe è [visible](#visibility) e ha un costruttore predefinito [visible](#visibility), IntelliTest può creare un'istanza della classe.
Se tutti i campi della classe sono [visible](#visibility), IntelliTest può impostare i campi automaticamente.

Se il tipo non è visibile o i campi non sono [visible](#visibility), IntelliTest richiede un apporto esterno per creare oggetti e impostare stati interessanti al fine di ottenere il massimo code coverage. IntelliTest potrebbe usare la reflection per creare e inizializzare istanze in modo arbitrario, ma in genere questo approccio non è  
consigliabile perché può impostare stati dell'oggetto che non possono mai verificarsi durante l'esecuzione normale del programma. IntelliTest si basa invece sui suggerimenti specificati dall'utente.

<a name="visibility"></a>
## <a name="visibility"></a>Visibility

.NET Framework offre un modello di visibilità elaborato: i tipi, i metodi, i campi e gli altri membri possono essere **private**, **public**, **internal** e altro ancora.

Quando IntelliTest genera test, prova a eseguire solo azioni (ad esempio la chiamata di costruttori o metodi e l'impostazione dei campi) valide in base alle regole di visibilità .NET all'interno del contesto dei test generati.

Le regole sono le seguenti:

* **Visibilità dei membri interni**
  * IntelliTest presuppone che i test generati avranno accesso ai membri interni che risultano visibili alla classe [PexClass](attribute-glossary.md#pexclass) di inclusione.
  Per estendere ad altri assembly la visibilità dei membri interni, .NET dispone di **InternalsVisibleToAttribute**.<p />

* **Visibilità di membri privati e della famiglia (protected in C#) della classe [PexClass](attribute-glossary.md#pexclass)**
  * IntelliTest inserisce sempre direttamente i test generati nella classe [PexClass](attribute-glossary.md#pexclass) o in una sottoclasse. Pertanto IntelliTest presuppone che può usare tutti i membri della famiglia visibili (**protected** in C#).
  * Se i test generati vengono inseriti direttamente in [PexClass](attribute-glossary.md#pexclass) (in genere usando le classi parziali), IntelliTest presuppone che può usare anche tutti i membri privati della classe [PexClass](attribute-glossary.md#pexclass).<p />

* **Visibilità dei membri pubblici**
  * IntelliTest presuppone che può usare tutti i membri esportati visibili nel contesto di [PexClass](attribute-glossary.md#pexclass).

<a name="parameterized-mocks"></a>
## <a name="parameterized-mocks"></a>Oggetti fittizi con parametri

Come testare un metodo che ha un parametro di un tipo di interfaccia? O di una classe non sealed? IntelliTest non può determinare quali implementazioni verranno usate dopo la chiamata di questo metodo. È anche possibile che al momento del test non sia disponibile un'implementazione reale.

La risposta convenzionale è l'uso di *oggetti fittizi* con comportamento esplicito. 

Un oggetto fittizio implementa un'interfaccia (o estende una classe non sealed). Non rappresenta un'implementazione reale, ma solo un collegamento che consente l'esecuzione di test usando l'oggetto fittizio. Il suo comportamento è definito manualmente in ogni test case nel quale viene usato. Esistono numerosi strumenti che semplificano la definizione degli oggetti fittizi e del comportamento previsto, ma questo comportamento va comunque definito manualmente.

Anziché usare valori hard-coded negli oggetti fittizi, IntelliTest può generare i valori. Così come supporta gli [unit test con parametri](test-generation.md#parameterized-unit-testing), IntelliTest supporta anche gli oggetti fittizi con parametri.

Per gli oggetti fittizi con parametri sono disponibili due modalità di esecuzione diverse:

* **Scelta**: durante l'esplorazione del codice, gli oggetti fittizi con parametri producono input di test aggiuntivi e IntelliTest prova a scegliere valori interessanti.
* **Riesecuzione**: quando si esegue un test generato in precedenza, gli oggetti fittizi con parametri funzionano come stub con comportamento (in altre parole, comportamento predefinito).

Per ottenere valori per gli oggetti fittizi con parametri, usare [PexChoose](static-helper-classes.md#pexchoose).

<a name="structs"></a>
## <a name="structs"></a>Struct

Il procedimento di IntelliTest con i valori **struct** è simile a quello usato con gli [oggetti](#objects).

<a name="arrays-and-strings"></a>
## <a name="arrays-and-strings"></a>Matrici e stringhe

IntelliTest consente di monitorare le istruzioni completate mentre esegue un test e il programma sottoposto a test. In particolare rileva quando il programma dipende dalla lunghezza di una stringa o di una matrice (e dai limiti inferiori e dalle lunghezze di una matrice multidimensionale). Rileva anche l'uso dei diversi elementi di una stringa o una matrice. Quindi usa un [risolutore di vincoli](#constraint-solver) per determinare le lunghezze e i valori degli elementi con i quali il test e il programma possono originare comportamenti interessanti.

IntelliTest prova a ridurre al minimo le dimensioni delle matrici e delle stringhe necessarie per attivare i comportamenti di programma interessanti.

<a name="additional-inputs"></a>
## <a name="obtaining-additional-inputs"></a>Recupero di input aggiuntivi

La classe statica [PexChoose](static-helper-classes.md#pexchoose) può essere usata per ottenere input aggiuntivi per un test e per implementare [oggetti fittizi con parametri](#parameterized-mocks).

<a name="further-reading"></a>
## <a name="further-reading"></a>Ulteriori informazioni

* [Funzionamento](https://blogs.msdn.microsoft.com/visualstudioalm/2014/12/11/smart-unit-tests-a-mental-model/)

## <a name="got-feedback"></a>Commenti?

Pubblicare idee e richieste di funzionalità in **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
