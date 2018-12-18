---
title: Live Unit Testing in Visual Studio | Microsoft Docs
ms.date: 2017-03-07
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload: dotnet
ms.openlocfilehash: 725b9e31e725106dcd9e461a8f5d3749230fd5c9
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="live-unit-testing-with-visual-studio-2017"></a>Live Unit Testing con Visual Studio 2017

Mentre si sviluppa un'applicazione, Live Unit Testing esegue automaticamente tutti gli unit test interessati in background, visualizzando in tempo reale i risultati e il code coverage nell'IDE di Visual Studio. Durante la modifica del codice, Live Unit Testing fornisce commenti e suggerimenti sull'impatto delle modifiche sui test esistenti e indica se il nuovo codice aggiunto è coperto da uno o più test esistenti. In questo modo si riceverà un promemoria relativo alla scrittura di unit test durante la correzione di bug o l'aggiunta di nuove funzionalità.

> [!NOTE]
> Live Unit Testing è disponibile per progetti C# e Visual Basic destinati a .NET Core o .NET Framework in Visual Studio 2017 Enterprise Edition.

Quando si usa Live Unit Testing per i test, Live Unit Testing salva in modo permanente i dati sullo stato dei test. La possibilità di usare i dati salvati in modo permanente consente a Live Unit Testing di offrire prestazioni superiori, eseguendo al tempo stesso i test in modo dinamico in risposta alle modifiche del codice.
 
## <a name="supported-test-frameworks"></a>Framework di test supportati
Live Unit Testing è compatibile con i tre framework di unit test elencati nella tabella seguente. Nella tabella è indicata anche la versione minima supportata degli adattatori e dei framework. I framework di unit test sono tutti disponibili su NuGet.org.
 
<table> 
<tr>
   <th>Framework di test</th>
   <th>Versione minima dell'adattatore di Visual Studio</th>
   <th>Versione minima del framework</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio versione 2.2.0-beta3-build1187</td>
   <td>xunit 1.9.2</td> 
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter versione 3.5.1</td>  
   <td>NUnit versione 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>MSTest.TestFramework 1.0.5-preview</td>
</tr>
</table>

Se si hanno progetti basati su MSTest meno recenti che fanno riferimento a `Microsoft.VisualStudio.QualityTools.UnitTestFramework` e non si vuole passare ai pacchetti NuGet MSTest più recenti, eseguire l'aggiornamento a Visual Studio 2017 versione 15.4. 

In alcuni casi, per consentire il funzionamento di Live Unit Testing, potrebbe essere necessario ripristinare in modo esplicito i pacchetti NuGet a cui viene fatto riferimento nei progetti della soluzione. Per eseguire questa operazione, compilare in modo esplicito la soluzione (selezionare **Compila**, **Ricompila soluzione** dal menu di primo livello di Visual Studio) oppure ripristinare i pacchetti nella soluzione (fare clic con il pulsante destro del mouse sulla soluzione e scegliere **Ripristina pacchetti NuGet**) prima di abilitare Living Unit Testing. 

#   <a name="configuring-live-unit-testing"></a>Configurazione di Live Unit Testing

Per configurare Live Unit Testing, selezionare **Strumenti**, **Opzioni** dal menu di primo livello di Visual Studio e quindi scegliere **Live Unit Testing** nel riquadro di sinistra della finestra di dialogo **Opzioni**. La figura seguente illustra le opzioni di configurazione di Live Unit Testing disponibili nella finestra di dialogo.

  ![Image](./media/lut-options.png)

Le opzioni configurabili includono:

- Sospensione dell'esecuzione di Live Unit Testing in caso di compilazione e debug di una soluzione.
 
- Sospensione dell'esecuzione di Live Unit Testing quando l'alimentazione a batteria del sistema scende sotto una soglia specificata.
- Esecuzione automatica di Live Unit Testing all'apertura di una soluzione.
- Directory in cui archiviare i dati salvati in modo permanente.   
   Il pulsante **Delete Persisted Data** (Elimina i dati salvati in modo permanente) consente di eliminare tutti i dati salvati in modo permanente. Questa opzione risulta utile quando Live Unit Testing si comporta in modo imprevedibile o imprevisto, suggerendo il danneggiamento dei dati salvati in modo permanente.   
- Intervallo dopo il quale si verifica il timeout di un test case; il valore predefinito è 30 secondi. 
- Numero massimo di processi di test creati da Live Unit Testing. 
- Quantità massima di memoria che i processi di Live Unit Testing possono utilizzare.
- Livello delle informazioni scritte nella finestra **Output** di Live Unit Testing.   
   È possibile scegliere di non visualizzare informazioni di log (**Nessuno**), solo i messaggi errore (**Errore**), messaggi di errore e messaggi informativi (**Informazioni**, che corrisponde al valore predefinito) o tutti i dettagli (**Dettagliato**).

