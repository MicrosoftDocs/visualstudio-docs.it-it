---
title: Debug di applicazioni ClickOnce che usano System.Deployment.Application | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 30cbf4aab2975b95703c24462604c1a43ed3554c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>Debug di applicazioni ClickOnce in cui si utilizza System.Deployment.Application
In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione consente di configurare la modalità di aggiornamento di un'applicazione. Tuttavia, se si desidera utilizzare e personalizzare avanzati [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] funzionalità di distribuzione, è necessario accedere al modello di oggetto di distribuzione fornito da <xref:System.Deployment.Application>. È possibile utilizzare il <xref:System.Deployment.Application> API per attività avanzate, ad esempio:  
  
-   Creazione di un'opzione "Aggiorna" nell'applicazione  
  
-   Download su richiesta condizionale, dei vari componenti dell'applicazione  
  
-   Aggiornamenti integrati direttamente nell'applicazione  
  
-   Per garantire che l'applicazione client sia sempre aggiornata  
  
 Poiché il <xref:System.Deployment.Application> API funzionano solo quando un'applicazione viene distribuita con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tecnologia, l'unico modo per eseguirne il debug consiste nella distribuzione dell'applicazione mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], connettersi a essa, quindi eseguire il debug. Può essere difficile il debug in tempo, perché spesso questo codice viene eseguito quando l'applicazione viene avviato e viene eseguito prima che è possibile collegare il debugger. Una soluzione consiste nell'inserimento di interruzioni (o viene arrestato, per i progetti di Visual Basic) prima del codice di verifica di aggiornamento o su richiesta.  
  
 La tecnica consigliata debug è il seguente:  
  
1.  Prima di iniziare, assicurarsi che i simboli (PDB) e vengono archiviati i file di origine.  
  
2.  Distribuire la versione 1 dell'applicazione.  
  
3.  Creare una nuova soluzione vuota. Dal **File** menu, fare clic su **New**, quindi **progetto**. Nel **nuovo progetto** la finestra di dialogo, aprire il **altri tipi di progetto** nodo, quindi selezionare il **soluzioni di Visual Studio** cartella. Nel **modelli** riquadro, selezionare **soluzione vuota**.  
  
4.  Aggiungere il percorso di origine archiviati per le proprietà per questa nuova soluzione. In **Esplora**, fare doppio clic sul nodo della soluzione, quindi fare clic su **proprietà**. Nel **pagine delle proprietà** nella finestra di dialogo **Esegui Debug dei file di origine**, quindi aggiungere la directory del codice sorgente archiviato. In caso contrario, il debugger Trova file di origine non aggiornate, poiché i percorsi dei file di origine vengono registrati nel file PDB. Se il debugger utilizza file di origine non aggiornati, è visualizzato un messaggio indicante che l'origine non corrisponde.  
  
5.  Verificare che il debugger è possibile trovare i file con estensione pdb. Se questi sono stati distribuiti con l'applicazione, il debugger li trova automaticamente. Sempre appare accanto all'assembly in questione prima. In caso contrario, sarà necessario aggiungere il percorso di archiviazione per il **percorsi dei file (con estensione pdb) di simboli** (per accedere a questa opzione, dal **strumenti** menu, fare clic su **opzioni**, quindi aprire il  **Debug** nodo e fare clic su **simboli**).  
  
6.  Eseguire il debug cosa accade tra il `CheckForUpdate` e `Download` / `Update` chiamate al metodo.  
  
     Ad esempio, il codice di aggiornamento potrebbe essere come segue:  
  
    ```  
        Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
            If My.Application.Deployment.IsNetworkDeployed Then  
  
                If (My.Application.Deployment.CheckForUpdate()) Then  
  
                    My.Application.Deployment.Update()  
                    Application.Restart()  
  
                End If  
  
            End If  
        End Sub  
    ```  
  
7.  Distribuire la versione 2.  
  
8.  Tentativo di collegare il debugger all'applicazione versione 1 durante il download di un aggiornamento per la versione 2. In alternativa è possibile utilizzare il `System.Diagnostics.Debugger.Break` metodo o semplicemente `Stop` in Visual Basic. Ovviamente, non è consigliabile lasciare queste chiamate al metodo nel codice di produzione.  
  
     Si supponga, ad esempio, si sviluppa un'applicazione Windows Form e un gestore eventi per questo metodo con la logica di aggiornamento è già. Per eseguirne il debug, è sufficiente collegare prima il pulsante è premuto, quindi impostare un punto di interruzione (assicurarsi aprire il file archiviato appropriato e impostato il punto di interruzione in tale).  
  
 Utilizzare il <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> proprietà per richiamare il <xref:System.Deployment.Application> API solo quando l'applicazione viene distribuita; le API non devono essere richiamate durante il debug di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Deployment.Application>