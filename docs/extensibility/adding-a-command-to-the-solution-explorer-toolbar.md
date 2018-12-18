---
title: L'aggiunta di un comando alla barra degli strumenti Esplora soluzione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6f732900ff3e73decb1dc01d5c131e26ba50669
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>L'aggiunta di un comando alla barra degli strumenti di Esplora soluzioni
Questa procedura dettagliata viene illustrato come aggiungere un pulsante per la **Esplora** barra degli strumenti.  
  
 Qualsiasi comando in una barra degli strumenti o un menu viene chiamato un pulsante in Visual Studio. Quando si fa clic sul pulsante, viene eseguito il codice nel gestore del comando. In genere, i comandi correlati vengono raggruppati insieme per formare un gruppo. Barre degli strumenti o menu fungono da contenitori per i gruppi. La priorità determina l'ordine in cui vengono visualizzati i singoli comandi in un gruppo nel menu o sulla barra degli strumenti. È possibile impedire che un pulsante visualizzato sulla barra degli strumenti o nel menu controllando la visibilità. Un comando che è elencato in un `<VisibilityConstraints>` sezione del file con estensione vsct viene visualizzato solo nel contesto associato. La visibilità non può essere applicata ai gruppi.  
  
 Per ulteriori informazioni sui menu, i comandi della barra degli strumenti e i file con estensione vsct, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
>  Utilizzare i file di tabella comandi XML (con estensione vsct) anziché i file di configurazione (CTC) nella tabella di comando per definire l'aspetto di menu e comandi in VSPackage. Per altre informazioni, vedere [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Creazione di un'estensione con un comando di Menu  
 Creare un progetto VSIX denominato `SolutionToolbar`. Aggiungere un modello di elemento di comando di menu denominato **ToolbarButton**. Per informazioni su come eseguire questa operazione, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>Aggiunta di un pulsante alla barra degli strumenti di Esplora soluzioni  
 In questa sezione della procedura dettagliata viene illustrato come aggiungere un pulsante per la **Esplora** barra degli strumenti. Quando si fa clic sul pulsante, viene eseguito il codice nel metodo di callback.  
  
1.  Nel file ToolbarButtonPackage.vsct, passare al `<Symbols>` sezione. Il `<GuidSymbol>` nodo contiene il gruppo di menu e comandi che è stato generato dal modello di pacchetto. Aggiungere un `<IDSymbol>` elemento per questo nodo per dichiarare il gruppo che conterrà il comando.  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  Nel `<Groups>` sezione, dopo la voce di gruppo esistente, definire il nuovo gruppo che è stato dichiarato nel passaggio precedente.  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     Impostare l'elemento padre coppia GUID: ID `guidSHLMainMenu` e `IDM_VS_TOOL_PROJWIN` assegna questo gruppo per il **Esplora soluzioni** inserisce dopo altri gruppi di comandi della barra degli strumenti e impostare un valore di priorità alta.  
  
3.  Nel `<Buttons>` sezione, modificare l'ID padre dell'oggetto generato `<Button>` voce in modo da riflettere il gruppo definito nel passaggio precedente. Modificato `<Button>` elemento dovrebbe essere simile al seguente:  
  
    ```xml  
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">  
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPicStrikethrough" />  
        <Strings>  
            <ButtonText>Invoke ToolbarButton</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
4.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.  
  
     Il **Esplora** barra degli strumenti deve visualizzare il nuovo pulsante di comando a destra dei pulsanti esistenti. L'icona del pulsante è il barrato.  
  
5.  Fare clic sul pulsante nuovo.  
  
     Finestra di dialogo che è presente il messaggio **ToolbarButtonPackage all'interno di SolutionToolbar.ToolbarButton.MenuItemCallback()** deve essere visualizzato.  
  
## <a name="controlling-the-visibility-of-a-button"></a>Controllare la visibilità di un pulsante  
 In questa sezione della procedura dettagliata viene illustrato come controllare la visibilità di un pulsante sulla barra degli strumenti. Impostando un contesto per uno o più progetti nel `<VisibilityConstraints>` sezione del file SolutionToolbar.vsct, si limita un pulsante deve essere visualizzato solo quando uno o più progetti aperti.  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Per visualizzare un pulsante quando uno o più progetti aperti.  
  
1.  Nel `<Buttons>` sezione di ToolbarButtonPackage.vsct, aggiungere due flag dei comandi esistente `<Button>` elemento, tra il `<Strings>` e `<Icons>` tag.  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     Il `DefaultInvisible` e `DynamicVisibility` flag devono essere impostati pertanto che le voci nel `<VisibilityConstraints>` sezione diventino effettive.  
  
2.  Creare un `<VisibilityConstraints>` sezione che presenta due `<VisibilityItem>` voci. Inserire la nuova sezione subito dopo la chiusura `</Commands>` tag.  
  
    ```xml  
    <VisibilityConstraints>  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasSingleProject" />  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasMultipleProjects" />  
    </VisibilityConstraints>  
    ```  
  
     Ogni elemento visibilità rappresenta una condizione in cui viene visualizzato il pulsante specificato. Per applicare più condizioni, è necessario creare più voci per lo stesso pulsante.  
  
3.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.  
  
     Il **Esplora** barra degli strumenti non contiene il pulsante barrato.  
  
4.  Aprire una soluzione contenente un progetto.  
  
     Pulsante Barrato viene visualizzato sulla barra degli strumenti a destra del pulsante esistente.  
  
5.  Nel **File** menu, fare clic su **Chiudi soluzione**. Il pulsante viene rimosso dalla barra degli strumenti.  
  
 La visibilità del pulsante è controllata da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fino a quando non viene caricato il pacchetto VSPackage. Dopo aver caricato il pacchetto VSPackage, la visibilità del pulsante è controllata dal pacchetto VSPackage.  Per ulteriori informazioni, vedere [tra oggetti MenuCommand e. OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)