---
title: Importare un progetto XCode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: xplat-cplusplus
ms.openlocfilehash: 9de84c4330bb87ad13b865bda39f9ecafab4debd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="import-an-xcode-project"></a>Importare un progetto XCode
Microsoft Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma include il supporto per lo spostamento dei progetti XCode in Visual Studio, in cui è possibile creare librerie multipiattaforma e condividere il codice con altri progetti. La procedura guidata Importa da Xcode semplifica il processo di importazione dei progetti e la suddivisione del codice C++ nelle destinazioni XCode per l'uso come libreria statica o come progetto di codice condiviso. È possibile gestire il codice specifico di iOS in Visual Studio e usare comunque XCode per creare storyboard ed eseguire compilazioni. Per informazioni su come spostare facilmente il codice tra Visual Studio e XCode, vedere Spostare le modifiche tra XCode e Visual Studio.  
  
## <a name="using-the-import-from-xcode-wizard"></a>Uso della procedura guidata Importa da Xcode  
 In questo argomento viene illustrato come spostare un progetto XCode in Visual Studio per trarre vantaggio dalla condivisione del codice e dalle soluzioni multipiattaforma. Come prerequisito, è necessario associare il Mac a Visual Studio per essere in grado di importare, esportare e compilare il progetto. Per istruzioni su come configurare l'associazione, vedere [Installare e configurare gli strumenti per la compilazione con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). È anche necessario condividere il progetto XCode in rete o spostarlo nel computer con Visual Studio per usare la procedura guidata Importa da Xcode.  
  
#### <a name="import-from-xcode"></a>Importa da Xcode  
  
1.  Dal menu **File** scegliere **Nuovo**, **Importa**, **Importa da Xcode**. Verrà aperta la finestra di dialogo della procedura guidata **Importa da Xcode**.  
  
     ![Scegliere il progetto di destinazione XCode da importare](../cross-platform/media/cppmdd_u2_importxcode_choose.PNG "CPPMDD_U2_ImportXCode_Choose")  
  
2.  Nel riquadro **Scegliere un progetto** fare clic sul pulsante Sfoglia per selezionare un file di XCode con estensione pbxproj. Passare al file di progetto nella finestra di dialogo **Seleziona il file di progetto Xcode**, quindi scegliere **Apri**.  
  
     ![Selezionare un file di progetto nella finestra di dialogo Seleziona il file di progetto Xcode](../cross-platform/media/cppmdd_u2_importxcode_browse.PNG "CPPMDD_U2_ImportXCode_Browse")  
  
     Nella procedura guidata Importa da Xcode scegliere **Avanti**.  
  
3.  Nel riquadro **Destinazioni di destinazione** selezionare le destinazioni del progetto XCode da importare nei progetti di Visual Studio. Le destinazioni di XCode sono simili ai progetti di Visual Studio: la maggior parte è una raccolta di codice e risorse che producono un file binario. La procedura guidata Importa da Xcode consente solo l'importazione di destinazioni che producono un file binario, ma non una libreria statica, come destinazioni di destinazione. Le destinazioni con una libreria statica XCode sono l'oggetto del passaggio successivo.  
  
     ![Riquadro Destinazioni di destinazione della procedura guidata Importa da Xcode](../cross-platform/media/cppmdd_u2_importxcode_destination.jpg "CPPMDD_U2_ImportXCode_Destination")  
  
     Per ogni destinazione selezionata in **Destinazioni da importare**, la procedura guidata rileva automaticamente i file di codice C++ che possono essere suddivisi in un progetto di libreria statica distinto e li inserisce nella sezione **Elementi progetto C++**. Altro codice e altre risorse vengono mantenuti nella sezione **Elementi progetto XCode**. Al termine del processo di importazione, questi elementi diventano progetti di libreria statica e di applicazioni distinti in Visual Studio. Per impostazione predefinita, unit test e destinazioni dei framework non vengono suddivisi in progetti distinti dalla procedura guidata.  
  
     Per modificare i file contenuti in ogni progetto, usare i pulsanti Su e Giù. Quando si è soddisfatti con i file in ogni progetto, scegliere **Avanti** per continuare.  
  
