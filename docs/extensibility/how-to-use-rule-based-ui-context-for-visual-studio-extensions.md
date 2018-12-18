---
title: 'Procedura: utilizzare il contesto dell''interfaccia utente basata su regole per le estensioni di Visual Studio | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
ms.workload: vssdk
ms.openlocfilehash: 92166106c1470aaf1af7198a133495dba333c121
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Procedura: utilizzare il contesto dell'interfaccia utente basata su regole per le estensioni di Visual Studio
Visual Studio consente il caricamento dei pacchetti VSPackage quando noto <xref:Microsoft.VisualStudio.Shell.UIContext>s vengono attivati. Questi contesti dell'interfaccia utente non sono molto accurati con granularità, non lasciando gli autori delle estensioni scelta tuttavia, per selezionare un contesto dell'interfaccia utente disponibili che attiva prima del punto volevano effettivamente il pacchetto VSPackage per caricare. Per un elenco di contesti dell'interfaccia utente ben noti, vedere <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.  
  
 Il caricamento dei pacchetti può avere un impatto sulle prestazioni e caricarli prima del necessario, non è consigliata. Visual Studio 2015 è stato introdotto il concetto di contesti dell'interfaccia utente basata su regole, un meccanismo che consente agli autori di estensione definire le condizioni esatte in cui viene attivato un contesto dell'interfaccia utente e caricato VSPackage associati.  
  
## <a name="rule-based-ui-context"></a>Contesto basato su regole dell'interfaccia utente  
 Una "regola" è costituita da un nuovo contesto dell'interfaccia utente (GUID) e un'espressione booleana che fa riferimento a uno o più "condizioni" combinati con logica "e", "o", "not" operazioni. "Condizioni" vengono valutate in modo dinamico in fase di esecuzione e l'espressione viene valutata nuovamente ogni volta che le modifiche apportate al relativo termini. Quando l'espressione restituisce true, viene attivato il contesto dell'interfaccia utente associato. In caso contrario, il contesto dell'interfaccia utente è disattivato.  
  
 Basato su regole di contesto dell'interfaccia utente può essere utilizzato in diversi modi:  
  
1.  Specificare i vincoli di visibilità per comandi e le finestre degli strumenti. È possibile nascondere le finestre degli strumenti di comandi/fino a quando non viene soddisfatta la regola di contesto dell'interfaccia utente.  
  
2.  Come automatica dei vincoli di carico: caricamento automatico dei pacchetti solo quando viene soddisfatta la regola  
  
3.  Posticipata di attività: ritardare il caricamento fino a quando non è trascorso un intervallo specificato e ancora viene soddisfatta la regola.  
  
 Il meccanismo può essere utilizzato da qualsiasi estensione di Visual Studio.  
  
## <a name="create-a-rule-based-ui-context"></a>Creare un contesto basato su regole dell'interfaccia utente  
 Si supponga di avere un'estensione denominata TestPackage, che offre un comando di menu che si applica solo ai file con estensione "config". Prima di VS2015, la scelta migliore è stato caricare TestPackage quando <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> contesto dell'interfaccia utente è stato attivato. Questo non è efficiente, poiché la soluzione caricata non può contenere anche un file con estensione config. Possiamo vedere come contesto di interfaccia utente basata su regole può essere utilizzato per attivare un contesto dell'interfaccia utente solo quando un file con estensione config sia selezionata e caricare TestPackage quando viene attivato il contesto dell'interfaccia utente.  
  
