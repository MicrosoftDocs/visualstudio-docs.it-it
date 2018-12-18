---
title: Uso del codice Visual C++ (Progettazione classi) | Microsoft Docs
ms.custom: ''
ms.date: 06/21/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- Visual C++, Class Designer
- Class Designer, Visual C++ support
- Class Designer, limitations
- Class Designer, tasks in Visual C++
- Visual C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 490ab617e52e78681f6fdd427548c5e1cbd59957
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="working-with-visual-c-code-class-designer"></a>Utilizzo del codice Visual C++ (Progettazione classi)
Progettazione classi usa un'area di progettazione visiva denominata *diagramma classi* per rappresentare visivamente gli elementi di codice nel progetto. Si possono usare i diagrammi classi per progettare e visualizzare le classi e gli altri tipi in un progetto.  

Progettazione classi supporta gli elementi di codice C++ seguenti:  

-   Classe (simile a una forma di classe gestita, con la differenza che può avere relazioni di ereditarietà multiple)  

-   Classe anonima (visualizza il nome generato da Visualizzazione classi per il tipo anonimo)  

-   Classe modello  

-   Struct  

-   Enum  

-   Macro (visualizza la prospettiva post-elaborata della macro)  

-   Typedef  

> [!NOTE]
>  Non corrisponde al diagramma classi UML, che è possibile creare in un progetto di modellazione. Per altre informazioni, vedere [UML Class Diagrams: Reference](../../modeling/uml-class-diagrams-reference.md) (Diagrammi classi UML: riferimenti)  

## <a name="troubleshooting-type-resolution-and-display-issues"></a>Risoluzione dei problemi relativi al tipo e alla visualizzazione  

### <a name="location-of-source-files"></a>Percorso dei file di origine  
Progettazione classi non tiene traccia del percorso dei file di origine. Di conseguenza, se si modifica la struttura del progetto o si spostano file di origine nel progetto, Progettazione classi può perdere traccia del tipo (soprattutto il tipo di origine di un typedef, classi base o tipi di associazione). Si potrebbe ricevere un errore, ad esempio **Progettazione classi: impossibile visualizzare il tipo**. In tal caso, trascinare di nuovo il codice sorgente modificato o riposizionato nel diagramma classi per visualizzarlo nuovamente.  

### <a name="update-and-performance-issues"></a>Problemi di aggiornamento e di prestazioni  
Per i progetti Visual C++, potrebbero essere necessari dai 30 ai 60 secondi perché una modifica nel file di origine venga visualizzata nel diagramma classi. A causa di questo ritardo, Progettazione classi potrebbe anche generare l'errore **Nessun tipo trovato nella selezione**. Se viene visualizzato un messaggio di errore di questo tipo, scegliere **Annulla** nel messaggio di errore e attendere che l'elemento di codice venga visualizzato in Visualizzazione classi. A questo punto, Progettazione classi dovrebbe essere in grado di visualizzare il tipo.  

Se il diagramma classi non viene aggiornato con le modifiche apportate nel codice, può essere necessario chiuderlo e riaprirlo.  

### <a name="type-resolution-issues"></a>Problemi di risoluzione del tipo  
Progettazione classi potrebbe non essere in grado di risolvere i tipi per i motivi seguenti:  
  
-   Il tipo si trova in un progetto o in un assembly a cui non viene fatto riferimento dal progetto che contiene il diagramma classi. Per correggere questo errore, aggiungere un riferimento al progetto o all'assembly che contiene il tipo. Per altre informazioni, vedere [Gestione dei riferimenti in un progetto](../managing-references-in-a-project.md).  
  
-   Il tipo non si trova nell'ambito corretto, di conseguenza Progettazione classi non è in grado di trovarlo. Verificare che nel codice non manchi un'istruzione `using`, `imports` o `#include`. Assicurarsi inoltre che il tipo (o un tipo correlato) non sia stato spostato dallo spazio dei nomi in cui si trovava in origine.  

-   Il tipo non esiste oppure è stato impostato come commento. Per correggere questo errore, assicurarsi di non aver impostato il tipo come commento o di non averlo eliminato.  

-   Il tipo si trova in una libreria a cui fa riferimento una direttiva #import. Una possibile soluzione alternativa consiste nell'aggiungere manualmente il codice generato (il file con estensione tlh) a una direttiva #include nel file di intestazione.  

Per un problema di risoluzione del tipo, l'errore più comunemente segnalato è **Impossibile trovare il codice per una o più forme nel diagramma classi '\<elemento>'**. Questo messaggio di errore non indica necessariamente che il codice sia errato. Indica solo che Progettazione classi non è in grado di visualizzare il codice.  Provare a eseguire le operazioni seguenti.  

