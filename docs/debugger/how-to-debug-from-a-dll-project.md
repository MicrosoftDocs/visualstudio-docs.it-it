---
title: 'Procedura: eseguire il Debug da un progetto di DLL | Documenti Microsoft'
ms.custom: ''
ms.date: 05/24/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63581cee8816e72492a67a0981a9077b9fec2935
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio"></a>Procedura: eseguire il Debug da un progetto DLL in Visual Studio
Per eseguire il debug di un progetto di DLL è possibile specificare l'applicazione chiamante nelle proprietà del progetto del progetto DLL e quindi è possibile avviare il debug dal progetto di DLL stessa. Per utilizzare questo metodo, l'applicazione deve chiamare la DLL e la DLL deve trovarsi nel percorso in cui l'applicazione prevede per individuarlo, (in caso contrario, l'applicazione potrebbe rilevare una versione differente della DLL e caricare che invece e non raggiunto i punti di interruzione). Per altri metodi di debug di DLL, vedere [progetti DLL di debug](../debugger/debugging-dll-projects.md).
  
Se una DLL gestita viene chiamata da codice nativo e si vuole eseguire il debug di entrambi, specificarlo nelle proprietà del progetto. Per altre informazioni, vedere [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md).   

Il layout e il contenuto delle pagine delle proprietà di C++ sono diversi da quelli delle pagine delle proprietà di C# e Visual Basic. 
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>Per specificare l'applicazione chiamante in un progetto C++  
  
1.  Pulsante destro del mouse sul nodo del progetto nel **Esplora** e selezionare **proprietà**.  
  
2.  Assicurarsi che il **configurazione** campo nella parte superiore della finestra è impostato su **Debug**. 

    Oggetto **Debug** configurazione è necessaria per questo metodo. 
  
3.  Passare a **le proprietà di configurazione > debug**.  
  
4.  Nel **Debugger da avviare** scegliere **Debugger Windows locale** o **Debugger Windows remoto**.  
  
5.  Nel **comando** o **comando remoto** , aggiungere il nome del percorso completo dell'applicazione chiamante (ad esempio un file .exe).

    ![Finestra proprietà di debug](../debugger/media/dbg-debugging-properties-dll.png "DebuggingPropertiesWindow")  
  
6.  Aggiungere tutti gli argomenti del programma necessari per il **gli argomenti del comando** casella.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>Per specificare l'applicazione chiamante in un progetto C# o Visual Basic  
  
1.  Pulsante destro del mouse sul nodo del progetto nel **Esplora** e selezionare **proprietà**e quindi selezionare il **Debug** scheda.

2.  Assicurarsi che il **configurazione** campo nella parte superiore della finestra è impostato su **Debug**.

3.  (.NET framework) Selezionare **Avvia programma esterno**e aggiungere il nome del percorso completo dell'applicazione chiamante.

4.  (.NET core) Selezionare **eseguibile** dal **avviare** elenco e quindi aggiungere il nome del percorso completo dell'applicazione chiamante nel **eseguibile** campo. 
  
     Se è necessario aggiungere gli argomenti della riga di comando del programma esterno, aggiungerli nel **argomenti della riga di comando** (o **argomenti applicazione**) campo.

    ![Finestra proprietà di debug](../debugger/media/dbg-debugging-properties-dll-csharp.png "DebuggingPropertiesWindow") 

5.  Se si desidera, è possibile chiamare anche un'applicazione come un URL. Potrebbe essere necessario eseguire questa operazione se si esegue il debug di una DLL gestita usata da un'applicazione ASP.NET locale.  
  
     In **azione di avvio**, selezionare il **Avvia browser con URL:** pulsante di opzione e specificare l'URL.
  
### <a name="to-start-debugging-from-the-dll-project"></a>Per avviare il debug dal progetto DLL  
  
1.  Impostare punti di interruzione nel progetto DLL. 

2.  Fare clic sul progetto DLL e scegliere **imposta come progetto di avvio**. 

    (Assicurarsi inoltre che il **configurazione delle soluzioni** campo è ancora impostato su **Debug**.)   
  
3.  Avviare il debug (premere F5, fare clic sulla freccia verde o fare clic su **Debug > Avvia debug**).

    I punti di interruzione verrà raggiunto nella DLL. Se non si è in grado di raggiungere i punti di interruzione, assicurarsi che la DLL di output (per impostazione predefinita, il **project\Debug** cartella) sia in un percorso che l'applicazione chiamante si aspetta per individuarlo.
  
## <a name="see-also"></a>Vedere anche  
 [Debug di progetti di DLL](../debugger/debugging-dll-projects.md)   
 [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)