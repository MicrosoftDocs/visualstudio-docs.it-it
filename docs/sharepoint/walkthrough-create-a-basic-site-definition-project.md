---
title: 'Procedura dettagliata: Creare un progetto di definizione di sito di base | Documenti Microsoft'
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
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 72a99a082fb1626013be6fa0ac5c759a43fd58a7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Procedura dettagliata: Creare un progetto di definizione di sito di base
  Questa procedura dettagliata viene illustrato come creare una definizione di sito di base che contiene una Web part visiva con alcuni controlli su di esso. Per maggiore chiarezza, la Web part visiva che crei dispone solo di alcuni controlli. Tuttavia, è possibile creare definizioni di sito di SharePoint più sofisticate che includono altre funzionalità.  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   Creazione di una definizione di sito utilizzando il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modello di progetto.  
  
-   Creazione di un sito di SharePoint tramite una definizione di sito di SharePoint.  
  
-   Aggiunta di una Web part visiva alla soluzione.  
  
-   Personalizzazione della pagina del sito default.aspx aggiungendovi la nuova Web part visiva.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Microsoft Windows e SharePoint. Per ulteriori informazioni, vedere i requisiti per lo sviluppo di soluzioni di SharePoint.  
  
-   Visual Studio.  
  
## <a name="creating-a-site-definition-solution"></a>Creazione di una soluzione di definizione del sito  
 Innanzitutto, creare il progetto di definizione del sito in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-create-a-site-definition-project"></a>Per creare un progetto di definizione del sito  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**. Se l'IDE è configurato per utilizzare le impostazioni di sviluppo di Visual Basic nella barra dei menu, scegliere **File**, **nuovo progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  Espandere il **Visual c#** nodo o **Visual Basic** nodo, espandere il **SharePoint** nodo e quindi scegliere il **2010** nodo.  
  
3.  Nel **modelli** scegliere il **progetto SharePoint 2010** modello.  
  
4.  Nel **nome** immettere **TestSiteDef**, quindi scegliere il **OK** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** viene visualizzato.  
  
5.  Nel **specificare il livello di sito e di sicurezza per il debug** pagina, immettere l'URL per il sito di SharePoint in cui si desidera eseguire il debug di definizione del sito o utilizzare il percorso predefinito (http://*nome sistema*/).  
  
6.  Nel **qual è il livello di attendibilità per la soluzione SharePoint?** , scegliere il **Distribuisci come soluzione farm** pulsante di opzione.  
  
     Tutti i progetti di definizione del sito devono essere distribuiti come soluzioni farm. Per ulteriori informazioni sulle soluzioni create mediante sandbox e soluzioni farm, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Scegliere il **fine** pulsante.  
  
     Il progetto verrà visualizzato **Esplora**.  
  
8.  In **Esplora**, scegliere il nodo del progetto e quindi nella barra dei menu scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
9. In presenza di **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.  
  
10. Nel **modelli** riquadro, scegliere il **definizione sito** modello, lasciare il **nome** come **SiteDefinition1**e quindi scegliere il  **Aggiungere** pulsante.  
  
## <a name="create-a-visual-web-part"></a>Creare una Web Part visiva  
 Successivamente, creare una Web part visiva da visualizzare nella pagina principale della definizione di sito.  
  
#### <a name="to-create-a-visual-web-part"></a>Per creare una Web part visiva  
  
1.  In **Esplora**, scegliere il **Mostra tutti i file** pulsante.  
  
2.  Scegliere il **SiteDefinition1** nodo del progetto e quindi nella barra dei menu scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
3.  Espandere il **Visual c#** nodo o **Visual Basic** nodo, espandere il **SharePoint** nodo e quindi scegliere il **2010** nodo.  
  
4.  Nell'elenco dei modelli, scegliere il **Web Part visiva** modello, mantenere il valore predefinito è nome VisualWebPart1 e quindi scegliere il **Aggiungi** pulsante.  
  
     Apre il file VisualWebPart1.ascx.  
  
