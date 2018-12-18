---
title: 'Procedura dettagliata: Creazione di una Web Part per SharePoint tramite una finestra di progettazione | Documenti Microsoft'
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
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 28be854f01234783ff9873753eb88ca92bc192d6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer"></a>Procedura dettagliata: creazione di una web part per SharePoint tramite una finestra di progettazione
  Se si crea una web part per un sito di SharePoint, gli utenti possono modificare direttamente il contenuto, l'aspetto e il comportamento delle pagine del sito utilizzando un browser. Questa procedura dettagliata viene illustrato come creare una web part visivamente tramite SharePoint **Web Part visiva** modello di progetto in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Consente di visualizzare la web part che verrà creata una visualizzazione di calendario mensile e una casella di controllo per ogni elenco di calendario nel sito. Gli utenti possono specificare quali elenchi di includere nella visualizzazione del calendario mensile selezionando le caselle di controllo calendario.  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di una web part tramite il **Web Part visiva** modello di progetto.  
  
-   Progettazione della web part tramite la finestra di progettazione di Visual Web Developer in Visual Studio.  
  
-   Aggiungere il codice per gestire gli eventi dei controlli web part.  
  
-   Test della web part in SharePoint.  
  
    > [!NOTE]  
    >  Il computer potrebbe essere diversi nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente per Visual Studio nelle istruzioni seguenti. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Le edizioni supportate di Windows e SharePoint. Vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]o versione successiva.  
  
## <a name="creating-a-web-part-project"></a>Creazione di un progetto di web part  
 Creare innanzitutto un progetto di web part tramite il **Web Part visiva** modello di progetto.  
  
#### <a name="to-create-a-visual-web-part-project"></a>Per creare un progetto di Web Part visiva  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilizzando il **Esegui come amministratore** opzione.  
  
2.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
3.  Nel **nuovo progetto** in presenza di una finestra di dialogo **Visual c#** o **Visual Basic**, espandere **Office/SharePoint**, quindi scegliere il  **Le soluzioni SharePoint** categoria.  
  
4.  Nell'elenco dei modelli, scegliere il **SharePoint 2013 - Web Part visiva** modello, quindi scegliere il **OK** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** viene visualizzato. Utilizzare questa procedura guidata, è possibile specificare il sito che si utilizzerà per eseguire il debug del progetto e il livello di attendibilità della soluzione.  
  
5.  Nel **qual è il livello di attendibilità per la soluzione SharePoint?** , scegliere il **Distribuisci come soluzione farm** pulsante di opzione.  
  
6.  Scegliere il **fine** pulsante per accettare il sito di SharePoint locale predefinito.  
  
## <a name="designing-the-web-part"></a>Progettazione di web part  
 Progettare la web part aggiungendo i controlli dal **della casella degli strumenti** nell'area della finestra di progettazione di Visual Web Developer.  
  
#### <a name="to-design-the-layout-of-the-web-part"></a>Per progettare il layout della web part  
  
1.  Nella finestra di progettazione di Visual Web Developer scegliere il **progettazione** tab per passare alla visualizzazione progettazione.  
  
2.  Sulla barra dei menu scegliere **Visualizza**, **Casella degli strumenti**.  
  
3.  Nel **Standard** nodo del **della casella degli strumenti**, scegliere il **CheckBoxList** controllare e quindi effettuare una delle operazioni seguenti:  
  
    -   Aprire il menu di scelta rapida per il **CheckBoxList** di controllo, scegliere **copia**, aprire il menu di scelta rapida per la prima riga nella finestra di progettazione e quindi scegliere **Incolla**.  
  
    -   Trascinare il **CheckBoxList** controllo il **della casella degli strumenti**e connettere il controllo per la prima riga nella finestra di progettazione.  
  
4.  Ripetere il passaggio precedente, ma spostare un pulsante alla riga successiva della finestra di progettazione.  
  
5.  Nella finestra di progettazione, scegliere il **Button1** pulsante.  
  
6.  Nella barra dei menu, scegliere **vista**, **finestra proprietà**.  
  
     Il **proprietà** verrà visualizzata la finestra.  
  
7.  Nel **testo** proprietà del pulsante, immettere **aggiornamento**.  
  
## <a name="handling-the-events-of-controls-on-the-web-part"></a>Gestione degli eventi dei controlli web part  
 Aggiungere il codice che consente all'utente di aggiungere calendari alla visualizzazione del calendario master.  
  
#### <a name="to-handle-events-of-controls-on-the-web-part"></a>Per gestire gli eventi dei controlli web part  
  
