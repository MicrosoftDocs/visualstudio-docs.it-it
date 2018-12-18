---
title: JIT debug e ottimizzazione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a9b18ab38c7c19fa5208d34439bd3133099e8bc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="jit-optimization-and-debugging"></a>Debug e ottimizzazione JIT
**Modalità di funzionamento di ottimizzazioni in .NET:** se si sta tentando di eseguire il debug di codice, è più semplice quando che codice **non** ottimizzato. Infatti, quando il codice è ottimizzato, il compilatore e il runtime di apportare modifiche al codice della CPU generato in modo che viene eseguito più velocemente, ma dispone di un mapping meno diretto al codice sorgente originale. Ciò significa che i debugger sono in grado di indicare il valore delle variabili locali e l'esecuzione di istruzioni del codice e i punti di interruzione potrebbe non funzionare come previsto.

In genere la configurazione della build di rilascio crea codice ottimizzato e non la configurazione di compilazione di Debug. Il `Optimize` proprietà MSBuild controlla se il compilatore viene informato di ottimizzare il codice.

All'interno dell'ecosistema di .NET, codice è attivato dall'origine di istruzioni CPU in un processo in due fasi: innanzitutto, il compilatore c# converte il testo immesso in un formato binario intermedio denominato MSIL e si scrive in file con estensione dll. In un secondo momento, il Runtime .NET converte questo MSIL in istruzioni CPU. Entrambi i passaggi possono ottimizzare in qualche misura, ma il secondo passaggio eseguito dal Runtime di .NET esegue le ottimizzazioni più significative.

**L'opzione 'Disattivare l'ottimizzazione JIT al caricamento del modulo (solo gestito)':** il debugger espone un'opzione che controlla cosa accade quando si carica una DLL che viene compilata con ottimizzazioni abilitate all'interno del processo di destinazione. Se questa opzione è selezionata (stato predefinito), quindi quando il Runtime .NET viene compilato il codice MSIL in codice della CPU, lascia le ottimizzazioni abilitate. Se l'opzione è selezionata, il debugger richiede che le ottimizzazioni disabilitata.

Il **disattivare l'ottimizzazione JIT al caricamento del modulo (solo gestito)** opzione è disponibile nel **generale** pagina il **debug** nodo il **opzioni** la finestra di dialogo.

**Quando è necessario selezionare questa opzione:** selezionare questa opzione quando la DLL è stato scaricato da un'altra origine, ad esempio un pacchetto nuget, e si desidera eseguire il debug di codice nella DLL. Affinché il funzionamento, è anche necessario trovare il file di simboli (PDB) per questa DLL.

Se si è solo interessati debug del codice che si sta compilando in locale, è consigliabile lasciare questa opzione è deselezionata, come, in alcuni casi, l'abilitazione di questa opzione in modo significativo rallenterà il debug. Esistono due motivo rallentamento:

* Codice ottimizzato viene eseguito più velocemente. Se si disattiva la ottimizzazioni di grandi quantità di codice, è possibile aggiungere l'impatto sulle prestazioni.
* Se si dispone di Just My Code attivata, il debugger non tenta e caricare i simboli per DLL ottimizzati. Ricerca di simboli può richiedere molto tempo.

**Limitazioni di questa opzione:** ci sono due casi in cui questa opzione verrà **non** di lavoro:

1. In situazioni in cui si collega il debugger a un processo già in esecuzione, questa opzione non avrà effetto sui moduli che sono stati già caricati al momento che il debugger è collegato.
2. Questa opzione non ha effetto sulle DLL che sono stati precompilati (noti anche come stato applicato Ngen) al codice nativo. Tuttavia, è possibile disabilitare l'utilizzo di codice precompilato avviando il processo con l'ambiente di che variabile 'COMPlus_ZapDisable' impostato su '1'.

## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Collegare a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processo di esecuzione gestita](/dotnet/standard/managed-execution-process)
