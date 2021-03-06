---
title: 'Creazione di un nuovo progetto: dietro le quinte, parte 1 | Microsoft Docs'
description: Esaminare in modo dettagliato cosa accade in Visual Studio Integrated Development Environment (IDE) quando si crea un tipo di progetto personalizzato (parte 1 di 2).
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27a7e0f3175388b963e85950ea903843caff3baa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063149"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Generazione nuovo progetto: Dietro le quinte, prima parte
Hai mai pensato come creare un tipo di progetto personalizzato? Cosa accade effettivamente quando si crea un nuovo progetto? Diamo un'occhiata sotto la cappa e vediamo cosa succede.

 Sono disponibili diverse attività coordinate da Visual Studio:

- Viene visualizzato un albero di tutti i tipi di progetto disponibili.

- Consente di visualizzare un elenco di modelli di applicazione per ogni tipo di progetto e di selezionarne uno.

- Raccoglie le informazioni sul progetto per l'applicazione, ad esempio il nome e il percorso del progetto.

- Queste informazioni vengono passate alla factory del progetto.

- Genera elementi e cartelle del progetto nella soluzione corrente.

## <a name="the-new-project-dialog-box"></a>Finestra di dialogo nuovo progetto
 Tutto inizia quando si seleziona un tipo di progetto per un nuovo progetto. Per iniziare, fare clic su **nuovo progetto** dal menu **file** . Verrà visualizzata la finestra di dialogo **nuovo progetto** con un aspetto simile al seguente:

 ![Screenshot della finestra di dialogo Nuovo progetto.](../../extensibility/internals/media/newproject.gif)

 Di seguito si spiegherà meglio questo concetto. Nell'albero dei **tipi di progetto** sono elencati i vari tipi di progetto che è possibile creare. Quando si seleziona un tipo di progetto, ad esempio **Visual C# Windows**, viene visualizzato un elenco di modelli di applicazione per iniziare. I **modelli di Visual Studio installati** vengono installati da Visual Studio e sono disponibili per qualsiasi utente del computer. I nuovi modelli creati o raccolti possono essere aggiunti ai **modelli personali** e sono disponibili solo per l'utente.

 Quando si seleziona un modello come **applicazione Windows**, nella finestra di dialogo viene visualizzata una descrizione del tipo di applicazione. in questo caso, **un progetto per la creazione di un'applicazione con un'interfaccia utente di Windows**.

 Nella parte inferiore della finestra di dialogo **nuovo progetto** verranno visualizzati diversi controlli che raccolgono ulteriori informazioni. I controlli visualizzati dipendono dal tipo di progetto, ma in genere includono una casella di testo **nome** progetto, una casella di testo **percorso** e un pulsante **Sfoglia** correlato e una casella di testo **Nome soluzione** e la relativa **Creazione Directory per soluzione** .

## <a name="populating-the-new-project-dialog-box"></a>Popolamento della finestra di dialogo nuovo progetto
 Da dove viene visualizzata la finestra di dialogo **nuovo progetto** ? Qui sono disponibili due meccanismi di lavoro, uno dei quali è deprecato. La finestra di dialogo **nuovo progetto** combina e visualizza le informazioni ottenute da entrambi i meccanismi.

 Il metodo precedente (obsoleto) utilizza le voci del registro di sistema e i file VSDIR. Questo meccanismo viene eseguito all'apertura di Visual Studio. Il metodo più recente utilizza i file con estensione vstemplate. Questo meccanismo viene eseguito quando viene inizializzato Visual Studio, ad esempio eseguendo

```
devenv /setup
```

 oppure

```
devenv /installvstemplates
```

### <a name="project-types"></a>Tipi di progetto
 La posizione e i nomi dei nodi radice dei **tipi di progetto** , ad esempio **Visual C#** e **altri linguaggi**, sono determinati dalle voci del registro di sistema. L'organizzazione dei nodi figlio, ad esempio **database** e **Smart Device**, rispecchia la gerarchia delle cartelle che contengono i file con estensione vstemplate corrispondenti. Esaminiamo prima i nodi radice.

#### <a name="project-type-root-nodes"></a>Nodi radice del tipo di progetto
 Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene inizializzato, attraversa le sottochiavi della chiave del registro di sistema HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs per compilare e denominare i nodi radice dell'albero dei **tipi di progetto** . Queste informazioni vengono memorizzate nella cache per un uso successivo. Esaminare la chiave TemplateDirs \\ {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1. Ogni voce è un GUID VSPackage. Il nome della sottochiave (/1) viene ignorato, ma la sua presenza indica che si tratta di un nodo radice dei **tipi di progetto** . Un nodo radice può a sua volta avere diverse sottochiavi che ne controllano l'aspetto nell'albero dei **tipi di progetto** . Esaminiamo alcuni di essi.

