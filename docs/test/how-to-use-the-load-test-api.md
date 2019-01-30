---
title: API del test di carico
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- APIs, load tests
ms.assetid: e15567bc-1f21-4feb-b81d-f17ba35cfde5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: fddd81ae64a53943e08457f4ed4a8c19f5d62ab0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970884"
---
# <a name="how-to-use-the-load-test-api"></a>Procedura: Usare l'API del test di carico

Visual Studio supporta plug-in di test di carico che consentono di controllare o migliorare un test di carico. I plug-in dei test di carico sono classi definite dall'utente che implementano l'interfaccia <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> presente nello spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.LoadTesting>. I plug-in dei test di carico consentono il controllo dei test di carico personalizzati, ad esempio per interrompere un test di carico quando viene raggiunta la soglia di un contatore o di un errore. Per ottenere o impostare i parametri del test di carico dal codice definito dall'utente, usare le proprietà nella classe <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest>. Per associare i delegati per le notifiche quando il test di carico è in fase di esecuzione, usare gli eventi nella classe <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest>.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Il visualizzatore oggetti consente di esaminare lo spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.LoadTesting>. Gli editor Visual C# e Visual Basic forniscono il supporto IntelliSense per la codifica delle classi nello spazio dei nomi.

È anche possibile creare plug-in per i test web. Per altre informazioni, vedere [Procedura: Creare un plug-in di test delle prestazioni Web](../test/how-to-create-a-web-performance-test-plug-in.md) e [Procedura: Creare un plug-in a livello di richiesta](../test/how-to-create-a-request-level-plug-in.md).

## <a name="to-use-the-loadtesting-namespace"></a>Per usare lo spazio dei nomi LoadTesting

1.  Aprire un progetto di test di carico e prestazioni Web che contenga un test di carico.

2.  Aggiungere un progetto Libreria di classi Visual C# o Visual Basic alla soluzione di test.

3.  Aggiungere un riferimento al progetto di libreria di classi nel progetto di test di carico e prestazioni Web.

4.  Aggiungere un riferimento alla DLL Microsoft.VisualStudio.QualityTools.LoadTestFramework nel progetto Libreria di classi.

5.  Nel file della classe contenuto nel progetto Libreria di classi aggiungere un'istruzione `using` per lo spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.LoadTesting>.

6.  Creare una classe pubblica che implementi l'interfaccia <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

7.  Compilare il progetto.

8.  Aggiungere il nuovo plug-in di test di carico mediante l'Editor test di carico:

    1.  Fare clic con il pulsante destro del mouse sul nodo radice del test di carico, quindi scegliere **Aggiungi plug-in test di carico**.

    2.  Viene visualizzata la finestra di dialogo **Aggiungi plug-in test di carico**.

    3.  Nel riquadro **Proprietà per il plug-in selezionato** impostare i valori iniziali per il plug-in da usare in fase di esecuzione.

        > [!NOTE]
        > È possibile esporre il numero di proprietà desiderato dai plug-in. È sufficiente renderle pubbliche, impostabili e di un tipo di base, ad esempio Integer, Boolean o String. È anche possibile modificare le proprietà del plug-in di test di carico in un secondo tempo usando la finestra **Proprietà**.

9. Eseguire il test di carico.

     Per l'implementazione di <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>, vedere [Procedura: Creare un plug-in test di carico](../test/how-to-create-a-load-test-plug-in.md).

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Creare codice personalizzato e plug-in per test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Procedura: Usare l'API del test prestazioni Web](../test/how-to-use-the-web-performance-test-api.md)
- [Procedura: Creare un plug-in test di carico](../test/how-to-create-a-load-test-plug-in.md)