5.  Nella parte inferiore della VisualWebPart1.ascx, aggiungere il markup seguente per aggiungere tre controlli al form: casella di testo, un pulsante e un'etichetta:  
  
    ```  
    <table>  
      <tr>  
        <td>  
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>  
        </td>  
        <td>  
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>  
        </td>  
        <td>  
          <asp:Label runat="server" ID="lblName"></asp:Label>  
        </td>  
      </tr>  
    </table>  
    ```  
  
6.  In VisualWebPart1.ascx, aprire il file VisualWebPart1.ascx.cs (per [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) o VisualWebPart1.ascx.vb (per [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), quindi aggiungere il codice seguente:  
  
     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
     Questo codice aggiunge la funzionalità per i clic del pulsante della web part.  
  
## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Aggiungere la Web Part visiva alla pagina ASPX predefinita  
 Successivamente, aggiungere la Web part visiva pagina ASPX predefinita della definizione di sito.  
  
#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Per aggiungere una Web part visiva a pagina ASPX predefinita  
  
1.  Aprire la pagina aspx e quindi aggiungere la riga seguente sotto il `WebPartPages` tag:  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     Questa riga associa il nome MyWebPartControls con la Web part e il relativo codice. Il *Namespace* parametro corrisponde lo spazio dei nomi utilizzato nel file di codice VisualWebPart1.ascx.  
  
2.  Dopo il `</asp:Content>` elemento, sostituire l'intero `ContentPlaceHolderId="PlaceHolderMain"` sezione e il relativo contenuto con il codice seguente:  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     Questo codice crea un riferimento a Web part visiva creato in precedenza.  
  
3.  In **Esplora**, aprire il menu di scelta rapida per il **SiteDefinition1** nodo, quindi scegliere **impostato come elemento di avvio**.  
  
## <a name="deploy-and-run-the-site-definition-solution"></a>Distribuire ed eseguire la soluzione di definizione di sito  
 Successivamente, distribuire il progetto di SharePoint e quindi eseguire il progetto.  
  
#### <a name="to-deploy-and-run-the-site-definition"></a>Per distribuire ed eseguire la definizione di sito  
  
-   Nella barra dei menu, scegliere **compilare**, **distribuire TestSiteDef**.  
  
-   Premere il tasto F5.  
  
     Visual Studio compila il codice, aggiunta le relative funzionalità, tutti i file dei pacchetti in un file di soluzione (WSP) di SharePoint e consente di distribuire il file WSP di SharePoint Server. SharePoint installa i file e quindi attiva le funzionalità.  
  
## <a name="create-a-site-based-on-the-site-definition"></a>Creare un sito in base alla definizione di sito  
 Successivamente, creare un sito con la nuova definizione di sito.  
  
#### <a name="to-create-a-site-by-using-the-site-definition"></a>Per creare un sito tramite la definizione di sito  
  
1.  Nel sito di SharePoint, viene visualizzata la pagina nuovo sito di SharePoint.  
  
2.  Nel **titolo e descrizione** immettere **nuovo sito personale** per il titolo e una descrizione del sito.  
  
3.  Nel **indirizzo del sito Web** immettere **NuovoSito** nel **nome URL** casella.  
  
4.  Nel **modello** , scegliere il **personalizzazioni di SharePoint** scheda.  
  
5.  Nel **selezionare un modello** scegliere **SiteDefinition1**.  
  
6.  Lasciare le altre impostazioni in base ai valori predefiniti e quindi scegliere il **crea** pulsante.  
  
     Viene visualizzato il nuovo sito.  
  
## <a name="test-the-new-site"></a>Testare il nuovo sito  
 Testare quindi il nuovo sito per verificare se funziona correttamente.  
  
#### <a name="to-test-the-new-site"></a>Per testare il nuovo sito  
  
-   Nella pagina ASPX predefinita, immettere il testo e quindi scegliere il **Modifica etichetta di testo** pulsante accanto alla casella di testo.  
  
     Il testo viene visualizzato nell'etichetta a destra del pulsante.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)   
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  