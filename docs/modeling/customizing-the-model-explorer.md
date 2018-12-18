---
title: Personalizzazione di Esplora modelli | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: eac91df1a07e54b80e88538695b1cc22353396d6
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="customizing-the-model-explorer"></a>Personalizzazione di Esplora modelli
È possibile modificare l'aspetto e il comportamento dell'esplorazione per la finestra di progettazione di linguaggio specifico di dominio come indicato di seguito:  
  
-   Modificare il titolo della finestra.  
  
-   Modificare l'icona di scheda.  
  
-   Modificare le icone per i nodi.  
  
-   Nascondere i nodi.  
  
## <a name="changing-the-window-title"></a>Modificare il titolo della finestra  
 Per modificare il titolo della finestra di Esplora generato, selezionare **comportamento Explorer** nel **Esplora DSL**e quindi nel **proprietà** finestra, impostare il  **Titolo** proprietà per il titolo desiderato.  
  
## <a name="changing-the-tab-icon"></a>Modifica dell'icona di scheda  
 Per modificare l'icona della scheda per Esplora risorse, utilizzare un'icona di 16x16 pixel in un file con estensione bmp. Inserire il file dell'icona nella cartella \DslPackage\Resources\ e quindi modificare il nome di file in **ModelExplorerToolWindowBitmaps.bmp**. Ad esempio, è possibile cambiare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] setup.ico icona file in formato BMP e rinominarlo **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. In Progettazione generata verrà visualizzata questa icona nella scheda della finestra di Esplora risorse quando è ancorata assieme **Esplora**.  
  
## <a name="setting-custom-icons-on-explorer-nodes"></a>L'impostazione di icone personalizzate nei nodi di Esplora  
 Utilizzando Esplora nodo Impostazioni, è possibile personalizzare i nodi in Esplora risorse. La procedura seguente viene illustrato come aggiungere un'icona a un nodo.  
  
#### <a name="to-add-an-icon-to-an-explorer-node"></a>Per aggiungere un'icona a un nodo di Esplora  
  
1.  Creare un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] soluzione usando il modello di soluzione del flusso attività.  
  
2.  Inserire un file con estensione bmp contenente un'icona di 16x16 pixel nel **Dsl\Resources** cartella della soluzione.  
  
3.  Nel **Esplora DSL**, fare doppio clic su **comportamento Explorer** e quindi fare clic su **aggiungere nuove impostazioni di Esplora nodo**.  
  
     Un **ExplorerNodeSettings** nodo viene visualizzato sotto il **personalizzato nodo Impostazioni** nodo.  
  
4.  Selezionare **ExplorerNodeSettings**e quindi la **proprietà** finestra, impostare **classe** a **attore**.  
  
5.  Impostare **icona da visualizzare** al percorso del file icona.  
  
6.  Trasforma tutti i modelli, quindi compilare ed eseguire la soluzione.  
  
7.  Nella finestra di progettazione generato, aprire il diagramma di esempio.  
  
     Esplora risorse deve visualizzare tre **attore** i nodi che hanno l'icona.  
  
> [!NOTE]
>  Se è stata impostata un'icona di nodo per qualsiasi elemento che viene visualizzato nella finestra di esplorazione generata, tutti i nodi di Esplora verranno visualizzata l'icona. Se non è stata impostata alcuna icona, i nodi visualizzerà l'icona predefinita.  
  
## <a name="changing-the-name-displayed-on-an-explorer-node"></a>La modifica del nome visualizzato su un nodo di Esplora  
 È possibile modificare la modalità in cui vengono visualizzati i nomi degli elementi del modello in Esplora risorse. La procedura seguente viene illustrato come visualizzare il nome del **attività** a cui fa riferimento un **commento** nel nodo di commento.  
  
#### <a name="to-display-a-property"></a>Per visualizzare una proprietà  
  
1.  Aprire la soluzione creata nella procedura precedente.  
  
2.  Assicurarsi che il **commento** fa riferimento solo una classe di dominio singolo impostando la molteplicità del ruolo con nome di proprietà **soggetti** a 0..1. Il nome della proprietà dovrebbe diventare **soggetto**, e il nome della relazione deve diventare **CommentReferencesSubject**.  
  
3.  Nel **Esplora DSL**, fare doppio clic su **comportamento Explorer** e quindi fare clic su **aggiungere nuove impostazioni di Esplora nodo**.  
  
     Un **ExplorerNodeSettings** nodo viene visualizzato sotto il **personalizzato nodo Impostazioni** nodo.  
  
4.  Selezionare **ExplorerNodeSettings**e quindi il **proprietà** finestra impostare **classe** per **commento**.  
  
5.  Fare doppio clic su di **commento** nodo e quindi fare clic su **aggiunta nuovo percorso di proprietà**.  
  
     Verrà visualizzato un nuovo nodo denominato **proprietà visualizzata**.  
  
6.  Selezionare **proprietà visualizzata**e quindi la **proprietà** finestra, fare clic sul campo valore di **proprietà al percorso**. Selezionare **commento**, quindi **CommentReferencesSubject**, quindi **FlowElement**. Il percorso risulta dovrebbe essere simile **CommentReferencesSubject.Subject/! Oggetto**.  
  
7.  Nel campo del valore **proprietà**selezionare **nome**.  
  
8.  Trasforma tutti i modelli, quindi compilare ed eseguire la soluzione.  
  
9. Nella finestra di progettazione generato, aprire il diagramma di esempio.  
  
10. Disegnare un **connettore commento** tra l'elemento di commento e **Attività1** elemento del diagramma.  
  
     Il nodo di Esplora deve essere visualizzato il commento come **Attività1**.  
  
## <a name="hiding-nodes"></a>Nodi di occultamento  
 È possibile nascondere un nodo in Esplora risorse aggiungendo il percorso per il **nodi nascosti** nodo del **Esplora DSL**. La procedura seguente viene illustrato come nascondere **commento** nodi.  
  
#### <a name="to-hide-an-explorer-node"></a>Per nascondere un nodo Esplora  
  
1.  Aprire la soluzione creata nella procedura precedente.  
  
2.  Nel **Esplora DSL**, fare doppio clic su **comportamento Explorer** e quindi fare clic su **aggiunta nuovo percorso di dominio**.  
  
     Oggetto **il percorso del dominio** nodo viene visualizzato nel **nodi nascosti**.  
  
3.  Selezionare **il percorso del dominio**e quindi la **proprietà** finestra, fare clic sul campo valore di **definizione del percorso**. Selezionare **FlowGraph**, quindi **FlowGraphHasComments**. Il percorso risulta dovrebbe essere simile **FlowGraphHasComments.Comments**  
  
4.  Trasforma tutti i modelli, quindi compilare ed eseguire la soluzione.  
  
5.  Nella finestra di progettazione generato, aprire il diagramma di esempio.  
  
     Le soluzioni devono visualizzare solo un **attori** nodo e non dovrebbe essere mostrato il **commenti** nodo.  
  
## <a name="see-also"></a>Vedere anche

[Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)