##### <a name="default"></a>Valore predefinito.
 Si tratta dell'ID risorsa della stringa localizzata che assegna un nome al nodo radice. La risorsa di stringa si trova nella DLL satellite selezionata dal GUID del pacchetto VSPackage.

 Nell'esempio, il GUID del pacchetto VSPackage è

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 e l'ID risorsa (valore predefinito) del nodo radice (/1) è #2345

 Se si cerca il GUID nella chiave dei pacchetti vicina ed esamina la sottochiave SatelliteDll, è possibile trovare il percorso dell'assembly che contiene la risorsa di stringa:

 \<Visual Studio installation path>\VC # \VCSPackages\1033\csprojui.dll

 Per verificarlo, aprire Esplora file e trascinare csprojui.dll nella directory di Visual Studio. La tabella delle stringhe Mostra che la risorsa #2345 ha la didascalia **Visual C#**.

##### <a name="sortpriority"></a>SortPriority
 Determina la posizione del nodo radice nell'albero dei **tipi di progetto** .

 SortPriority REG_DWORD 0x00000014 (20)

 Più basso è il numero di priorità, maggiore è la posizione nella struttura ad albero.

##### <a name="developeractivity"></a>DeveloperActivity
 Se questa sottochiave è presente, la posizione del nodo radice viene controllata dalla finestra di dialogo Impostazioni sviluppatore. Ad esempio,

 DeveloperActivity REG_SZ VC #

 indica che Visual C# sarà un nodo radice se Visual Studio è impostato per [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] lo sviluppo. In caso contrario, sarà un nodo figlio di **altri linguaggi**.

