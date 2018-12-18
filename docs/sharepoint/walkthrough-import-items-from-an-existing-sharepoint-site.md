---
title: 'Procedura dettagliata: Importare gli elementi da un sito di SharePoint esistente | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b9d1bcc72bd22e7c528b2a3d8752d15b7005fea5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Procedura dettagliata: importare gli elementi da un sito di SharePoint esistente
  Questa procedura dettagliata viene illustrato come importare elementi da un sito di SharePoint esistente in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto SharePoint.  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   Personalizzazione di un sito di SharePoint tramite l'aggiunta di una colonna di sito personalizzato (noto anche come un *campo*.  
  
-   Esportazione di un sito di SharePoint in un file con estensione wsp.  
  
-   L'importazione del file con estensione wsp in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint tramite il progetto di importazione con estensione wsp.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Le edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="customizing-a-sharepoint-site"></a>Personalizzazione di un sito di SharePoint  
 Per questo esempio, si verrà creare e personalizzare un sito secondario di SharePoint aggiungendovi una nuova colonna del sito e la creazione di un altro sito secondario per un utilizzo successivo. Verrà successivamente, esportare il primo sito secondario in un file con estensione wsp e quindi importare la colonna di sito personalizzato il secondo sito secondario tramite il progetto di importazione con estensione wsp.  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>Per creare e personalizzare un sito di SharePoint  
  
1.  Aprire un sito di SharePoint utilizzando un Web browser, ad esempio http://*nome sistema*/SitePages/Home.aspx.  
  
2.  Creare un sito secondario dal sito di SharePoint principale aprendo il **Azioni sito** menu e scegliendo **nuovo sito**.  
  
3.  Il sito **crea** finestra di dialogo scegliere la **sito vuoto** tipo.  
  
4.  Nel **titolo** immettere **prova colonna sito 1**, nel **nome URL** immettere **columntest1**; lasciare le altre impostazioni in base all'impostazione predefinita valori. e quindi scegliere il **crea** pulsante.  
  
5.  Dopo la creazione del sito, passare nel browser al sito principale, http://*nome sistema*/SitePages/Home.aspx.  
  
6.  Nuovamente, creare un sito secondario vuoto dal sito di SharePoint principale aprendo il **Azioni sito** menu, scegliendo **nuovo sito**e quindi scegliendo il **sito vuoto** tipo.  
  
7.  Nel **titolo** immettere **prova colonna sito 2**, nel **nome URL** immettere **columntest2**; lasciare le altre impostazioni in base all'impostazione predefinita valori. e quindi scegliere il **crea** pulsante.  
  
8.  Tornare al primo sito secondario, http://*NomeSistema*/columntest1/default.aspx.  
  
9. Nel **Azioni sito** menu, scegliere **Impostazioni sito** per visualizzare la pagina Impostazioni sito.  
  
10. Nel **raccolte** , scegliere il **colonne sito** collegamento.  
  
11. Nella parte superiore del **Raccolta colonne del sito** pagina, scegliere il **crea** pulsante.  
  
12. Nel **nome di colonna** immettere **colonna Test**, mantenere gli altri valori predefiniti e quindi scegliere il **OK** pulsante.  
  
13. Il **colonna Test** colonna viene visualizzata sotto le colonne personalizzate intestazione nella raccolta di colonne del sito.  
  
## <a name="exporting-the-sharepoint-site"></a>Esportare il sito di SharePoint  
 Successivamente, ottenere un file di installazione (con estensione wsp) di SharePoint che contiene i elementi di SharePoint e gli elementi che si desidera importare i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto SharePoint. Se si dispone già di un file con estensione wsp, è necessario crearne uno da un sito di SharePoint esistente. Per questo esempio, si esporterà il sito di SharePoint predefinito in un file con estensione wsp.  
  
> [!IMPORTANT]  
>  Se si riceve un errore di runtime di eseguire la procedura seguente, è necessario eseguire la procedura in un sistema che ha accesso al sito di SharePoint.  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>Per esportare un sito di SharePoint esistente  
  
1.  Nel sito di SharePoint, scegliere **Impostazioni sito** sul **Azioni sito** scheda per visualizzare la pagina Impostazioni sito.  
  
2.  Nel **Azioni sito** sezione della pagina Impostazioni sito, scegliere il **sito Salva come modello** collegamento.  
  
3.  Nel **nome File** immettere **ExampleSite**e il **nome modello** immettere **esempio del sito**.  
  
