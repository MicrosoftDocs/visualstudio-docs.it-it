---
title: 'Procedura dettagliata: Configurazione e utilizzo di un Set di regole | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b72a86f10c6e864406929fdccfb59bdd9393752e
ms.sourcegitcommit: a0a49cceb0fdc1465ddf76d131c6575018b628b8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/05/2018
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Procedura dettagliata: Configurazione e uso di un set di regole personalizzate

Questa procedura dettagliata viene illustrato come utilizzare gli strumenti di analisi codice che sono stati configurati per l'utilizzo di un oggetto personalizzato *set di regole* in una libreria di classi. È possibile selezionare un set di regole correlato al tipo di progetto che è stato specificato per la soluzione, oppure è possibile selezionare il set di regole alternativi per soddisfare esigenze specifiche, ad esempio l'analisi del codice legacy per i problemi che possono essere risolti in modo che non determina interruzione. In entrambi i casi, i set di regole possono essere personalizzati anche per ottimizzare per i requisiti del progetto.  
  
In questa procedura dettagliata, verranno esaminati i processi:  
  
-   Creare una libreria di classi.  
  
-   Selezionare il **regole base delle linee guida di progettazione Microsoft** set di regole di analisi del codice.  
  
-   Aggiungere codice alla classe.  
  
-   Eseguire l'analisi del codice.  
  
-   Personalizzare il set di regole.  
  
-   Eseguire l'analisi del codice e vedere come il set di regole comportamento delle personalizzazioni.  
  
## <a name="using-rule-sets-with-code-analysis"></a>Regola di utilizzo di set con l'analisi del codice

Innanzitutto, creare una libreria di classi semplice.  
  
### <a name="create-a-class-library"></a>Creare una libreria di classi  
  
1.  Scegliere **Nuovo** dal menu **File** , quindi fare clic su **Progetto**.  
  
2.  Nel **nuovo progetto** nella finestra di dialogo **tipi di progetto**, fare clic su **Visual c#**.  
  
3.  In **Visual c#**selezionare **libreria di classi**.  
  
4.  Nel **nome** nella casella di testo **RuleSetSample** e quindi fare clic su **OK**.  
  
 Successivamente, selezionerà il **regole base delle linee guida di progettazione Microsoft** set di regole e salvarlo con il progetto.  
  
### <a name="select-a-code-analysis-rule-set"></a>Selezionare un set di regole di analisi codice  
  
1.  Nel **Analizza** menu, fare clic su **Configura analisi codice per RuleSetSample**.  
  
     Vengono visualizzate le impostazioni di configurazione per l'analisi codice.  
  
