---
title: Creare applicazioni in lingue bidirezionali | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Hebrew character display, creating applications
- bi-directional language support, about bi-directional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1b0d0010d9aa4c56fdffef2eceb458776a863d23
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="creating-applications-in-bi-directional-languages"></a>Creazione di applicazioni in lingue bidirezionali
È possibile usare Visual Studio per creare applicazioni che visualizzano correttamente il testo nelle lingue scritte da destra a sinistra, tra cui l'arabo e l'ebraico. Per alcune funzionalità basta impostare delle proprietà. In altri casi è necessario implementare le funzionalità nel codice.  
  
> [!NOTE]
>  Per l'immissione e la visualizzazione delle lingue bidirezionali è necessario usare una versione di Windows configurata per la lingua appropriata. Può essere una versione di Windows in inglese con il Language Pack appropriato o una versione di Windows localizzata nella lingua desiderata.  
  
## <a name="types-of-application-that-support-bi-directional-languages"></a>Tipi di applicazioni che supportano le lingue bidirezionali  
  
1.  Applicazioni Windows. È possibile creare applicazioni completamente bidirezionali che includono il supporto per il testo bidirezionale, l'ordine di lettura da destra a sinistra e il mirroring (inversione del layout di finestre, menu, finestre di dialogo e così via). Fatta eccezione per il mirroring, queste funzionalità sono disponibili per impostazione predefinita o come impostazioni di proprietà. Il mirroring è supportato intrinsecamente per alcune funzionalità, ad esempio le finestre di messaggio. In altri casi è invece necessario implementare il mirroring nel codice. Per altre informazioni, vedere [Supporto bidirezionale per le applicazioni Windows Forms](http://msdn.microsoft.com/Library/7b622fa4-f390-4e4d-b624-83a1917cccf2).  
  
