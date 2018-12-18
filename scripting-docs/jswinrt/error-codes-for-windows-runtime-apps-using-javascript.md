---
title: Codici di errore per le app di Windows Runtime tramite JavaScript | Microsoft Docs
ms.custom: 
ms.date: 05/10/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- JavaScript, Windows Runtime error codes
- VS.WebClient.Help.APPHOST9601
- VS.WebClient.Help.APPHOST9602
- VS.WebClient.Help.APPHOST9603
- VS.WebClient.Help.APPHOST9604
- VS.WebClient.Help.APPHOST9605
- VS.WebClient.Help.APPHOST9606
- VS.WebClient.Help.APPHOST9607
- VS.WebClient.Help.APPHOST9608
- VS.WebClient.Help.APPHOST9610
- VS.WebClient.Help.APPHOST9611
- VS.WebClient.Help.APPHOST9613
- VS.WebClient.Help.APPHOST9614
- VS.WebClient.Help.APPHOST9615
- VS.WebClient.Help.APPHOST9616
- VS.WebClient.Help.APPHOST9617
- VS.WebClient.Help.APPHOST9618
- VS.WebClient.Help.APPHOST9619
- VS.WebClient.Help.APPHOST9620
- VS.WebClient.Help.APPHOST9623
- VS.WebClient.Help.APPHOST9624
- VS.WebClient.Help.APPHOST9626
ms.assetid: 4c6d4e90-602a-4b56-ae74-3458929da442
caps.latest.revision: "1"
author: erikadoyle
ms.author: edoyle
manager: jken
ms.openlocfilehash: 89b91a3246d0a6e2980459c2c35c7361168bccd4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="error-codes-for-windows-runtime-apps-using-javascript"></a>Codici di errore per le app di Windows Runtime tramite JavaScript
Ecco i codici di errore visualizzati dalla console di Microsoft Visual Studio quando si sviluppano le app di Windows Runtime tramite JavaScript.
  
