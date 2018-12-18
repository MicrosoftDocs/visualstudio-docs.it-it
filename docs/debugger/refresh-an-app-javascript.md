---
title: Aggiornare un'app UWP | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: a45564f34fe0167821febb511a023c01f7c38358
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Aggiornare un'app UWP in Visual Studio
  
 È possibile apportare modifiche al codice mentre si sta eseguendo il debug e quindi aggiornarla un'app UWP con JavaScript scegliendo il **Aggiorna applicazione Windows** pulsante il **Debug** barra degli strumenti. Facendo clic su questo pulsante, l'app viene ricaricata senza arrestare e riavviare il debugger. La funzionalità di aggiornamento ti consente di modificare il codice HTML, CSS e JavaScript e visualizzare rapidamente i risultati. Questa funzionalità è supportata per App UWP.  
  
 L'aggiornamento non mantiene lo stato dell'app né riflette le seguenti modifiche nell'app:  
  
-   Modifiche al file manifesto del pacchetto, incluse le modifiche alle immagini specificato nel manifesto di pacchetto.  
  
-   Modifiche dei riferimenti, ad esempio l'aggiunta o la rimozione di un riferimento SDK, o le modifiche ai componenti Windows Runtime (file con estensione winmd).  
  
-   Modifiche delle risorse, ad esempio modifiche alle stringhe nei file con estensione resjson.  
  
-   Modifiche dei file di progetto che causano modifiche dei nomi di percorso, nuovi file di progetto e file eliminati.  
  
-   Modifiche delle proprietà di elementi e progetti, ad esempio modifiche al dispositivo di debug selezionato o modifiche all'azione del pacchetto per un file (nella finestra Proprietà).  
  
> [!IMPORTANT]
>  Quando modifichi i riferimenti, cambi il manifesto del pacchetto o apporti altre modifiche specificate nell'elenco precedente, devi arrestare e riavviare il debugger per aggiornare i file di origine HTML, CSS e JavaScript.  
  
### <a name="to-refresh-an-app"></a>Per aggiornare un'app  
  
1.  Con il progetto UWP aperto in Visual Studio, selezionare **computer locale** come destinazione di debug.
  
     ![Elenco di destinazione di debug selezionare](../debugger/media/js_select_target.png "JS_Select_Target")  
  
3.  Premi F5 per eseguire l'app in modalità debug.  
  
4.  Passa a Visual Studio. 
  
5.  Nella home page dell'app UWP, modificare alcune HTML.
  
7.  Fare clic su di **Aggiorna applicazione Windows** pulsante, che ha un aspetto simile: ![pulsante di aggiornamento Windows app](../debugger/media/js_refresh.png "JS_Refresh"). o premi F4.  
  
8.  Torna all'app. L'app viene ricaricata e aggiornato HTML viene utilizzato per eseguire il rendering dell'app.
  
## <a name="see-also"></a>Vedere anche  
 [Guida introduttiva: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)