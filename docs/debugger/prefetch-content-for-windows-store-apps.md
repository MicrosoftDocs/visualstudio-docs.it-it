---
title: Eseguire il debug utilizzando il contenuto di prelettura nelle App UWP | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 241937c8462577d6af375d2440efe828a738a8cc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Debug di App UWP con contenuto di prelettura in Visual Studio
  
 Per rendere più la risposta dell'app UWP, è possibile richiedere Windows per precaricare parte del contenuto web, ad esempio immagini o pagine web, all'app [WinINet](http://msdn.microsoft.com/library/0a06f2af-957a-4dff-a8cc-187370181b5c) cache. Questa funzionalità, nota come "caricamento di contenuto in background", È particolarmente utile per il contenuto usato all'avvio, ma è possibile caricare in background altro contenuto usato di frequente, troppo. I metodi del [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) classe consentono di specificare l'URI del contenuto che si desidera precaricare. Vedi il Windows SDK [esempio prelettura di contenuto](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) per esempi relativi all'aggiunta della funzionalità ContentPrefetcher all'app.  
  
 Windows usa le regole euristiche per determinare quando e se caricare contenuto in background e quali risorse verranno scaricate. Le regole euristiche tengono conto delle condizioni di alimentazione e rete del sistema, della cronologia di utilizzo delle app utente e dei risultati dei precedenti tentativi di caricamento in background. In Visual Studio, è possibile utilizzare il **Trigger prelettura App di Windows Store** comando per forzare Windows a ignorare le regole euristiche ContentPrefetcher e a precaricare tutto il contenuto web specificato. Questo può essere utile se desideri testare le prestazioni o il comportamento dell'app con il contenuto da caricare in background in uno stato noto (caricato o meno).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Per forzare il precaricamento delle risorse specificate di ContentPrefetcher  
 Questa procedura presuppone che tu abbia già impostato la funzionalità ContentPrefetcher e specificato gli URI di contenuto da precaricare nel progetto dell'app. Per forzare il precaricamento del contenuto quando le risorse specificate sono nuove o modificate, devi avviare e arrestare l'app prima che venga scelto il **Trigger prelettura App di Windows Store** comando. Prima di tutto esegui l'app per registrare gli URI. **Trigger prelettura applicazioni Windows Store** comando forza la funzionalità ContentPrefetcher a scaricare il contenuto e ad aggiungerlo nella cache. Nelle esecuzioni successive dell'app, puoi presupporre che il contenuto sia stato precaricato.  
  
1.  Avvia l'app per registrare gli URI del contenuto caricati in background con l'app. Nel **Debug** menu, scegliere **Avvia debug** (tasto di scelta rapida: F5).  
  
2.  Nel **Debug** menu, scegliere **Termina debug** (tasto di scelta rapida: MAIUSC + F5).  
  
3.  Nel **Debug** menu, scegliere **altre destinazioni Debug** e quindi scegliere **Trigger prelettura App di Windows Store**.  
  
 Ora puoi eseguire testare, analizzare o eseguire il debug dell'app con le risorse Web caricate in background.  
  
> [!NOTE]
>  Ripeti questi passaggi quando aggiungi o modifichi il contenuto Web specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Post di blog: trigger prelettura per applicazioni Windows Store in Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)