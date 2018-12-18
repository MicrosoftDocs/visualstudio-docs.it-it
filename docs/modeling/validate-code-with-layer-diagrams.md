---
title: Convalidare il codice con diagrammi di dipendenza | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 484afcd70717162719e9eaf8ace294cb1f71cbcd
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="validate-code-with-dependency-diagrams"></a>Convalidare il codice con diagrammi di dipendenza

**Ultime notizie**: vedere [questo post di blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/11/30/live-dependency-validation-in-visual-studio-2017/).

[Video: Convalidare le dipendenze di architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 

## <a name="why-use-dependency-diagrams"></a>Perché utilizzare diagrammi dipendenza?

Per assicurarsi che non siano in conflitto con la progettazione codice, è possibile convalidare il codice con diagrammi di dipendenza in Visual Studio. In questo modo è possibile effettuare le operazioni seguenti:  
  
-   Trovare conflitti tra le dipendenze nel codice e le dipendenze nel diagramma di dipendenza.  
  
-   Trovare le dipendenze sulle quali potrebbero influire le modifiche proposte.  
  
     Ad esempio, è possibile modificare il diagramma di dipendenze per mostrare le potenziali modifiche all'architettura e quindi convalidare il codice per visualizzare le dipendenze interessate.  
  
-   Effettuare il refactoring o la migrazione del codice in una progettazione diversa.  
  
     Trovare codice o dipendenze che richiedono azioni quando si sposta il codice in un'architettura diversa.  
  
 **Requisiti**  
  
-   Visual Studio  
  
-   Visual Studio sul server Team Foundation Build in uso per convalidare il codice automaticamente con Team Foundation Build  
  
-   Una soluzione che include un progetto di modellazione con un diagramma di dipendenze. Questo diagramma dipendenza deve essere collegato agli elementi nei progetti c# o Visual Basic che si desidera convalidare. Vedere [creare diagrammi dipendenza dal codice](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 È possibile convalidare il codice manualmente da un diagramma di dipendenza aperto in Visual Studio o da un prompt dei comandi. È inoltre possibile convalidare il codice automaticamente quando sono in esecuzione compilazioni locali o Team Foundation Build. Vedere [Video di Channel 9: progettazione e convalidare l'architettura con diagrammi di dipendenza](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
> [!IMPORTANT]
>  Se si desidera eseguire la convalida dei livelli in Team Foundation Build, è inoltre necessario installare la stessa versione di Visual Studio nel server di compilazione.  
  
-   [Verificare se un elemento supporta la convalida](#SupportsValidation)  
  
-   [Includere altri progetti per la convalida e l'assembly .NET](#IncludeReferences)  
  
-   [Convalidare manualmente il codice](#ValidateManually)  
  
-   [Convalidare automaticamente il codice](#ValidateAuto)  
  
-   [Risolvere i problemi di convalida dei livelli](#TroubleshootingValidation)  
  
-   [Comprendere e risolvere gli errori di convalida dei livelli](#UnderstandingValidationErrors)  

## <a name="live-dependency-validation"></a>Convalida della dipendenza in tempo reale

In questa versione di Visual Studio, convalida della dipendenza si verifica in tempo reale e gli errori vengono visualizzati immediatamente nella finestra Elenco errori di Visual Studio.

* Convalida in tempo reale è supportata per c# e Visual Basic.NET. 

* Per abilitare l'analisi della soluzione completa quando si utilizza una dipendenza in tempo reale convalida, aprire le impostazioni delle opzioni da barra gold visualizzata nell'elenco errori. 
 - È possibile ignorare questa barra gold definitivamente se non si è interessati a visualizzare tutti i problemi dell'architettura della soluzione.
 - Se non si abilita l'analisi della soluzione completa, l'analisi viene eseguita solo per i file da modificare.<p /> 

* Quando si aggiornano progetti per attivare la convalida in tempo reale, una finestra di dialogo viene visualizzato lo stato della conversione.

* Quando si aggiorna un progetto per la convalida della dipendenza in tempo reale, la versione del pacchetto NuGet in modo da essere uguale per tutti i progetti ed è la versione più recente in uso. 

* Aggiunta di un nuovo trigger di progetto di convalida dipendenza un aggiornamento del progetto. 
  
##  <a name="SupportsValidation"></a>Verificare se un elemento supporta la convalida  
 È possibile collegare i livelli a siti Web, documenti Office, file di testo normale e file in progetti condivisi tra più app, ma il processo di convalida non li includerà. Gli errori di convalida non verranno visualizzati per i riferimenti a progetti oppure a assembly collegati a livelli separati quando tra tali livelli non è presente alcuna dipendenza. Tali riferimenti non vengono considerati dipendenze a meno che il codice non li usi.  
  
1.  Nel diagramma di dipendenza, selezionare uno o più livelli, destro la selezione e quindi fare clic su **Visualizza collegamenti**.  
  
2.  In **Esplora livello**, esaminare il **supporta la convalida** colonna. Se il valore è false, l'elemento non supporta la convalida.  
  
##  <a name="IncludeReferences"></a>Includere altri progetti per la convalida e l'assembly .NET  
 Quando si trascinano elementi nel diagramma di dipendenza, i riferimenti a progetti o assembly di .NET corrispondenti vengono aggiunti automaticamente al **riferimenti livello** cartella nel progetto di modellazione. Questa cartella contiene i riferimenti agli assembly e ai progetti analizzati durante la convalida. È possibile includere altri assembly .NET e progetti per la convalida senza trascinarli manualmente nel diagramma di dipendenza.  
  
1.  In **Esplora**, fare clic sul progetto di modellazione o **riferimenti livello** cartella e quindi fare clic su **Aggiungi riferimento**.  
  
2.  Nel **Aggiungi riferimento** nella finestra di dialogo selezionare l'assembly o progetti e quindi fare clic su **OK**.  
  
##  <a name="ValidateManually"></a>Convalidare manualmente il codice  
 Se si dispone di un diagramma aperto dipendenza che è collegato a elementi di soluzione, è possibile eseguire il **convalida** comando di scelta rapida del diagramma. È anche possibile utilizzare il prompt dei comandi per eseguire il **msbuild** comando con il **ValidateArchitecture** proprietà personalizzata impostata su **True**. Ad esempio, analogamente alle modifiche nel codice, eseguire regolarmente la convalida dei livelli in modo da rilevare tempestivamente conflitti di dipendenza.  
  
#### <a name="to-validate-code-from-an-open-dependency-diagram"></a>Per convalidare il codice da un diagramma aperto dipendenza   
  
1.  Pulsante destro del mouse sulla superficie del diagramma e quindi fare clic su **Convalida architettura**.  
  
    > [!NOTE]
    >  Per impostazione predefinita, il **azione di compilazione** file del diagramma (con estensione layerdiagram) dipendenza è impostata su **convalida** in modo che il diagramma è incluso nel processo di convalida.  
  
     Il **elenco errori** finestra segnala gli eventuali errori. Per ulteriori informazioni sugli errori di convalida, vedere [individuare e risolvere gli errori di convalida livello](#UnderstandingValidationErrors).  
  
2.  Per visualizzare l'origine di ogni errore, fare doppio clic su errore nel **elenco errori** finestra.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] potrebbe essere visualizzata una mappa del codice anziché l'origine dell'errore. Questo errore si verifica quando il codice ha una dipendenza su un assembly che non viene specificato per il diagramma di dipendenze o al codice manca una dipendenza specificata nel diagramma di dipendenza. Esaminare la mappa del codice o il codice per determinare se la dipendenza deve esistere. Per ulteriori informazioni sulle mappe del codice, vedere [mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md).  
  
3.  Per gestire gli errori, vedere [gestire errori di convalida](#ManageErrors).  
  
#### <a name="to-validate-code-at-the-command-prompt"></a>Per convalidare il codice al prompt dei comandi  
  
1.  Aprire il prompt dei comandi di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Effettuare una delle seguenti operazioni:  
  
    -   Per convalidare il codice rispetto a un progetto di modellazione specifico nella soluzione, eseguire [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] con la seguente proprietà personalizzata.  
  
        ```  
        msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true  
        ```  
  
         - oppure -  
  
         Passare alla cartella che contiene il modello di progetto file (con estensione modelproj) e il diagramma di dipendenze, quindi eseguire [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] con la seguente proprietà personalizzata:  
  
        ```  
        msbuild /p:ValidateArchitecture=true   
        ```  
  
    -   Per convalidare il codice rispetto a tutti i progetti di modellazione nella soluzione, eseguire [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] con la seguente proprietà personalizzata:  
  
        ```  
        msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true   
        ```  
  
         - oppure -  
  
         Passare alla cartella della soluzione, che deve contenere un progetto di modello che contiene un diagramma di dipendenze, quindi eseguire [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] con la seguente proprietà personalizzata:  
  
        ```  
        msbuild /p:ValidateArchitecture=true  
        ```  
  
     Verranno elencati tutti gli errori che si verificano. Per ulteriori informazioni su [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], vedere [MSBuild](../msbuild/msbuild.md) e [attività MSBuild](../msbuild/msbuild-task.md).  
  
 Per ulteriori informazioni sugli errori di convalida, vedere [individuare e risolvere gli errori di convalida livello](#UnderstandingValidationErrors).  
  
###  <a name="ManageErrors"></a>Gestire gli errori di convalida  
 Durante il processo di sviluppo, potrebbe essere necessario eliminare alcuni conflitti segnalati durante la convalida. Ad esempio, è possibile eliminare gli errori che sono già stati corretti o che non sono attinenti allo scenario in questione. Quando si elimina un errore, è buona norma registrare un elemento di lavoro in [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].  
  
> [!WARNING]
>  Per creare un elemento di lavoro o aggiungere un collegamento ad esso, è necessario essere già connessi al controllo del codice sorgente TFS. Se si prova ad aprire una connessione in un'istanza diversa del controllo del codice sorgente TFS, Visual Studio chiude automaticamente la soluzione corrente. Prima di provare a creare un elemento di lavoro o ad aggiungervi un collegamento, verificare di essere già connessi all'istanza appropriata del controllo del codice sorgente. Nelle versioni successive di Visual Studio, i comandi di menu non sono disponibili se non si è connessi a un'istanza del controllo del codice sorgente.  
  
##### <a name="to-create-a-work-item-for-a-validation-error"></a>Per creare un elemento di lavoro per un errore di convalida  
  
-   Nel **elenco errori** finestra destro l'errore, scegliere **Crea elemento di lavoro**, quindi fare clic sul tipo di elemento di lavoro che si desidera creare.  
  
 Usare queste attività per gestire errori di convalida nel **elenco errori** finestra:  
  
|**Per**|**Seguire questi passaggi**|  
|------------|----------------------------|  
|Eliminare gli errori selezionati durante la convalida|Fare doppio clic su uno o più errori selezionati, scegliere **Gestisci errori di convalida**, quindi fare clic su **Elimina errori**.<br /><br /> Gli errori eliminati vengono visualizzati come barrati. Alla successiva convalida, questi errori non saranno visualizzati.<br /><br /> Gli errori eliminati vengono rilevati in un file con estensione suppressions per il file di diagramma di dipendenza corrispondente.|  
|Interrompere l'eliminazione di errori selezionati|Fare doppio clic su selezionato eliminati gli errori, scegliere **Gestisci errori di convalida**, quindi fare clic su **Interrompi eliminazione errori**.<br /><br /> Alla successiva convalida, gli errori eliminati selezionati verranno visualizzati.|  
|Ripristinare tutti gli errori eliminati nella **elenco errori** finestra|Fare clic nel **elenco errori** finestra, scegliere **Gestisci errori di convalida**, quindi fare clic su **Mostra tutti gli errori eliminati**.|  
|Nascondere tutti gli errori eliminati dal **elenco errori** finestra|Fare clic nel **elenco errori** finestra, scegliere **Gestisci errori di convalida**, quindi fare clic su **Nascondi errori eliminati**.|  
  
##  <a name="ValidateAuto"></a>Convalidare automaticamente il codice  
 È possibile eseguire la convalida dei livelli ogni volta che si esegue una compilazione. Se il team usa Team Foundation Build, è possibile eseguire la convalida dei livelli nelle archiviazioni gestite, che si possono specificare creando un'attività personalizzata MSBuild, e usare i rapporti di compilazione per raccogliere gli errori di convalida. Per creare compilazioni di archiviazione gestite, vedere [utilizzare un processo di compilazione di archiviazione gestita per convalidare le modifiche](http://msdn.microsoft.com/Library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).  
  
#### <a name="to-validate-code-automatically-during-a-local-build"></a>Per convalidare automaticamente il codice durante una compilazione locale  
  
-   Usare un editor di testo per aprire il file del progetto di modellazione (.modelproj), quindi includere la proprietà seguente:  
  
```  
<ValidateArchitecture>true</ValidateArchitecture>  
```  
  
 \- oppure -  
  
1.  In **Esplora**, fare clic sul progetto che contiene il diagramma di dipendenze o i diagrammi di modellazione e quindi fare clic su **proprietà**.  
  
2.  Nel **proprietà** finestra, impostare il progetto di modellazione **Convalida architettura** proprietà **True**.  
  
     Il progetto di modellazione viene incluso nel processo di convalida.  
  
3.  In **Esplora**, fare clic sul file di diagramma (con estensione layerdiagram) delle dipendenze che si desidera utilizzare per la convalida.  
  
4.  Nel **proprietà** finestra, assicurarsi che il diagramma **azione di compilazione** è impostata su **convalida**.  
  
     Il diagramma di dipendenza viene incluso nel processo di convalida.  
  
 Per gestire gli errori nella finestra Elenco errori, vedere [Gestisci errori di convalida](#ManageErrors).  
  
#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Per convalidare codice automaticamente durante un'operazione di Team Foundation Build  
  
1.  In **Team Explorer**, fare doppio clic sulla definizione di compilazione e quindi fare clic su **processo**.  
  
2.  In **parametri processo di compilazione**, espandere **compilazione**e digitare il comando seguente nel **argomenti MSBuild** parametro:  
  
     `/p:ValidateArchitecture=true`  
  
 Per ulteriori informazioni sugli errori di convalida, vedere [individuare e risolvere gli errori di convalida livello](#UnderstandingValidationErrors). Per altre informazioni su [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)], vedere:  
  
-   [Compilazione e versione](/vsts/build-release/index)  
  
-   [Utilizzare il modello predefinito per il processo di compilazione](http://msdn.microsoft.com/Library/43930b12-c21b-4599-a980-2995e3d16e31)  
  
-   [Modificare una compilazione Legacy che si basa sull'UpgradeTemplate.xaml](http://msdn.microsoft.com/Library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)  
  
-   [Personalizzare il modello del processo di compilazione](http://msdn.microsoft.com/Library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
-   [Monitorare lo stato di una compilazione in esecuzione](http://msdn.microsoft.com/Library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)  
  
##  <a name="TroubleshootingValidation"></a>Risolvere i problemi di convalida dei livelli  
 Nella tabella seguente vengono descritti i problemi di convalida dei livelli e la relativa risoluzione. Questi problemi differiscono dagli errori risultanti da conflitti tra il codice e la progettazione. Per ulteriori informazioni su questi errori, vedere [individuare e risolvere gli errori di convalida livello](#UnderstandingValidationErrors).  
  
|**Problema**|**Possibile causa**|**Risoluzione**|  
|---------------|------------------------|--------------------|  
|Gli errori di convalida non si verificano come previsto.|La convalida non funziona sui diagrammi di dipendenza che vengono copiati da altri diagrammi di dipendenza in Esplora soluzioni e che sono nello stesso progetto di modellazione. diagrammi di dipendenza che vengono copiati in questo modo contengono gli stessi riferimenti del diagramma di dipendenza originale.|Aggiungere un nuovo diagramma dipendenze al progetto di modello.<br /><br /> Copiare gli elementi dal diagramma di dipendenza di origine al nuovo diagramma.|  
  
##  <a name="UnderstandingValidationErrors"></a>Comprensione e risoluzione degli errori di convalida dei livelli  
 Quando si convalida il codice rispetto a un diagramma di dipendenze, si verificano errori di convalida quando il codice è in conflitto con la progettazione. In presenza delle condizioni seguenti è possibile ad esempio che si verifichino errori di convalida:  
  
-   Un elemento viene assegnato al livello errato. In questo caso, spostare l'elemento.  
  
-   Un elemento, ad esempio una classe, usa un'altra classe in un modo che causa conflitti con l'architettura. In questo caso, eseguire il refactoring del codice per rimuovere la dipendenza.  
  
 Per risolvere gli errori, aggiornare il codice finché non verranno più visualizzati errori di convalida. È possibile eseguire questa attività in modo iterativo.  
  
 Nella sezione seguente viene descritta la sintassi usata negli errori, viene illustrato il significato degli errori e vengono indicate le operazioni che è possibile eseguire per risolverli o gestirli.  
  
|**Sintassi**|**Descrizione**|  
|----------------|---------------------|  
|*ArtifactN*(*ArtifactTypeN*)|*Artefatton* è un elemento che è associato a un livello nel diagramma di dipendenza.<br /><br /> *Tipoelementon* è il tipo di *Artefatton*, ad esempio un **classe** o **metodo**, ad esempio:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Metodo)|  
|*NamespaceNameN*|Nome di uno spazio dei nomi.|  
|*LayerNameN*|Il nome di un livello nel diagramma di dipendenza.|  
|*Tipodipendenza*|Il tipo di relazione di dipendenza tra *Elemento1* e *elemento2*. Ad esempio, *Elemento1* ha un **chiamate** relazione con *elemento2*.|  
  
|**Sintassi errore**|**Descrizione dell'errore**|  
|----------------------|---------------------------|  
|DV0001: **dipendenza non valida**|Questo problema viene segnalato quando un elemento di codice (spazio dei nomi, tipo, membro) mappato a riferimenti a un livello un elemento di codice eseguito il mapping a un altro livello, ma non c'è alcuna freccia di dipendenza tra questi livelli nel diagramma convalida dipendenza contenente questo livelli. Ciò costituisce una violazione di vincolo di dipendenza.|  
|DV1001: **nome spazio dei nomi non valido**|Questo problema viene segnalato in un elemento di codice associato a un livello che la proprietà "Consentito Namespace Names" non contiene lo spazio dei nomi in cui è definito l'elemento di codice. Si tratta di una violazione dei vincoli di denominazione. Si noti che la sintassi di "Consentiti nomi di Namespace" è per un elenco di punti e virgola di spazi dei nomi in cui il codice, gli elementi associati vengono livello sono consentite da definire.|  
|DV1002: **dipendenza spazio dei nomi unreferenceable**|Questo problema viene segnalato in un elemento di codice associato a un livello e che fanno riferimento a un altro elemento di codice definito in uno spazio dei nomi definito nella proprietà "Namespace Unreferenceable" del livello. Si tratta di una violazione dei vincoli di denominazione. Si noti che la proprietà "Unreferenceable spazi dei nomi" è definita come un elenco separato da punto e virgola di spazi dei nomi che non deve essere fatto riferimento negli elementi di codice associati a questo livello.|  
|DV1003: **nome spazio dei nomi non consentito**|Questo problema viene segnalato in un elemento di codice associato a un livello contenente la proprietà "Nomi di Namespace non consentito" lo spazio dei nomi in cui è definito l'elemento di codice. Si tratta di una violazione dei vincoli di denominazione. Si noti che la proprietà "Nome spazio dei nomi non consentito" è definita come un elenco separato da punto e virgola di spazi dei nomi in cui il codice non devono essere definiti gli elementi associati a questo livello.|  
|DV3001: **collegamento mancante**|Livello '*nomelivello*'Collega a'*artefatto*' che non viene trovato. Probabilmente manca un riferimento a un assembly.|*Nomelivello* Collega a un elemento che non è stato trovato. Ad esempio, è possibile che manchi un collegamento a una classe perché nel progetto di modellazione manca un riferimento all'assembly che contiene la classe.|  
|DV9001: **errori interni di analisi dell'architettura**|I risultati potrebbero non essere completi. Per altre informazioni, vedere il log dettagliato degli eventi di compilazione o la finestra di output.|Per altre informazioni, vedere il log degli eventi di compilazione o la finestra di output.|  

 
## <a name="see-also"></a>Vedere anche  
 [Convalidare il sistema durante lo sviluppo](../modeling/validate-your-system-during-development.md)   
 [Video: Convalidare le dipendenze di architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   
