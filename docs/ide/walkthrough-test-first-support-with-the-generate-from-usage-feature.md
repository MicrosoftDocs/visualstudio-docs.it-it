---
title: "Procedura dettagliata: Sviluppo di test preventivi con la funzionalità di generazione dall'utilizzo | Microsoft Docs"
ms.custom: ''
ms.date: 10/09/2017
ms.technology: vs-ide-general
dev_langs:
- VB
- CSharp
ms.topic: conceptual
helpviewer_keywords:
- Generate From Usage
- Test-First Development
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8bf7a4a4f78ca0de8594a95681c6a5118f1083cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>Procedura dettagliata: Sviluppo di test preventivi con la funzionalità di generazione dall'utilizzo

Questo argomento illustra come usare la funzionalità di [generazione dall'utilizzo](../ide/visual-csharp-intellisense.md#generate-from-usage), che supporta lo sviluppo di test preventivi.  
  
 Lo*sviluppo di test preventivi* è un approccio alla progettazione software in cui prima si scrivono unit test in base alle specifiche del prodotto e quindi si scrive il codice sorgente necessario per fare in modo che i test abbiano esito positivo. Visual Studio supporta lo sviluppo di test preventivi grazie alla generazione di nuovi tipi e membri nel codice sorgente quando si fa riferimento a essi per la prima volta nei test case, prima che vengano definiti.  
  
 Visual Studio genera i nuovi tipi e membri con un'interruzione minima del flusso di lavoro. È possibile creare stub per tipi, metodi, proprietà, campi o costruttori senza abbandonare la posizione corrente nel codice. Quando si apre una finestra di dialogo per specificare le opzioni per la generazione dei tipi, lo stato attivo torna immediatamente al file aperto corrente quando si chiude la finestra di dialogo.  
  
 La funzionalità di generazione dall'utilizzo può essere usata con framework di test che si integrano con Visual Studio. In questo argomento viene illustrato il framework di unit test Microsoft.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-windows-class-library-project-and-a-test-project"></a>Per creare un progetto di libreria di classi Windows e un progetto di test  
  
1.  In [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] creare un nuovo progetto di **libreria di classi Windows**. Assegnare al progetto il nome `GFUDemo_VB` o `GFUDemo_CS`, a seconda del linguaggio in uso.  
  
2.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sull'icona della soluzione nella parte superiore, scegliere **Aggiungi** e selezionare **Nuovo progetto**. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** scegliere **Test**.  
  
3.  Nel riquadro centrale scegliere **Progetto unit test** e accettare il nome predefinito UnitTestProject1. La figura seguente mostra la finestra di dialogo quando viene visualizzata in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. In [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] l'aspetto della finestra di dialogo è simile.  
  
     ![Finestra di dialogo Nuovo progetto di test](../ide/media/newproject_test.png "NewProject_Test")  
  
4.  Scegliere **OK** per chiudere la finestra di dialogo **Nuovo progetto**.  

### <a name="to-add-a-reference-to-the-class-library-project"></a>Per aggiungere un riferimento al progetto di libreria di classi

1.  Nel progetto di unit test in **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla voce **Riferimenti** e scegliere **Aggiungi riferimento**.

2.  Nella finestra di dialogo **Gestione riferimenti** selezionare **Progetti** e scegliere un progetto di libreria di classi.

3.  Scegliere **OK** per chiudere la finestra di dialogo **Gestione riferimenti**.  
    
4.  Salvare la soluzione. A questo punto, è possibile iniziare a scrivere test.  
  
### <a name="to-generate-a-new-class-from-a-unit-test"></a>Per generare una nuova classe da uno unit test  
  
1.  Il progetto di test contiene un file denominato UnitTest1. Fare doppio clic su questo file in **Esplora soluzioni** per aprirlo nell'editor del codice. Vengono generati una classe di test e un metodo di test.  
  
2.  Individuare la dichiarazione della classe `UnitTest1` e rinominarla in `AutomobileTest`.  
  
 > [!NOTE]
 >  IntelliSense offre ora due alternative per il completamento delle istruzioni IntelliSense: la *modalità di terminazione* e la *modalità con suggerimenti*. Usare la modalità con suggerimenti per i casi in cui classi e membri vengono usati prima di essere definiti. Quando una finestra di IntelliSense è aperta, è possibile premere **CTRL+ALT+BARRA SPAZIATRICE** per passare dalla modalità di terminazione alla modalità con suggerimenti, e viceversa. Per altre informazioni, vedere [Using IntelliSense](../ide/using-intellisense.md) . La modalità con suggerimenti sarà utile quando si digita `Automobile` nel passaggio successivo.  
  
3.  Individuare il metodo `TestMethod1()` e rinominarlo in `DefaultAutomobileIsInitializedCorrectly()`. All'interno di questo metodo creare una nuova istanza di una classe denominata `Automobile`, come illustrato negli screenshot seguenti. Vengono visualizzate una sottolineatura ondulata che indica un errore in fase di compilazione e una lampadina [Azioni rapide](../ide/quick-actions.md) a sinistra (solo C#) o direttamente sotto la sottolineatura a zigzag se si passa il puntatore del mouse sopra.  
  
     ![Azioni rapide in Visual Basic](../ide/media/genclass_underlinevb.png "GenClass_UnderlineVB")  

     ![Azioni rapide in C&#35;](../ide/media/genclass_underline.png "GenClass_Underline")  
  
4.  Scegliere o fare clic sulla lampadina Azioni rapide. Verrà visualizzato un messaggio di errore a indicare che il tipo `Automobile` non è definito. Vengono anche proposte alcune soluzioni.  
  
5. Fare clic su **Genera nuovo tipo...** per aprire la finestra di dialogo **Genera tipo**. Questa finestra di dialogo contiene alcune opzioni, tra cui la possibilità di generare il tipo in un progetto diverso.  

6. Nell'elenco **Progetto** fare clic su **GFUDemo\_VB** o **GFUDemo_CS** per indicare a Visual Studio di aggiungere il file al progetto di libreria di classi invece che al progetto di test. Se non è già selezionata, scegliere l'opzione **Crea nuovo file** e denominare il file **Automobile.cs** o **Automobile.vb**.  
  
     ![Finestra di dialogo Genera nuovo tipo](../ide/media/genotherdialog.png "GenOtherDialog")  
  
6.  Fare clic su **OK** per chiudere la finestra di dialogo e creare il nuovo file.  
  
7.  In **Esplora soluzioni**esaminare sotto il nodo di progetto GFUDemo_VB o GFUDemo_CS per verificare che sia presente il nuovo file Automobile.vb o Automobile.cs. Nell'editor del codice lo stato attivo è ancora in `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`. È quindi possibile continuare a scrivere il test con un'interruzione minima.  
  
### <a name="to-generate-a-property-stub"></a>Per generare uno stub per una proprietà  
Si supponga che la specifica del prodotto indichi che la classe `Automobile` ha due proprietà pubbliche denominate `Model` e `TopSpeed`. Queste proprietà devono essere inizializzate con i valori predefiniti `"Not specified"` e `-1` dal costruttore predefinito. Lo unit test seguente verificherà che il costruttore predefinito imposti le proprietà sui valori predefiniti corretti.  
  
1. Aggiungere la riga di codice seguente al metodo di test di `DefaultAutomobileIsInitializedCorrectly`.  
  
     [!code-csharp[VbTDDWalkthrough#1](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.cs)]
     [!code-vb[VbTDDWalkthrough#1](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.vb)]  
  
2. Poiché il codice fa riferimento a due proprietà non definite in `Automobile`, viene visualizzata una sottolineatura ondulata sotto `Model` e `TopSpeed`. Passare il puntatore del mouse su `Model`, scegliere la lampadina Azioni rapide e poi l'opzione **Genera proprietà 'Automobile.Model'**.  

3. Generare uno stub per la proprietà `TopSpeed` nello stesso modo.  
  
     Nella classe `Automobile` i tipi delle nuove proprietà vengono dedotti correttamente dal contesto.  
  
### <a name="to-generate-a-stub-for-a-new-constructor"></a>Per generare uno stub per un nuovo costruttore  
A questo punto viene creato un metodo di test che genererà uno stub per il costruttore per inizializzare le proprietà `Model` e `TopSpeed`. Successivamente, verrà aggiunto altro codice per completare il test.  

1. Aggiungere l'ulteriore metodo di test seguente alla classe `AutomobileTest` .  
  
     [!code-csharp[VbTDDWalkthrough#2](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.cs)]
     [!code-vb[VbTDDWalkthrough#2](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.vb)]  
  
2.  Fare clic sulla lampadina Azioni rapide sotto la sottolineatura rossa a zigzag e selezionare **Genera costruttore in 'Automobile'**.  

     Nel file della classe `Automobile` osservare che il nuovo costruttore ha esaminato i nomi delle variabili locali che vengono usati nella chiamata al costruttore, ha trovato le proprietà che hanno gli stessi nomi nella classe `Automobile` e ha fornito il codice nel corpo del costruttore per archiviare i valori degli argomenti nelle proprietà `Model` e `TopSpeed` .
  

3.  Dopo aver generato il nuovo costruttore, viene visualizzata una sottolineatura ondulata sotto la chiamata al costruttore predefinito in `DefaultAutomobileIsInitializedCorrectly`. Il messaggio di errore indica che la classe `Automobile` non ha un costruttore che accetta zero argomenti. Per generare un costruttore predefinito esplicito che non ha parametri, fare clic sulla lampadina Azioni rapide e fare clic su **Genera costruttore in 'Automobile'**.  
  
### <a name="to-generate-a-stub-for-a-method"></a>Per generare uno stub per un metodo  
Si supponga che la specifica indichi che un nuovo oggetto `Automobile` può essere impostato in uno stato di esecuzione se le sue proprietà `Model` e `TopSpeed` sono impostate su valori diversi da quelli predefiniti.  

1. Aggiungere le righe seguenti al metodo `AutomobileWithModelNameCanStart` .
  
     [!code-csharp[VbTDDWalkthrough#3](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.cs)]
     [!code-vb[VbTDDWalkthrough#3](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.vb)]  
  
2.  Fare clic sulla lampadina Azioni rapide per la chiamata al metodo `myAuto.Start` e quindi su **Genera metodo 'Automobile.Start'**.  
  
3.  Fare clic sulla lampadina Azioni rapide per la proprietà `IsRunning` e quindi su **Genera proprietà 'Automobile.IsRunning'**.  

     La classe `Automobile` ora contiene un metodo denominato `Start()` e una proprietà denominata `IsRunning`.  
  
### <a name="to-run-the-tests"></a>Per eseguire i test  
  
1.  Scegliere **Esegui**, **Tutti i test** dal menu **Test**.  

     Il comando **Esegui**, **Tutti i test** esegue tutti i test in tutti i framework di test scritti per la soluzione corrente. In questo caso ci sono due test e hanno entrambi esito negativo, come previsto. Il test `DefaultAutomobileIsInitializedCorrectly` ha esito negativo perché la condizione `Assert.IsTrue` restituisce `False`. Il test `AutomobileWithModelNameCanStart` ha esito negativo perché il metodo `Start` nella classe `Automobile` genera un'eccezione.  
  
     La finestra **Risultati test** è illustrata nella figura seguente.  
  
     ![Risultati dei test non riusciti](../ide/media/testsfailed.png "TestsFailed")  
  
2.  Nella finestra **Risultati del test** fare doppio clic su ogni riga dei risultati del test per passare alla posizione di ogni test.  
  
### <a name="to-implement-the-source-code"></a>Per implementare il codice sorgente  
  
1.  Aggiungere il codice seguente al costruttore predefinito in modo che le proprietà `Model`, `TopSpeed` e `IsRunning` vengano tutte inizializzate con i valori predefiniti corretti, ovvero `"Not specified"`, `-1`e `False` (o `false` per C#).  
  
     [!code-csharp[VbTDDWalkthrough#5](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.cs)]
     [!code-vb[VbTDDWalkthrough#5](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.vb)]  
  
2.  Quando il metodo `Start` viene chiamato, deve impostare il flag `IsRunning` su true solo se la proprietà `Model` o `TopSpeed` è impostata su un valore diverso da quello predefinito. Rimuovere `NotImplementedException` dal corpo del metodo e aggiungere il codice seguente.  
  
     [!code-csharp[VbTDDWalkthrough#6](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.cs)]
     [!code-vb[VbTDDWalkthrough#6](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.vb)]  
  
### <a name="to-run-the-tests-again"></a>Per eseguire di nuovo il test  
  
- Scegliere **Esegui** dal menu **Test** e fare clic su **Tutti i test**.  

     Questa volta il test ha esito positivo. La finestra **Risultati test** è illustrata nella figura seguente.  
  
     ![Risultati dei test riusciti](../ide/media/testspassed.png "TestsPassed")
  
## <a name="see-also"></a>Vedere anche  
 [Generazione dall'utilizzo](../ide/visual-csharp-intellisense.md#generate-from-usage)   
 [Scrittura di codice](../ide/writing-code-in-the-code-and-text-editor.md)   
 [Utilizzo di IntelliSense](../ide/using-intellisense.md)   
 [Eseguire unit test del codice](../test/unit-test-your-code.md)  
 [Azioni rapide](../ide/quick-actions.md)  