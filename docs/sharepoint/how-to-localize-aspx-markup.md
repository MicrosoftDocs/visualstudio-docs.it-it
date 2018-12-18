---
title: 'Procedura: localizzare il Markup ASPX | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9dd127fea21a53b9a29082f536ac8c0404299c63
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-localize-aspx-markup"></a>Procedura: localizzare il markup ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagine (con estensione aspx) usano in genere i valori stringa a livello di codice. Per localizzare le stringhe, sostituirli con espressioni che fanno riferimento alle risorse localizzate.  
  
## <a name="localizing-aspx-markup"></a>Localizzazione Markup ASPX  
  
#### <a name="to-localize-aspx-markup"></a>Per localizzare il markup ASPX  
  
1.  Aggiungere file di risorse separati: uno per la lingua predefinita e uno per ogni lingua localizzata.  
  
     Se si localizza solo il markup e non di codice, aggiungere un elemento di progetto di File di risorse globali. Se si localizza codice e markup, aggiungere un elemento di progetto di File di risorse.  
  
    1.  Per aggiungere un File di risorse globali in **Esplora**, aprire il menu di scelta rapida per un elemento di progetto SharePoint e quindi scegliere **Aggiungi**, **nuovo elemento**. In SharePoint **2010** nodo, scegliere il **File di risorse globali** modello.  
  
    2.  Per aggiungere un File di risorse, in **Esplora**, aprire il menu di scelta rapida per un elemento di progetto SharePoint e quindi scegliere **Aggiungi**, **nuovo elemento**. Sotto il **Visual Basic** o **Visual c#** nodo, scegliere il **File di risorse** modello.  
  
    > [!NOTE]  
    >  Assicurarsi di aggiungere i file di risorse a un elemento di progetto SharePoint per abilitare la proprietà del tipo di distribuzione. Questa proprietà è necessario più avanti in questa procedura. Se la soluzione non dispone di un elemento di progetto SharePoint, è possibile aggiungere un progetto SharePoint vuoto e rimuovere il file Elements.xml predefinito.  
  
2.  Assegnare il file di risorse di lingua predefinita di un nome di propria scelta con estensione resx, ad esempio MyAppResources. Utilizzare lo stesso nome base per ogni file di risorse localizzato, ma aggiungere l'[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] delle impostazioni cultura. Assegnare un nome, ad esempio, una risorsa localizzata tedesca MyAppResources.de-de.  
  
3.  Modificare il valore della **tipo di distribuzione** proprietà di ogni file di risorse per **AppGlobalResource** per cartella App_GlobalResources del server.  
  
4.  Se si utilizzano le risorse per localizzare il codice oltre al markup ASPX, lasciare il valore di **azione di compilazione** proprietà di ogni file come **risorsa incorporata**. Se si utilizza i file di risorse solo per localizzare il markup, è possibile modificare facoltativamente il valore della proprietà dei file **contenuto**. Per ulteriori informazioni, vedere [localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Aprire ogni file di risorse e aggiungere le stringhe localizzate, utilizzando la stessa stringa ID in ogni file.  
  
6.  Nel [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] markup per la pagina ASPX o di un controllo, sostituire le stringhe hardcoded con i valori che utilizzano il formato seguente:  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Per localizzare il testo per un controllo etichetta in una pagina applicazione, ad esempio, sarebbe modificare:  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     in  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  Premere il tasto F5 per compilare ed eseguire l'applicazione.  
  
8.  In SharePoint, modificare la lingua di visualizzazione da quello predefinito.  
  
     Le stringhe localizzate visualizzata nell'applicazione. Per visualizzare le risorse localizzate, il server di SharePoint deve disporre di un language pack installati che corrispondono alle impostazioni cultura del file di risorse.  
  
## <a name="see-also"></a>Vedere anche  
 [Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Procedura: localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)   
 [Procedura: aggiungere un File di risorse](../sharepoint/how-to-add-a-resource-file.md)   
 [Procedura: Localizzare il codice](../sharepoint/how-to-localize-code.md)  
  
  