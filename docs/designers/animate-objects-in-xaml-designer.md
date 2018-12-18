---
title: Animare oggetti in una finestra di progettazione XAML | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 57aa814ac458fc3c893f8a2d557840d936ed033b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="animate-objects-in-xaml-designer"></a>Animare oggetti in una finestra di progettazione XAML
È possibile creare brevi animazioni per spostare gli oggetti o per applicare agli oggetti la dissolvenza in entrata e in uscita.  
  
 Per iniziare, creare uno *storyboard*. Uno storyboard contiene uno o più *sequenze temporali*. Impostare i *fotogrammi chiave* in una sequenza temporale per contrassegnare le modifiche alle proprietà. Quando poi si esegue l'animazione, Blend interpola le modifiche alle proprietà nel periodo di tempo indicato, garantendo in tal modo una transizione graduale. È possibile aggiungere un'animazione a qualsiasi proprietà che appartiene a un oggetto, anche quelle non visive.  
  
 La figura seguente mostra uno storyboard denominato **MoveUp**. La sequenza temporale contiene fotogrammi chiave che indicano le posizioni X e Y di un rettangolo. Quando si esegue questa animazione, il rettangolo si sposta da una posizione a un altro in modo graduale.  
  
 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")  
  
 Per imparare a creare animazioni, è possibile guardare i video seguenti.  
  
|Breve video:|Procedure incluse:|  
|--------------------------|-------------------|  
|![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Creare sequenze temporali](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|Creare una sequenza temporale e usare gli oggetti nella sequenza temporale.|  
|![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Aggiungere fotogrammi chiave e ripetere l'animazione](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|Aggiungere fotogrammi chiave e impostare le proprietà di ogni fotogramma. Eseguire quindi l'animazione e notare la transizione graduale applicata agli oggetti.|  
|![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Aggiungere trigger di evento per l'interattività](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|Avviare un'animazione quando si verifica un evento, ad esempio quando viene caricata la finestra.|  
|![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Aggiungere un'animazione ai colori](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|Per modificare il colore di un oggetto, usare un'animazione.|  
|![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Creare e modificare i percorsi animazione](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|Animare oggetti lungo un percorso.|  
|![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Semplificare i fotogrammi chiave](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|Velocizzare o rallentare un'animazione nella parte iniziale (*interpolazione con variazione in entrata*) o nella parte finale (*interpolazione con variazione in uscita*) di un'animazione.|  
|![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Aggiungere un'animazione al pulsante](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|Creare effetti interessanti visualizzati su un pulsante quando viene selezionato dall'utente.|  
|![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Creare l'animazione e usare l'interpolazione](https://www.youtube.com/watch?v=mAJXYrwxGYo)|Aggiungere un'animazione agli effetti visualizzati quando un utente fa clic su un pulsante nell'immagine di una calcolatrice.|  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'interfaccia utente usando Blend per Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)