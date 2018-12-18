---
title: Eseguire il debug in fase di progettazione - Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 02/21/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 33e0210023de05047957e7fbf55a8f970fda19d9
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="debug-at-design-time-in-visual-studio"></a>Eseguire il debug in fase di progettazione in Visual Studio

In alcuni scenari, si desidera eseguire il debug di codice in fase di progettazione ora invece che durante l'esecuzione dell'applicazione. È possibile farlo usando il **immediato** finestra. Se si desidera eseguire il debug di codice XAML che interagisce con altro codice, ad esempio il codice di associazione dati, è possibile utilizzare **Debug** > **Connetti a processo** a tale scopo.
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>Eseguire il debug in fase di progettazione utilizzando la finestra controllo immediata  

È possibile utilizzare Visual Studio **immediato** finestra per eseguire una funzione o una subroutine quando l'applicazione non è in esecuzione. Se la funzione o subroutine contiene un punto di interruzione, Visual Studio interromperà l'esecuzione al momento appropriato. È quindi possibile usare le finestre del debugger per esaminare lo stato del programma. Questa funzionalità è denominata debug in fase di progettazione.  

Nell'esempio seguente è in Visual Basic, ma la **immediato** finestra è supportata anche nelle applicazioni c# e C++.
  
1.  Incollare il codice seguente in un'applicazione console Visual Basic:  
  
    ```vb  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  Impostare un punto di interruzione sulla riga che legge, `s="Add BreakPoint Here"`.  
  
3.  Aprire il **immediato** finestra (**Debug** > **Windows** > **immediato**) e digitare il comando seguente nel finestra: `?MyFunction<enter>`  
  
4.  Verificare che lo stack di chiamate è accurato e che è stato raggiunto il punto di interruzione.  
  
5.  Nel **Debug** menu, fare clic su **continua**e verificare che sia ancora in modalità progettazione.  
  
6.  Digitare il comando seguente nel **immediato** finestra: `?MyFunction<enter>`  
  
7.  Digitare il comando seguente nel **immediato** finestra: `?MySub<enter>`  
  
8.  Verificare che il punto di interruzione e controllare il valore della variabile statica `i` nel **variabili locali** finestra. Deve essere il valore 3.  
  
9. Verificare che lo stack di chiamate sia accurato.  
  
10. Nel **Debug** menu, fare clic su **continua**e verificare che sia ancora in modalità progettazione.  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>Eseguire il debug in fase di progettazione dalla finestra di progettazione XAML

Può essere utile eseguire il debug di codice dalla finestra di progettazione XAML in alcuni scenari di associazione dati dichiarativa.

1. Nel progetto, aggiungere una nuova pagina XAML, ad esempio *temp.xaml*. Lasciare vuota la nuova pagina XAML. 

1. Compilare la soluzione.

1. Aprire *temp.xaml*, che carica la finestra di progettazione (*UwpSurface.exe* in un'app UWP, o *XDesProc.exe*) in modo è possibile collegarvi nei passaggi successivi. 

1. Aprire una nuova istanza di Visual Studio. Nella nuova istanza, aprire il **Connetti a processo** la finestra di dialogo (**Debug** > **Connetti a processo**), impostare il **allegarvi** campo al tipo di codice corretto, ad esempio **codice gestito (CoreCLR)** o il tipo di codice corretto in base alla versione di .NET. Selezionare il processo di progettazione corretto dall'elenco e scegliere **collegamento**.

    Per UWP progetti per compilare 16299 o versioni successive, il processo di progettazione è *UwpSurface.exe*. Per WPF o le versioni di piattaforma UWP precedenti a 16299, il processo di progettazione è *XDesProc.exe*.

1. Quando connesso al processo, passare al progetto, aprire il code-behind in cui si desidera eseguire il debug e impostare un punto di interruzione.

1. Infine, aprire la pagina che contiene il codice XAML che include l'associazione dati.

    Ad esempio, è possibile impostare un punto di interruzione nel codice del convertitore di tipo per il codice XAML seguente, che associa un controllo TextBlock in fase di progettazione.

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Quando il caricamento della pagina, il punto di interruzione viene raggiunto.
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debugger Basics](../debugger/debugger-basics.md) (Nozioni di base sul debugger)
