---
title: Organizzare gli oggetti in contenitori di layout nella finestra di progettazione XAML | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 9c7b9c8f0f36435c2595a5df648daa54a614e278
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Organizzare gli oggetti in contenitori nella finestra di progettazione XAML
Si supponga di voler impostare la posizione degli oggetti, quali immagini, pulsanti e video, in una pagina. È probabile che si preferisca organizzarli in righe e colonne, su un'unica riga disposti orizzontalmente o verticalmente o impostare per ognuno una posizione fissa.  
  
 Dopo aver dedicato tempo all'organizzazione degli oggetti nella pagina, è possibile passare alla scelta di un pannello di layout. Inizialmente in tutte le pagine è presente un pannello di layout in quanto viene usato per aggiungervi gli oggetti. Il pannello di layout predefinito è di tipo **Grid**, ma è possibile modificarlo.  
  
 I pannelli di layout non vengono però usati unicamente per organizzare gli oggetti in una pagina, ma anche per progettare tenendo conto di risoluzioni e dimensioni dello schermo diverse. Quando gli utenti eseguono l'app, tutti gli elementi presenti in un pannello di layout vengono ridimensionati in base all'area dello schermo del dispositivo. Se si preferisce che gli elementi non vengano ridimensionati, è ovviamente possibile disattivare questo comportamento per una parte o per l'intero layout, usando a tale scopo le proprietà height e width.  
  
 Oltre a una descrizione dei pannelli e dei controlli di layout disponibili, questa pagina include i collegamenti a brevi video introduttivi su questi elementi.  
  
> [!NOTE]
>  Alcuni dei video possono fare riferimento a Blend o Expression Blend, che usano la stessa finestra di progettazione XAML di Visual Studio e Blend per Visual Studio.  
  
## <a name="layout-panels"></a>Pannelli di layout  
 Per definire inizialmente la pagina, scegliere uno dei seguenti pannelli di layout. La pagina può comunque contenere più pannelli di layout. Si può infatti iniziare con un pannello di layout di tipo **Grid** e quindi aggiungerne uno di tipo **StackPanel** a un'area del pannello **Grid** in modo da disporre i controlli verticalmente in tale elemento.  
  
 I seguenti pannelli di layout sono quelli più usati, ma ne esistono altri. Tutti i controlli sono disponibili nel pannello **Asset**.  
  