2.  Nel **eseguire il set di regole** elenco a discesa, seleziona **tutte le regole Microsoft**.  
  
     Per ulteriori informazioni sui set di regole disponibili, vedere [riferimento del set di regole di analisi codice](../code-quality/code-analysis-rule-set-reference.md).  
  
     Dal menu File, fare clic su **Salva elementi selezionati** per aggiornare il file di progetto con informazioni sul set di regole selezionato e le relative impostazioni.  
  
    > [!TIP]
    >  In una situazione reale, consiglia di utilizzare le priorità dei problemi di destinazione con l'analisi del codice è iniziare con il **regole minime consigliate** set di regole e correggere i problemi desiderati e quindi aggiungere in modo incrementale altre regole o regole imposta per trovare e correggere i problemi aggiuntivi.  
  
 Successivamente, si aggiungerà codice alla libreria di classi che verrà utilizzata per illustrare le violazioni del CA1704 "Gli identificatori devono essere digitati correttamente" regola di analisi del codice. Per ulteriori informazioni, vedere [CA1704: gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
### <a name="add-your-own-code"></a>Aggiungere codice personalizzato  
  
-   In Esplora soluzioni, aprire il file Class1. cs e sostituire il codice esistente con il seguente:  
  
    ```csharp
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace RuleSetSample  
    {  
        public class Class1  
        {  
            //The variable parameter names "a" and "b" will cause  
            //the warning CA 1704 Microsoft.Naming "Consider   
            //providing a more meaningful name" to fire  
            public int AddIntegers(int a, int b)  
            {  
  
                int sum = a + b;  
  
                return (sum);  
            }  
        }  
    }
    ```
  
È ora possibile eseguire l'analisi del codice sul progetto RuleSetSample e cercare eventuali errori e avvisi generati nella finestra Elenco errori.  
  
### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Eseguire l'analisi del codice sul progetto RuleSetSample  
  
1.  Nel **Analizza** menu, fare clic su **Esegui analisi del codice su RuleSetSample**.  
  
2.  Nella finestra Elenco errori, fare clic su **avvisi** e quindi fare clic su di **descrizione** intestazione di colonna per ordinare gli avvisi in ordine alfanumerico.  
  
     In un'applicazione reale, vorrebbero correggere eventuali violazioni delle regole corrispondente a questo punto, o, facoltativamente, disattivare o eliminare una regola se è possibile determinare che non è necessario correggere. Per ulteriori informazioni, vedere [esclusione di avvisi](../code-quality/in-source-suppression-overview.md).
  
3.  Si noti gli avvisi CA1704. Tali violazioni di questa regola indicano che è "consigliabile fornire un nome più significativo per i parametri." È stato possibile risolvere il problema nel codice oppure è possibile disabilitare la regola, come illustrato nella procedura successiva.  
  
 Successivamente, si personalizzerà il set di regole per escludere l'avviso CA1704, "Gli identificatori devono essere digitati correttamente".  
  
### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Personalizzare il set di regole per il progetto disabilitare una regola specifica  
  
1.  Nel **Analizza** menu, fare clic su **Configura analisi codice per RuleSetSample**.  
  
2.  Nel **eseguire il set di regole** elenco a discesa elenco, verificare che il **tutte le regole Microsoft** sia ancora evidenziato set di regole e quindi fare clic su **aprire**. Verrà visualizzata la pagina di set di regole.  
  
3.  Espandere il nodo della categoria Microsoft. naming e quindi selezionare l'avviso CA1704.  
  
4.  Sotto il **azione** colonna, selezionare **nessuno.** CA1704 ciò impedisce la visualizzazione come un avviso o errore nella finestra Elenco errori.  
  
     Ora è utile per sperimentare i vari pulsanti della barra degli strumenti e per acquisire familiarità con le opzioni di filtro. Ad esempio, è possibile utilizzare il **Group By** elenco a discesa per consentire l'individuazione di una regola specifica, o categoria delle regole. Un altro esempio è che è possibile utilizzare il **Nascondi regole disabilitate** sulla barra degli strumenti regola del set di pagine per nascondere o mostrare tutte le regole con il **azione** colonna impostata su **Nessuno**. Questo può essere utile se si desidera cercare eventuali regole che è stato disattivato per verificare che si desidera abilitarle o meno.  
  
5.  Dal menu Visualizza, fare clic sulla finestra Proprietà. Tipo **My Custom Rule Set** nella casella nome della finestra Proprietà. Il nome visualizzato di nuovo set di regole in questo modo viene modificata la [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] IDE.  
  
6.  Nel **File** menu, fare clic su **Rules.ruleset tutti Microsoft salvare** per salvare la regola personalizzata set. Passare alla cartella radice del progetto. In **il nome del file** nella casella di testo **SetRegolePersonalizzato**. Ora è possibile selezionare il set di regole personalizzate per l'utilizzo con il progetto.  
  
Con il nuovo set di regole creato, ora è necessario configurare le impostazioni del progetto per specificare che si desidera utilizzare la nuova regola, impostare con esso.  
  
### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Specificare la nuova regola impostata per l'utilizzo con il progetto  
  
1.  In Esplora soluzioni, fare clic sul progetto e quindi selezionare **proprietà**.  
  
2.  Nel **proprietà** scheda, fare clic su **analisi del codice**.  
  
     Nel **eseguire il set di regole** elenco a discesa, fare clic su  **\<Sfoglia... >**. Passare alla cartella radice del progetto del codice e quindi selezionare **SetRegolePersonalizzato**. Questo è il nuovo set di regole creato nella procedura precedente.  
  
3.  Nel **File** menu, fare clic su **salvare** per salvare la configurazione del progetto. Il set di regole personalizzato ora è utilizzabile con il progetto.  
  
 Infine, verrà eseguito nuovamente utilizzando il set di regole SetRegolePersonalizzato analisi del codice. Si noti che la finestra Elenco errori non vengono visualizzate la violazione delle regole di prestazioni CA1704.  
  
### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Eseguire l'analisi del codice sul progetto RuleSetSample per la seconda volta  
  
1.  Nel **Analizza** menu, fare clic su **Esegui analisi del codice su RuleSetSample**.  
  
2.  Nella finestra Elenco errori, si noti che quando si fa clic **avvisi**, non si visualizzano più la violazione CA1704 per la regola "Gli identificatori devono essere digitati correttamente".  
  
## <a name="see-also"></a>Vedere anche

[Procedura: configurare l'analisi codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
[Tabella di riferimento del set di regole di analisi del codice](../code-quality/code-analysis-rule-set-reference.md)