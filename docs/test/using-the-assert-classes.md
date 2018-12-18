---
title: Uso delle classi Assert per il testing unità in Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ff40f25e9beffa848185fe2c1f95df96928543d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="use-the-assert-classes"></a>Usare le classi Assert

Usare le classi Assert dello spazio dei nomi UnitTestingFramework per verificare funzionalità specifiche. Un metodo di unit test verifica il codice di un metodo nel codice di sviluppo, ma segnala la correttezza del comportamento del codice soltanto se sono state incluse istruzioni Assert.

## <a name="kinds-of-asserts"></a>Tipi di asserzioni
 Lo spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.UnitTesting> rende disponibili diversi tipi di classi Assert:

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

 Nel metodo di test è possibile chiamare qualsiasi numero di metodi della classe Assert, ad esempio Assert.AreEqual(). La classe Assert offre numerosi metodi tra cui scegliere e molti di questi metodi presentano vari overload.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

 Usare la classe CollectionAssert per confrontare raccolte di oggetti e per verificare lo stato di una o più raccolte.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

 Usare la classe StringAssert per confrontare stringhe. Questa classe contiene numerosi metodi utili, ad esempio StringAssert.Contains, StringAssert.Matches e StringAssert.StartsWith.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

 L'eccezione AssertFailedException è generata ogni volta che un test non viene superato. Un test non viene superato se scade a causa di un timeout, genera un'eccezione imprevista o contiene un'istruzione Assert che produce un risultato Non superato.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

 L'eccezione AssertInconclusiveException è generata ogni volta che un test produce un risultato Senza risultati. In genere, un'istruzione Assert.Inconclusive viene aggiunta a un test su cui si sta lavorando per indicare che non è ancora pronto per l'esecuzione.

> [!NOTE]
>  Una strategia alternativa sarebbe contrassegnare un test che non è pronto per l'esecuzione con l'attributo Ignore. Tuttavia, ciò comporta lo svantaggio che non è possibile generare facilmente un report sul numero di test rimasti da implementare.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

 Se si scrive una nuova classe di eccezione Assert, impostare tale classe in modo che erediti dalla classe di base UnitTestAssertException rende più semplice identificare l'eccezione come un errore di asserzione, anziché un'eccezione imprevista generata dal codice di test o di produzione.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

 Decorare un metodo di test con l'attributo ExpectedExceptionAttribute quando si vuole che il metodo di test verifichi che un'eccezione di cui è prevista la generazione da parte di un metodo nel codice di sviluppo sia effettivamente generata nel metodo.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [Eseguire unit test del codice](../test/unit-test-your-code.md)
