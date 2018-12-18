---
title: Operatori logici e avanzati nelle espressioni di ricerca | Microsoft Docs
ms.custom: ''
ms.date: 11/02/2017
ms.technology:
- vs-help-viewer
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 952aea626dd59a303fd7091a4d36fdbf512db6bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>Operatori logici e avanzati nelle espressioni di ricerca
È possibile usare gli operatori logici e gli operatori di ricerca avanzati per perfezionare la ricerca del contenuto della Guida in Help Viewer.

## <a name="logical-operators"></a>Operatori logici
Gli operatori logici specificano in che modo più termini di ricerca debbano essere combinati in una query di ricerca. La tabella seguente illustra gli operatori logici AND, OR, NOT e NEAR.
  
|Per cercare|Usa|Esempio|Risultato|  
|-------------------|---------|-------------|------------|  
|Entrambi i termini nello stesso articolo|AND|DIB AND tavolozza|Argomenti che contengono sia "DIB" che "tavolozza".|  
|Uno dei termini in un articolo|OR|raster OR vettore|Argomenti che contengono "raster" o "vettore".|  
|Primo termine senza il secondo nello stesso articolo|NOT|"sistema operativo" NOT DOS|Argomenti che contengono "sistema operativo" ma non "DOS".|  
|Entrambi i termini, vicini in un articolo|VICINO|utente NEAR kernel|Gli argomenti che contengono "utente" in prossimità di "kernel".|  
  
> [!IMPORTANT]
> Per essere riconosciuti dal motore di ricerca, gli operatori logici devono essere immessi interamente in lettere maiuscole.

## <a name="advanced-operators"></a>Operatori avanzati
Gli operatori di ricerca avanzati consentono di affinare la ricerca di contenuto specificando l'area di un articolo in cui cercare il termine. La tabella seguente descrive i quattro operatori di ricerca avanzata disponibili.

|Per cercare|Usa|Esempio|Risultato|  
|-------------------|---------|-------------|------------|  
|Un termine nel titolo dell'articolo|title:|title:binaryreader|Argomenti che contengono "binaryreader" nei titoli.|  
|Un termine in un esempio di codice|code:|code:readdouble|Argomenti che contengono "readdouble" in un esempio di codice.|  
|Un termine in un 'esempio di un linguaggio di programmazione specifico|code:vb:|code:vb:string|Argomenti che contengono "string" in un esempio di codice di Visual Basic.|  
|Un articolo associato a una parola chiave di indice specifica|keyword:|keyword:readbyte|Argomenti associati alla parola chiave di indice "readbyte".|  

> [!IMPORTANT]
> È necessario immettere gli operatori di ricerca avanzati seguiti da due punti senza spazio affinché il motore di ricerca li possa riconoscere.    

### <a name="programming-languages-for-code-examples"></a>Linguaggi di programmazione per esempi di codice
È possibile usare l'operatore **code:** per trovare contenuti relativi a uno dei diversi linguaggi di programmazione. Per restituire gli esempi per un linguaggio di programmazione specifico, usare uno dei valori di linguaggio di programmazione seguenti:  

|Linguaggio di programmazione|Sintassi dell'operatore di ricerca|  
|--------------------|---------|  
|Visual Basic|code:vb<br/>code:visualbasic|  
|C#|code:c#<br/>code:csharp|  
|C++|code:cpp<br/>code:c++<br/>code:cplusplus|  
|F#|code:f#<br/>code:fsharp|  
|JavaScript|code:javascript<br/>code:js|  
|XAML|: xaml|

> [!NOTE]
> L'operatore **code:** trova solo il contenuto contrassegnato con un'etichetta di linguaggio di programmazione, anziché il contenuto contrassegnato in modo generico come codice. 
  
## <a name="see"></a>Vedere 
[Procedura: Eseguire la ricerca di argomenti](how-to-search-for-topics.md)  
[Microsoft Help Viewer](microsoft-help-viewer.md)