1.  Definire un nuovo GUID UIContext e aggiungere alla classe VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> e <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.  
  
     Ad esempio, si supponga che un nuovo UIContext "UIContextGuid" è da aggiungere. GUID creato (è possibile creare un GUID facendo clic su Strumenti -> creare un guid) è "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Aggiungere il seguente all'interno della classe del pacchetto:  
  
    ```csharp  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     Per gli attributi, aggiungere il seguente: (dettagli di questi attributi verranno spiegati più avanti)  
  
    ```csharp  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     Questi metadati definire il nuovo GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) e un'espressione che fa riferimento a un solo termine, "DotConfig". Il termine "DotConfig" restituisce true ogni volta che la selezione corrente nella gerarchia attivo ha un nome corrispondente al criterio di espressione regolare "\\config$" (termina con "config"). Il valore (predefinito) definisce un nome facoltativo per la regola è utile per il debug.  
  
     I valori dell'attributo vengono aggiunti a pkgdef generati durante la fase di compilazione in un secondo momento.  
  
2.  Nel file VSCT per i comandi del TestPackage, aggiungere il flag "DynamicVisibility" per i comandi appropriati:  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  Nella sezione di visibilità del VSCT, associare i comandi appropriati per il nuovo UIContext GUID definito in #1:  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  Nella sezione simboli, aggiungere la definizione di UIContext:  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     A questo punto, i comandi di menu di scelta per i file config saranno visibili solo quando l'elemento selezionato in Esplora soluzioni è un file "con estensione config" e il pacchetto non verrà caricato finché non viene selezionato uno dei tali comandi.  
  
 Successivamente, è possibile utilizzare un debugger per verificare che il pacchetto viene caricato solo quando è previsto. Per eseguire il debug TestPackage:  
  
1.  Impostare un punto di interruzione nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo.  
  
2.  Compilare il TestPackage e avviare il debug.  
  
3.  Creare un progetto o aprire uno.  
  
4.  Selezionare qualsiasi file con estensione diversa da config. Non verrà raggiunto il punto di interruzione.  
  
5.  Selezionare il file app. config.  
  
 Il TestPackage carica e si ferma in corrispondenza del punto di interruzione.  
  
## <a name="adding-more-rules-for-ui-context"></a>Aggiunta di ulteriori regole per il contesto dell'interfaccia utente  
 Poiché le regole di contesto dell'interfaccia utente sono espressioni booleane, è possibile aggiungere più limitato di regole per un contesto dell'interfaccia utente. Ad esempio, nel contesto dell'interfaccia utente precedente, è possibile specificare che la regola viene applicata solo quando viene caricata una soluzione con un progetto. In questo modo, i comandi non vengono visualizzati se si apre un file "con estensione config" come file autonomo, non come parte di un progetto.  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 A questo punto l'espressione fa riferimento a tre termini. Le prime due condizioni, "SingleProject" e "MultipleProjects", fare riferimento ad altri contesti dell'interfaccia utente noto (in base al GUID). Il terzo termine, "DotConfig" è definito in precedenza il contesto dell'interfaccia utente basato su regole.  
  
## <a name="delayed-activation"></a>Attivazione ritardata  
 Regole possono avere un parametro facoltativo "ritardo". Viene specificato il ritardo in millisecondi. Se presente, il ritardo comporta l'attivazione o disattivazione del contesto dell'interfaccia utente di una regola per essere posticipato da tale intervallo di tempo. Se prima dell'intervallo di ritardo di nuovo le modifiche di regola, quindi non accade nulla. Questo meccanismo è utilizzabile per operazioni di inizializzazione - particolarmente inizializzazione unica senza basarsi su timer o di registrazione per le notifiche di inattività "scaglionare".  
  
 Ad esempio, è possibile specificare la regola di test di carico per hanno un ritardo di 100 millisecondi:  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## <a name="term-types"></a>Tipi di termine  
 Ecco i diversi tipi di termini che sono supportati:  
  
