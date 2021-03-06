---
title: 'Procedura: localizzare il codice | Microsoft Docs'
description: Informazioni su come localizzare il codice in SharePoint sostituendo le stringhe hardcoded con le chiamate a GetGlobalResourceObject, un metodo che fa riferimento a risorse localizzate.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e76b8cfb2e9fcb513905918bd4ae87524078f6c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931643"
---
# <a name="how-to-localize-code"></a>Procedura: localizzare il codice
  Il codice non localizzato utilizza valori di stringa hardcoded. Per localizzare le stringhe di codice, sostituirle con chiamate a <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> , che è un metodo che fa riferimento a risorse localizzate.

## <a name="localize-code"></a>Localizzare il codice

#### <a name="to-localize-code"></a>Per localizzare il codice

1. In **Esplora soluzioni** aprire il menu di scelta rapida per un elemento del progetto, quindi scegliere **Aggiungi**  >  **modulo**.

     Scegliere il modello **file di risorse** .

    > [!NOTE]
    > Assicurarsi di aggiungere il file di risorse a un elemento del progetto SharePoint in modo che la proprietà tipo di distribuzione sia disponibile. Questa proprietà è obbligatoria più avanti in questa procedura.

2. Assegnare al file di risorse della lingua predefinita un nome a scelta aggiunto con un'estensione *resx* , ad esempio *MyAppResources. resx*.

3. Ripetere i passaggi 1 e 2 per aggiungere file di risorse separati all'elemento di progetto SharePoint, uno per ogni lingua localizzata.

     Usare lo stesso nome di base per ogni file di risorse localizzato, ma aggiungere l'ID delle impostazioni cultura. Ad esempio, assegnare un nome a una risorsa localizzata in tedesco *MyAppResources.de-de. resx*.

4. Aprire ogni file di risorse e aggiungere stringhe localizzate. Utilizzare gli stessi ID di stringa in ogni file.

5. Modificare il valore della proprietà **tipo distribuzione** di ogni file di risorse in **AppGlobalResource** per fare in modo che ogni file venga distribuito nella cartella App_GlobalResources del server.

6. Lasciare il valore della proprietà **operazione di compilazione** di ogni file come **risorsa incorporata**.

     Le risorse incorporate vengono compilate nella DLL del progetto.

7. Compilare il progetto per creare le DLL satellite delle risorse.

8. In **Progettazione pacchetti** scegliere la scheda **Avanzate** , quindi aggiungere l'assembly satellite.

9. Nella casella **percorso** anteporre una cartella ID impostazioni cultura al percorso, ad esempio *de-de \\ \<Project Item Name>.resources.dll*.

10. Se la soluzione non fa già riferimento all'assembly System. Web, aggiungervi un riferimento e aggiungere una direttiva nel codice a <xref:System.Web> .

11. Individuare tutte le stringhe hardcoded nel codice visibili agli utenti, ad esempio il testo dell'interfaccia utente, errori e testo del messaggio. Sostituirle con una chiamata al metodo <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> utilizzando la sintassi seguente:

    ```csharp
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")
    ```

12. Premere il tasto **F5** per compilare ed eseguire l'applicazione.

13. In SharePoint modificare la lingua di visualizzazione dal valore predefinito.

     Le stringhe localizzate vengono visualizzate nell'applicazione. Per visualizzare le risorse localizzate, è necessario che nel server SharePoint sia installato un Language Pack corrispondente alle impostazioni cultura del file di risorse.

## <a name="see-also"></a>Vedi anche
- [Localizzare le soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Procedura: localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)
- [Procedura: localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Procedura: aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)
