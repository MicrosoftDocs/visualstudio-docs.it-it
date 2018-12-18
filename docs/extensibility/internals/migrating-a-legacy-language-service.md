---
title: La migrazione di un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 412b09016a3f889e0d6c5e40ff75895d5ae8ff48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="migrating-a-legacy-language-service"></a>La migrazione di un servizio di linguaggio Legacy
È possibile eseguire la migrazione di un servizio di linguaggio legacy a una versione successiva di Visual Studio l'aggiornamento del progetto e l'aggiunta di un file vsixmanifest al progetto. Il servizio di linguaggio stesso continuerà a funzionare come prima, poiché l'editor di Visual Studio consente di adattare il.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul programma per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a usare il nuovo editor di API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>La migrazione di una soluzione di servizio di linguaggio di Visual Studio 2008 a una versione successiva  
 La procedura seguente viene illustrato come adattare un esempio di Visual Studio 2008 denominato RegExLanguageService. È possibile trovare in questo esempio in un'installazione di Visual Studio 2008 SDK, il *il percorso di installazione di Visual Studio SDK*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ cartella.  
  
> [!IMPORTANT]
>  Se il servizio di linguaggio non definisce i colori, è necessario impostare esplicitamente <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> a `true` nel pacchetto VSPackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Per eseguire la migrazione di un servizio di linguaggio di Visual Studio 2008 a una versione successiva  
  
1.  Installare le versioni più recenti di Visual Studio e Visual Studio SDK. Per ulteriori informazioni sui modi per installare il SDK, vedere [l'installazione di Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Modificare il file RegExLangServ.csproj (senza caricarlo in Visual Studio.  
  
     Nel `Import` nodo che fa riferimento al file Microsoft.VsSDK.targets, sostituire il valore con il testo seguente.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  Salvare il file e chiuderlo.  
  
4.  Aprire la soluzione RegExLangServ.sln.  
  
5.  Il **aggiornamento unidirezionale** verrà visualizzata la finestra. Fare clic su **OK**.  
  
6.  Aggiornare le proprietà del progetto. Aprire il **le proprietà del progetto** selezionando il nodo del progetto nel **Esplora**facendo e selezionando **proprietà**.  
  
    -   Nel **applicazione** modificare **framework di destinazione** a **4.6.1**.  
  
    -   Nel **Debug** nella scheda il **Avvia programma esterno** digitare  **\<il percorso di installazione di Visual Studio > \Common7\IDE\devenv.exe.**.  
  
         Nel **argomenti della riga di comando** digitare /**/rootsuffix Exp**.  
  
7.  Aggiornare i riferimenti seguenti:  
  
    -   Rimuovere il riferimento a Microsoft.VisualStudio.Shell.9.0.dll, quindi aggiungere i riferimenti a Microsoft.VisualStudio.Shell.14.0.dll e Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    -   Rimuovere il riferimento a Microsoft.VisualStudio.Package.LanguageService.9.0.dll, quindi aggiungere un riferimento a Microsoft.VisualStudio.Package.LanguageService.14.0.dll.  
  
    -   Aggiungere un riferimento a Microsoft.VisualStudio.Shell.Interop.10.0.dll.  
  
8.  Aprire il file VsPkg.cs e modificare il valore della `DefaultRegistryRoot` attributo  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. L'esempio originale non consente di registrare il servizio di linguaggio, pertanto è necessario aggiungere il seguente attributo VsPkg.cs.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. È necessario aggiungere un file vsixmanifest.  
  
    -   Copiare questo file da un'estensione esistente alla directory del progetto. (Per ottenere questo file consiste nel creare un progetto VSIX (in **File**, fare clic su **New**, quindi fare clic su **progetto**. Fare clic in Visual Basic o c# **estendibilità**, quindi selezionare **progetto VSIX**.)  
  
    -   Aggiungere il file al progetto.  
  
    -   Il file **proprietà**, impostare **azione di compilazione** a **Nessuno**.  
  
    -   Aprire il file con il **Editor Manifest VSIX**.  
  
    -   Modificare i campi seguenti:  
  
    -   **ID**: RegExLangServ  
  
    -   **Nome del prodotto**: RegExLangServ  
  
    -   **Descrizione**: un servizio di linguaggio di espressioni regolari.  
  
    -   In **asset**, fare clic su **New**, selezionare il **tipo** a **Microsoft.VisualStudio.VsPackage**, impostare il **origine** a **un progetto nella soluzione corrente**, quindi impostare il **progetto** a **RegExLangServ**.  
  
    -   Salvare e chiudere il file.  
  
11. Compilare la soluzione. I file compilati vengono distribuiti a **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**.  
  
12. Avviare il debug. Aprire una seconda istanza di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md)