-   Verificare l'esistenza del tipo. Verificare di non aver involontariamente eliminato o impostato come codice il codice sorgente.  

-   Verificare che Progettazione classi supporti il tipo inserito. Vedere [Limitazioni per gli elementi di codice C++](#limitations).  

-   Provare a risolvere il tipo. Il tipo potrebbe trovarsi in un progetto o in un assembly a cui non viene fatto riferimento dal progetto che contiene il diagramma classi. Per correggere questo errore, aggiungere un riferimento al progetto o all'assembly che contiene il tipo. Per altre informazioni, vedere [Gestione dei riferimenti in un progetto](../managing-references-in-a-project.md).  

-   Verificare che il tipo si trovi nell'ambito corretto in modo che Progettazione classi possa trovarlo. Assicurarsi che nel codice non manchi un'istruzione `using`, `imports` o `#include`. Assicurarsi inoltre che il tipo (o un tipo correlato) non sia stato spostato dallo spazio dei nomi in cui si trovava in origine.  

### <a name="troubleshooting-other-error-messages"></a>Risoluzione di altri messaggi di errore  
È possibile ottenere assistenza per la risoluzione dei problemi relativi a errori e avvisi nei forum pubblici MSDN (Microsoft Developer Network). Vedere il [forum dedicato a Progettazione classi di Visual Studio](http://go.microsoft.com/fwlink/?linkid=160754).  

##  <a name="limitations"></a> Limitazioni per gli elementi di codice C++  

-   Quando viene caricato un progetto Visual C++, Progettazione classi funziona in modalità di sola lettura. È possibile modificare il diagramma classi, ma non salvare modifiche dal diagramma classi nel codice sorgente.  

-   Progettazione classi supporta solo semantica C++ nativa.  Per i progetti Visual C++ compilati in codice gestito, Progettazione classi visualizzerà solo gli elementi di codice che sono tipi nativi. Di conseguenza, è possibile aggiungere un diagramma classi a un progetto, ma Progettazione classi non consentirà di visualizzare elementi in cui la proprietà `IsManaged` è impostata su `true` (ovvero tipi di valore e tipi di riferimento).  

-   Per i progetti Visual C++, Progettazione classi legge soltanto la definizione del tipo. Ad esempio, si supponga di definire un tipo in un file di intestazione (.h) e i relativi membri in un file di implementazione (.cpp). Se si richiama "Visualizza diagramma classi" sul file di implementazione (.cpp), Progettazione classi non visualizzerà niente. Per fare un altro esempio, se si richiama "Visualizza diagramma classi" su un file .cpp che usa un'istruzione `#include` per includere altri file ma non contiene definizioni della classe, Progettazione classi analogamente non visualizzerà niente.  

-   I file IDL (.idl), che definiscono le interfacce COM e le librerie dei tipi, non vengono visualizzati nei diagrammi a meno che non siano compilati in codice C++ nativo.  

-   Progettazione classi non supporta funzioni e variabili globali.  

-   Progettazione classi non supporta unioni. Si tratta di un tipo speciale di classe in cui la memoria allocata è solo la quantità necessaria per il membro dati più grande dell'unione.  

-   Progettazione classi non visualizza tipi di dati di base come ad esempio `int` e `char`.  

-   Progettazione classi non visualizza tipi definiti all'esterno del progetto corrente se il progetto non ha riferimenti corretti a tali tipi.  

-   Progettazione classi visualizza i tipi annidati, ma non le relazioni tra un tipo annidato e altri tipi.  

-   Progettazione classi non può visualizzare tipi void o che derivano da un tipo void.  

## <a name="see-also"></a>Vedere anche
[Designing and Viewing Classes and Types](designing-and-viewing-classes-and-types.md)  (Progettazione e visualizzazione di classi e tipi)  
[Uso di diagrammi classi](working-with-class-diagrams.md)   
[Progettazione di classi e tipi](designing-classes-and-types.md)   
[Additional Information About Class Designer Errors](additional-information-about-errors.md)  (Informazioni aggiuntive sugli errori di Progettazione classi)  
[Visual C++ Classes in Class Designer](visual-cpp-classes.md)  (Classi Visual C++ in Progettazione classi)  
[Visual C++ Structures in Class Designer](visual-cpp-structures.md)  (Strutture Visual C++ in Progettazione classi)  
[Visual C++ Enumerations in Class Designer](visual-cpp-enumerations.md)  (Enumerazioni Visual C++ in Progettazione classi)  
[Typedef di Visual C++ in Progettazione classi](visual-cpp-typedefs.md)
