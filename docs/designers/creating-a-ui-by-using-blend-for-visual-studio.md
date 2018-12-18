---
title: Creazione di un'interfaccia utente usando Blend per Visual Studio
ms.date: 07/17/2017
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8c7c5ab82c45ed183b8e6a6ae2031b50e2a086c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Creazione di un'interfaccia utente usando Blend per Visual Studio

Blend per Visual Studio consente di progettare applicazioni Windows e Web basate su XAML. Offre la stessa esperienza di progettazione XAML di base disponibile in Visual Studio e aggiunge finestre di progettazione visive per attività avanzate, quali animazioni e comportamenti. Per un confronto tra Blend e Visual Studio, vedere [Progettazione di XAML in Visual Studio e Blend per Visual Studio](../designers/designing-xaml-in-visual-studio.md).

Blend per Visual Studio è un componente di Visual Studio. Per installare Blend, nel **programma di installazione di Visual Studio** scegliere il carico di lavoro **Sviluppo di app per la piattaforma UWP (Universal Windows Platform)** o **Sviluppo per desktop .NET**. Entrambi questi carichi di lavoro includono il componente Blend per Visual Studio.

![Componenti del carico di lavoro UWP](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Componenti del carico di lavoro Sviluppo per desktop .NET](media/installer-dotnet-desktop.png)

Se non si ha familiarità con Blend per Visual Studio, dedicare alcuni minuti all'esame delle funzionalità specifiche dell'area di lavoro. In questo argomento è disponibile una breve panoramica.

