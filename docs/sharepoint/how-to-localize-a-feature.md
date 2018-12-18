---
title: 'Procedura: localizzare una funzionalità | Documenti Microsoft'
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
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 08756ce33d97e156d63fd873c63d4d6fc282285b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-localize-a-feature"></a>Procedura: localizzare una funzionalità
  Per impostazione predefinita, le descrizioni e i titoli di funzionalità utilizzano i valori stringa hardcoded. Per localizzare il titolo della funzionalità e la descrizione, sostituire le stringhe con espressioni che fanno riferimento alle risorse localizzate.  
  
## <a name="localizing-a-feature"></a>Localizzazione di una funzionalità  
  
#### <a name="to-localize-a-feature"></a>Per localizzare una funzionalità  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il **Feature1** nodo, quindi scegliere **Aggiungi risorsa funzionalità**.  
  
2.  Nel **Aggiungi risorsa** finestra di dialogo scegliere **lingua invariante** dall'elenco come impostazioni cultura per il file di risorse funzionalità lingua predefinita.  
  
3.  Ripetere il passaggio precedente per ogni lingua localizzata, selezionando le lingue desiderate per i file di risorse della funzionalità localizzati.  
  
     Vengono creati file di risorse di funzionalità separati, uno per la lingua predefinita e uno per ogni lingua localizzata da supportare.  
  
4.  Aprire ogni file di risorse nell'Editor risorse e immettere tutti gli ID di stringa e i relativi valori.  
  
     Ad esempio, nel file di risorse della funzionalità predefinito, immettere un ID di stringa di **titolo** con un valore di **My Feature Title**, e una seconda stringa di ID di **descrizione** con un valore di **My Feature Description**. Per ogni file di risorse localizzato, utilizzare gli stessi ID di stringa utilizzati nella risorsa della funzionalità predefinita, ma immettere stringhe localizzate per i valori.  
  
5.  Dopo avere immesso tutti i valori delle risorse, aprire il menu di scelta rapida per la funzionalità (ad esempio Feature1. feature) e quindi scegliere **Visualizza finestra di progettazione** per aprire la funzionalità in Progettazione funzionalità.  
  
6.  Per localizzare il **titolo** e **descrizione** campi nella funzionalità, utilizzare il formato seguente per immettere i valori desiderati nelle rispettive caselle:  
  
     `$Resources:` *ID stringa*  
  
     Ad esempio, immettere $Resources:**titolo** nel **Feature Title** casella e $Resources:**descrizione** nel **descrizione delle funzionalità** casella .  
  
     Gli ID di stringa devono corrispondere a quelli utilizzati nei file di risorse.  
  
7.  Premere il tasto F5 per compilare ed eseguire l'applicazione.  
  
8.  In SharePoint, aprire il **Azioni sito** dal menu scegliere **Impostazioni sito**, quindi il **Azioni sito** sezione scegliere il **Gestisci caratteristiche sito** collegamento.  
  
9. In SharePoint, modificare la lingua di visualizzazione da quello predefinito.  
  
     Il titolo della funzionalità localizzati e la descrizione visualizzata nell'applicazione. Per visualizzare le risorse localizzate, il server di SharePoint deve disporre di un language pack installati che corrispondono alle impostazioni cultura del file di risorse.  
  
## <a name="see-also"></a>Vedere anche  
 [Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Procedura: aggiungere un File di risorse](../sharepoint/how-to-add-a-resource-file.md)   
 [Procedura: localizzare il Markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Procedura: Localizzare il codice](../sharepoint/how-to-localize-code.md)  
  
  