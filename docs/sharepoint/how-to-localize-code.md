---
title: 'Procedura: localizzare il codice | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 07c9347bbfb42e3c2e20a1b4ecf6d852c567edbf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-localize-code"></a>Procedura: localizzare il codice
  Codice non localizzato Usa i valori stringa hardcoded. Per localizzare le stringhe di codice, sostituirli con chiamate a <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>, che è un metodo che fa riferimento a risorse localizzate.  
  
## <a name="localizing-code"></a>Localizzazione di codice  
  
#### <a name="to-localize-code"></a>Per localizzare il codice  
  
1.  In **Esplora**, aprire il menu di scelta rapida per un elemento di progetto e quindi scegliere **Aggiungi**, **modulo**.  
  
     Scegliere il **File di risorse** modello.  
  
    > [!NOTE]  
    >  Assicurarsi di aggiungere il file di risorse a un elemento di progetto SharePoint in modo che la proprietà del tipo di distribuzione è disponibile. Questa proprietà è necessario più avanti in questa procedura.  
  
2.  Assegnare il file di risorse di lingua predefinita di un nome di propria scelta con estensione resx, ad esempio MyAppResources.  
  
3.  Ripetere i passaggi 1 e 2 per aggiungere file di risorse separati all'elemento di progetto SharePoint, uno per ogni lingua localizzata.  
  
     Utilizzare lo stesso nome di base per ogni file di risorse localizzato, ma è aggiungere l'ID delle impostazioni cultura. Assegnare un nome, ad esempio, una risorsa localizzata tedesca MyAppResources.de-de.  
  
4.  Aprire ogni file di risorse e aggiungere le stringhe localizzate. Utilizzare gli stessi ID di stringa in ogni file.  
  
5.  Modificare il valore della **tipo di distribuzione** proprietà di ogni file di risorse per **AppGlobalResource** in modo che ogni file per cartella App_GlobalResources del server.  
  
6.  Lasciare il valore di **azione di compilazione** proprietà di ogni file come **risorsa incorporata**.  
  
     Le risorse incorporate vengono compilate nella DLL del progetto.  
  
7.  Compilare il progetto per creare la risorsa DLL satellite.  
  
8.  Nel **Progettazione pacchetti**, scegliere il **avanzate** scheda e quindi aggiungere l'assembly satellite.  
  
9. Nel **percorso** casella, anteporre una cartella con l'ID delle impostazioni cultura al percorso, ad esempio de-DE\\*nome di elemento di progetto*. Resources.  
  
10. Se la soluzione non fa già riferimento all'assembly System. Web, aggiungere un riferimento a esso e aggiungere una direttiva nel codice per <xref:System.Web>.  
  
11. Individuare tutte le stringhe hardcoded nel codice visibili agli utenti, ad esempio il testo dell'interfaccia utente, errori e testo del messaggio. Sostituirle con una chiamata al metodo <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> utilizzando la sintassi seguente:  
  
    ```  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. Premere il tasto F5 per compilare ed eseguire l'applicazione.  
  
13. In SharePoint, modificare la lingua di visualizzazione da quello predefinito.  
  
     Le stringhe localizzate visualizzata nell'applicazione. Per visualizzare le risorse localizzate, il server di SharePoint deve disporre di un language pack installati che corrispondono alle impostazioni cultura del file di risorse.  
  
## <a name="see-also"></a>Vedere anche  
 [Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Procedura: localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)   
 [Procedura: localizzare il Markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Procedura: Aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)  
  
  