2.  Applicazioni Web. I servizi Web supportano l'invio e la ricezione di testo UTF-8 e Unicode, quindi sono adatti per applicazioni con lingue bidirezionali. L'interfaccia utente delle applicazioni Web client è basata sui browser, pertanto il livello di supporto bidirezionale di un'applicazione Web dipende dal grado di supporto delle funzionalità bidirezionali nel browser dell'utente. In Visual Studio è possibile creare applicazioni con supporto per testo in arabo o ebraico, ordine di lettura da destra a sinistra, codifica di file e impostazioni cultura locali. Per altre informazioni, vedere [Supporto bidirezionale per applicazioni Web ASP.NET](http://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).  
  
3.  applicazioni console Le applicazioni console non includono il supporto del testo per le lingue bidirezionali. Questo fatto dipende dall'interazione tra Windows e le applicazioni console.  
  
## <a name="visual-studio-features-that-are-fully-supported"></a>Funzionalità di Visual Studio completamente supportate  
 In fase di progettazione con Visual Studio è possibile usare le lingue bidirezionali nei modi seguenti:  
  
-   **Immissione di testo** Visual Studio supporta Unicode, pertanto, se il sistema è configurato con le impostazioni locali e la lingua di input appropriate, è possibile immettere testo in arabo o ebraico. (Il supporto per l'arabo include le linee kashida e i segni diacritici.)  
  
-   **Nomi degli oggetti** È possibile usare le lingue bidirezionali per assegnare nomi a soluzioni, progetti, file, cartelle e così via. Nel codice è possibile usare le lingue bidirezionali per i nomi di variabili, classi, oggetti, attributi, metadati e altri elementi.  
  
-   **Codifica file** È possibile salvare e aprire file con codifica Unicode o specifica della lingua. Per altre informazioni, vedere [Procedura: salvare e aprire file con codifica](../ide/how-to-save-and-open-files-with-encoding.md).  
  
## <a name="features-with-limited-or-no-support"></a>Funzionalità con supporto limitato o non supportate  
 Altre funzionalità comuni delle applicazioni in lingue bidirezionali non sono completamente supportate in Visual Studio, o in alcuni casi non lo sono affatto. Sono inclusi:  
  
-   **Ordine di lettura da destra a sinistra** Per impostazione predefinita i controlli per l'immissione di testo usati in Visual Studio adottano l'ordine di lettura da sinistra a destra. Nella maggior parte dei casi è possibile cambiare l'ordine di lettura con operazioni standard di Windows. Ad esempio è possibile premere Ctrl+MAIUSC destro per impostare il supporto dell'ordine di lettura da destra a sinistra per i valori delle proprietà nella finestra Proprietà.  
  
     Tuttavia, l'ordine di lettura da destra a sinistra non è supportato ovunque in Visual Studio. Le eccezioni sono le seguenti:  
  
    -   Le caselle di controllo, gli elenchi a discesa e gli altri controlli delle finestre di dialogo di Visual Studio usano sempre l'ordine di lettura da sinistra a destra.  
  
    -   L'editor di codice (e l'editor di testo) non supportano l'ordine di lettura da destra a sinistra. È possibile immettere il testo in una lingua bidirezionale, ma l'ordine di lettura è sempre da sinistra a destra.  
  
## <a name="naming-things-using-arabic-or-hebrew-text"></a>Denominazione di elementi con testo in arabo o ebraico  
 È possibile usare testo in arabo o ebraico per assegnare nomi a cartelle, variabili o altri oggetti. Quando si usa l'arabo è possibile usare qualsiasi carattere incluse le linee kashida e i segni diacritici.  
  
 I seguenti elementi possono essere denominati in arabo o ebraico e vengono gestiti correttamente in Visual Studio:  
  
-   Nomi di soluzioni, progetti e file, incluse le eventuali cartelle incluse nel percorso del progetto. Esplora soluzioni visualizza correttamente i nomi di elementi e soluzioni.  
  
-   Contenuto di file. È possibile aprire o salvare file con codifica Unicode o con una tabella codici selezionata.  
  
    > [!NOTE]
    >  L'editor di codice è un caso a parte. Per informazioni dettagliate, vedere i paragrafi che seguono.  
  
-   Elementi di dati. In **Esplora server** questi elementi vengono visualizzati correttamente e possono essere modificati.  
  
-   Elementi copiati negli Appunti di Windows.  
  
-   Attributi e metadati.  
  
-   Valori delle proprietà. Nella finestra Proprietà è possibile usare testo in arabo o ebraico. La finestra consente di alternare tra l'ordine di lettura da destra a sinistra e da sinistra a destra con combinazioni di tasti standard di Windows (CTRL+MAIUSC destro per l'ordine da destra a sinistra e CTRL+MAIUSC sinistro per l'ordine da sinistra a destra).  
  
-   Codice e testo letterale. Nell'editor di codice (che è anche l'editor di testo) è possibile usare l'arabo o l'ebraico per assegnare nomi a classi, funzioni, variabili, proprietà, valori letterali stringa, attributi e così via. Tuttavia l'editor non supporta l'ordine di lettura da destra a sinistra: il testo inizia sempre sul margine sinistro.  
  
    > [!TIP]
    > È consigliabile inserire i valori letterali stringa nei file di risorse anziché specificarli a livello di codice nei programmi. Per altre informazioni, vedere [Risorse nelle applicazioni desktop (.NET Framework)](/dotnet/framework/resources/index).
  
    > [!NOTE]
    > È necessario mantenere la coerenza nei riferimenti a oggetti denominati in queste lingue. Se ad esempio si usano le linee kashida quando si assegna una variabile in arabo, è sempre necessario usare la notazione kashida nei riferimenti a tale variabile. In caso contrario si verificheranno degli errori.  
  
-   Commenti del codice. È possibile creare commenti in arabo o in ebraico. È possibile usare queste lingue anche nello strumento per la generazione di commenti.  
  
## <a name="see-also"></a>Vedere anche

[Supporto bidirezionale per le Windows Forms Application](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications)  
[Supporto bidirezionale per applicazioni Web ASP.NET](http://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03)  
[Globalizzazione di applicazioni](../ide/globalizing-applications.md)  
[Localizzazione di applicazioni](../ide/localizing-applications.md)