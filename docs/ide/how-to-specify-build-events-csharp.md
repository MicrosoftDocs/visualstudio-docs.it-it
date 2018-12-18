---
title: 'Procedura: Specificare gli eventi di compilazione (C#) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 1fcba0ef7abec3c8f5d71d34b8ff4e19e047d50b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-build-events-c"></a>Procedura: specificare eventi di compilazione (C#)
È possibile usare gli eventi di compilazione per specificare i comandi da eseguire prima dell'inizio o al termine della compilazione. Gli eventi di compilazione vengono eseguiti solo se la compilazione raggiunge correttamente i punti corrispondenti nel processo di compilazione.  
  
 Quando un progetto viene compilato, gli eventi di pre-compilazione vengono aggiunti a un file denominato PreBuildEvent.bat mentre gli eventi di post-compilazione vengono aggiunti a un file denominato PostBuildEvent.bat. Per garantire il controllo degli errori, aggiungere comandi di controllo degli errori personalizzati alle istruzioni di compilazione.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="how-to-specify-pre-build-and-post-build-events"></a>Come specificare eventi di pre e post-compilazione  
  
#### <a name="to-specify-a-build-event"></a>Per specificare un evento di compilazione  
  
1.  In **Esplora soluzioni** selezionare il progetto per il quale si vuole specificare l'evento di compilazione.  
  
2.  Scegliere **Proprietà** dal menu **Progetto**.  
  
3.  Selezionare la scheda **Eventi di compilazione**.  
  
4.  Nella casella **Riga di comando eventi pre-compilazione** specificare la sintassi per l'evento di compilazione.  
  
    > [!NOTE]
    >  Gli eventi di pre-compilazione non vengono eseguiti se il progetto è aggiornato e non viene attivata alcuna compilazione.  
  
5.  Nella casella **Riga di comando eventi post-compilazione** specificare la sintassi per l'evento di compilazione.  
  
    > [!NOTE]
    >  Aggiungere un'istruzione `call` prima di tutti gli eventi di compilazione che eseguono file con estensione BAT. Ad esempio, `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
6.  Nella casella **Esegui evento post-compilazione** specificare con quali condizioni eseguire l'evento di post-compilazione.  
  
    > [!NOTE]
    >  Per aggiungere una sintassi più lunga o per selezionare macro di compilazione dalla [finestra di dialogo Riga di comando eventi pre-compilazione/post-compilazione](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), fare clic sul pulsante con i puntini di sospensione (**...** ) per visualizzare una casella di modifica.  
  
     La sintassi dell'evento di compilazione può includere qualsiasi comando che sia valido in un prompt dei comandi o in un file bat. Perché vengano sicuramente eseguiti tutti i comandi successivi, il nome di un file batch deve essere preceduto da `call`.  
  
     **Nota** Se l'evento di pre-compilazione o di post-compilazione non viene completato correttamente, è possibile terminare la compilazione forzando l'uscita dell'azione dell'evento con un codice diverso da zero (0), che indica un esito positivo.  
  
## <a name="example-how-to-change-manifest-information-by-using-a-post-build-event"></a>Esempio: come modificare le informazioni di un manifesto usando un evento di post-compilazione  
 La procedura seguente illustra come impostare la versione minima del sistema operativo nel manifesto dell'applicazione usando un comando exe chiamato da un evento di post-compilazione (il file exe.manifest nella directory del progetto). La versione minima del sistema operativo è un numero composto da quattro parti, ad esempio 4.10.0.0. A tale scopo, il comando modificherà la sezione `<dependentOS>` del manifesto:  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Per creare un comando exe per modificare il manifesto dell'applicazione  
  
1.  Creare un'applicazione console per il comando. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** espandere **Visual C#**, fare clic su **Windows** e quindi scegliere il modello **Applicazione console**. Denominare il progetto `ChangeOSVersionCS`.  
  
3.  In Program.cs aggiungere la riga seguente alle altre istruzioni `using` all'inizio del file:  
  
    ```  
    using System.Xml;  
    ```  
  
