---
title: Uso di classi Assert | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 01d41202f49a61a1ae2ba0f926b5c5b563ab351c
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="using-the-assert-classes"></a>Utilizzo di classi Assert
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

<xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
[Eseguire unit test del codice](../test/unit-test-your-code.md)
