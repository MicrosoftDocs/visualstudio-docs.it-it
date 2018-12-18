---
title: Inserire i controlli e modificarne il comportamento nella finestra di progettazione XAML | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 09eb82bede66b839b7b3facdb61d8fc5d3ed2bd0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Inserire i controlli e modificarne il comportamento in XAML Designer
I controlli consentono agli utenti di interagire con l'app. È possibile usarli per raccogliere informazioni e per eseguire azioni come animare un oggetto o eseguire query su un'origine dati.  
  
 **Contenuto dell'argomento:**  
  
-   [Aggiungere controlli alla tavola da disegno](#Insert)  
  
-   [Impostare i controlli per l'esecuzione di operazioni](#Modify)  
  
##  <a name="Insert"></a> Aggiungere controlli alla tavola da disegno  
 È possibile trascinare controlli dal pannello **Asset** nella **tavola da disegno**e quindi modificarli nella finestra **Proprietà** .  
  
 ![Blend &#45; Assets &#45; FlipView](../designers/media/blend_assetsflipview_xaml.png "blend_AssetsFlipView_XAML")  
  
 Questi video illustrano come usare alcuni dei controlli più comuni.  
  
|Control|Breve video:|  
|-------------|-------------------------|  
|`Menu` ![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c-0b2b-4253-ac57-b86fcb8c9591")|![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Aggiungere i controlli](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|  
|`Button` ![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779-a68f-436b-b834-a91b7995a3ec")|![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Disegnare un pulsante](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|  
|`Textblock` ![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963-00f7-4a33-abcd-b0849edebada")|![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Aggiungere immagini a un blocco di testo](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|  
|`Slider` ![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92-3c74-4218-815c-e98c930ac189")|![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Compilare un dispositivo di scorrimento con una descrizione comando](http://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|  
|`GridSplitter` ![](../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be")|![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Usare un controllo GridSplitter](http://msdn.microsoft.com/expression/cc188687.aspx)|  
  
### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Creare un controllo da un'immagine, una forma o un percorso  
 È possibile trasformare qualsiasi oggetto in un controllo.  
  
 ![Blend Make Into Control dialog box](../designers/media/blend_makeintocontrol_xaml.png "blend_MakeIntoControl_XAML")  
  
 Immaginare, ad esempio, l'immagine di un televisore al centro di una pagina. È possibile creare controlli da piccole immagini simili ai pulsanti del televisore per consentire agli utenti di cambiare canale facendo clic su questi pulsanti  
  
 che di fatto sono controlli. Grazie ai controlli è possibile rispondere alle interazioni dell'utente, in questo caso quando l'utente fa clic su un pulsante.  
  
 Per creare un controllo, selezionare un oggetto. Scegliere quindi **Crea controllo** dal menu **Strumenti**.  
  
##  <a name="Modify"></a> Impostare i controlli per l'esecuzione di operazioni  
 I controlli possono eseguire azioni durante le interazioni degli utenti, ad esempio possono avviare un'animazione, aggiornare un'origine dati o riprodurre un video.  
  
 Per impostare i controlli per l'esecuzione di operazioni, usare *trigger*, *comportamenti*ed *eventi* .  
  
### <a name="triggers"></a>trigger  
 Un *trigger* modifica una proprietà o esegue un'attività in risposta a un evento o a una modifica in un'altra proprietà. Ad esempio, è possibile modificare il colore di un pulsante al passaggio del mouse.  
  
 ![The "Triggers" panel](../designers/media/custom_button_blend_propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
 **Vedere un breve video:** ![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Aggiungere un trigger di proprietà](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).  
  
### <a name="behaviors"></a>comportamenti  
 Un *comportamento* è un pacchetto di codice riutilizzabile che consente di eseguire altre operazioni oltre alla modifica delle proprietà, ad esempio di eseguire query su un servizio dati. Blend include una piccola raccolta di comportamenti, ma è possibile aggiungerne altri. Trascinare un comportamento su un oggetto qualsiasi nella tavola da disegno e quindi personalizzare il comportamento impostando le proprietà.  
  
 ![FluidMoveBehavior in the Properties panel](../designers/media/b4_fluidmovebehaviorproperties_sample.png "b4_FluidMoveBehaviorProperties_Sample")  
  
 **Vedere un breve video:** ![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Suggerimenti sulla fusione: introduzione all'uso dei comportamenti Parte 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).  
  
### <a name="events"></a>Eventi  
 Per la massima flessibilità è possibile gestire un *evento*. Sarà necessario scrivere codice.  
  
 **Vedere un breve video:** ![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Aggiungere un evento mouse](https://www.youtube.com/watch?v=2PMxAlb-x_E).