4.  Per questo esempio, lasciare il **includono contenuto** casella di controllo.  
  
     Se si seleziona questa casella, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Salva tutti gli elenchi e raccolte documenti e il relativo contenuto nel file con estensione wsp. Anche se ciò è utile in alcuni casi, non è necessaria per questo esempio.  
  
5.  Quando l'operazione viene completata correttamente, scegliere il **raccolta soluzioni** collegamento per visualizzare il file con estensione wsp.  
  
     Per visualizzare la pagina Raccolta soluzioni successive, aprire il **Azioni sito** menu, scegliere **Impostazioni sito**, scegliere il **Vai alle impostazioni di sito di livello superiore** sul collegamento nel  **Amministrazione raccolta siti** sezione e quindi scegliere il **soluzioni** collegare il **raccolte** sezione.  
  
6.  Nella raccolta di soluzioni, scegliere il **ExampleSite** collegamento.  
  
7.  Nel **Download del File** finestra di dialogo scegliere la **salvare** pulsante per salvare il file nel sistema locale, per impostazione predefinita, nella cartella di download.  
  
## <a name="importing-the-wsp-file"></a>L'importazione del File con estensione wsp  
 Ora che si dispone di un file con estensione wsp contiene un elemento che si desidera riutilizzare (la colonna di prova di colonna di sito personalizzato), importare il file con estensione wsp per accedervi.  
  
#### <a name="to-import-a-wsp-file"></a>Per importare un file con estensione wsp  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sulla barra dei menu, scegliere **File**, **New**, **progetto** per visualizzare il **nuovo progetto** la finestra di dialogo. Se l'IDE è configurato per utilizzare le impostazioni di sviluppo di Visual Basic nella barra dei menu, scegliere **File**, **nuovo progetto**.  
  
2.  Espandere il **SharePoint** nodo sotto **Visual c#** o **Visual Basic**, quindi scegliere il **2010** nodo.  
  
3.  Scegliere il **Importa pacchetto di soluzione SharePoint 2010** modello il **modelli** riquadro, lasciare il nome del progetto WspImportProject1 e quindi scegliere il **OK** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** viene visualizzato.  
  
4.  Nel **specificare il livello di sito e di sicurezza per il debug** pagina, immettere il [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] per il secondo sito secondario di SharePoint creato in precedenza. Si aggiungerà il nuovo personalizzato, elemento campo http://*nome sistema*/columntest2, a tale sito secondario.  
  
5.  Nel **qual è il livello di attendibilità per la soluzione SharePoint?** sezione, lasciare la selezione come **Distribuisci come soluzione creata mediante sandbox**.  
  
6.  Nel **specificare l'origine del nuovo progetto** pagina, passare al percorso nel sistema in cui è stato salvato il file con estensione wsp in precedenza e quindi scegliere il **Avanti** pulsante.  
  
    > [!NOTE]  
    >  Se si sceglie il **fine** verranno importati in questa pagina, tutti gli elementi disponibili nel file con estensione wsp.  
  
7.  Nel **selezionare gli elementi da importare** deselezionare tutte le caselle di controllo nell'elenco, ad eccezione di **colonna Test**, quindi scegliere il **fine** pulsante.  
  
     Poiché l'elenco contiene molti elementi, è possibile scegliere di Ctrl + tasti per selezionare tutti gli elementi nell'elenco, scegliere la barra spaziatrice per cancellare tutte le caselle di controllo e quindi selezionare la casella di controllo accanto al **colonna Test** elemento.  
  
     Al termine dell'operazione di importazione, un nuovo progetto denominato **WspImportProject1** creato che contiene una cartella denominata **campi**. In questa cartella è la colonna di sito personalizzato **colonna Test** e il file di definizione Elements.  
  
## <a name="deploying-the-project"></a>La distribuzione del progetto  
 Infine, distribuire **WspImportProject1** sito secondario per il secondo SharePoint creata in precedenza per visualizzare la colonna di sito personalizzato.  
  
#### <a name="to-deploy-the-project"></a>Per distribuire il progetto  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], premere il tasto F5 per distribuire ed eseguire il progetto di importazione con estensione wsp.  
  
2.  Nel sito di SharePoint, aprire il **Azioni sito** menu, quindi scegliere **Impostazioni sito** per visualizzare la pagina Impostazioni sito.  
  
3.  Nel **raccolte** , scegliere il **colonne sito** collegamento.  
  
4.  Scorrere verso il basso il **colonne personalizzate** sezione.  
  
     Si noti che la colonna di sito personalizzato che è stato importato dal primo sito di SharePoint viene visualizzato nell'elenco.  
  
## <a name="see-also"></a>Vedere anche  
 [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Creazione di controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  