Per visualizzare l'output dettagliato nella finestra **Output** di Live Unit Testing, è anche possibile assegnare il valore "1" a una variabile di ambiente a livello di utente denominata `VS_UTE_DIAGNOSTICS` e riavviare Visual Studio. 

Per acquisire in un file i messaggi di log dettagliati di MSBuild restituiti da Live Unit Testing, impostare la variabile di ambiente a livello di utente `LiveUnitTesting_BuildLog` sul nome del file in cui salvare il log.

Dopo l'abilitazione di Live Unit Testing (vedere la sezione successiva, [Avvio, sospensione e arresto di Live Unit Testing](#starting-pausing-and-stopping-live-unit-testing), è possibile aprire la finestra di dialogo **Opzioni** anche selezionando **Test**, **Live Unit Testing**, **Opzioni**.

## <a name="starting-pausing-and-stopping-live-unit-testing"></a>Avvio, sospensione e arresto di Live Unit Testing

Per abilitare Live Unit Testing, selezionare **Test**, **Live Unit Testing**, **Avvia** dal menu di primo livello di Visual Studio. Dopo l'abilitazione, le opzioni disponibili nel menu di **Live Unit Testing** cambiano e passano da una voce, ovvero **Avvia**, a tre, ovvero **Sospendi**, **Arresta** e **Reset Clean** (Reimposta e pulisci).

> [!NOTE]
> Se si avvia Live Unit Testing in una soluzione che non include un progetto di unit test, le opzioni **Pausa**, **Interrompi**, e **Reset Clean** (Reimposta e pulisci) vengono visualizzate nel menu **Live Unit Testing**, ma Live Unit Testing non viene avviato. Nella finestra **Output** viene visualizzato un messaggio che inizia con "No supported test adapters are referenced by this solution..." (La soluzione non fa riferimento ad alcun adattatore di test supportato).  

È possibile sospendere temporaneamente o arrestare completamente Live Unit Testing in qualsiasi momento. È opportuno scegliere una di queste opzioni se, ad esempio, è in corso un'operazione di refactoring e si sa che i test verranno interrotti per un certo periodo di tempo. Le tre opzioni di menu sono:

- **Sospendi**, che sospende temporaneamente l'esecuzione di Live Unit Testing. 
 
    Quando l'esecuzione di Live Unit Testing è sospesa, la visualizzazione del code coverage non è presente nell'editor, ma tutti i dati raccolti vengono mantenuti. Per riprendere l'esecuzione di Live Unit Testing, selezionare **Continua** dal menu di Live Unit Testing. Live Unit Testing esegue le operazioni necessarie per intercettare tutte le modifiche apportate da quando è stata sospesa l'esecuzione e aggiorna i glifi di conseguenza. 

- **Arresta**, che consente di arrestare completamente l'esecuzione di Live Unit Testing. Con questa opzione tutti i dati raccolti vengono rimossi.

- **Reset Clean** (Reimposta e pulisci), che interrompe l'esecuzione di Live Unit Testing, elimina i dati salvati in modo permanente e riavvia Live Unit Testing.

