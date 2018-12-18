---
title: 'Procedura dettagliata: Creazione di una pagina dell''applicazione SharePoint | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 33c718707ce284179b69e33677d5b29f0d4433c7
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2018
---
# <a name="walkthrough-creating-a-sharepoint-application-page"></a>Procedura dettagliata: creazione di una pagina di un'applicazione SharePoint
 
Una pagina dell'applicazione è un tipo speciale di una pagina ASP.NET. Le pagine dell'applicazione includono contenuto che viene unito con una pagina master di SharePoint. Per ulteriori informazioni, vedere [la creazione di pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Questa procedura dettagliata viene illustrato come creare una pagina dell'applicazione e quindi eseguire il debug tramite un sito di SharePoint locale. Questa pagina vengono visualizzati tutti gli elementi di ogni utente ha creato o modificato in tutti i siti nella server farm.

Questa procedura dettagliata illustra le attività seguenti:

- Creazione di un progetto SharePoint.
- Aggiunta di una pagina dell'applicazione per il progetto di SharePoint.
- Aggiunta di controlli ASP.NET per la pagina dell'applicazione.
- Aggiungere il codice dietro i controlli ASP.NET.
- La pagina dell'applicazione di test.

> [!NOTE]
> I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti

- Le edizioni supportate di Windows e SharePoint. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

## <a name="creating-a-sharepoint-project"></a>Creazione di un progetto SharePoint

Creare innanzitutto un **progetto SharePoint vuoto**. Successivamente, si aggiungerà un **pagina applicazione** elemento al progetto.

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Aprire il **nuovo progetto** finestra di dialogo espandere il **Office/SharePoint** nodo sotto il linguaggio che si desidera utilizzare e quindi scegliere il **soluzioni SharePoint** nodo.

3. Nel **Modelli Visual Studio installati** riquadro, scegliere il **SharePoint 2010 - progetto vuoto** modello. Denominare il progetto **MySharePointProject**, quindi scegliere il **OK** pulsante.

     Il **Personalizzazione guidata SharePoint** viene visualizzato. Questa procedura guidata consente di selezionare il sito che verrà utilizzato per eseguire il debug del progetto e il livello di attendibilità della soluzione.

4. Scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **fine** pulsante per accettare il sito di SharePoint locale predefinito.

## <a name="creating-an-application-page"></a>Creazione di una pagina dell'applicazione

Per creare una pagina applicazione, aggiungere un **pagina applicazione** elemento al progetto.

1. In **Esplora**, scegliere il **MySharePointProject** progetto.

2. Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.

3. Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere la **pagina dell'applicazione (solo soluzione Farm** modello.

4. Denominare la pagina **nome SearchItems**, quindi scegliere il **Aggiungi** pulsante.

     La finestra di progettazione di Visual Web Developer consente di visualizzare la pagina dell'applicazione in **origine** vista in cui è possibile visualizzare gli elementi HTML della pagina. La finestra di progettazione viene visualizzato il markup per diverse <xref:System.Web.UI.WebControls.Content> controlli. Ogni controllo è associato a un <xref:System.Web.UI.WebControls.ContentPlaceHolder> controllo definito nella pagina principale dell'applicazione predefinita.

## <a name="designing-the-layout-of-the-application-page"></a>Progettare il Layout della pagina dell'applicazione

L'elemento pagina applicazione consente di utilizzare una finestra di progettazione per aggiungere controlli ASP.NET alla pagina dell'applicazione. Questa finestra di progettazione è la stessa finestra di progettazione utilizzata in Visual Web Developer. Aggiungere un'etichetta, un elenco di pulsanti di opzione e una tabella per la **origine** visualizzazione della finestra di progettazione e quindi impostare le proprietà, come avviene quando si progetta una pagina ASP.NET standard.

1. Sulla barra dei menu scegliere **Visualizza**, **Casella degli strumenti**.

2. Nel nodo di Standard di **della casella degli strumenti**, eseguire una delle operazioni seguenti:

    - Aprire il menu di scelta rapida per il **etichetta** voce, scegliere **copia**, aprire il menu di scelta rapida per la riga sotto il **PlaceHolderMain** controllo nella finestra di progettazione, contenuto e quindi Scegliere **Incolla**.

    - Trascinare il **etichetta** articolo dal **della casella degli strumenti** nel corpo del **PlaceHolderMain** controllo contenuto.

3. Ripetere il passaggio precedente per aggiungere un **DropDownList** elemento e un **tabella** elemento il **PlaceHolderMain** controllo contenuto.

4. Nella finestra di progettazione, modificare il valore della `Text` attributo del controllo etichetta a **Mostra tutti gli elementi**.

5. Nella finestra di progettazione, sostituire il `<asp:DropDownList>` elemento con il seguente codice XML.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handling-the-events-of-controls-on-the-page"></a>Gestione degli eventi dei controlli nella pagina

Come per qualsiasi pagina ASP.NET, la gestione dei controlli in una pagina dell'applicazione. In questa procedura, gestirà la `SelectedIndexChanged` evento dell'elenco a discesa.

1. Nel **vista** menu, scegliere **codice**.

     File di codice della pagina di applicazione viene aperto nell'Editor di codice.

2. Aggiungere il metodo seguente alla classe `SearchItems`. Questo codice gestisce il <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> evento del <xref:System.Web.UI.WebControls.DropDownList> chiamando un metodo che verrà creato più avanti in questa procedura dettagliata.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Aggiungere le istruzioni seguenti all'inizio del file di codice della pagina di applicazione.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Aggiungere il metodo seguente alla classe `SearchItems`. Questo metodo scorre tutti i siti nella server farm e Cerca elementi creati o modificati dall'utente corrente.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Aggiungere il metodo seguente alla classe `SearchItems`. Questo metodo consente di visualizzare gli elementi creati o modificati dall'utente corrente nella tabella.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="testing-the-application-page"></a>La pagina dell'applicazione di test

Quando si esegue il progetto, viene aperto il sito di SharePoint e viene visualizzata la pagina dell'applicazione.

1. In **Esplora**, aprire il menu di scelta rapida per la pagina dell'applicazione e quindi scegliere **imposta come elemento di avvio**.

2. Premere il tasto F5.

     Apre il sito di SharePoint.

3. Nella pagina dell'applicazione, scegliere il **modificati dall'utente** opzione.

     La pagina dell'applicazione viene aggiornata e visualizza tutti gli elementi che è stato modificato in tutti i siti nella server farm.

4. Nella pagina dell'applicazione, scegliere **creati da me** nell'elenco.

     La pagina dell'applicazione viene aggiornata e visualizza tutti gli elementi che è stato creato in tutti i siti nella server farm.

## <a name="next-ateps"></a>Ateps successivo

Per ulteriori informazioni sulle pagine dell'applicazione di SharePoint, vedere [la creazione di pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

È possibile ottenere ulteriori informazioni sulla progettazione di contenuto di pagina di SharePoint utilizzando la finestra di progettazione Web visiva da questi argomenti:

- [Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Creazione di controlli utente riutilizzabili per Web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Vedere anche

[Procedura: Creare una pagina applicazione](../sharepoint/how-to-create-an-application-page.md)  
[Tipo di pagina applicazione layouts](http://go.microsoft.com/fwlink/?LinkID=169274)