-   [Griglia](#Grid)  
  
-   [UniformGrid](#Uniform)  
  
-   [Canvas](#Canvas)  
  
-   [StackPanel](#Stack)  
  
-   [WrapPanel](#Wrap)  
  
-   [DockPanel](#Dock)  
  
###  <a name="Grid"></a> Grid  
 Consente di disporre gli oggetti in righe e colonne.  
  
 ![](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png "98b234b2-ac3b-441f-9136-98375fee87b7")  
  
 **Vedere un breve video:** ![Configure Installed Features] (Configurare le funzionalità installate)(../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Using Grids](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids) (Uso delle griglie).  
  
###  <a name="Uniform"></a> UniformGrid  
 Consente di disporre gli oggetti in aree della griglia uguali o uniformi. Questo pannello è molto utile per definire la disposizione di un elenco di immagini.  
  
 ![](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png "928b9284-a7e8-4678-875a-656b80b78076")  
  
 (Disponibile solo per i progetti WPF)  
  
 **Vedere un breve video:** ![Configure Installed Features] (Configurare le funzionalità installate)(../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with a UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid) (Uso di UniformGrid).  
  
###  <a name="Canvas"></a> Canvas  
 Consente di disporre gli oggetti nel modo desiderato. Quando gli utenti eseguono l'app, a questi elementi verranno assegnate posizioni fisse sullo schermo.  
  
 ![](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png "e1ae27f0-3a57-454e-b580-877dcea8836d")  
  
 **Vedere un breve video:** ![Configure Installed Features] (Configurare le funzionalità installate)(../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with the canvas](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas) (Uso di canvas).  
  
###  <a name="Stack"></a> StackPanel  
 Consente di disporre gli oggetti su un'unica riga orizzontalmente o verticalmente.  
  
 ![](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png "a85a7b57-b0a8-495e-b985-f0291e41d093")  
  
 **Vedere un breve video:** ![Configure Installed Features] (Configurare le funzionalità installate)(../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with StackPanel and WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel) (Uso di StackPanel e WrapPanel).  
  
###  <a name="Wrap"></a> WrapPanel  
 Consente di disporre gli oggetti in modo sequenziale da sinistra verso destra. Quando il pannello esaurisce lo spazio all'estremità destra, *esegue il wrapping* del contenuto sulla riga successiva e così via da sinistra verso destra e dall'alto verso il basso. È anche possibile impostare per un pannello di questo tipo l'orientamento verticale in modo che gli oggetti vengano spostati dall'alto verso il basso e da sinistra verso destra.  
  
 (Disponibile solo per i progetti WPF)  
  
 ![](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png "b1c415fb-9a32-4a18-aa0b-308fca994ac9")  
  
 **Vedere un breve video:** ![Configure Installed Features] (Configurare le funzionalità installate)(../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with StackPanel and WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel) (Uso di StackPanel e WrapPanel).  
  
###  <a name="Dock"></a> DockPanel  
 È anche possibile disporre gli oggetti in modo che rimangano *ancorati* a un bordo del pannello.  
  
 (Disponibile solo per i progetti WPF)  
  
 ![](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png "72d46b58-9a49-4dd5-8af7-6843c0440226")  
  
 **Vedere un breve video:** ![Configure Installed Features] (Configurare le funzionalità installate)(../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [WPF - DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo).  
  
## <a name="layout-controls"></a>Controlli di layout  
 È possibile aggiungere oggetti anche ai controlli di layout, che pur includendo un minor numero di funzionalità rispetto a un pannello di layout, possono risultare utili per determinati scenari.  
  
 I seguenti controlli di layout sono quelli più usati, ma ne esistono altri. Tutti i controlli sono disponibili nel pannello **Asset**.  
  
-   [Bordo](#Border)  
  
-   [Popup](#Popup)  
  
-   [ScrollViewer](#Scroll)  
  
-   [UniformGrid](#Uniform)  
  
-   [Viewbox](#View)  
  
###  <a name="Border"></a> Border  
 Consente di creare un bordo, uno sfondo o entrambi intorno a un oggetto. È possibile aggiungere un solo oggetto a un controllo **Border**. Per applicare un bordo o uno sfondo a più oggetti, aggiungere a **Border** il pannello di layout, quindi aggiungere gli oggetti al pannello o al controllo.  
  
 ![](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png "e761238b-99fd-43c5-bbc4-57538b8289ff")  
  
 **Vedere un breve video:** ![Configure Installed Features] (Configurare le funzionalità installate)(../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with Borders](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders) (Uso di bordi).  
  
###  <a name="Popup"></a> Popup  
 Consente di visualizzare informazioni o opzioni destinate agli utenti in una finestra. È possibile aggiungere un solo oggetto a un controllo **Popup**. Per impostazione predefinita, un controllo **Popup** contiene un pannello di layout **Grid**, ma è possibile modificare questa impostazione.  
  
###  <a name="Scroll"></a> ScrollViewer  
 Consente agli utenti di scorrere verso il basso in una pagina o un'area di una pagina. Dal momento che è possibile aggiungere un solo oggetto a un controllo **ScrollViewer**, è preferibile aggiungere un pannello di layout, come **Grid** o **StackPanel**.  
  
 ![](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png "06b326d4-f23d-41a6-b26b-e1aff37572a7")  
  
###  <a name="View"></a> Viewbox  
 Consente di ridimensionare gli oggetti come con un controllo zoom. È possibile aggiungere un solo oggetto a un controllo **Viewbox**. Se si vuole applicare questo effetto a più oggetti, aggiungere un pannello di layout a **ViewBox** e quindi aggiungere i controlli a tale pannello.  
  
 (Disponibile solo per i progetti WPF)  
  
 ![](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png "f5b13c66-d918-4141-8a16-bd8f8628687a")  
  
## <a name="see-also"></a>Vedere anche  
 [Working with elements in XAML Designer](../designers/working-with-elements-in-xaml-designer.md)   
 [Creazione di un'interfaccia utente tramite la finestra di progettazione XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)