Errore | Note
----- | -------
APPHOST9601: "Impossibile caricare *remoteURI*. Un'app non può caricare il contenuto web remoto nel contesto locale." | Per altre informazioni su ciò che è consentito nel contesto web, vedere [Caratteristiche e restrizioni in base al contesto](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9602: "'javascript:' è un valore di attributo non valido e verrà ignorato. Non usare 'javascript:' URI nel contesto locale. " | Per motivi di sicurezza, non è possibile usare 'javascript:' URI nel contesto locale. Per altre informazioni su ciò che è consentito nel contesto locale, vedere [Caratteristiche e restrizioni in base al contesto](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9603: "Impossibile caricare il plug-di ActiveX che ha l'ID di classe *classID*.  Le app non possono caricare i controlli ActiveX." | Le app di Windows Runtime tramite JavaScript non supportano ActiveXcontrols di Microsoft personalizzato. Se è necessario un controllo dell'interfaccia utente, usare un controllo web standard, una libreria di controlli, o creare un proprio controllo personalizzato. Se è necessario eseguire la logica personalizzata, creare invece un oggetto di Windows Runtime personalizzato. Per informazioni su altre differenze tra HTML, CSS e JavaScript, vedere [Funzionalità e differenze tra HTML, CSS e JavaScript](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx).
APPHOST9604: "Non è possibile passare a *uri* perché usa una codifica di carattere non valida.  Un'app può passare solo ai file con codifica UTF8." | Tutti gli elementi di HTML, JavaScript e CSS a cui si accede da un Windows Runtime devono essere codificati come Unicode Transformation Format (UTF-8) a 8 bit. Per informazioni su altre differenze tra HTML, CSS e JavaScript, vedere [Funzionalità e differenze tra HTML, CSS e JavaScript](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx).
APPHOST9605: "Non è possibile passare a *targetURI* da *sourceURI* perché l'URI di destinazione è in un'area di sicurezza superiore. Non è possibile passare da una zona con livello di sicurezza inferiore a una zona con un livello di sicurezza maggiore, a meno che non si stia passando a un URI del contesto locale da un URI del contesto web e non si sia registrato l'URI del contesto locale URI con il metodo MSApp.addPublicLocalApplicationUri." | Per altre informazioni, vedere [MSApp.addPublicLocalApplicationUri](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465759.aspx).
APPHOST9606: "Impossibile caricare *uri* perché usa una connessione HTTP ed l'elemento meta ms-https-connections-only è presente. Quando si usa l'elemento meta ms-https-connections-only, sono consentite solo connessioni HTTPS. Usare una connessione HTTPS o, se non è necessaria una connessione protetta, rimuovere l'elemento meta." | Per altre informazioni, vedere [Come richiedere una connessione HTTPS](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx).
APPHOST9607: "Non è possibile avviare l'URI in *uri* a causa di questo errore: *failureCode*." | Manca una risorsa o un file non valido sono le cause più comuni di questo errore.
APPHOST9608: "Non è stato possibile far passare l'app alla pagina vuota about:blankpage a causa di questo errore: *errorCode*." | 
APPHOST9610: "L'app ha riscontrato un errore durante la preparazione per passare a una pagina di errore personalizzata: *errorCode*." |
APPHOST9611: "Non è stato possibile far passare l'app alla pagina di errore personalizzata a causa di questo errore: *errorCode*." |
APPHOST9613: "Non è stato possibile far passare l'app a * uri* a causa di questo errore: *errorCode*." | 
APPHOST9614: "Un documento all'interno di un iframe ha richiesto la modalità di doc *requestedDocMode*, ma il sistema applica la modalità di doc *currentDocMode*. L'iframe userà la modalità di doc *currentDocMode*." | Per altre informazioni sulla visualizzazione del contenuto web remoto, vedere [Come creare collegamenti a pagine web esterne](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx).
APPHOST9615: "L'app non può scaricare il file in *uri* perché è stata richiamata a livello di codice all'esterno del contesto locale." | Si verifica quando il contenuto nel contesto web cerca di eseguire il download di un file a livello di codice.
APPHOST9616: "Questo URI non può usare le API di georilevazione.  Le API di georilevazione possono essere richiamate solo da un URI che fa parte del pacchetto o è incluso nell'elemento ApplicationContentUris del manifesto." | Per altre informazioni su ciò che è consentito nel contesto web, vedere [Caratteristiche e restrizioni in base al contesto](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9617: "Questo URI non può usare le API degli appunti.  Le API degli appunti possono essere richiamate solo da un URI che fa parte del pacchetto o è incluso nell'elemento ApplicationContentUris del manifesto." | Per altre informazioni su ciò che è consentito nel contesto web, vedere [Caratteristiche e restrizioni in base al contesto](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9618: "Questo URI non può usare windows.close.  Il metodo window.close può essere richiamato solo dal contenuto nel pacchetto che è stato caricato con uno schema dell'URI ms-appx." | Per altre informazioni su ciò che è consentito nel contesto web, vedere [Caratteristiche e restrizioni in base al contesto](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9619: "L'app non può passare a *uri* perché una pagina nel contesto web non può essere il documento di livello superiore dell'app. Caricare invece la pagina in un iframe." | Non è possibile passare alla pagina principale di una pagina web remota, ma l'app può visualizzare una pagina web in un [iframe](https://msdn.microsoft.com/en-us/library/ms535258(v=vs.85).aspx). Per altre informazioni sulla visualizzazione del contenuto web remoto, vedere [Come creare collegamenti a pagine web esterne](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx).
APPHOST9620: "Questa app è stata chiusa perché ha usato una connessione HTTP e l'elemento meta ms-https-connections-only è presente. Quando si usa l'elemento meta ms-https-connections-only, sono consentite solo connessioni HTTPS. Usare una connessione HTTPS o, se non è richiesta una connessione protetta, rimuovere l'elemento meta." | Per altre informazioni, vedere [Come richiedere una connessione HTTPS](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx).
APPHOST9623: "L'app non è riuscita a risolvere *url* a causa di questo errore: *errorCode*." | Una causa comune di questo errore è un file mancante.  
APPHOST9624: "L'app non può usare lo script per caricare l'*url* perché l'url avvia un'altra app. Solo l'interazione diretta dell'utente può avviare un'altra app." | Le app non possono avviare altre app direttamente. Le altre app possono essere avviate dall'utente quando l'app implementa alcuni contratti. Per altre informazioni, vedere [Contratti ed estensioni delle app](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh464906.aspx).
APPHOST9626: "è stato rilevato un riferimento diretto al file della risorsa `ms-appx://1d33240b-0b00-40e4-a416-a4750c48787f/ja-jp\images\logo.scale-140.png`. Questo riferimento genera errori quando viene usato al di fuori dell'ambiente di debug." | A causa del percorso del file di `logo.scale-140.png`, questo file PNG viene considerato come una risorsa localizzata, generando l'errore in quanto alle risorse localizzate non si può fare riferimento direttamente. Vedere [Globalizzazione dell'app (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465006.aspx) se si prevede di usare questo file come una risorsa del linguaggio. In caso contrario, provare a rinominare la directory della problematica.
  
## <a name="see-also"></a>Vedere anche  
 [Uso di Windows Runtime in JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)