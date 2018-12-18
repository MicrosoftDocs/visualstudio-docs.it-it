---
title: 'Procedura dettagliata: Download di assembly su richiesta con l''API della distribuzione ClickOnce | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 640c0852a3745d11aae119e3c00e024b594d9132
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Procedura dettagliata: download di assembly su richiesta con l'API della distribuzione ClickOnce
Per impostazione predefinita, tutti gli assembly inclusi un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione vengono scaricati alla prima esecuzione dell'applicazione. Tuttavia, è possibile parti dell'applicazione usati da un set ridotto di utenti. In questo caso, è consigliabile scaricare un assembly solo quando si crea uno dei relativi tipi. La procedura dettagliata seguente viene illustrato come contrassegnare determinati assembly nell'applicazione come "facoltativi" e per scaricarli usando le classi nel <xref:System.Deployment.Application> dello spazio dei nomi quando common language runtime (CLR).  
  
> [!NOTE]
>  Per usare questa procedura, è necessario eseguire l'applicazione con attendibilità totale.  
  
## <a name="prerequisites"></a>Prerequisiti  
 È necessario uno dei componenti seguenti per completare questa procedura dettagliata:  
  
-   Windows SDK. il SDK di Windows può essere scaricato dal Microsoft Download Center.  
  
-   Visual Studio.  
  
## <a name="creating-the-projects"></a>Creazione dei progetti  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Per creare un progetto che utilizza un assembly su richiesta  
  
1.  Creare una directory denominata ClickOnceOnDemand.  
  
2.  Aprire il prompt dei comandi di Windows SDK o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prompt dei comandi.  
  
3.  Passare alla directory ClickOnceOnDemand.  
  
4.  Generare una coppia di chiavi pubblica/privata usando il comando seguente:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  Utilizzando blocco note o un altro editor di testo, definire una classe denominata `DynamicClass` con una singola proprietà denominata `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  Salvare il testo con un file denominato `ClickOnceLibrary.cs` o `ClickOnceLibrary.vb`, a seconda del linguaggio utilizzato per la directory ClickOnceOnDemand.  
  
7.  Compilare il file in un assembly.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Per ottenere la chiave pubblica token per l'assembly, usare il comando seguente:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Creare un nuovo file utilizzando il testo dell'editor e immettere il codice seguente. Questo codice crea un'applicazione Windows Form che consente di scaricare l'assembly ClickOnceLibrary quando necessario.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. Nel codice, individuare la chiamata a <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Impostare`PublicKeyToken` sul valore recuperato in precedenza.  
  
12. Salvare il file come `Form1.cs` o `Form1.vb`.  
  
13. Compila in un eseguibile usando il comando seguente.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Contrassegnare gli assembly come facoltativi  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Per contrassegnare gli assembly come facoltativi in un'applicazione ClickOnce con MageUI.exe  
  
1.  Usando MageUI.exe, creare un manifesto dell'applicazione, come descritto in [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Utilizzare le seguenti impostazioni per il manifesto dell'applicazione:  
  
    -   Nome del manifesto dell'applicazione `ClickOnceOnDemand`.  
  
    -   Nel **file** pagina, nella riga ClickOnceLibrary, impostare il **tipo di File** colonna **Nessuno**.  
  
    -   Nel **file** nella riga ClickOnceLibrary. dll, tipo pagina `ClickOnceLibrary.dll` nel **gruppo** colonna.  
  
2.  Usando MageUI.exe, creare un manifesto di distribuzione come descritto in [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Utilizzare le seguenti impostazioni per il manifesto di distribuzione:  
  
    -   Denominare il manifesto di distribuzione `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Test del nuovo assembly  
  
#### <a name="to-test-your-on-demand-assembly"></a>Per testare l'assembly su richiesta  
  
1.  Caricare il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione a un server Web.  
  
2.  Avviare l'applicazione distribuita con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] da un browser immettendo l'URL del manifesto di distribuzione. Se si chiama il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione `ClickOnceOnDemand`e caricarlo nella directory radice di adatum.com, l'URL sarà simile al seguente:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Quando viene visualizzato il modulo principale, premere l'oggetto <xref:System.Windows.Forms.Button>. Dovrebbe essere una stringa in una finestra di messaggio che legge "Hello, World!".  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Deployment.Application.ApplicationDeployment>