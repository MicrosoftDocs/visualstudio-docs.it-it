---
title: 'Procedura dettagliata: Aggiunta di XAML personalizzato alla pagina iniziale | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18e6e782e703282f9eb4e189671c086eb17db427
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Procedura dettagliata: Aggiunta di XAML personalizzato alla pagina iniziale
Questa procedura dettagliata viene illustrato come creare una pagina iniziale personalizzata di Visual Studio contenente un Web browser.  
  
## <a name="adding-custom-xaml"></a>Aggiunta di XAML personalizzato  
  
1.  Creare una pagina iniziale seguendo le istruzioni in [la creazione di una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md).  
  
2.  Nel file MainWindow. XAML, è possibile trovare il \<griglia > sezione.  
  
3.  Aggiungere un \<TabControl > elemento e un \<TabItem > all'interno di \< griglia > elemento, come illustrato nell'esempio seguente.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  Aggiungere un secondo \<TabItem >, con un \<pulsante > elemento che viene aperto un nuovo progetto:  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="MyButton" Height="Auto">  
                <Button Name="btnNewProj" Content="New Project"   
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
                    CommandParameter="File.NewProject" >  
                </Button>  
            </TabItem>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
## <a name="testing-the-custom-start-page"></a>Test della pagina iniziale personalizzata  
  
1.  Premere F5.  
  
     Apre l'istanza sperimentale di Visual Studio, con la pagina iniziale personalizzata installata ma non è selezionata.  
  
2.  Nell'istanza sperimentale di Visual Studio, aprire il **Strumenti/opzioni / ambiente** pagina.  
  
3.  Selezionare **avvio**. Nel **Personalizza pagina iniziale** elenco, selezionare il file XAML e fare clic su **OK**.  
  
4.  Scegliere **Pagina iniziale** dal menu **Visualizza**.  
  
5.  Fare clic su di **Bing** scheda.  
  
     Si dovrebbe essere una pagina web di Bing.  
  
6.  Fare clic su di **MyButton** scheda.  
  
     Verrà visualizzato un **MyProject** pulsante, verrà visualizzata la **nuovo progetto** finestra di dialogo.  
  
7.  Chiudere l'istanza sperimentale.  
  
## <a name="applying-the-custom-start-page"></a>L'applicazione della pagina iniziale personalizzata  
  
#### <a name="to-test-the-custom-start-page"></a>Per testare la pagina iniziale personalizzata  
  
1.  In **Strumenti / opzioni / ambiente**selezionare **avvio**. Nel **Personalizza pagina iniziale** elenco, selezionare il file XAML e fare clic su **OK**.  
  
## <a name="next-steps"></a>Passaggi successivi  
 La pagina iniziale di Visual Studio contiene ora una scheda che contiene una scheda del Web browser e una scheda MyButton. È possibile creare pagine iniziali personalizzate che dispongono di altre funzionalità utilizzando il *codice* modello per aggiungere un file dll personalizzato, come illustrato nella [aggiunta controllo utente alla pagina avvio](../extensibility/adding-user-control-to-the-start-page.md). È possibile condividere pagine iniziali personalizzate con altri utenti pubblicando il file VSIX risultante il [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) sito Web o a un altro sito Web o rete condividere. Per ulteriori informazioni, vedere [distribuzione pagine iniziali di personalizzato](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione della pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Controlli contenitore WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)