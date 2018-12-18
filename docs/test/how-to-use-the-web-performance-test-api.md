---
title: API del test prestazioni Web in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: ed7cbc7375cbf416d82a56c140479925569dad8d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-the-web-performance-test-api"></a>Procedura: utilizzare l'API del test delle prestazioni Web

È possibile scrivere codice per i test Web. L'API del test Web viene utilizzata per creare test Web codificati, plug-in test Web, plug-in richiesta, richieste, regole di estrazione e regole di convalida. Le classi che compongono queste tipologie sono le classi di base in questa API. Gli altri tipi in questa API vengono utilizzati per supportare la creazione degli oggetti <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> e <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>. Lo spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.WebTesting> consente di creare test Web personalizzati.

 È anche possibile utilizzare l'API del test Web per creare e salvare test Web dichiarativi a livello di codice. A tale scopo, utilizzare le classi <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> e <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer>.

> [!TIP]
>  Il visualizzatore oggetti consente di esaminare lo spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.WebTesting>. Gli editor Visual C# e Visual Basic forniscono il supporto IntelliSense per la codifica delle classi nello spazio dei nomi.

 È possibile creare anche plug-in per i test di carico. Per altre informazioni, vedere [Procedura: Usare l'API del test di carico](../test/how-to-use-the-load-test-api.md) e [Procedura: Creare un plug-in test di carico](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>Per utilizzare lo spazio dei nomi WebTesting

1.  Aprire un progetto di test di carico e prestazioni Web che contenga un test delle prestazioni Web.

2.  Aggiungere un progetto Libreria di classi Visual C# o Visual Basic alla soluzione di test.

3.  Aggiungere un riferimento al progetto di libreria di classi nel progetto di test di carico e prestazioni Web.

4.  Aggiungere un riferimento alla DLL Microsoft.VisualStudio.QualityTools.WebTestFramework nel progetto di libreria di classi.

5.  Nel file della classe contenuto nel progetto Libreria di classi aggiungere un'istruzione `using` per lo spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.WebTesting>.

6.  Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

7.  Compilare il progetto.

8.  Aggiungere un nuovo plug-in del test delle prestazioni Web utilizzando l'Editor test prestazioni Web.

    1.  Scegliere **Aggiungi plug-in test Web** nella barra degli strumenti.

         Viene visualizzata la finestra di dialogo **Aggiungi plug-in test Web**.

    2.  In **Seleziona un plug-in** selezionare la classe del plug-in del test prestazioni Web.

    3.  Nel riquadro **Proprietà per il plug-in selezionato** impostare i valori iniziali per il plug-in da usare in fase di esecuzione.

        > [!NOTE]
        > È possibile esporre il numero di proprietà desiderato dai plug-in; è sufficiente renderle pubbliche, impostabili e di un tipo di base quale Integer, Boolean o String. È anche possibile modificare le proprietà del plug-in di test delle prestazioni Web in un secondo momento utilizzando la finestra Proprietà.

    4.  Scegliere **OK**.

9. Eseguire il test Web.

     Per un esempio di implementazione di <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, vedere [Procedura: Creare un plug-in di test prestazioni Web](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Creare codice personalizzato e plug-in per test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Procedura: Usare l'API del test di carico](../test/how-to-use-the-load-test-api.md)
- [Procedura: Creare un plug-in di test prestazioni Web](../test/how-to-create-a-web-performance-test-plug-in.md)