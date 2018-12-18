---
title: 'Procedura dettagliata: Creazione di un SDK tramite C++ | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 33880dc3b9c359798c47c666debc3d5564524794
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Procedura dettagliata: Creazione di un SDK tramite C++
Questa procedura dettagliata viene illustrato come creare una libreria C++ nativa matematiche SDK, pacchetto SDK come un Visual Studio Extension (VSIX) e quindi utilizzarlo per creare un'app. La procedura dettagliata è suddivisa in questi passaggi:  
  
-   [Per creare il nativo e le librerie di Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Per creare il progetto di estensione NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Per creare un'app di esempio che utilizza la libreria di classi](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Per creare il nativo e le librerie di Windows Runtime  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2.  Nell'elenco dei modelli, espandere **Visual C++**, **universali di Windows**, quindi selezionare il **DLL (app di Windows universale)** modello. Nel **nome** specificare `NativeMath`, quindi scegliere il **OK** pulsante.  
  
3.  Aggiornare NativeMath.h affinché corrisponda al codice seguente.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Aggiornare NativeMath.cpp corrispondano questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  In **Esplora**, aprire il menu di scelta rapida per **soluzione 'NativeMath'**, quindi scegliere **Aggiungi**, **nuovo progetto**.  
  
6.  Nell'elenco dei modelli, espandere **Visual C++**, quindi selezionare il **componente Windows Runtime** modello. Nel **nome** specificare `NativeMathWRT`, quindi scegliere il **OK** pulsante.  
  
7.  Aggiornare Class1 corrispondano questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Aggiornare Class1.cpp in modo che corrisponda a questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
##  <a name="createVSIX"></a> Per creare il progetto di estensione NativeMathVSIX  
  
1.  In **Esplora**, aprire il menu di scelta rapida per **soluzione 'NativeMath'**, quindi scegliere **Aggiungi**, **nuovo progetto**.  
  
2.  Nell'elenco dei modelli, espandere **Visual c#**, **estendibilità**, quindi selezionare **progetto VSIX**. Nel **nome** specificare **NativeMathVSIX**, quindi scegliere il **OK** pulsante.
  
3.  In **Esplora**, aprire il menu di scelta rapida per **vsixmanifest**, quindi scegliere **Visualizza codice**.  
  
4.  Utilizzare il seguente codice XML per sostituire il codice XML esistente.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5.  In **Esplora**, aprire il menu di scelta rapida per il **NativeMathVSIX** del progetto e quindi scegliere **Aggiungi**, **nuovo elemento**.  
  
6.  Nell'elenco di **elementi di Visual c#**, espandere **dati**, quindi selezionare **File XML**. Nel **nome** specificare `SDKManifest.xml`, quindi scegliere il **OK** pulsante.  
  
7.  Utilizzare questo codice XML per sostituire il contenuto del file:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
8. In **Esplora**nella **NativeMathVSIX** del progetto, creare la struttura di cartelle:  
  
    ```  
  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
9. In **Esplora**, aprire il menu di scelta rapida per **soluzione 'NativeMath'**, quindi scegliere **Apri cartella in Esplora File**.  
  
10. In **Esplora File**, $SolutionRoot$\NativeMath\NativeMath.h, copiare e quindi in **Esplora**nel **NativeMathVSIX** del progetto, incollarlo nel $SolutionRoot$ \ Cartella NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\.  
  
     Copiare $SolutionRoot$\Debug\NativeMath\NativeMath.lib e quindi incollarlo nella cartella \NativeMathVSIX\DesignTime\Debug\x86\ $SolutionRoot$.  
  
     Copiare $SolutionRoot$\Debug\NativeMath\NativeMath.dll e incollarlo nella cartella \NativeMathVSIX\Redist\Debug\x86\ $SolutionRoot$.  
  
     Copiare $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll e incollarlo nella cartella \NativeMathVSIX\Redist\Debug\x86 $SolutionRoot$.  
  
     Copiare $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd e incollarlo nella cartella \NativeMathVSIX\References\CommonConfiguration\Neutral $SolutionRoot$.  
  
     Copiare $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri e incollarlo nella cartella \NativeMathVSIX\References\CommonConfiguration\Neutral $SolutionRoot$.  
  
11. Nella cartella \NativeMathVSIX\DesignTime\Debug\x86\ $ $SolutionRoot, creare un file di testo denominato NativeMathSDK.props e quindi incollare il contenuto seguente in essa contenuti:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
12. Nella barra dei menu, scegliere **vista**, **altre finestre**, **finestra proprietà** (tastiera: premere il tasto F4).  
  
13. In **Esplora**, selezionare il **NativeMathWRT.winmd** file. Nel **proprietà** finestra, modifica il **azione di compilazione** proprietà **contenuto**e quindi modificare il **Includi in VSIX** proprietà  **True**.  
  
     Ripetere questo processo per il **NativeMath.h** file.  
  
     Ripetere questo processo per il **NativeMathWRT.pri** file.  
  
     Ripetere questo processo per il **NativeMath.Lib** file.  
  
     Ripetere questo processo per il **NativeMathSDK.props** file.  
  
14. In **Esplora**, selezionare il **NativeMath.h** file. Nel **proprietà** finestra, modifica il **Includi in VSIX** proprietà **True**.  
  
     Ripetere questo processo per il **NativeMath.dll** file.  
  
     Ripetere questo processo per il **NativeMathWRT.dll** file.  
  
     Ripetere questo processo per il **SDKManifest.xml** file.  
  
15. Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
16. In **Esplora**, aprire il menu di scelta rapida per il **NativeMathVSIX** del progetto e quindi scegliere **Apri cartella in Esplora File**.  
  
17. In **Esplora File**, passare alla cartella $SolutionRoot$ \NativeMathVSIX\bin\Debug\ e quindi eseguire NativeMathVSIX.vsix per iniziare l'installazione.  
  
18. Scegliere il **installare** pulsante, attendere il completamento dell'installazione e quindi avviare Visual Studio.  
  
##  <a name="createSample"></a> Per creare un'app di esempio che utilizza la libreria di classi  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2.  Nell'elenco dei modelli, espandere **Visual C++**, **universali di Windows**, quindi selezionare **applicazione vuota**. Nel **nome** specificare **NativeMathSDKSample**, quindi scegliere il **OK** pulsante.  
  
3.  In **Esplora**, aprire il menu di scelta rapida per il **NativeMathSDKSample** del progetto e quindi scegliere **Aggiungi**, **riferimento**.  
  
4.  Nel **Aggiungi riferimento** espandere la finestra di dialogo, nell'elenco dei tipi di riferimento, **Windows universale**, quindi selezionare **estensioni**. Infine, selezionare il **nativo Math SDK** casella di controllo e quindi scegliere il **OK** pulsante.
  
5.  Visualizzare le proprietà del progetto per NativeMathSDKSample.  
  
     Le proprietà definite in NativeMathSDK.props sono state applicate quando è stato aggiunto il riferimento. È possibile verificarlo esaminando i **directory di VC + +** proprietà del progetto **le proprietà di configurazione**.  
  
6.  In **Esplora**, aprire il file MainPage e quindi utilizzare il seguente codice XAML per sostituire il relativo contenuto:  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
7.  Aggiornare MainPage corrispondano questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
8. Aggiornare MainPage.xaml.cpp corrispondano questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
9. Premere il tasto F5 per eseguire l'app.  
  
10. Nell'app, immettere i due numeri, selezionare un'operazione e quindi scegliere il **=** pulsante.  
  
     Viene visualizzato il risultato corretto.  
  
 Questa procedura dettagliata viene illustrato come creare e usare un SDK di estensione per chiamare un [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] libreria e non -[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] libreria.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un SDK tramite c# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Creazione di un Software Development Kit](../extensibility/creating-a-software-development-kit.md)