4.  Nello spazio dei nomi `ChangeOSVersionCS` sostituire l'implementazione della classe `Program` con il codice seguente:  
  
    ```  
    class Program  
    {  
       /// <summary>  
       /// This function will set the minimum operating system version for a ClickOnce application.  
       /// </summary>  
       /// <param name="args">  
       /// Command Line Arguments:  
       /// 0 - Path to application manifest (.exe.manifest).  
       /// 1 - Version of OS  
       ///</param>  
       static void Main(string[] args)  
       {  
          string applicationManifestPath = args[0];  
          Console.WriteLine("Application Manifest Path: " + applicationManifestPath);  
  
          // Get version name.  
          Version osVersion = null;  
          if (args.Length >=2 ){  
             osVersion = new Version(args[1]);  
          }else{  
             throw new ArgumentException("OS Version not specified.");  
          }  
          Console.WriteLine("Desired OS Version: " + osVersion.ToString());  
  
          XmlDocument document;  
          XmlNamespaceManager namespaceManager;  
          namespaceManager = new XmlNamespaceManager(new NameTable());  
          namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");  
          namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");  
  
          document = new XmlDocument();  
          document.Load(applicationManifestPath);  
  
          string baseXPath;  
          baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";  
  
          // Change minimum required operating system version.  
          XmlNode node;  
          node = document.SelectSingleNode(baseXPath, namespaceManager);  
          node.Attributes["majorVersion"].Value = osVersion.Major.ToString();  
          node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();  
          node.Attributes["buildNumber"].Value = osVersion.Build.ToString();  
          node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();  
  
          document.Save(applicationManifestPath);  
       }  
    }  
    ```  
  
     Il comando accetta due argomenti: il percorso del manifesto dell'applicazione, ovvero la cartella in cui il processo di compilazione crea il manifesto (in genere Projectname.publish), e la versione del nuovo sistema operativo.  
  
5.  Compilare il progetto. Scegliere **Compila soluzione** dal menu **Compila**.  
  
6.  Copiare il file EXE in una directory, ad esempio `C:\TEMP\ChangeOSVersionVB.exe`.  
  
 Richiamare quindi questo comando in un evento di post-compilazione per modificare il manifesto dell'applicazione.  
  
#### <a name="to-invoke-a-post-build-event-to-modify-the-application-manifest"></a>Per richiamare un evento di post-compilazione per modificare il manifesto dell'applicazione  
  
1.  Creare un'applicazione Windows per il progetto da pubblicare. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** espandere **Visual C#**, fare clic su **Desktop classico di Windows** e quindi fare clic sul modello **Applicazione Windows Form**. Denominare il progetto `CSWinApp`.  
  
3.  Con il progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
4.  In Creazione progetti, individuare la pagina **Pubblica** e impostare **Posizione di pubblicazione** su `C:\TEMP\`.  
  
5.  Pubblicare il progetto facendo clic su **Pubblica**.  
  
     Il file manifesto verrà compilato e salvato in `C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest`. Per visualizzare il manifesto, fare clic con il pulsante destro del mouse sul file, scegliere **Apri con**, selezionare **Seleziona il programma da un elenco** e quindi fare clic su **Blocco note**.  
  
     Ricercare nel file l'elemento `<osVersionInfo>`. Ad esempio, la versione potrebbe essere:  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  In Creazione progetti fare clic sulla scheda **Eventi di compilazione** e fare clic sul pulsante **Modifica post-compilazione**.  
  
7.  Nella casella **Riga di comando eventi post-compilazione** digitare il comando seguente:  
  
     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     Quando si compila il progetto, questo comando imposterà la versione minima del sistema operativo nel manifesto dell'applicazione su 5.1.2600.0.  
  
     Poiché la macro `$(TargetPath)` esprime il percorso completo del file eseguibile in corso di creazione, il file `$(TargetPath)`.manifest specificherà il manifesto dell'applicazione creato nella directory bin. La pubblicazione copierà questo manifesto nel percorso di pubblicazione impostato in precedenza.  
  
8.  Pubblicare nuovamente il progetto. Passare alla pagina **Pubblica** e fare clic su **Pubblica**.  
  
     Visualizzare nuovamente il manifesto. Per visualizzare il manifesto, aprire la directory di pubblicazione, fare clic con il pulsante destro del mouse sul file, scegliere **Apri con**, selezionare **Seleziona il programma da un elenco** e quindi fare clic su **Blocco note**.  
  
     Adesso la versione dovrebbe essere:  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Pagina Eventi di compilazione, Creazione progetti (C#)](../ide/reference/build-events-page-project-designer-csharp.md)   
 [Finestra di dialogo Riga di comando eventi pre-compilazione/post-compilazione](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Procedura: Specificare gli eventi di compilazione (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)   
 [Compiling and Building](../ide/compiling-and-building-in-visual-studio.md) (Compilazione e creazione)