|||  
|-|-|  
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Il GUID si riferisce a un contesto dell'interfaccia utente. Al termine sarà true ogni volta che il contesto dell'interfaccia utente è attivo e false in caso contrario.|  
|HierSingleSelectionName:\<modello >|Al termine sarà true ogni volta che la selezione nella gerarchia attivo è un singolo elemento e il nome dell'elemento selezionato corrisponde all'espressione regolare .net specificato da "modello".|  
|UserSettingsStoreQuery:\<query >|"query" rappresenta un percorso completo nell'archivio impostazioni utente che deve restituire un valore diverso da zero. La query è suddiviso in una "collection" e "propertyName" all'ultima barra.|  
|ConfigSettingsStoreQuery:\<query >|"query" rappresenta un percorso completo nell'archivio di impostazioni di configurazione che deve restituire un valore diverso da zero. La query è suddiviso in una "collection" e "propertyName" all'ultima barra.|  
|ActiveProjectFlavor:\<projectTypeGuid >|Al termine sarà true ogni volta che il progetto selezionato è versione (aggregato) e dispone di una versione che corrisponde al tipo di progetto specificato GUID.|  
|ActiveEditorContentType:\<contentType >|Al termine sarà true quando il documento selezionato è un editor di testo con il tipo di contenuto specificato.|  
|ActiveProjectCapability:\<espressione >|Il termine è true quando le funzionalità del progetto attivo corrisponde all'espressione specificata. Un'espressione può essere simile a VB &#124; CSharp|  
|SolutionHasProjectCapability:\<espressione >|Simile alla precedente, ma termine è true quando si dispone di alcun progetto caricato che corrisponde all'espressione.|  
|SolutionHasProjectFlavor:\<projectTypeGuid >|Al termine sarà true ogni volta che una soluzione di progetto che è del (aggregato) che ha una versione che corrisponde al tipo di progetto specificato GUID.|


  
## <a name="compatibility-with-cross-version-extension"></a>Compatibilità con estensione tra versioni  
 Regole base contesti dell'interfaccia utente è una nuova funzionalità in Visual Studio 2015 e potrebbe non essere trasferito a versioni precedenti. Questo costituisce un problema con le estensioni/pacchetti destinati a più versioni di Visual Studio che devono essere caricati automaticamente in Visual Studio 2013 e versioni precedenti, ma possono trarre vantaggio da contesti dell'interfaccia utente basato su regole per evitare che viene caricato automaticamente in Visual Studio 2015.  
  
 Per supportare tali pacchetti, AutoLoadPackages voci nel Registro di sistema ora possono fornire un flag nel campo relativo al valore per indicare che la voce deve essere ignorata in Visual Studio 2015 e versioni successive. Questa operazione può essere eseguita mediante l'aggiunta di un'opzione di flag per <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Ora è possono aggiungere pacchetti VSPackage **SkipWhenUIContextRulesActive** opzione loro <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> attributo per indicare la voce deve essere ignorata in Visual Studio 2015 e versioni successive.  
  
## <a name="extensible-ui-context-rules"></a>Regole di contesto estendibile dell'interfaccia utente  
 In alcuni casi, pacchetti non è possibile utilizzare regole di contesto dell'interfaccia utente statiche. Si supponga, ad esempio, che si dispone di un pacchetto di supporto di estendibilità in modo che lo stato del comando è basato su tipi di editor che sono supportati dai provider MEF importati. Il comando è abilitato se c'è un'estensione che supporta il tipo di modifica corrente. In questi casi il pacchetto stesso non è possibile usare una regola dell'interfaccia utente contesto statica, perché comporterebbe la modifica a seconda di quale MEF le estensioni sono disponibili le condizioni.  
  
 Per supportare tali pacchetti, i contesti dell'interfaccia utente basato su regole supportano un'espressione hardcoded "*" che indica tutti i termini del contratto verrà unita con o. In questo modo per il pacchetto master definire una regola nota basati su contesto dell'interfaccia utente e collegare lo stato dei comandi per questo contesto. In un secondo momento tutte le estensioni MEF per il pacchetto master di destinazione è possono aggiungere le condizioni per l'editor che supporta senza conseguenze per le altre condizioni o l'espressione master.  
  
 Il costruttore <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> documentazione viene illustrata la sintassi per le regole di contesto dell'interfaccia utente estendibile.