- **Opzioni**, che visualizza la finestra di dialogo **Opzioni** illustrata nella sezione[Configurazione di Live Unit Testing](#configuring-live-unit-testing).
 
##  <a name="viewing-coverage-visualization-in-the-editor-as-you-type"></a>Accesso alla visualizzazione del code coverage nell'editor durante la digitazione

Dopo l'abilitazione, Live Unit Testing aggiorna le singole righe di codice nell'editor di Visual Studio in modo da indicare se il codice scritto è coperto da unit test e se i test coperti vengono superati.  La figura seguente mostra le righe di codice con test superati e non superati, nonché le righe di codice non coperte dai test. Le righe contraddistinte da un segno di spunta "✓" verde sono coperte solo da test superati, quelle contraddistinte da una "x" rossa sono coperte da uno o più test non superati, mentre quelle contraddistinte da un simbolo "➖" blu non sono coperte da alcun test.

  ![Image](./media/lut-codewindow.png)

La visualizzazione del code coverage di Live Unit Testing viene aggiornata immediatamente quando si modifica il codice nell'editor del codice. Durante l'elaborazione delle modifiche, la visualizzazione cambia per indicare che i dati non sono aggiornati e viene aggiunta l'immagine di un timer rotondo sotto i test superati, non superati e non coperti, come illustrato nella figura seguente.

  ![Image](./media/lut-codeupdating.png)
 
## <a name="getting-information-on-successful-or-failed-tests"></a>Recupero delle informazioni su test superati o non superati

Per visualizzare il numero di test eseguiti su una certa riga, è possibile passare il puntatore sul simbolo di test superato o non superato nella finestra del codice. Se si fa clic sul simbolo, verrà visualizzato lo stato dei singoli test, come illustrato nella figura seguente:
 
  ![Image](./media/lut-failedinfo.png) 

Oltre a fornire i nomi e i risultati dei test, la descrizione comando consente di eseguire di nuovo il set di test, oltre a eseguire il set di test usando il debugger. Se si selezionano uno o più test nella descrizione comando, è anche possibile eseguire o sottoporre a debug solo tali test. Ciò consente di eseguire il debug dei test senza uscire dalla finestra del codice. Durante il debug, oltre a osservare eventuali punti di interruzione già configurati, l'esecuzione del programma viene sospesa quando il debugger esegue un metodo [`Assert`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert) che restituisce un risultato imprevisto. 

Quando si passa il puntatore su un test non superato nella descrizione comando, questa si espande e visualizza informazioni aggiuntive sull'errore, come illustrato nell'immagine seguente. Fare doppio clic sul test non superato nella descrizione comando per visualizzarlo.

  ![Image](./media/lut-failedmsg.png) 

Quando si passa al test non riuscito, Live Unit Testing indica anche visivamente nella firma del metodo i test con esito positivo (indicati da un becher mezzo pieno con un simbolo "✓" verde), i test con esito negativo (indicati da un becher mezzo pieno con un simbolo "🞩" rosso) o i test non interessati da Live Unit Testing (indicati da un becher mezzo pieno con un simbolo "➖" blu). I metodi non di test non sono decorati con simboli. La figura seguente illustra tutti e quattro i tipi di metodi.
 
  ![Image](media/lut-testsource.png)
 
## <a name="diagnosing-and-correcting-test-failures"></a>Diagnosi e correzione degli errori di test

A partire dal test non superato è possibile eseguire facilmente il debug nel codice del prodotto, apportare modifiche e continuare a sviluppare l'applicazione. Poiché Live Unit Testing viene eseguito in background, non è necessario arrestare e riavviare Live Unit Testing durante il ciclo di debug, modifica e continuazione.

L'errore di test illustrato nella figura precedente, ad esempio, è stato causato da un presupposto non corretto presente nel metodo di test in base al quale i caratteri non alfabetici restituiscono `true` quando vengono passati al metodo <xref:System.Char.IsLower%2A?displayProperty=fullName>. Dopo aver corretto il metodo di test, tutti i test vengono superati. Mentre si esegue questa operazione, non è necessario sospendere o arrestare l'esecuzione di Live Unit Testing.

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing ed Esplora test

**Esplora test** offre in genere l'interfaccia che consente di avviare, eseguire il debug e analizzare i risultati del test. Live Unit Testing si integra con **Esplora test**. Quando Live Unit Testing non è abilitato o è stato arrestato, **Esplora Test** visualizza lo stato degli unit test durante l'ultima esecuzione di un test. Se si apportano modifiche al codice sorgente, è necessario eseguire di nuovo i test. Quando invece è abilitato Live Unit Testing, lo stato degli unit test in **Esplora test** viene aggiornato immediatamente. Non è quindi più necessario eseguire gli unit test in modo esplicito. 

> [!NOTE]
> È possibile aprire **Esplora test** selezionando **Test**, **Windows**, **Esplora Test** dal menu di primo livello di Visual Studio.  

Come si può notare, nella finestra **Esplora test** alcuni test sono visualizzati in modo attenuato. Ad esempio, quando si abilita Live Unit Testing dopo l'apertura di un progetto salvato in precedenza, la finestra **Esplora test** mostra come attenuati tutti i test tranne quello con esito negativo, come illustrato nella figura seguente. In questo caso, Live Unit Testing ha ripetuto l'esecuzione del test con esito negativo, ma non ha ripetuto l'esecuzione dei test con esito positivo, perché i dati salvati in modo permanente di Live Unit Testing indicano che non sono state apportate modifiche dopo l'ultima esecuzione con esito positivo dei test.

  ![Image](media/lut-test-explorer.png)

È possibile ripetere l'esecuzione di eventuali test visualizzati in modo attenuato selezionando le opzioni **Esegui tutto** o **Esegui** dal menu **Esplora test** oppure selezionando uno o più test nel menu **Esplora test**, facendo clic con il pulsante destro del mouse e quindi scegliendo **Esegui test selezionati** o **Esegui debug test selezionati** dal menu di scelta rapida. Quando i test vengono eseguiti, vengono visualizzati nella parte superiore.

Esistono alcune differenze tra l'esecuzione automatica di Live Unit Testing e l'aggiornamento dei risultati dei test e l'esecuzione esplicita di test da **Esplora test**. Ecco alcune di queste differenze:

- Durante l'esecuzione o il debug di test dalla finestra Esplora test vengono eseguiti file binari normali, mentre con Live Unit Testing vengono eseguiti file instrumentati. 
- Live Unit Testing non crea un nuovo dominio applicazione per eseguire i test, ma esegue i test dal dominio predefinito. Quando i test vengono eseguiti dalla finestra **Esplora test**, viene invece creato un nuovo dominio applicazione.
- Live Unit Testing esegue i test di ogni assembly di test in modo sequenziale. Se si eseguono più test dalla finestra **Esplora test** e il pulsante **Esegui test in parallelo** è selezionato, i test vengono eseguiti in parallelo.

## <a name="live-unit-testing-and-large-solutions"></a>Live Unit Testing e soluzioni di grandi dimensioni

Se la soluzione include 10 o più progetti, quando si avvia Live Unit Testing e non sono presenti dati permanenti oppure quando si seleziona l'opzione **Test**, **Live Unit Testing**, **Reset Clean** (Reimposta e pulisci) dal menu di primo livello di Visual Studio, Visual Studio visualizza la finestra di dialogo seguente per informare l'utente che l'esecuzione dinamica di un numero elevato di test in progetti di grandi dimensioni può influire negativamente sulle prestazioni. Se si seleziona **OK**, Live Unit Testing esegue tutti i test della soluzione. Se si seleziona **Annulla**, è possibile selezionare i test da eseguire. Per informazioni su come eseguire questa operazione, vedere la sezione seguente: [Inclusione ed esclusione di progetti e metodi di test](#including-and-excluding-test-projects-and-test-methods).  

 ![Finestra di dialogo di Live Unit Testing per progetti di grandi dimensioni](media/lut-large-project.png)

## <a name="including-and-excluding-test-projects-and-test-methods"></a>Inclusione ed esclusione di progetti e metodi di test

Per le soluzioni che contengono molti progetti di test, è possibile controllare i progetti e i singoli metodi di un progetto inclusi in Live Unit Testing. Se ad esempio una soluzione contiene centinaia di progetti di test, è possibile selezionare un set specifico di progetti di test da includere in Live Unit Testing. È possibile eseguire questa operazione in molti modi, in base alla necessità di escludere tutti i test nel progetto o nella soluzione, di includere o escludere la maggior parte dei test o di escludere i test singolarmente. In Live Unit Testing lo stato di inclusione/esclusione viene salvato come impostazione utente e memorizzato alla chiusura o alla riapertura di una soluzione. 

**Esclusione di tutti i test in un progetto o in una soluzione**

Per selezionare i singoli progetti negli unit test, eseguire le operazioni seguenti dopo aver avviato Live Unit Testing:

1.  Fare clic con il pulsante destro del mouse sulla soluzione in Esplora soluzioni e scegliere **Test attivi**, **Escludi** per escludere l'intera soluzione.
1.  Fare clic con il pulsante destro del mouse su ogni progetto di test da includere nei test e scegliere **Test attivi**, **Includi**.

**Esclusione di singoli test dalla finestra dell'editor del codice**

Per includere o escludere singoli metodi di test, è possibile usare la finestra dell'editor del codice. Fare clic con il pulsante destro del mouse sulla firma del primo metodo di test nella finestra dell'editor del codice, quindi scegliere **Live Tests** (Test live), **Include [the selected method]** (Includi [metodo selezionato]), **Live Tests** (Test live), **Exclude [the selected method]** (Escludi [metodo selezionato]) o **Live Tests** (Test live), **Exclude All But [the selected method]** (Escludi tutto tranne [metodo selezionato]), dove "metodo selezionato" è il nome del metodo selezionato nella finestra del codice. 

**Esclusione dei test a livello di codice** 

È possibile applicare l'attributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> per evitare a livello di codice che metodi, classi o strutture restituiscano informazioni sul code coverage in Live Unit Testing.

Puoi anche usare gli attributi seguenti per escludere singoli metodi da Live Unit Testing:

- Per xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Per NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Per MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]` 
 
## <a name="see-also"></a>Vedere anche

[Strumenti di test del codice](https://www.visualstudio.com/vs/testing-tools/)   
[Live Unit Testing Blog](https://go.microsoft.com/fwlink/?linkid=842514)  (Blog di Live Unit Testing)  
[Domande frequenti su Live Unit Testing](live-unit-testing-faq.md)    
[Channel 9 Video: Live Unit Testing in Visual Studio 2017](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105) (Video di Channel 9: Live Unit Testing in Visual Studio 2017)

