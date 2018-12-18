---
title: Aggiungere parametri di contesto a un'impostazione di esecuzione test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 03db08b701574a4e910b96c843d0f2638e71a4f7
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Procedura: aggiungere parametri di contesto a un'impostazione di esecuzione test di carico

Dopo aver creato il test di carico mediante la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le proprietà degli scenari in modo da soddisfare le necessità e gli obiettivi di test specifici.

> [!NOTE]
> Per un elenco completo delle proprietà delle impostazioni esecuzione test e delle relative descrizioni, vedere [Proprietà delle impostazioni esecuzione test di carico](../test/load-test-run-settings-properties.md).

È possibile creare parametri di contesto da utilizzare in un'impostazione di esecuzione del test di carico utilizzando l'Editor test di carico. I parametri di contesto consentono di parametrizzare una stringa.

Si supponga che il test di carico contenga un test delle prestazioni Web che già utilizza un URL di server Web con parametri tramite un parametro di contesto. È possibile aggiungere un parametro di contesto a un'impostazione di esecuzione del test di carico che utilizza lo stesso valore di nome utilizzato nel test delle prestazioni Web. In questo modo il test delle prestazioni Web verrà mappato a un server diverso quando si esegue il test di carico. Ad esempio, se il test di carico include un test delle prestazioni Web che utilizza un parametro di contesto denominato WebServer1 per il nome del server Web nell'URL, se si specifica quindi un parametro di contesto nell'impostazione di esecuzione del test di carico che sia anche denominato WebServer1, il test di carico utilizzerà il parametro di contesto assegnato nell'impostazione di esecuzione del test di carico. In altre parole, se il test delle prestazioni Web incluso nel test di carico utilizza un parametro di contesto con lo stesso nome di un parametro di contesto nel test di carico, il parametro di contesto nel test di carico eseguirà l'override del parametro di contesto utilizzato nel test delle prestazioni Web.

> [!WARNING]
> Prestare attenzione a non eseguire l'override accidentale del parametro di contesto di un test delle prestazioni Web quando si usano parametri di contesto in un'impostazione di esecuzione test. Evitare di utilizzare gli stessi nomi per i parametri di contesto a meno che lo si faccia intenzionalmente.

Se si assegna il valore del parametro di contesto Webserver1 a `http://CorporateStagingWebServer`, è possibile usare `WebServer1` in tutto il test di carico e cambiare facilmente il valore in un altro server Web in qualsiasi momento.

Inoltre, assegnando valori diversi a un parametro di contesto utilizzando lo stesso nome nelle diverse impostazioni di esecuzione del test di carico, è possibile eseguire il test di carico in ambienti diversi:

-   Impostazione di esecuzione test Server Web aziendale di gestione temporanea: il parametro di contesto denominato WebServer1=http://CorporateStagingWebServer

-   Impostazione di esecuzione test Server Web aziendale di produzione: il parametro di contesto denominato WebServer1=http://CorporateProductionWebServer

 **Modifica dell'impostazione di esecuzione test dalla riga di comando**

 Se si desidera utilizzare impostazioni di esecuzione test differenti dalla riga di comando per sfruttare la strategia dei parametri di contesto, utilizzare i comandi seguenti:

 **Set Test.UseRunSetting= CorporateStagingWebServer**

 -e-

 **mstest /testcontainer:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Per aggiungere un parametro di contesto a un'impostazione di esecuzione

1.  Aprire un test di carico.

2.  Espandere la cartella **Impostazioni di esecuzione** nell'albero del test di carico dell'Editor test di carico.

3.  Fare clic con il pulsante destro del mouse sulle impostazioni esecuzione test specifiche a cui si vuole aggiungere un parametro di contesto e scegliere **Aggiungi parametro di contesto**.

     Un nuovo parametro di contesto viene aggiunto alla cartella **Parametri di contesto** nella cartella **Impostazioni di esecuzione** nell'albero del test di carico.

     oppure

     Se le impostazioni esecuzione test già contengono una cartella **Parametri di contesto**, è possibile fare clic con il pulsante destro del mouse sulla cartella e scegliere **Aggiungi parametro di contesto**.

4.  Nella finestra Proprietà modificare il valore di **Nome** nel modo appropriato (ad esempio, WebServer1). Nella finestra Proprietà, modificare **Valore** nel parametro che si vuole usare, ad esempio http://CorporateStagingWebServer.

5.  (Facoltativo) Ripetere i passaggi da 3 a 5 e utilizzare una stringa diversa per la proprietà **Valore**, ad esempio http://CorporateProductionWebServer.

6.  Scegliere quali impostazioni esecuzione test devono essere attive. Aprire il menu di scelta rapida nelle impostazioni esecuzione test e scegliere **Imposta come attivo**.

## <a name="see-also"></a>Vedere anche

- [Configurazione delle impostazioni esecuzione test di carico](../test/configure-load-test-run-settings.md)