##### <a name="folder"></a>Cartella
 Se questa sottochiave è presente, il nodo radice diventa un nodo figlio della cartella specificata. Viene visualizzato un elenco di cartelle possibili sotto la chiave

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders

 Ad esempio, la voce progetti di database ha una chiave di cartella che corrisponde alla voce altri tipi di progetto in PseudoFolders. Nell'albero dei **tipi di progetto** , quindi, i **progetti di database** saranno un nodo figlio di **altri tipi di progetto**.

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Tipi di progetto nodi figlio e file con estensione vstdir
 La posizione dei nodi figlio nell'albero dei **tipi di progetto** segue la gerarchia delle cartelle nelle cartelle ProjectTemplates. Per i modelli di computer (**modelli Visual Studio installati**), il percorso tipico è \Programmi\microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\ e per i modelli utente (**modelli personali**), il percorso tipico è \My Documenti\Visual Studio 14.0 \ Templates\ProjectTemplates \\ . Le gerarchie di cartelle da queste due posizioni vengono unite per creare l'albero dei **tipi di progetto** .

 Per le impostazioni di Visual Studio con C# Developer, l'albero dei **tipi di progetto** ha un aspetto simile al seguente:

 ![Screenshot dell'albero delle cartelle dei tipi di progetto in Visual Studio con le impostazioni per sviluppatori C#.](../../extensibility/internals/media/projecttypes.png)

 La cartella ProjectTemplates corrispondente ha un aspetto simile al seguente:

 ![Screenshot dell'albero delle cartelle dei modelli di progetto in Visual Studio con le impostazioni per sviluppatori C#.](../../extensibility/internals/media/projecttemplates.png)

 Quando viene visualizzata la finestra di dialogo **nuovo progetto** , [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] attraversa la cartella ProjectTemplates e ricrea la relativa struttura nell'albero dei **tipi di progetto** con alcune modifiche:

- Il nodo radice nell'albero dei **tipi di progetto** è determinato dal modello di applicazione.

- Il nome del nodo può essere localizzato e può contenere caratteri speciali.

- È possibile modificare l'ordinamento.

##### <a name="finding-the-root-node-for-a-project-type"></a>Ricerca del nodo radice per un tipo di progetto
 Quando Visual Studio attraversa le cartelle ProjectTemplates, apre tutti i file con estensione zip ed estrae tutti i file con estensione vstemplate. Un file con estensione vstemplate utilizza XML per descrivere un modello di applicazione. Per altre informazioni, vedere [creazione di un nuovo progetto: dietro le quinte, parte 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Il \<ProjectType> tag determina il tipo di progetto per l'applicazione. Il file di \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip, ad esempio, contiene un file EmptyProject. vstemplate con questo tag:

```
<ProjectType>CSharp</ProjectType>
```

 Il \<ProjectType> tag e non la sottocartella nella cartella ProjectTemplates determina il nodo radice di un'applicazione nell'albero dei **tipi di progetto** . Nell'esempio, Windows CE le applicazioni vengono visualizzate nel nodo radice di **Visual c#** e anche se si sposta la cartella di Windows Forms nella cartella VisualBasic, le applicazioni Windows CE vengono comunque visualizzate nel nodo radice di **Visual c#** .

##### <a name="localizing-the-node-name"></a>Localizzazione del nome del nodo
 Quando Visual Studio attraversa le cartelle ProjectTemplates, esamina tutti i file con estensione vstdir trovati. Un file con estensione vstdir è un file XML che controlla l'aspetto del tipo di progetto nella finestra di dialogo **nuovo progetto** . Nel file con estensione vstdir usare il \<LocalizedName> tag per assegnare un nome al nodo **tipi di progetto** .

 Ad esempio, il file \CSharp\Database\TemplateIndex.vstdir contiene questo tag:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 Ciò determina la DLL satellite e l'ID risorsa della stringa localizzata che assegna un nome al nodo radice, in questo caso il **database**. Il nome localizzato può contenere caratteri speciali che non sono disponibili per i nomi delle cartelle, ad esempio **.NET**.

 Se non \<LocalizedName> è presente alcun tag, il tipo di progetto viene denominato dalla cartella stessa, **SmartPhone2003**.

##### <a name="finding-the-sort-order-for-a-project-type"></a>Ricerca dell'ordinamento per un tipo di progetto
 Per determinare l'ordinamento del tipo di progetto, i file con estensione vstdir utilizzano il \<SortOrder> tag.

 Ad esempio, il file \CSharp\Windows\Windows.vstdir contiene questo tag:

```
<SortOrder>5</SortOrder>
```

 Il file \CSharp\Database\TemplateIndex.vstdir contiene un tag con un valore più grande:

```
<SortOrder>5000</SortOrder>
```

 Più basso è il numero nel \<SortOrder> tag, maggiore è la posizione nella struttura ad albero, quindi il nodo **Windows** viene visualizzato più in alto rispetto al nodo del **database** nell'albero dei **tipi di progetto** .

 Se \<SortOrder> per un tipo di progetto non viene specificato alcun tag, questo viene visualizzato in ordine alfabetico in base ai tipi di progetto che contengono \<SortOrder> specifiche.

 Si noti che non sono presenti file con estensione vstdir nelle cartelle Documents (**My templates**). I nomi dei tipi di progetto di applicazione utente non sono localizzati e sono visualizzati in ordine alfabetico.

#### <a name="a-quick-review"></a>Una rapida verifica
 Modificare la finestra di dialogo **nuovo progetto** e creare un nuovo modello di progetto utente.

1. Aggiungere una sottocartella MyProjectNode alla cartella \Programmi\microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\CSharp

2. Creare un file MyProject. vstdir nella cartella MyProjectNode usando un editor di testo.

3. Aggiungere le righe seguenti al file con estensione vstdir:

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. Salvare e chiudere il file con estensione vstdir.

5. Creare un file MyProject. vstemplate nella cartella MyProjectNode usando un editor di testo.

6. Aggiungere le righe seguenti al file con estensione vstemplate:

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. Salvare il file con estensione vstemplate e chiudere l'editor.

8. Inviare il file con estensione vstemplate a una nuova cartella MyProjectNode\MyProject.zip compressa.

9. Dalla finestra di comando di Visual Studio, digitare:

    ```
    devenv /installvstemplates
    ```

   Aprire Visual Studio.

10. Aprire la finestra di dialogo **nuovo progetto** ed espandere il nodo del progetto **Visual C#** .

    ![Screenshot dell'albero delle cartelle dei tipi di progetto nella finestra di dialogo nuovo progetto con MyProjectNode evidenziato nel nodo del progetto Visual C# espanso.](../../extensibility/internals/media/myprojectnode.png)

    **MyProjectNode** viene visualizzato come nodo figlio di Visual C# solo sotto il nodo Windows.

## <a name="see-also"></a>Vedi anche
- [Generazione nuovo progetto: Dietro le quinte, seconda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
