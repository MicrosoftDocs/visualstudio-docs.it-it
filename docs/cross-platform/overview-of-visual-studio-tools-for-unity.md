---
title: Panoramica di Visual Studio Tools per Unity |Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: "4"
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload: unity
ms.openlocfilehash: d7d692ba1ee1bf2eb0fda5430b2576edc9646ebf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="overview-of-visual-studio-tools-for-unity"></a>Panoramica di Visual Studio Tools per Unity
Questa sezione contiene altre informazioni sulle funzionalità offerte da Visual Studio Tools per Unity e su come usarle per incrementare la produttività con Unity.  

 Con Visual Studio Tools per Unity (*VSTU*) è possibile usare Visual Studio per scrivere script di giochi ed editor in C# e quindi usare il debugger avanzato per individuare e correggere gli errori. La versione più recente di VSTU include la colorazione della sintassi per il linguaggio ShaderLab di Unity, un'ottimizzazione delle visualizzazioni del debugger e un miglioramento nella generazione del codice per la procedura guidata MonoBehavior. VSTU integra anche i file di progetto Unity, i messaggi della console e la possibilità di iniziare il gioco in Visual Studio evitando in tal modo di dover passare dall'editor di Unity a Visual Studio e viceversa durante la scrittura del codice.  

 Per altre informazioni su queste funzionalità, continuare a leggere questa pagina.  

## <a name="integration-with-unity"></a>Integrazione con Unity  
 Visual Studio Tools per Unity non sarebbe così utile per la produttività se fosse necessario passare in continuazione dall'editor di Unity a Visual Studio e viceversa. Ecco perché Visual Studio Tools per Unity semplifica la possibilità di continuare a lavorare senza uscire da Visual Studio.  

-   **Esplora progetti Unity** visualizza l'intero progetto Unity all'interno di Visual Studio usando la stessa gerarchia visualizzata nell'editor di Unity.  

-   L'integrazione della console di Unity permette di visualizzare l'output della console direttamente all'interno della finestra degli errori di Visual Studio.  

-   È possibile avviare il debug del gioco da Visual Studio senza alcuna necessità di tornare a Unity, semplicemente premendo F5.  

## <a name="superior-debugging"></a>Debug di livello superiore  
 Connettere il potente debugger di Visual Studio al gioco Unity per eseguire il debug degli script e delle DLL C#, indipendentemente dal fatto che venga eseguito in modo autonomo o nell'editor di Unity. È possibile usare tutte le funzionalità di debug usate normalmente in Visual Studio.  

-   Punti di interruzione, anche condizionali.  

-   Valutazione di espressioni complesse nella finestra Espressioni di controllo.  

-   Controllo e modifica del valore di variabili e argomenti.  

-   Drill down in strutture di dati e oggetti complessi.  

 È persino possibile completare il debug del gioco Unity mentre questo viene eseguito in un altro computer o nella rete.  

## <a name="productivity"></a>Produttività  
 Oltre alla collaudata produttività di Visual Studio per la scrittura e il refactoring del codice in C#, Visual Studio Tools per Unity offre agli sviluppatori di Unity funzionalità aggiuntive per la produttività.  

-   La colorazione della sintassi per il linguaggio ShaderLab di Unity aiuta a individuare gli errori negli shader prima che diventino bug. È sufficiente aprire i file ShaderLab in Visual Studio.  

-   La procedura guidata MonoBehavior permette di esplorare un elenco di comportamenti di Unity e di creare codice boilerplate per i comportamenti meno familiari. Premere CTRL+MAIUSC+M.  

-   Una volta acquisita familiarità con i comportamenti di Unity usati più spesso, la procedura guidata rapida MonoBehavior permette di accedervi in tutta semplicità. Premere CTRL+ALT+Q.  

-   È possibile accedere alla documentazione di Unity da Visual Studio. È sufficiente evidenziare la chiamata API su cui si vogliono ottenere informazioni e quindi premere CTRL+ALT+M, CTRL+H.  

-   È possibile accedere a tutte le funzionalità e ad altro ancora usando i tasti di scelta rapida.  

## <a name="visual-studio-tools-for-unity-api"></a>API di Visual Studio Tools per Unity  
 Le API fornite permettono di personalizzare ed estendere il comportamento di Visual Studio Tools per Unity.  

-   Visual Studio Tools per Unity registra un callback di log in modo da poter eseguire la console di Unity in Visual Studio. Se sono presenti script di editor che registrano informazioni, è possibile inserirli nello stesso callback per inviare i messaggi a Visual Studio. Per altre informazioni, vedere l'esempio di callback di log.  

-   È possibile modificare il modo in cui Visual Studio Tools per Unity genera file di progetto usando il callback in stile Unity ProjectFileGeneration. Per altre informazioni, vedere l'esempio di generazione di file di progetto.  

## <a name="see-also"></a>Vedere anche  
 [Home page di Unity](http://unity3d.com)
