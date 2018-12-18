---
title: Aggiornamento dei test codificati dell'interfaccia utente da Visual Studio 2010 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 1af9c5634770b08b7903033226f44630bdb0e133
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Aggiornamento dei test codificati dell'interfaccia utente da Visual Studio 2010
I progetti di test contenenti test codificati dell'interfaccia utente creati in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 vengono ripristinati in modo invisibile all'utente all'apertura in Visual Studio 2012 o versioni successive. Se i progetti di test vengono archiviati nel controllo del codice sorgente, i file di progetto vengono estratti per questo ripristino. Una volta ripristinati, questi progetti di test contenenti test codificati dell'interfaccia utente possono essere usati sia in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 che in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
 **Requisiti**  
  
-   Visual Studio Enterprise  
  
> [!NOTE]
> Visual Studio include più di un tipo di progetto di test. Un nuovo test codificato dell'interfaccia utente verrà creato in un tipo di progetto di test codificato dell'interfaccia utente.
  
> [!WARNING]
>  I progetti di test di[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] contenenti test codificati dell'interfaccia utente devono essere ricompilati quando li si apre in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] o in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] affiancato a [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
> [!WARNING]
>  Quando un progetto di test creato in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] e contenente solo unit test viene aperto in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], non è possibile aggiungervi test codificati dell'interfaccia utente. Analogamente, non è possibile aggiungere un test codificato dell'interfaccia utente a un progetto di unit test creato in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012-or-later"></a>Problemi di compatibilità tra Visual Studio 2010 e Visual Studio 2012 o versioni successive  
 La seguente tabella elenca i problemi da tenere in considerazione quando si esegue la migrazione dei test codificati dell'interfaccia utente tra [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] e [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
> [!CAUTION]
>  Esiste un problema noto relativo ai riferimenti nei progetti di test codificati dell'interfaccia utente non visualizzati in Esplora soluzioni. Per altre informazioni, vedere il file leggimi incluso nel supporto di installazione di [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] .  
  
|Funzionalità interfaccia utente codificata|Problema|Soluzione|  
|----------------------------|-----------|--------------|  
|Il test dell'interfaccia utente di Silverlight non è supportato in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|**La compilazione avrà esito negativo**<br /><br /> Se si dispone di [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2 e sono stati creati progetti di test codificato dell'interfaccia utente per applicazioni Silverlight, questi progetti non possono essere aperti in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|È consigliabile gestirli solo in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2.|  
|Il test dell'interfaccia utente di Firefox non è supportato in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|**La compilazione avrà esito positivo, l'esecuzione del test avrà esito negativo**<br /><br /> Se si dispone di [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2 e sono stati creati progetti di test codificato dell'interfaccia utente per applicazioni Web in Firefox, questi progetti non possono essere aperti in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|È consigliabile gestirli solo in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2.|  
|In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]sono state aggiunte nuove API di test del codice dell'interfaccia utente|**La compilazione avrà esito negativo**<br /><br /> Se si creano test codificati dell'interfaccia utente usando la nuova API di test dell'interfaccia utente in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], questi progetti non possono essere aperti in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].|I progetti che usano la nuova API devono essere gestiti solo in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] .|  
|In [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] sono stati aggiunti riferimenti all'interno di un'istruzione 'Choose' nel file csproj. In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], un file di destinazioni di feedback viene utilizzato per includere i riferimenti ad assembly di test codificato dell'interfaccia utente.|In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], un test codificato dell'interfaccia utente non può essere aggiunto a un progetto di test creato in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] (o SP1) che non conteneva un test codificato dell'interfaccia utente.<br /><br /> Il processo di ripristino aggiunge il file di destinazioni e l'istruzione Choose. Se un test codificato dell'interfaccia utente non è nel progetto di test, il progetto viene contrassegnato come ripristinato e i riferimenti appropriati non verranno aggiunti quando si aggiungerà il test codificato dell'interfaccia utente in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|Sarà necessario creare un nuovo progetto di test nella stessa soluzione usando [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] e aggiungervi il nuovo test codificato dell'interfaccia utente. In alternativa, è possibile aggiungere i test codificati dell'interfaccia utente nel progetto di test in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 e aprirlo in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|  
  
##  <a name="UpgradingCodedUIFromVS2010_Update"></a> Aggiornamento di Visual Studio 2010 SP1  
 Un aggiornamento a [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] SP1 con il supporto di compatibilità per Visual Studio 2012 o versioni successive e Windows 8 o versioni successive è disponibile per il download nell'[Area download Microsoft](http://www.microsoft.com/download/details.aspx?id=34677) nonché come aggiornamento di Visual Studio.  
  
 Dopo avere applicato l'aggiornamento, le seguenti funzionalità dello strumento di test codificati dell'interfaccia utente [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] SP1 vengono aggiornate per Windows 8:  
  
-   È possibile eseguire un test codificato dell'interfaccia utente per i controlli WPF (Windows Presentation Foundation) basati su Microsoft .NET Framework 4.5 in un computer che esegue Windows 8.  
  
-   È possibile eseguire un test codificato dell'interfaccia utente per Internet Explorer 10 a 64 bit (x64) in un computer che esegue Windows 8.  
  
 L'aggiornamento contiene anche le correzioni per i seguenti problemi:  
  
-   **Copertura codice:** impossibilità di aprire un file di code coverage (con estensione coverage) creato da Visual Studio 2012 SP1 in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] .  
  
-   **Elementi di test bloccati:** il team dispone di un elemento di test assegnato a un utente non valido in Team Foundation Server (TFS) 2010. Ad esempio, un utente ha lasciato l'azienda, ma un test case è ancora assegnato a lui. Eseguire l'aggiornamento di TFS 2010 a TFS 2012. Utilizzare [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 2010 per connettersi al server TFS aggiornato. Non è possibile assegnare l'elemento di test ad alcuni utenti TFS utilizzando [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 2010.  
  
-   **Test di carico:** quando si esegue un test di carico con un tipo di rete diverso dal profilo della rete locale (LAN) in un computer che esegue Windows 8, il driver dell'emulatore di rete causa l'arresto anomalo del sistema operativo. Per altre informazioni, vedere l' [articolo KB 2736182](http://support.microsoft.com/kb/2736182).  
  
## <a name="see-also"></a>Vedere anche

[Portabilità, migrazione e aggiornamento dei progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)  
[Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)  
[Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