> [!NOTE]
> Per una panoramica delle funzionalità di progettazione, ad esempio la tavola da disegno, la finestra Struttura documento e la finestra Dispositivo, vedere [Creazione di un'interfaccia utente tramite la finestra di progettazione XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="tour-of-the-tools-panel"></a>Panoramica del pannello Strumenti

È possibile usare il pannello **Strumenti** in Blend per Visual Studio per creare e modificare oggetti nell'applicazione. Per creare oggetti, si seleziona lo strumento e si disegna sulla tavola da disegno con il mouse.

![Pannello Strumenti](../designers/media/blend5toolspanel.png "Blend5Toolspanel")

|||||
|-|-|-|-|
|![](../designers/media/b1_1.png "B1_1")|**Strumenti di selezione** Selezionare oggetti e percorsi.<br /><br /> Usare lo strumento **Selezione diretta** per selezionare gli oggetti annidati e i segmenti di percorso.|![Callout A](../designers/media/b5_label_a.png "b5_label_A")|**Strumenti Sfumatura e tratto**|
|![](../designers/media/b1_2.png "B1_2")|**Strumenti di visualizzazione** Consente di modificare la visualizzazione della tavola da disegno, ad esempio per la panoramica e lo zoom.|![Callout B](../designers/media/b5_label_b.png "b5_label_B")|**Strumenti per i tracciati**|
|![](../designers/media/b1_3.png "B1_3")|**Strumenti per i pennelli** Consente di usare gli attributi visivi di un oggetto, ad esempio cambiare un pennello, disegnare un oggetto o selezionare gli attributi di un oggetto da applicare a un altro oggetto.|![Callout C](../designers/media/b5_label_c.png "b5_label_C")|**Strumenti per le forme**|
|![](../designers/media/b1_4.png "B1_4")|**Strumenti per gli oggetti** Consente di disegnare gli oggetti più comuni sulla tavola da disegno, ad esempio tracciati, forme, pannelli di layout, testo e controlli.|![Callout D](../designers/media/b5_label_d.png "b5_label_D")|**Pannelli di layout**|
|![](../designers/media/b1_5.png "B1_5")|**Strumenti per gli asset** Consente di accedere al pannello **Assets** e visualizzare l'ultimo asset usato nella libreria.|![Callout E](../designers/media/b5_label_e.png "b5_label_E")|**Controlli testo**|
|||![Callout F](../designers/media/b5_label_f.png "b5_label_F")|**Controlli comuni**|

**Vedere un breve video:** ![Configure Installed Features] (Configurare le funzionalità installate)(../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Barra degli strumenti](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).

## <a name="tour-of-the-assets-panel"></a>Panoramica del pannello Asset

Tutti i controlli sono disponibili nel pannello **Assets**, che è simile alla **Casella degli strumenti** in Visual Studio. Oltre ai controlli, nel pannello **Asset** è disponibile tutto ciò che può essere aggiunto alla tavola da disegno, inclusi gli stili, gli elementi multimediali, i comportamenti e gli effetti.

![Pannello Asset](../designers/media/blend5_assets_panel.png "Blend5_Assets_panel")

|||
|-|-|
|![](../designers/media/b1_1.png "B1_1")|**Casella di ricerca** Digitare testo nella casella **Cerca** per filtrare l'elenco di asset.|
|![](../designers/media/b1_2.png "B1_2")|**Modalità griglia e Modalità elenco** Consente di passare dalla visualizzazione **Modalità griglia** alla visualizzazione **Modalità elenco** e viceversa.|
|![](../designers/media/b1_3.png "B1_3")|**Categorie di asset** Fare clic su una categoria o sottocategoria per visualizzare l'elenco di asset corrispondente.|
|![](../designers/media/b1_4.png "B1_4")|**Stili** Consente di visualizzare tutti gli stili disponibili nel dizionario risorse.|
|![](../designers/media/b1_5.png "B1_5")|**Descrizione** Consente di visualizzare una descrizione della categoria o sottocategoria di asset selezionata.|

## <a name="tour-of-the-objects-and-timeline-panel"></a>Panoramica del pannello Oggetti e sequenza temporale

Usare questo pannello per organizzare gli oggetti nella tavola da disegno e, se si vuole, per animarli.

![Pannello Oggetti e sequenza temporale in modalità animazione](../designers/media/b5_object_timeline_animation.png "b5_object_timeline_animation")

|||
|-|-|
|![](../designers/media/b1_1.png "B1_1")|**Visualizzazione Oggetti** Consente di visualizzare una struttura ad albero visuale di un documento. È possibile accedere a diversi livelli di dettaglio. È anche possibile aggiungere livelli per organizzare ulteriormente gli oggetti nella tavola da disegno. In questo modo è possibile bloccarli e nasconderli come gruppi.|
|![](../designers/media/b1_2.png "B1_2")|**Indicatore della modalità di registrazione** Consente di verificare se è in corso la registrazione delle modifiche delle proprietà in una sequenza temporale.|
|![](../designers/media/b1_3.png "B1_3")|**Selezione storyboard** Consente di visualizzare un elenco degli storyboard creati.|
|![](../designers/media/b1_4.png "B1_4")|**Chiudere lo storyboard** Consente di chiudere lo storyboard corrente.|
|![](../designers/media/b1_5.png "B1_5")|**Opzioni di storyboard** Consente di creare, duplicare, invertire, eliminare, rinominare o chiudere uno storyboard.|
|![](../designers/media/b1_6.png "B1_6")|**Controlli di riproduzione** Consente di esplorare la sequenza temporale. Per spostarsi nella sequenza temporale, o *eseguire lo scrubbing*, è anche possibile trascinare l'indicatore di riproduzione.|
|![](../designers/media/b1_7.png "B1_7")|**Reimposta l'ambito** Consente di reimpostare l'ambito della visualizzazione oggetti sull'oggetto radice o ambito precedente. È possibile solo quando si modifica uno stile o modello.|
|![](../designers/media/b1_8.png "B1_8")|**Registra fotogramma chiave** Consente di registrare uno snapshot delle proprietà dell'oggetto selezionato nell'istante corrente.|
|![](../designers/media/b1_9.png "B1_9")|**Opzioni snapping** Consente di impostare l'allineamento della sequenza temporale, la risoluzione di snap e disattivare l'allineamento della sequenza temporale.|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Mostra/Nascondi**, **Blocca/Sblocca** Consente di visualizzare o nascondere le opzioni di visibilità e blocco della visualizzazione degli oggetti.|
|![](../designers/media/b1_11.png "B1_11")|**Posizione indicatore di riproduzione nella sequenza temporale** Consente di visualizzare il tempo corrente in millisecondi. In questo campo è possibile immettere direttamente un valore di tempo per passare a un istante specifico. La precisione dipende dalla risoluzione di snap impostata in **Opzioni snapping**.|
|![](../designers/media/b1_12.png "B1_12")|**Indicatore di riproduzione** Consente di determinare il punto temporizzato in cui si trova l'animazione. L'indicatore di riproduzione può essere trascinato lungo la sequenza temporale per visualizzare l'animazione in anteprima.|
|![](../designers/media/b1_13.png "B1_13")|**Fotogrammi chiave impostati su sequenze temporali** Consente di modificare un valore di proprietà in un istante specifico.|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Modifica dell'ordine degli oggetti** Consente di impostare l'ordine di visualizzazione degli oggetti. Fare clic su questo pulsante per disporre gli oggetti nella visualizzazione struttura secondo l'ordine Z (da primo a ultimo) o in base all'ordine di markup, ovvero l'ordine in cui compaiono nella visualizzazione **XAML**.|
|![](../designers/media/b1_15.png "B1_15")|**Zoom sequenza temporale** Consente di impostare la risoluzione di zoom della sequenza temporale. Lo zoom avanti permette di modificare un'animazione a un maggior livello di dettaglio, mentre lo zoom indietro permette di ottenere una panoramica del comportamento di un'animazione su periodi di tempo più lunghi. Se si applica lo zoom avanti, ma non è possibile impostare un fotogramma chiave nella posizione corrispondente all'istante desiderato, verificare che la risoluzione di snap sia sufficientemente elevata.|
|![Callout 16](../designers/media/b5_label_16.png "b5_label_16")|**Area di composizione della sequenza temporale** Consente di visualizzare la sequenza temporale e spostare i fotogrammi chiave trascinandoli o usando i relativi menu di scelta rapida.|

## <a name="tour-of-the-properties-panel"></a>Panoramica del pannello Proprietà

Usare questo pannello per visualizzare e modificare le proprietà di un oggetto. È anche possibile impostarle direttamente sulla tavola da disegno. In questo caso, le modifiche alle proprietà si rifletteranno nel pannello **Proprietà**.

![Pannello Proprietà](../designers/media/blend5_properties_panel.png "Blend5_properties_panel")

**Categorie** Consente di espandere e comprimere le categorie delle proprietà. Fare clic su **Espandi** ![](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png "6375953d-074c-421a-bbb3-6f5055b67b64") e **Comprimi** ![Comprimi](../designers/media/b5_collapse_button.png "b5_collapse_button") per visualizzare o nascondere i dettagli della categoria.

|||
|-|-|
|![](../designers/media/b1_1.png "B1_1")|**Nome e tipo** Consente di visualizzare l'icona, il nome e il tipo dell'oggetto selezionato.|
|![](../designers/media/b1_2.png "B1_2")|**Disponi per** Consente di ordinare alfabeticamente le proprietà per nome, database di origine o categoria.|
|![](../designers/media/b1_3.png "B1_3")|**Proprietà dei pennelli** Consente di configurare le proprietà visive dei pennelli, ad esempio riempimento, tratto e primo piano.|
|![](../designers/media/b1_4.png "B1_4")|**Editor dei colori** Consente di usare pennelli a tinta unita e con sfumatura.|
|![](../designers/media/b1_5.png "B1_5")|**Selezione colori** Consente di selezionare un colore.|
|![](../designers/media/b1_6.png "B1_6")|**Caselle del colore** Consente di visualizzare il colore iniziale, il colore corrente e l'ultimo colore|
|![](../designers/media/b1_7.png "B1_7")|**Contagocce** Consente di usare il colore di qualsiasi elemento sullo schermo. Il **Contagocce colore** è disponibile quando è selezionato il **pennello tinta unita**. Il **Contagocce sfumatura** è disponibile quando è selezionato il **pennello sfumatura**.|
|![](../designers/media/b1_8.png "B1_8")|**Proprietà ed eventi** Consente di impostare le proprietà o scegliere gli eventi per un elemento selezionato.|
|![](../designers/media/b1_9.png "B1_9")|**Casella di ricerca** Consente di cercare le proprietà. Filtrare le proprietà visualizzate digitando nella casella **Cerca**.|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Schede Editor del pennello**. Consente di selezionare un editor del pennello. È possibile scegliere **Nessun pennello**, **Pennello tinta unita**, **Pennello sfumato**, **Pennello tessera** o **Risorsa pennello**.|
|![](../designers/media/b1_11.png "B1_11")|**Risorse colore** Consente di applicare lo stesso colore a proprietà diverse. La scheda **Risorse colore** include **Risorse locali** e **Risorse di sistema**.|
|![](../designers/media/b1_12.png "B1_12")|**Spazio colori RGB** Consente di modificare il colore cambiando i valori per gli editor di numero **R**, **G** o **B** (rosso, verde, blu).|
|![](../designers/media/b1_13.png "B1_13")|**Canale alfa** Consente di modificare il valore alfa usando l'editor di numero accanto ad **A**.|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Converti colore in risorsa** Consente di convertire il colore selezionato in una risorsa di colore. Le risorse di colore sono disponibili quando si fa clic sulla scheda Risorse colore.|
|![](../designers/media/b1_15.png "B1_15")|**Valore hex** Consente di visualizzare il valore esadecimale del colore visualizzato.|
|![Callout 16](../designers/media/b5_label_16.png "b5_label_16")|**Cursore sfumatura** Viene visualizzato solo se è selezionato un pennello sfumato.|
|![](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png "d50027a1-6824-4ad8-8b4e-558b0756dcf8")|**Mostra proprietà avanzate** Consente di visualizzare le categorie di proprietà che vengono usate meno.|

**Vedere un breve video:** ![Configure Installed Features] (Configurare le funzionalità installate)(../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Pannello Proprietà](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).

## <a name="see-also"></a>Vedere anche

- [Inserire i controlli e modificarne il comportamento](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)
- [Animare oggetti](../designers/animate-objects-in-xaml-designer.md)
- [Disegnare forme e tracciati](../designers/draw-shapes-and-paths.md)
- [Progettazione di XAML in Visual Studio e Blend per Visual Studio](../designers/designing-xaml-in-visual-studio.md)