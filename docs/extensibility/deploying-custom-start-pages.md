---
title: Distribuzione di pagine iniziali personalizzate | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c52a71ebb521f84f96bead09502389f6b395e90c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-custom-start-pages"></a>Distribuzione di pagine iniziali personalizzate
È possibile distribuire pagine iniziali personalizzate utilizzando la distribuzione VSIX oppure copiando i file nelle posizioni corrette nel computer di destinazione.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Distribuzione VSIX usando il modello di progetto di pagina iniziale  
 Quando si crea una pagina iniziale utilizzando il modello di progetto di pagina iniziale e quindi compilare il progetto, Visual Studio crea un file con estensione VSIX che è possibile distribuire. Assemblaggio di una pagina iniziale in un file. VSIX offre le seguenti opzioni per la distribuzione, a seconda i destinatari desiderati:  
  
-   È possibile inserire il file VSIX in una condivisione di rete o in un sito Web pubblico. Quando un utente apre il file, la pagina iniziale viene installata automaticamente.  
  
-   È possibile caricare il file VSIX il [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) sito Web in modo che gli utenti possono installarla utilizzando **Extension Manager**.  
  
 Il modello di progetto di pagina iniziale Crea una copia del valore predefinito la pagina iniziale di Visual Studio in modo che è possibile modificare la copia e conservare l'originale.  
  
 È possibile ottenere il modello di progetto di pagina iniziale utilizzando **Extension Manager** o scaricarlo dal sito Web.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Distribuzione VSIX senza utilizzare il modello di progetto di pagina iniziale  
 Una corretta distribuzione VSIX richiede un'estensione per essere installati in cartelle che sono riconosciute dal processo di registrazione VSIX e da **Extension Manager**. Poiché il modello di progetto di pagina iniziale specifica già le cartelle corrette, è consigliabile utilizzarlo ogni volta che si desidera creare un pacchetto di un'estensione per la distribuzione VSIX. Tuttavia, se si dispone di un caso in cui non è possibile utilizzare il modello, è possibile creare una distribuzione VSIX senza utilizzarlo.  
  
 Per creare una distribuzione VSIX senza usare il modello di progetto di pagina iniziale, creare innanzitutto un file. VSIX per la pagina iniziale in uno di questi due modi:  
  
-   Aggiungendo i file della pagina iniziale personalizzati a un progetto VSIX vuoto. Per ulteriori informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).  
  
-   Creando manualmente un file con estensione VSIX. Per creare manualmente un file. VSIX:  
    
    1.  Creare il file extension vsixmanifest e il file [Content_Types] XML in una nuova cartella. Per ulteriori informazioni, vedere [Anatomia di un pacchetto VSIX](/visualstudio/extensibility/anatomy-of-a-vsix-package).  
  
    2.  In Esplora risorse, fare clic sulla cartella che contiene i due file XML, fare clic su Invia a e quindi fare clic sulla cartella compressa. Rinominare il file ZIP risultante in Filename.vsix, in cui Filename è il nome del file ridistribuibile che installa il pacchetto.  
  
 Per Visual Studio per riconoscere una pagina iniziale, il `Content Element` del manifesto VSIX deve contenere un `CustomExtension Element` che ha il `Type` attributo impostato su `"StartPage"`. Un'estensione di pagina iniziale che è stata installata utilizzando la distribuzione VSIX è presente il **Personalizza pagina iniziale** elenco il **avvio** pagina Opzioni come **[installato estensione]** *Nome estensione*.  
  
 Se il pacchetto di pagina iniziale include gli assembly, è necessario aggiungere la registrazione di percorso di associazione in modo che siano disponibili quando si avvia Visual Studio. A tale scopo, assicurarsi che il pacchetto include un file. pkgdef che contiene le informazioni seguenti.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>Distribuzione VSIX per tutti gli utenti  
 Per impostazione predefinita, le estensioni distribuite nei pacchetti VSIX installare solo per l'utente corrente. È possibile apportare a un'installazione di pagina iniziale per tutti gli utenti del computer di destinazione mediante la creazione di una distribuzione di tutti gli utenti.  
  
##### <a name="to-create-an-all-users-deployment"></a>Per creare una distribuzione di tutti gli utenti  
  
1.  Aprire il file Extension. vsixmanifest nella visualizzazione codice.  
  
2.  Nel `Identifier` elemento del manifesto vsix, aggiungere un `AllUsers` elemento che presenta un valore di `true`.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     In questo modo il programma di installazione di vsix richiedere le autorizzazioni di amministratore e quindi installare i file in \Common7\IDE\Extensions.  
  
3.  Aprire il file. pkgdef.  
  
4.  Modificare il pkgdef per impostare la pagina iniziale predefinita in HKLM aggiungendo il comando seguente, dove *MyStartPage.xaml* è il nome del file con estensione XAML contenente la pagina iniziale.  
  
     [$RootKey$ \StartPage\Default]  
  
     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"  
  
     In questo modo Visual superato per la ricerca nella nuova posizione di pagina iniziale.  
  
## <a name="file-copy-deployment"></a>Distribuzione tramite Copia file  
 Non è necessario creare un file con estensione VSIX per distribuire una pagina iniziale personalizzata. In alternativa, è possibile copiare il markup e un file di supporto direttamente nella cartella \StartPages\ dell'utente. Il **Personalizza pagina iniziale** elenco il **avvio** opzioni nella pagina sono elencati tutti i file con estensione XAML in quella cartella, con il percorso, ad esempio, %USERPROFILE%\My Documents\Visual Studio  *versione*\StartPages\\*nome File*con estensione XAML. Se la pagina iniziale include i riferimenti agli assembly privato, è necessario copiarli e incollarli nella cartella \privateassemblies\..  
  
 Per distribuire una pagina iniziale creato senza pacchetti in un file con estensione VSIX, è consigliabile utilizzare una strategia di copia del file di base, ad esempio, uno script batch o qualsiasi altra tecnologia di distribuzione che consente di inserita i file nella directory richieste.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>Per installare manualmente una pagina iniziale personalizzata  
  
1.  Copiare il file con estensione XAML contenente il markup della pagina iniziale, insieme a eventuali file di supporto diverso da assembly e incollarli nella cartella \StartPages\ dell'utente.  
  
2.  Se la pagina iniziale richiede l'assembly, copiarli e incollarli in... \\ *Cartella di installazione di visual Studio*\Common7\IDE\PrivateAssemblies.\\.  
  
3.  Nel **Personalizza pagina iniziale** elenco il **avvio** opzioni pagina, selezionare la nuova pagina iniziale. Per altre informazioni, vedere [Personalizzazione della pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione della pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Aggiunta di un controllo utente nella pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)