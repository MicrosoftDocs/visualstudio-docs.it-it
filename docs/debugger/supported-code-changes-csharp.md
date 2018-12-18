---
title: Modifiche supportate al codice (c# e Visual Basic) | Documenti Microsoft
ms.custom: ''
ms.date: 10/11/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 855e8111721480b98c1395811090a54dd6e3ab2a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Modifiche al codice supportate (c# e Visual Basic)
La funzionalità Modifica e continuazione è in grado di gestire la maggior parte dei tipi di modifiche al codice all'interno del corpo del metodo. Tuttavia, non è possibile applicare durante il debug la maggior parte delle modifiche all'esterno del corpo del metodo nonché alcune modifiche all'interno del corpo del metodo. Per applicare tali modifiche non supportate, interrompere il debug e riavviarlo utilizzando una versione aggiornata del codice.

## <a name="supported-changes-to-code"></a>Modifiche supportate al codice

Nella tabella seguente mostra le modifiche che potrebbero essere apportate in c# e Visual Basic (codice) durante una sessione di debug senza riavviare la sessione.

|Elemento/funzionalità del linguaggio|Operazione di modifica supportati|Limitazioni|
|-|-|-|
|Tipi|Aggiungere metodi, campi, costruttori, e altri|[Sì](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iterators|Aggiungere o modificare|No|
|espressioni Async/await|Aggiungere o modificare|[Sì](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Oggetti dinamici|Aggiungere o modificare|No|
|espressioni lambda|Aggiungere o modificare|[Sì](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Espressioni LINQ|Aggiungere o modificare|[Come espressioni lambda](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Funzionalità del linguaggio più recenti, ad esempio interpolazione di stringhe e operatori condizionali null in genere sono supportate in modifica e continuazione. Per informazioni più aggiornate, vedere il [Enc supportato modifica](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) pagina.

## <a name="unsupported-changes-to-code"></a>Modifiche non supportate al codice
 Non è possibile applicare le modifiche seguenti al codice c# e Visual Basic durante una sessione di debug:  
  
-   Modifiche all'istruzione corrente o a qualsiasi altra istruzione attiva.  
  
     Le istruzioni attive includono qualsiasi istruzione, nelle funzioni presenti nello stack di chiamate, che è stata chiamata per ottenere l'istruzione corrente.  
  
     L'istruzione corrente è contrassegnata con uno sfondo giallo nella finestra del codice sorgente. Le altre istruzioni attive sono contrassegnate con uno sfondo ombreggiato e sono di sola lettura. È possano cambiare i colori predefiniti di **opzioni** la finestra di dialogo.

- La tabella seguente illustra le modifiche non supportate al codice dall'elemento di linguaggio.

|Elemento/funzionalità del linguaggio|Operazione di modifica non supportata|
|-|-|
|Tutti gli elementi di codice|Ridenominazione|
|Spazi dei nomi|Aggiunta|
|Spazi dei nomi, tipi, membri|Eliminare|
|Generics|Aggiungere o modificare|
|Interfacce|Modifica|
|Tipi|Aggiungere il membro astratto o virtuale, aggiungere sostituzione (vedere [dettagli](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Tipi|Aggiungere un distruttore|
|Membri|Modificare un membro che fanno riferimento a un tipo di interoperabilità incorporato|
|Membri (Visual Basic)|Modificare un membro con l'istruzione On Error o Resume|
|Membri (Visual Basic)|Modificare un membro che contiene una clausola di query di aggregazione, Group By, Join semplice o gruppo Join LINQ|
|Metodi|Modificare le firme|
|Metodi|Impostare un metodo astratto diventano non astratta tramite l'aggiunta di un corpo del metodo|
|Metodi|Eliminare il corpo (metodo)|
|Attributi|Aggiungere o modificare|
|Proprietà o eventi|Modificare un parametro di tipo, il tipo di base, il tipo delegato o tipo restituito |
|Operatori o gli indicizzatori|Modificare un parametro di tipo, il tipo di base, il tipo delegato o tipo restituito |
|blocchi catch|Modificare quando contiene un'istruzione attiva|
|blocchi try-catch-finally|Modificare quando contiene un'istruzione attiva|
|utilizzo di istruzioni|Aggiunta|
|metodi/espressioni lambda asincrone|Modificare una metodo/espressione lambda asincrona in un progetto destinato a .NET Framework 4 e ridurre (vedere [dettagli](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iterators|Modificare un iteratore in un progetto destinato a .NET Framework 4 e ridurre (vedere [dettagli](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
  
## <a name="unsafe-code"></a>Codice di tipo unsafe  
 Le modifiche a codice non sicuro hanno le stesse limitazioni delle modifiche a codice sicuro, con un'ulteriore restrizione: Modifica e continuazione non supporta modifiche a codice non sicuro all'interno di un metodo che contiene l'operatore `stackalloc`.  

## <a name="unsupported-app-scenarios"></a>Scenari di app non supportato

Piattaforme e applicazioni non supportate includono ASP.NET 5, Silverlight 5 e Windows 8.1.

> [!NOTE]
> App supportate includono UWP in x86 e x64 App destinate a .NET Framework 4.6 e Windows 10 desktop o versioni successive (.NET Framework è solo una versione desktop).
  
## <a name="unsupported-scenarios"></a>Scenari non supportati  
 Modifica e continuazione non è disponibile nei seguenti scenari di debug:  
  
-   Debug in modalità mista (nativo/gestito).  
  
-   Debug SQL.  
  
-   Debug di un dump di Dr. Watson.  
  
-   Debug di un'applicazione di runtime incorporata.  
  
-   Debug di un'applicazione utilizzando Connetti a processo (**Debug > Connetti a processo**) invece di eseguire l'applicazione da **avviare** dal **Debug** menu.  
  
-   Debug di codice ottimizzato.  
  
-   Debug di una versione precedente del codice dopo l'esito negativo della compilazione di una nuova versione a causa di errori di compilazione.
  
## <a name="see-also"></a>Vedere anche  
 [Modifica e continuazione (Visual c#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Procedura: Usare Modifica e continuazione (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)