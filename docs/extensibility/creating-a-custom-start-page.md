---
title: Pagina iniziale di creazione di un oggetto personalizzato | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f1ce8112adffabcee835d7adf598e73d327ca3b6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-custom-start-page"></a>Creazione di una pagina iniziale personalizzata
È possibile creare una pagina iniziale personalizzata seguendo i passaggi descritti in questo documento.  
  
## <a name="creating-a-blank-start-page"></a>Creazione di una pagina iniziale vuota  
 Verificare innanzitutto una pagina iniziale vuota creando un file con estensione XAML che ha una struttura di tag che riconosce Visual Studio. Quindi, aggiungere il markup e code-behind per produrre l'aspetto e funzionalità che si desidera.  
  
#### <a name="to-create-a-blank-start-page"></a>Per creare una pagina iniziale vuota  
  
1.  Creare un nuovo progetto di tipo **applicazione WPF** (**Visual c# / Desktop Windows**.  
  
2.  Aggiungere un riferimento a `Microsoft.VisualStudio.Shell.14.0`.  
  
3.  Aprire il file XAML nell'editor XML e modificare il livello superiore \<finestra > elemento da un \<UserControl > elemento senza rimuovere le dichiarazioni dello spazio dei nomi.  
  
4.  Rimuovere il `x:Class` dichiarazione di elemento di primo livello. In questo modo il contenuto XAML compatibile con la finestra degli strumenti di Visual Studio che ospita la pagina iniziale.  
  
5.  Aggiungere le seguenti dichiarazioni dello spazio dei nomi di primo livello \<UserControl > elemento.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Questi spazi dei nomi consentono di accedere ai comandi di Visual Studio, controlli e le impostazioni dell'interfaccia utente. Per ulteriori informazioni, vedere [aggiunta di comandi di Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     Nell'esempio seguente viene illustrato il markup nel file XAML per una pagina iniziale vuota. Qualsiasi contenuto personalizzato deve andare nelle interna <xref:System.Windows.Controls.Grid> elemento.  
  
    ```vb  
    <UserControl  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        xmlns:local="clr-namespace:StartPageHost"  
        mc:Ignorable="d"  
         Height="350" Width="525">  
        <Grid>  
        <!--Add content here.-->  
        </Grid>  
    </UserControl>  
    ```  
  
6.  Aggiungere controlli a vuoto \<UserControl > elemento per riempire la pagina iniziale personalizzata. Per informazioni su come aggiungere funzionalità specifiche per Visual Studio, vedere [aggiunta di comandi di Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testing e applicazione della pagina iniziale personalizzata  
 Non impostare l'istanza primaria di Visual Studio per eseguire la pagina iniziale personalizzata fino a quando non è verificare che arresta in modo anomalo Visual Studio. In alternativa, eseguirne il test nell'istanza sperimentale.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Per testare una pagina di avvio personalizzata creata manualmente  
  
1.  Copiare il file XAML e qualsiasi file di testo o markup supporto file, al **%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\**  cartella.  
  
2.  Se la pagina iniziale fa riferimento a tutti i controlli o i tipi negli assembly che non sono installati da Visual Studio, copiare gli assembly e incollarli in *cartella di installazione di Visual Studio***\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  Al prompt dei comandi di Visual Studio digitare **devenv /rootsuffix Exp** per aprire un'istanza sperimentale di Visual Studio.  
  
4.  Nell'istanza sperimentale, passare al **Strumenti / opzioni / ambiente / avvio** pagina e selezionare il file XAML dal **Personalizza pagina iniziale** elenco a discesa.  
  
5.  Scegliere **Pagina iniziale** dal menu **Visualizza**.  
  
     La pagina iniziale personalizzata deve essere visualizzata. Se si desidera modificare i file, è necessario chiudere l'istanza sperimentale, apportare le modifiche, copiare e incollare i file modificati e quindi aprire nuovamente l'istanza sperimentale per visualizzare le modifiche.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Per applicare l'oggetto personalizzato pagina iniziale nell'istanza primaria di Visual Studio  
  
-   Dopo aver verificato la pagina iniziale e ha rilevato che è stabile, utilizzare il **Personalizza pagina iniziale** opzione il **opzioni** la finestra di dialogo selezionare come pagina iniziale nell'istanza primaria di Visual Studio  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Aggiunta di XAML personalizzato alla pagina iniziale](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Aggiunta di controllo utente alla pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)   
 [Aggiunta di comandi di Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Procedura dettagliata: Salvataggio delle impostazioni utente in una pagina iniziale](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Distribuzione di pagine iniziali personalizzate](../extensibility/deploying-custom-start-pages.md)