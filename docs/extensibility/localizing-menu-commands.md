---
title: Localizzazione dei comandi di Menu | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4fd8f2b42464b31c71b2983dd3e5c66f4a03351
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="localizing-menu-commands"></a>Localizzazione dei comandi di Menu
È possibile fornire il testo localizzato per menu e barra degli strumenti dei comandi di creazione di file con estensione vsct localizzato e localizzata per il pacchetto VSPackage e quindi aggiornare i file di progetto incorporare le modifiche in file con estensione resx.  
  
 Per informazioni su come localizzare l'esperienza di installazione, vedere [localizzazione pacchetti VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>I nomi dei comandi di localizzazione  
 Nei pacchetti VSPackage i comandi di menu e pulsanti della barra degli strumenti sono definiti nel file vsct.  
  
1.  In **Esplora**, modificare il nome del file con estensione vsct da *filename*vsct a *filename*.en-us.aspx US.vsct.  
  
2.  Creare una copia di *filename*. en-US.vsct per ogni lingua localizzata.  
  
     Nome di ogni copia *filename*. *Impostazioni locali*vsct, in cui *internazionali* è un nome di impostazioni cultura specifiche. Per un elenco di valori di nome delle impostazioni cultura, vedere [ID impostazioni locali assegnati da Microsoft](https://msdn.microsoft.com/en-us/library/windows/apps/jj657969.aspx).  
  
     Questi *filename*. *Impostazioni locali*file vsct conterrà il testo del menu localizzata per il pacchetto.  
  
3.  Aprire ogni *filename*. *Impostazioni locali*file vsct per localizzare il testo.  
  
    1.  Modificare il [ButtonText](../extensibility/buttontext-element.md) elemento i valori come appropriato per la lingua particolare.  
  
    2.  Se si fornirà icone localizzate, modificare il [Bitmap](../extensibility/bitmap-element.md) valori in modo che punti ai file di destinazione.  
  
     L'esempio seguente mostra l'inglese e spagnolo testo del pulsante per un comando per aprire una finestra degli strumenti dell'albero genealogico Explorer.  
  
     [FamilyTree.en US.vsct]  
  
    ```xml  
    <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <Icon guid="guidImages" id="bmpPic2" />  
      <Strings>  
        <CommandName>cmdidFamilyTree</CommandName>  
        <ButtonText>Family Tree Explorer</ButtonText>  
      </Strings>  
    </Button>  
    ```  
  
     [FamilyTree.es ES.vsct]  
  
    ```xml  
    <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <Icon guid="guidImages" id="bmpPic2" />  
      <Strings>  
        <CommandName>cmdidFamilyTree</CommandName>  
        <ButtonText>Explorar el arbol genealogico</ButtonText>  
      </Strings>  
    </Button>  
  
    ```  
  
## <a name="localizing-other-text-resources"></a>Altre risorse di testo (localizzazione)  
 Risorse di testo diversi da nomi di comando sono definite nel file di risorse (resx).  
  
1.  Rinominare VSPackage.resx VSPackage.en-us.  
  
2.  Creare una copia del file VSPackage.en-us per ogni lingua localizzata.  
  
     Nome di ogni copia del pacchetto VSPackage. *Delle impostazioni locali*. resx, in cui *internazionali* è un nome di impostazioni cultura specifiche.  
  
3.  Rinominare Resources. resx in Resources. en-us.  
  
4.  Creare una copia del file resources. en-us per ogni lingua localizzata.  
  
     Nome di ogni copia di risorse. *Delle impostazioni locali*. resx, in cui *internazionali* è un nome di impostazioni cultura specifiche.  
  
5.  Aprire ogni file con estensione resx per modificare i valori stringa come appropriato per la lingua particolare. Nell'esempio seguente viene illustrata la definizione di risorsa localizzata per la barra del titolo di una finestra degli strumenti.  
  
     [Resources. en-US]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-es. resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Incorporare le risorse localizzate nel progetto  
 È necessario modificare il file assemblyinfo.cs e il file di progetto per incorporare le risorse localizzate.  
  
1.  Dal **proprietà** nodo **Esplora**, aprire file assemblyinfo.cs o AssemblyInfo. vb nell'editor.  
  
2.  Aggiungere la voce seguente.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Consente di impostare l'inglese come lingua predefinita.  
  
3.  Scaricare il progetto.  
  
4.  Aprire il file di progetto nell'editor.  
  
5.  Individuare il `ItemGroup` elemento contenente `EmbeddedResource` elementi.  
  
6.  Nel `EmbeddedResource` elemento che chiama VSPackage.en-us, sostituire il `ManifestResourceName` elemento con un `LogicalName` elemento, impostato su `VSPackage.en-US.Resources`, come indicato di seguito.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Per ogni lingua localizzata, copiare il `EmbeddedResource` elemento per VsPackage.en-US, quindi impostare il **Include** attributo e **LogicalName** elemento della copia per le impostazioni locali di destinazione, come illustrato di seguito esempio.  
  
8.  A ogni localizzata `VSCTCompile` elemento, aggiungere un `ResourceName` elemento che punta a `Menus.ctmenu`, come illustrato nell'esempio seguente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Salvare il file di progetto e ricaricare il progetto.  
  
10. Compilare il progetto.  
  
     Crea un assembly principale e gli assembly di risorse per ogni lingua. Per informazioni sulla localizzazione il processo di distribuzione, vedere [localizzazione pacchetti VSIX](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)   
 [Confronto tra oggetti MenuCommand e OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)   
 [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)