4.  Nel riquadro **Destinazioni librerie** scegliere le destinazioni con una libreria statica del progetto XCode da importare nei progetti di Visual Studio. In questo riquadro è possibile scegliere quali file inserire in un progetto di codice condiviso e quali in un progetto di libreria statica. In ciascuna delle destinazioni nell'elenco **Destinazioni da importare** è possibile controllare quali file inserire in **Elementi progetto codice condiviso** e **Elementi progetto libreria statica** usando i pulsanti Su e Giù.  
  
     ![Riquadro Destinazioni librerie della procedura guidata Importa da Xcode](../cross-platform/media/cppmdd_u2_importxcode_library.jpg "CPPMDD_U2_ImportXCode_Library")  
  
     Un progetto di codice condiviso è un modo per condividere un set di file di codice sorgente tra progetti di Visual Studio. Il codice viene compilato come parte del progetto in cui è incluso, non come un progetto indipendente. Poiché i progetti che includono il codice condiviso possono avere diverse architetture e configurazioni, questo è il modo migliore per fornire un singolo progetto che contiene codice che può essere compilato per molti tipi di piattaforme.  
  
     Quando si è soddisfatti con i file in ogni progetto, scegliere **Avanti** per continuare.  
  
5.  Il riquadro **Proprietà globali** può essere usato per impostare un percorso di ricerca framework e un percorso di ricerca intestazioni incluse per tutti i progetti iOS in Visual Studio. Visual Studio usa questi percorsi per l'esplorazione del codice sorgente e per IntelliSense. Questi percorsi globali sono utili quando si creano progetti iOS che usano un set comune di intestazioni e framework.  
  
     ![Riquadro Proprietà globali della procedura guidata Importa da Xcode](../cross-platform/media/cppmdd_u2_importxcode_global.jpg "CPPMDD_U2_ImportXCode_Global")  
  
     Questi percorsi globali possono anche essere impostati nella finestra di dialogo **Opzioni** di Visual Studio. Per individuarli, scegliere **Opzioni** dal menu **Strumenti**. Nella finestra di dialogo **Opzioni** espandere **Multipiattaforma**, **C++**, **iOS**, **Proprietà globali**.  
  
     Scegliere **Avanti** per continuare.  
  
6.  Il riquadro **Framework** viene usato per configurare i percorsi usati da Visual Studio per l'esplorazione e IntelliSense per il progetto. I percorsi devono essere accessibili a Visual Studio per ogni framework a cui fa riferimento il progetto XCode. La procedura guidata controlla i riferimenti ai framework nei progetti XCode e indica se Visual Studio può individuare il framework. Qualsiasi percorso che è già stato impostato in Proprietà globali verrà individuato da Visual Studio. Le eccezioni sono elencate nell'elenco Framework. Per ciascun framework elencato con una X, specificare un percorso accessibile nel PC in cui Visual Studio può individuare il framework. È possibile usare il pulsante Sfoglia […] per aprire la finestra di dialogo **Selezione cartella** e specificare il percorso. Il percorso del framework può fare riferimento a una copia locale o a una condivisione di rete accessibile sul Mac.  
  
     ![Riquadro Framework della procedura guidata Importa da Xcode](../cross-platform/media/cppmdd_u2_importxcode_frameworks.jpg "CPPMDD_U2_ImportXCode_Frameworks")  
  
     Scegliere **Avanti** per continuare.  
  
7.  Il riquadro **Impostazioni progetto** consente di modificare il framework e di includere le impostazioni del percorso di ricerca intestazioni incluse per ogni progetto creato. Usare questo riquadro per impostare i percorsi specifici del progetto che differiscono dalle impostazioni globali.  
  
     Per impostare un percorso per un progetto specifico, nell'elenco a discesa **Progetto di destinazione** selezionare il file di progetto, quindi impostare i valori nei controlli **Percorso di ricerca framework** e **Percorso di ricerca intestazioni incluse**. È possibile usare il pulsante Sfoglia […] accanto a ogni controllo per aprire la finestra di dialogo **Selezione cartella** e specificare il percorso.  
  
     ![Riquadro Progetti della procedura guidata Importa da Xcode](../cross-platform/media/cppmdd_u2_importxcode_projects.jpg "CPPMDD_U2_ImportXCode_Projects")  
  
     Se non è stato associato alcun Mac remoto a questo PC in Visual Studio, viene visualizzato il collegamento Configura un computer remoto. Per istruzioni su come configurare l'associazione, vedere [Installare e configurare gli strumenti per la compilazione con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
     Per importare il progetto XCode usando le impostazioni della procedura guidata, scegliere **Importa**.  
  
 La procedura guidata Importa da Xcode crea progetti in Visual Studio che corrispondono alle destinazioni del progetto XCode selezionato. Il codice che può essere condiviso con altri progetti C++ è suddiviso in progetti di codice condiviso e di libreria statica distinti. Il codice rimanente viene inserito in progetti di libreria e di applicazioni iOS, che possono essere compilati in remoto da Visual Studio. Per altre informazioni sullo spostamento di codice tra Visual Studio e XCode, vedere [Sincronizzare le modifiche tra XCode e Visual Studio](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).