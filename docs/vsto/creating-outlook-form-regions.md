---
title: Creazione di aree del modulo di Outlook | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio]
- form regions [Office development in Visual Studio], creating
- Outlook [Office development in Visual Studio], form regions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 86f325784fdd175b5b449eb4d55d920a3f9df2d4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="creating-outlook-form-regions"></a>Creating Outlook Form Regions
  È possibile usare aree del modulo per personalizzare i moduli di Microsoft Office Outlook. Visual Studio fornisce strumenti avanzati che semplificano la progettazione, lo sviluppo e il debug delle aree del modulo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 In questo argomento vengono fornite le seguenti informazioni:  
  
-   [Vantaggi dell'utilizzo di aree del modulo](#Enhance)  
  
-   [Aggiunta di un'area del modulo di Outlook al progetto](#Adding)  
  
-   [Utilizzando Progettazione aree di modulo](#UsingFormRegionDesigner)  
  
-   [Utilizzo di un'area del modulo progettata in Outlook](#UsingFormRegionDesignedOutlook)  
  
-   [Aggiungere il codice personalizzato per un'area del modulo](#AddingCustomCode)  
  
-   [Compilazione del progetto](#Building)  
  
-   [Debug di un'area del modulo](#Debugging)  
  
-   [Distribuzione di un'area del modulo](#Deploying)  
  
##  <a name="Enhance"></a>Vantaggi dell'utilizzo di aree del modulo  
 Le aree del modulo offrono numerosi miglioramenti rispetto allo sviluppo di moduli Outlook tradizionali:  
  
-   Personalizzare la pagina predefinita di qualsiasi modulo standard.  
  
-   Aggiungere fino a 12 pagine aggiuntive a qualsiasi modulo standard.  
  
-   Sostituire o migliorare un modulo standard.  
  
-   Visualizzare l'interfaccia utente personalizzata nel riquadro di lettura e nei controlli.  
  
 Per ulteriori informazioni, vedere [personalizzazione delle pagine di Form e aree del modulo](http://msdn.microsoft.com/library/office/ff869060.aspx).  
  
##  <a name="Adding"></a>Aggiunta di un'area del modulo di Outlook al progetto  
 È possibile utilizzare il **nuova area del modulo di Outlook** procedura guidata per progettare una nuova area del modulo o importare un'area del modulo progettata in Outlook. È anche possibile riutilizzare un'area del modulo esistente, precedentemente usata in un altro progetto di componente aggiuntivo VSTO di Outlook.  
  
###  <a name="CreatingFormRegion"></a>Creazione di una nuova area del modulo utilizzando la procedura guidata  
 Per creare un'area del modulo, aggiungere un **area del modulo di Outlook** elemento a un progetto di componente aggiuntivo VSTO di Outlook. Verrà avviata la **nuova area del modulo di Outlook** procedura guidata.  
  
 Usare la procedura guidata per indicare se si vuole progettare una nuova area del modulo o importare un'area del modulo progettata in Outlook. Per ulteriori informazioni sulla progettazione di una nuova area del modulo, vedere [usando Progettazione aree di modulo](#UsingFormRegionDesigner). Per ulteriori informazioni sull'utilizzo di un'area del modulo progettata in Outlook, vedere [l'importazione di un'area di modulo progettata in Outlook](#UsingFormRegionDesignedOutlook).  
  
 Usare la procedura guidata per specificare il tipo di area del modulo da creare. La tabella seguente descrive ciascun tipo di area del modulo.  
  
|Tipo di area|Descrizione|  
|-----------------|-----------------|  
|Separa|Aggiunge l'area del modulo come una nuova pagina a un modulo di Outlook.|  
|Adiacente|Aggiunge l'area del modulo alla parte inferiore della pagina predefinita di un modulo di Outlook.|  
|Sostituzione|Aggiunge l'area del modulo come una nuova pagina che sostituisce la pagina predefinita di un modulo di Outlook.|  
|Sostituzione completa|Sostituisce l'intero modulo di Outlook con l'area del modulo.|  
  
 È anche possibile usare la procedura guidata per specificare le condizioni di visualizzazione e selezionare il tipo di modulo da estendere. Per ulteriori informazioni, vedere [procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Le selezioni effettuate nella procedura guidata influiscono sulle opzioni disponibili in altre pagine della procedura guidata. Ad esempio, se si seleziona **adiacente** o **separato** nel **creare una nuova area del modulo di Outlook** pagina, quindi il **titolo** e **Descrizione** campi non sono disponibili nel **fornire un testo descrittivo e selezionare le preferenze di visualizzazione** pagina. Questo avviene perché Outlook non usa questi campi quando viene visualizzata un'area del modulo adiacente o separata.  
  
#### <a name="form-region-files"></a>File area del modulo  
 Quando si completa la **nuova area del modulo di Outlook** procedura guidata, Visual Studio aggiunge automaticamente i seguenti file al progetto:  
  
-   Un file di codice dell'area del modulo. Questo file contiene il nome specificato per il **area del modulo di Outlook** elemento il **Aggiungi nuovo elemento** la finestra di dialogo. Aggiungere a questo file il codice per gestire gli eventi dell'area del modulo.  
  
-   Un file di codice di Progettazione aree di form. Questo file contiene il codice generato da Progettazione aree di form e non può essere modificato direttamente.  
  
-   Un file ofs (Outlook Form Storage).  
  
    > [!NOTE]  
    >  Questo file viene aggiunto al progetto solo se si importa un'area del modulo progettata in Outlook.  
  
#### <a name="form-region-factory-class"></a>Classe factory dell'area del modulo  
 Il file di codice dell'area del modulo contiene una classe parziale che implementa l'interfaccia <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory>. Si tratta della classe factory dell'area del modulo che è responsabile della creazione di nuove istanze dell'area del modulo.  
  
 Questa classe è disponibile espandendo il **Factory area del modulo** area.  
  
 Il **nuova area del modulo di Outlook** guidata aggiunge attributi per questa classe che specificano il nome interno dell'area del modulo e le classi di messaggi che consentono di visualizzare l'area del modulo. È possibile modificare manualmente questi attributi dopo che il file è stato aggiunto al progetto.  
  
 La maggior parte della classe factory dell'area del modulo è implementata nel file di Progettazione aree di form. Tuttavia, il gestore eventi `FormRegionInitializing` è esposto nel file di codice dell'area del modulo e può essere usato per specificare se l'area del modulo deve essere visualizzata in Outlook. Per ulteriori informazioni, vedere [gestione degli eventi dell'area del modulo](#HandlingFormRegionEvents).  
  
###  <a name="AddingExistingFormRegion"></a>Aggiunta di un'area del modulo esistente al progetto  
 Un'area del modulo di Outlook di un altro progetto di Outlook può essere riutilizzata nel progetto corrente di componente aggiuntivo VSTO per Outlook con la finestra di dialogo **Aggiungi elemento esistente** .  
  
 L'area del modulo esistente deve avere un file di codice (VB o cs); non è possibile aggiungere file di modulo OFS (Outlook Storage) utilizzando il **Aggiungi elemento esistente** la finestra di dialogo. Tuttavia, è possibile creare un'area del modulo nuova importando un file ofs (Outlook From Storage). Per ulteriori informazioni, vedere [procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
##  <a name="UsingFormRegionDesigner"></a>Utilizzando Progettazione aree di modulo  
 Progettazione aree di form consente di configurare il layout e l'aspetto di un'area del modulo. È possibile trascinare i controlli gestiti nell'area della finestra di progettazione, fare doppio clic sui controlli per aprire i gestori eventi e impostare le proprietà nel **proprietà** finestra.  
  
> [!NOTE]  
>  È possibile trovare le proprietà che interessano la modalità di visualizzazione dell'area del modulo in Outlook sotto il **manifesto** nodo il **proprietà** finestra.  
  
 Progettazione aree di modulo è disponibile solo se si seleziona **Progetta nuova area del modulo** nel **selezionare come si desidera creare l'area del modulo** pagina il **nuova area del modulo di Outlook** procedura guidata.  
  
 È possibile aprire Progettazione aree di form in tre modi diversi:  
  
-   In **Esplora**, fare doppio clic sul file di codice di area del modulo.  
  
-   In **Esplora**, fare doppio clic su file di codice di area del modulo e quindi fare clic su **Visualizza finestra di progettazione**.  
  
-   In **Esplora**, selezionare i file di codice dell'area del modulo e quindi scegliere il **vista** menu, fare clic su **progettazione**.  
  
 Progettazione aree di form supporta solo i controlli gestiti. Non è possibile aggiungere controlli nativi di Outlook.  
  
##  <a name="UsingFormRegionDesignedOutlook"></a>L'importazione di un'area del modulo progettata in Outlook  
 Quando si progetta in Outlook, è possibile aggiungere all'area del modulo i controlli nativi di Outlook che consentono di effettuare associazioni ai dati di Outlook in fase di progettazione. Tuttavia, non si potrà usare in seguito Progettazione aree di form per aggiungere i controlli gestiti o modificare la progettazione dell'area del modulo.  
  
 È possibile importare aree del modulo in un progetto di componente aggiuntivo VSTO di Outlook mediante il **nuova area del modulo di Outlook** procedura guidata. Nel **selezionare come si desidera creare l'area del modulo** selezionare **importare un file (OFS) di Outlook Form Storage**. Quindi, selezionare il percorso di un file ofs (Outlook Form Storage). Outlook salva le aree del modulo come file ofs.  
  
 Il **nuova area del modulo di Outlook** guidata copia il file OFS nella directory del progetto e aggiunge i riferimenti a controlli per il file di progettazione aree di modulo. È possibile quindi gestire gli eventi di controllo nel file di codice dell'area del modulo.  
  
 Per gestire gli eventi in un progetto Visual Basic, selezionare un evento dall'elenco dei nomi di metodo nella parte superiore dell'editor di codice.  
  
 Per gestire gli eventi in un progetto C#, sottoscrivere gli eventi di controllo nel metodo <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>. Per ulteriori informazioni, vedere [procedura: sottoscrivere e annullare la sottoscrizione di eventi &#40; C &#35; Guida per programmatori &#41; ](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events).  
  
 È possibile modificare le proprietà dell'area del modulo nel metodo `InitializeManifest` della classe factory dell'area del modulo.  
  
> [!NOTE]  
>  Per importare un'area del modulo, è necessario lavorare a un progetto destinato alla stessa versione di Outlook installata nel computer di sviluppo. Ad esempio, se è installato Outlook 2010, l'importazione di un modulo area funziona solo in un progetto è stato creato utilizzando il **componente aggiuntivo per Outlook 2010** modello di progetto.  
  
### <a name="updating-an-imported-form-regions-design"></a>Aggiornamento della progettazione di un'area del modulo importata  
 È possibile aggiungere, rimuovere o modificare i controlli dell'area del modulo. Prima di eseguire queste operazioni, effettuare il backup del codice aggiunto al file di codice dell'area del modulo. Quindi, aprire il file OFS in Outlook, modificare l'area del modulo e salvare le modifiche. Utilizzare il **nuova area del modulo di Outlook** guidata per importare il file OFS modificato. È quindi possibile incollare il codice nel file di codice della nuova area del modulo.  
  
##  <a name="AddingCustomCode"></a>Aggiungere il codice personalizzato per un'area del modulo  
 Lo spazio dei nomi <xref:Microsoft.Office.Tools.Outlook> fornisce l'accesso alle classi che rappresentano l'area del modulo, all'elemento di Outlook che visualizza l'area del modulo e ad altri elementi utili. Il **area del modulo di Outlook** elemento aggiunge automaticamente un riferimento all'assembly nel progetto e inserisce appropriata **utilizzando** o **importazioni** istruzione all'inizio del file di codice.  
  
 È possibile utilizzare le classi, metodi e proprietà nello spazio dei nomi Microsoft.Office.Interop.Outlook per eseguire la maggior parte delle attività di programmazione di Outlook. Per ulteriori informazioni sul modello a oggetti di Outlook, vedere [Cenni preliminari sul modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md). Per esempi di attività tipiche che si avvalgono del modello a oggetti di Outlook, vedere [soluzioni Outlook](../vsto/outlook-solutions.md).  
  
###  <a name="HandlingFormRegionEvents"></a>Gestione degli eventi dell'area del modulo  
 Il **area del modulo di Outlook** elemento aggiunge automaticamente i seguenti tre gestori eventi per i file di codice di area del modulo.  
  
|event|Descrizione|  
|-----------|-----------------|  
|FormRegionInitializing|Si verifica prima dell'inizializzazione dell'area del form. È possibile selezionare le condizioni di questo gestore eventi per determinare se l'area del modulo deve essere visualizzata in Outlook. Per ulteriori informazioni, vedere [come: Outlook impedire la visualizzazione di un'area del modulo](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|  
|FormRegionShowing|Si verifica dopo la creazione di un'istanza dell'area del modulo, ma prima della visualizzazione dell'area del modulo.|  
|FormRegionClosed|Si verifica prima della chiusura dell'area del modulo.|  
  
##  <a name="Building"></a>Compilazione del progetto  
 Quando si compila un progetto di componente aggiuntivo VSTO per Outlook contenente un'area del modulo, Visual Studio aggiunge le informazioni seguenti al Registro di sistema:  
  
-   Una chiave per ogni classe di messaggi associata a una o più aree del modulo.  
  
-   Una voce per ogni area del modulo e un valore associato che rappresenta il nome del componente aggiuntivo VSTO di Outlook.  
  
 Outlook usa queste informazioni per caricare le aree del modulo.  
  
##  <a name="Debugging"></a>Debug di un'area del modulo  
 È possibile eseguire il debug di un componente aggiuntivo VSTO di Outlook contenente un'area del modulo proprio come se si trattasse del debug di altri progetti [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. All'avvio del debugger di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Visual Studio avvia automaticamente Outlook.  
  
 Per visualizzare l'area del modulo è necessario aprire l'elemento di Outlook appropriato. Ad esempio, se un'area del modulo adiacente viene aggiunta alla fine di un elemento di posta, aprire un elemento di posta.  
  
##  <a name="Deploying"></a>Distribuzione di un'area del modulo  
 Le aree del modulo sono distribuite automaticamente con il componente aggiuntivo VSTO di Outlook associato. Non è quindi necessario eseguire un'attività particolare per distribuire un'area del modulo. Per ulteriori informazioni sulla distribuzione di componenti aggiuntivi VSTO, vedere [distribuisce una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Linee guida per la creazione delle aree di modulo di Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)|Fornisce informazioni che consentono di ottimizzare le aree del modulo ed evitare eventuali problemi.|  
|[Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo per Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Viene illustrato come creare un'area del modulo per estendere un modulo standard o personalizzato di Microsoft Office Outlook usando la **nuova area del modulo di Outlook** procedura guidata.|  
|[Associazione di un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Illustra come specificare quali elementi di Microsoft Office Outlook consentono di visualizzare un'area del modulo associando l'area del modulo alla classe di messaggio di ogni elemento.|  
|[Procedura dettagliata: progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)|Mostra come progettare un'area del modulo personalizzata che viene visualizzata come una nuova pagina nella finestra di controllo di un contatto.|  
|[Procedura dettagliata: importazione di un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Viene illustrato come progettare un'area del modulo in Microsoft Office Outlook e quindi importare l'area del modulo in un progetto di componente aggiuntivo VSTO di Outlook mediante il **nuova area del modulo di Outlook** procedura guidata.|  
|[Accesso a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)|Descrive come scrivere codice per mostrare, nascondere o modificare i controlli presenti in un'area del modulo e consentire agli utenti di eseguire il codice da altre aree del progetto usando la classe `Globals`.|  
|[Procedura: Impedire la visualizzazione di un'area del modulo in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Illustra come impedire a Microsoft Office Outlook di visualizzare un'area del modulo per un particolare elemento.|  
|Illustra come accedere all'elemento di Outlook in cui viene visualizzata un'area del modulo.|  
|[Azioni personalizzate nelle aree del modulo di Outlook](../vsto/custom-actions-in-outlook-form-regions.md)|Descrive come consentire agli utenti di rispondere a un elemento di Outlook.|  
  
  