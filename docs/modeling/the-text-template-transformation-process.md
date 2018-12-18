---
title: Processo di trasformazione del modello di testo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 322a8aac233f739180de903779210e1446306166
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="the-text-template-transformation-process"></a>Processo di trasformazione del modello di testo
Il processo di trasformazione del modello testo accetta un file di modello di testo come input e genera un nuovo file di testo come output. Ad esempio, è possibile utilizzare modelli di testo per generare il codice Visual Basic o c# oppure è possibile generare un report HTML.

 Tre componenti prendono parte di questo processo: il motore, l'host e i processori di direttiva. Il motore controlla il processo. Questa utilità interagisce con l'host e il processore di direttiva per generare il file di output. L'host fornisce qualsiasi interazione con l'ambiente, ad esempio l'individuazione di file e assembly. Il processore di direttiva aggiunge funzionalità, ad esempio la lettura dei dati da un file XML o un database.

 Il processo di trasformazione di modello di testo viene eseguito in due passaggi. In primo luogo, il motore crea una classe temporanea, nota come classe della trasformazione generata. Questa classe contiene il codice generato dalle direttive e blocchi di controllo. Successivamente, il motore compila ed esegue la classe della trasformazione generata per generare il file di output.

## <a name="components"></a>Componenti

|Componente|Descrizione|Personalizzabile (Sì/No)|
|---------------|-----------------|------------------------------|
|Motore di|Il componente motore controlla il processo di trasformazione di modello di testo|No.|
|Host|L'host è l'interfaccia tra il motore e l'ambiente utente. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è un host del processo di trasformazione del testo.|Sì. È possibile scrivere un host personalizzato.|
|Processori di direttiva|Processori di direttive sono classi che gestiscono direttive nei modelli di testo. È possibile utilizzare le direttive per fornire dati per un modello di testo da un'origine di input.|Sì. È possibile scrivere processori di direttive personalizzate|

## <a name="the-engine"></a>Il motore di
 Il motore riceve il modello sotto forma di stringa dall'host, che gestisce tutti i file che vengono utilizzati nel processo di trasformazione. Il motore chiede quindi l'host per individuare eventuali processori di direttiva personalizzati e altri aspetti dell'ambiente. Quindi, il motore compila ed esegue la classe della trasformazione generata. Il motore restituisce il testo generato per l'host, che generalmente Salva il testo in un file.

## <a name="the-host"></a>L'Host
 L'host è responsabile per qualsiasi elemento che si riferisce all'ambiente all'esterno del processo di trasformazione, inclusi i seguenti:

-   Individuazione file di testo e binari richiesti dal motore di o a un processore di direttiva. L'host può cercare le directory e global assembly cache per individuare gli assembly. L'host può individuare il codice di processore di direttiva personalizzato per il motore. L'host può anche individuare e leggere i file di testo e restituire il contenuto come stringhe.

-   Fornire gli elenchi di assembly standard e gli spazi dei nomi utilizzati dal motore per creare una classe della trasformazione generata.

-   Fornire il dominio dell'applicazione che viene utilizzato quando il motore compila ed esegue la classe della trasformazione generata. Un dominio applicazione separato viene utilizzato per proteggere l'applicazione host da errori nel codice del modello.

-   Scrittura del file di output generato.

-   Impostazione dell'estensione predefinita per il file di output generato.

-   Gestione degli errori di trasformazione modello di testo. Ad esempio, l'host può visualizzare gli errori nell'interfaccia utente o scriverli in un file. (In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], gli errori vengono visualizzati nella finestra di messaggio di errore.)

-   Se un utente ha chiamato una direttiva senza fornire un valore, fornendo un valore di parametro obbligatorio. Il processore di direttiva può specificare il nome della direttiva e il parametro e chiedere all'host di fornire un valore predefinito se ne ha uno.

## <a name="directives-and-directive-processors"></a>Direttive e processori di direttiva
 Una direttiva è un comando nel modello di testo. Fornisce i parametri per il processo di generazione. In genere, le direttive definiscono l'origine e il tipo del modello o di altri tipi di input e l'estensione del file di output.

 Un processore di direttiva può elaborare una o più direttive. Quando si trasforma un modello, è necessario aver installato un processore di direttiva possa gestire le direttive del modello.

 Le direttive funzionano aggiungendo codice nella classe della trasformazione generata. Si chiamano direttive da un modello di testo e il motore elabora tutte le chiamate direttive durante la creazione di classe della trasformazione generata. Dopo aver chiamato una direttiva correttamente, il resto del codice che scrive nel modello di testo può basarsi sulle funzionalità che la direttiva fornisce. Ad esempio, è possibile effettuare la chiamata seguente al `import` direttiva del modello:

 `<#@ import namespace="System.Text" #>`

 Il processore di direttiva standard converte in un `using` istruzione nella classe della trasformazione generata. È quindi possibile utilizzare il `StringBuilder` classe nella parte restante del codice del modello senza qualificare come `System.Text.StringBuilder`.