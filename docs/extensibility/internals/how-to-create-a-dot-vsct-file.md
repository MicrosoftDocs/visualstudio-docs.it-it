---
title: 'Procedura: creare una. Il File Vsct | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b64d9b35030a18a6258de52ed0f12f9796044ba5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-vsct-file"></a>Procedura: creare una. File Vsct  
  
Esistono diversi modi per creare un file di configurazione (con estensione vsct) basato su XML di Visual Studio Command Table.  
  
-   È possibile creare un nuovo VSPackage nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modello di pacchetto.  
  
-   Il compilatore comando basato su XML di configurazione di tabella, Vsct.exe, è possibile utilizzare per generare un file da un file CTC esistente.  
  
-   È possibile utilizzare Vsct.exe per generare un file con estensione vsct da un file CTO esistente.  
  
-   È possibile creare manualmente un nuovo file con estensione vsct.  
  
 In questo argomento viene illustrato come creare manualmente un nuovo file con estensione vsct.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Per creare manualmente un nuovo file con estensione vsct  
  
1.  Avviare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2.  Nel **File** dal menu **New**, quindi fare clic su **File**.  
  
3.  Nel **modelli** riquadro, fare clic su **File XML** e quindi fare clic su **aprire**.  
  
4.  Nel **vista** menu, fare clic su **finestra proprietà** per visualizzare le proprietà del file XML.  
  
5.  Nel **proprietà** finestra, fare clic sul pulsante Sfoglia (...) la proprietà di schemi.  
  
6.  Nell'elenco di schemi XSD, selezionare lo schema vsct.xsd. Se non è nell'elenco, fare clic su **Aggiungi** e quindi individuare il file in un'unità locale. Fare clic su **OK** quando si è finito.  
  
7.  Nel file XML, digitare `<CommandTable` e quindi premere TAB. Chiudere il tag digitando `>`.  
  
     Verrà creato un file con estensione vsct base.  
  
8.  Inserire gli elementi del file XML che si desidera aggiungere, in base al [VSCT Schema](../../extensibility/vsct-xml-schema-reference.md). Per ulteriori informazioni, vedere [creazione e modifica. File Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Procedura: Creare un file con estensione vsct da un file CTC esistente  
  
È possibile creare un file con estensione vsct basato su XML da un file di origine CTC esistente della tabella comandi. In questo modo, è possibile sfruttare il nuovo basato su XML [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] formato del compilatore tabella (VSCT) del comando.  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Per creare un file con estensione vsct da un file CTC  
  
1.  Ottenere una copia del linguaggio Perl.  
  
2.  Ottenere una copia dello script Perl ConvertCTCToVSCT.pl, in genere si trova nel  *\<il percorso di installazione di Visual Studio SDK >*\visualstudiointegration\tools\bin. cartella.  
  
3.  Ottenere una copia del file di origine CTC da convertire.  
  
4.  Inserire i file nella stessa directory.  
  
5.  Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la finestra Prompt dei comandi, passare alla directory.  
  
6.  Digitare  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     dove PkgCmd.ctc è il nome del file CTC e PkgCmd.vsct è il nome del file con estensione vsct da creare.  
  
     Verrà creato un nuovo file di origine XML della tabella comandi con estensione vsct. È possibile compilare il file con Vsct.exe, il compilatore VSCT, come si farebbe con qualsiasi altro file con estensione vsct.  
  
    > [!NOTE]
    >  È possibile migliorare la leggibilità del file con estensione vsct riformattando i commenti XML.  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Procedura: Creare un file con estensione vsct da un file CTO esistente  
  
È possibile creare un file con estensione vsct basato su XML da un file CTO binario esistente. Questa operazione consente di sfruttare il nuovo formato di compilatore della tabella comandi. Questo processo funziona anche se il file CTO è stato compilato da un file CTC. È possibile modificare e compilare il file VSCT in un altro file CTO.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Per creare un file con estensione vsct da un file CTO  
  
1.  Ottenere copie del file CTO e del corrispondente file CTSYM.  
  
2.  Inserire i file nella stessa directory del compilatore vsct.exe.  
  
3.  Nel prompt dei comandi di Visual Studio, passare alla directory che contiene i file con estensione cto e ctsym.  
  
4.  Digitare **vsct.exe** *ctofilename***.cto** *vsctfilename***.vsct -S***symfilename***.ctsym**.  
  
     `ctofilename`è il nome del file CTO, `vsctfilename` è il nome del file vsct che si desidera creare, e `symfilename` è il nome del file ctsym.  
  
     Questo processo crea un nuovo file del compilatore della tabella comandi XML con estensione vsct. È possibile modificare e compilare il file con vsct.exe, il compilatore vsct, come si farebbe con qualsiasi altro file VSCT.  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Semplicemente l'aggiunta di un file con estensione vsct a un progetto non viene spostato da compilare. È necessario incorporarlo nel processo di compilazione.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Per aggiungere un file vsct per la compilazione del progetto  
  
1.  Aprire il file di progetto nell'editor. Se il progetto viene caricato, è necessario scaricare prima.  
  
2.  Aggiungere un [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) che contiene un elemento VSCTCompile, come illustrato nell'esempio seguente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     L'elemento di ResourceName deve sempre essere impostato su `Menus.ctmenu`.  
  
3.  Se il progetto contiene un file con estensione resx, aggiungere un elemento risorsa incorporata che contiene un elemento MergeWithCTO, come illustrato nell'esempio seguente.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     In questo markup deve essere all'interno dell'elemento ItemGroup che contiene risorse incorporate.  
  
4.  Aprire il file del pacchetto, in genere denominato *ProjectName*Package.cs o *ProjectName*Package.vb, nell'editor.  
  
5.  Aggiungere un attributo ProvideMenuResource alla classe del pacchetto, come illustrato nell'esempio seguente.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Il primo valore del parametro deve corrispondere al valore dell'attributo ResourceName che è definito nel file di progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [La creazione. File Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio Command Table (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)