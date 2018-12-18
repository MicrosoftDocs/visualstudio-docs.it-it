---
title: Aggiunta di un Menu alla barra dei Menu di Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a391da85c38176d79a1c77ce8836ce510e8d27e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Aggiunta di un Menu alla barra dei Menu di Visual Studio
Questa procedura dettagliata viene illustrato come aggiungere un menu alla barra dei menu dell'ambiente di sviluppo integrato (IDE) di Visual Studio. Barra dei menu IDE contiene le categorie di menu, ad esempio **File**, **modifica**, **vista**, **finestra**, e **Guida** .  
  
 Prima di aggiungere un nuovo menu alla barra dei menu di Visual Studio, è consigliabile se i comandi devono essere inseriti all'interno di un menu esistente. Per ulteriori informazioni sul posizionamento di comando, vedere [menu e comandi di Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).  
  
 I menu vengono dichiarati nel file vsct del progetto. Per ulteriori informazioni sui menu e i file con estensione vsct, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Completando questa procedura dettagliata, è possibile creare un menu denominato **TestMenu** che contiene un unico comando.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Creazione di un progetto VSIX che include un modello di elemento di comando personalizzata  
  
1.  Creare un progetto VSIX denominato `TopLevelMenu`. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c#** / **estendibilità**.  Per ulteriori informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato denominato **TestCommand**. Nel **Esplora**del mouse sul nodo del progetto e scegliere **Aggiungi / nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo, passa a **Visual c# / Extensibility** e selezionare **comando personalizzato**. Nel **nome** campo nella parte inferiore della finestra, modificare il nome del file di comando in **TestCommand.cs**.  
  
## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Creazione di un Menu nella barra dei Menu IDE  
  
#### <a name="to-create-a-menu"></a>Per creare un menu  
  
1.  In **Esplora**, aprire TestCommandPackage.vsct.  
  
     Alla fine del file, vi è un \<simboli > nodo che contiene diversi \<GuidSymbol > nodi. Nel nodo denominato guidTestCommandPackageCmdSet, aggiungere un nuovo simbolo, come segue:  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  Creare un oggetto vuoto \<menu > nodo il \<comandi > nodo appena prima \<gruppi >. Nel \<menu > nodo, aggiungere un \<Menu > nodo, come indicato di seguito:  
  
    ```xml  
    <Menus>  
          <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">  
            <Parent guid="guidSHLMainMenu"  
                    id="IDG_VS_MM_TOOLSADDINS" />  
            <Strings>  
              <ButtonText>TestMenu</ButtonText>  
              <CommandName>TestMenu</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Il `guid` e `id` valori del menu specificano il set di comandi e menu specifico nel set di comandi.  
  
     Il `guid` e `id` i valori dell'elemento padre di posizionare il menu nella sezione della barra dei menu di Visual Studio che contiene i menu Strumenti e componenti aggiuntivi.  
  
     Il valore di `CommandName` stringa specifica che il testo deve essere incluso nella voce di menu.  
  
3.  Nel \<gruppi >, quindi individuare il \<gruppo > e modificare il \<padre > elemento in modo che punti al menu di cui è stato appena aggiunto:  
  
    ```csharp  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     In questo modo la parte del gruppo del nuovo menu.  
  
4.  Trovare il `Buttons` sezione. Si noti che il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ha generato il modello di pacchetto un `Button` elemento con il relativo elemento padre impostata su `MyMenuGroup`. Di conseguenza, questo comando verrà visualizzato nel menu.  
  
## <a name="building-and-testing-the-extension"></a>Compilazione e test dell'estensione  
  
1.  Compilare il progetto e avviare il debug. Dovrebbe essere visualizzata un'istanza dell'istanza sperimentale.  
  
2.  Barra dei menu nell'istanza sperimentale deve contenere un **TestMenu** menu.  
  
3.  Nel **TestMenu** menu, fare clic su **richiamare comando Test**.  
  
     Una finestra di messaggio dovrà essere visualizzato e visualizzare il messaggio "TestCommand pacchetto all'interno di TopLevelMenu.TestCommand.MenuItemCallback()". Ciò indica che il nuovo comando funziona.  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)