1.  Eseguire una delle procedure seguenti:  
  
    -   Nella finestra di progettazione, fare doppio clic su di **aggiornamento** pulsante.  
  
    -   Nel **proprietà** finestra per il **aggiornamento** pulsante, scegliere il **eventi** pulsante. Nel **fare clic su** proprietà, immettere **Button1_Click**e quindi premere INVIO.  
  
     Il file di codice del controllo utente verrà aperto nell'Editor di codice e `Button1_Click` gestore eventi viene visualizzato. Successivamente, verrà aggiunto il codice a questo gestore eventi.  
  
2.  Aggiungere le istruzioni seguenti all'inizio del file di codice del controllo utente.  
  
     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
3.  Aggiungere la seguente riga di codice per la `VisualWebPart1` classe. Questo codice dichiara un controllo calendario mensile.  
  
     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]  
  
4.  Sostituire il `Page_Load` metodo la `VisualWebPart1` classe con il codice seguente. Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Aggiunge una visualizzazione di calendario mensile per il controllo utente.  
  
    -   Aggiunge una casella di controllo per ogni elenco calendario nel sito.  
  
    -   Specifica un modello per ogni tipo di elemento che viene visualizzato nella visualizzazione del calendario.  
  
     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]  
  
5.  Sostituire il `Button1_Click` metodo la `VisualWebPart1` classe con il codice seguente. Questo codice aggiunge gli elementi da ogni calendario selezionato alla visualizzazione del calendario master.  
  
     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]  
  
## <a name="testing-the-web-part"></a>Test della web part  
 Quando si esegue il progetto, viene aperto il sito di SharePoint. La web part viene automaticamente aggiunto alla raccolta Web Part in SharePoint. Per questo progetto di test, verranno eseguite le attività seguenti:  
  
-   Aggiungere un evento a ognuno dei due elenchi di calendario separato.  
  
-   Aggiungere la web part a una pagina web part.  
  
-   Specificare gli elenchi da includere nella visualizzazione del calendario mensile.  
  
#### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Per aggiungere eventi agli elenchi di calendario nel sito  
  
1.  In Visual Studio, premere il tasto F5.  
  
     Apre il sito di SharePoint e [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] in questa pagina è visualizzato sulla barra Avvio veloce.  
  
2.  Sulla barra Avvio veloce in **Elenca**, scegliere il **calendario** collegamento.  
  
     Il **calendario** verrà visualizzata la pagina.  
  
     Se si alcun collegamento di calendario viene visualizzato sulla barra Avvio veloce, scegliere il **contenuto del sito** collegamento. Se la pagina di contenuto del sito non è presente un **calendario** elemento, crearne uno.  
  
3.  Nella pagina del calendario, scegliere un giorno e quindi scegliere il **Aggiungi** collegamento nel giorno selezionato per aggiungere un evento.  
  
4.  Nel **titolo** immettere **evento nel calendario predefinito**, quindi scegliere il **salvare** pulsante.  
  
5.  Scegliere il **contenuto del sito** collegamento e quindi scegliere il **aggiungere un'app** riquadro.  
  
6.  Nel **crea** pagina, scegliere il **calendario** tipo, denominare il calendario e quindi scegliere il **crea** pulsante.  
  
7.  Aggiungere un evento per il nuovo calendario, assegnare il nome dell'evento **evento nel calendario personalizzato**, quindi scegliere il **salvare** pulsante.  
  
#### <a name="to-add-the-web-part-to-a-web-part-page"></a>Per aggiungere la web part a una pagina web part  
  
1.  Nel **contenuto del sito** pagina, aprire il **pagine del sito** cartella.  
  
2.  Sulla barra multifunzione, scegliere il **file** scheda, aprire il **nuovo documento** menu e quindi scegliere il **pagina Web Part** comando.  
  
3.  Nel **nuova pagina Web Part** pagina, denominare la pagina **SampleWebPartPage.aspx**, quindi scegliere il **crea** pulsante.  
  
     Verrà visualizzata la pagina web part.  
  
4.  Nell'area superiore della pagina web part, scegliere il **inserire** scheda e quindi scegliere il **Web Part** pulsante.  
  
5.  Scegliere il **personalizzato** cartella, scegliere il **VisualWebPart1** web part e quindi scegliere il **Aggiungi** pulsante.  
  
     La web part verrà visualizzata la pagina. I controlli seguenti vengono visualizzati nella web part:  
  
    -   Una visualizzazione di calendario mensile.  
  
    -   Un **aggiornamento** pulsante.  
  
    -   Oggetto **calendario** casella di controllo.  
  
    -   Oggetto **calendario personalizzato** casella di controllo.  
  
#### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Per specificare gli elenchi da includere nella visualizzazione del calendario mensile  
  
1.  Nella web part, specificare calendari che si desidera includere nella visualizzazione del calendario mensile e quindi scegliere il **aggiornamento** pulsante.  
  
     Gli eventi da tutti i calendari specificati vengono visualizzati nella visualizzazione del calendario mensile.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Procedura: creare una Web Part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Procedura: creare una Web Part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Procedura dettagliata: creazione di una web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)  
  
  