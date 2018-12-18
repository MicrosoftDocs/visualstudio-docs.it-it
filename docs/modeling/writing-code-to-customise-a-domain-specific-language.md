---
title: Personalizzare un linguaggio specifico di dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: e441de64c955fcc6780c4606a5a9855907d63f9f
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Scrivere codice per personalizzare un linguaggio specifico di dominio

In questa sezione viene illustrato come utilizzare codice personalizzato per accedere, modificare o creare un modello in un linguaggio specifico di dominio.

Esistono diversi contesti in cui è possibile scrivere codice che interagisce con un linguaggio DSL:

-   **Comandi personalizzati.** È possibile creare un comando che gli utenti possono richiamare facendo clic sul diagramma e che possono modificare il modello. Per ulteriori informazioni, vedere [procedura: aggiungere un comando al Menu di scelta rapida](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

-   **Convalida.** È possibile scrivere codice che verifica che il modello è in uno stato corretto. Per ulteriori informazioni, vedere [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).

-   **Override del comportamento predefinito.** È possibile modificare molti aspetti del codice generato da DslDefinition.dsl. Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).

-   **Trasformazione del testo.** È possibile scrivere modelli di testo che contengono codice che accede a un modello e genera un file di testo, ad esempio per generare codice programma. Per ulteriori informazioni, vedere [la generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md).

-   **Altre estensioni di Visual Studio.** È possibile scrivere le estensioni VSIX separate che può leggere e modificare i modelli. Per altre informazioni, vedere [procedura: aprire un modello dal File di codice programma](../modeling/how-to-open-a-model-from-file-in-program-code.md)

Le istanze delle classi definite in DslDefinition.dsl vengono mantenute in una struttura di dati denominata la *archivio In memoria* (IMS) o *archivio*. Classi definite in un linguaggio DSL sempre accettano un archivio come argomento al costruttore. Ad esempio, se il modello DSL definisce una classe denominata esempio:

`Example element = new Example (theStore);`

mantenere gli oggetti in un archivio (anziché oggetti solo come normali) offre diversi vantaggi.

-   **Le transazioni**. È possibile raggruppare una serie di modifiche correlate in una transazione:

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Se si verifica un'eccezione durante le modifiche, in modo che non viene eseguito il commit finale, l'archivio verrà reimpostato lo stato precedente. Questo permette di assicurarsi che gli errori non sia il modello in uno stato incoerente. Per ulteriori informazioni, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

-   **Le relazioni binarie**. Se si definisce una relazione tra due classi, le istanze a entrambe le estremità hanno una proprietà che consente di spostarsi verso l'altra estremità. Le due estremità sono sempre sincronizzate. Ad esempio, se si definisce una relazione parenthood con ruoli denominati elementi padre e figlio, è possibile scrivere:

     `John.Children.Add(Mary)`

     Entrambe le espressioni seguenti sono true:

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     È anche possibile ottenere lo stesso effetto scrivendo:

     `Mary.Parents.Add(John)`

     Per ulteriori informazioni, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

-   **Le regole e gli eventi**. È possibile definire regole che vengono generati quando si apportano modifiche specificate. Regole vengono utilizzate, ad esempio, per mantenere aggiornati con gli elementi del modello che presentano le forme nel diagramma. Per ulteriori informazioni, vedere [propagazione delle modifiche e risposta agli](../modeling/responding-to-and-propagating-changes.md).

-   **Serializzazione**. L'archivio fornisce un modo standard per serializzare oggetti in che esso contenuti in un file. È possibile personalizzare le regole per la serializzazione e deserializzazione. Per ulteriori informazioni, vedere [archiviazione dei File di personalizzazione e la serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md).

## <a name="see-also"></a>Vedere anche

- [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)